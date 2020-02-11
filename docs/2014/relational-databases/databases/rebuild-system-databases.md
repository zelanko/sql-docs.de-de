---
title: Neuerstellen von Systemdatenbanken | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
helpviewer_keywords:
- master database [SQL Server], rebuilding
- REBUILDDATABASE parameter
- rebuilding databases, master
- system databases [SQL Server], rebuilding
ms.assetid: af457ecd-523e-4809-9652-bdf2e81bd876
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: b58378e8ba2193a186fb58e3e784bf9bc3cb4d4c
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "62871277"
---
# <a name="rebuild-system-databases"></a>Neuerstellen von Systemdatenbanken
  System Datenbanken müssen neu erstellt werden, um Beschädigungs Probleme in den System Datenbanken [Master](master-database.md), [Model](model-database.md), [msdb](msdb-database.md)oder [Resource](resource-database.md) zu beheben oder die Standardsortierung auf Serverebene zu ändern. Dieses Thema enthält schrittweise Anweisungen für die Neuerstellung von Systemdatenbanken in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].  
  
 **In diesem Thema**  
  
-   **Vorbereitungen:**  
  
     [Einschränkungen](#Restrictions)  
  
     [Voraussetzungen](#Prerequisites)  
  
-   **Abläufen**  
  
     [Neuerstellen von Systemdatenbanken](#RebuildProcedure)  
  
     [Erneutes Erstellen der Ressourcendatenbank](#Resource)  
  
     [Erstellen einer neuen msdb-Datenbank](#CreateMSDB)  
  
-   **Zur Nachverfolgung:**  
  
     [Beheben von Fehlern bei der Neuerstellung](#Troubleshoot)  
  
##  <a name="BeforeYouBegin"></a> Vorbereitungen  
  
###  <a name="Restrictions"></a> Einschränkungen  
 Bei der Neuerstellung der Systemdatenbanken master, model, msdb und tempdb werden die Datenbanken abgelegt und an ihrem ursprünglichen Speicherort neu erstellt. Wenn in der REBUILD-Anweisung eine neue Sortierung angegeben wird, werden die Systemdatenbanken unter Verwendung dieser Sortiereinstellung erstellt. Alle Benutzeränderungen an diesen Datenbanken gehen verloren. Beispielsweise kann die master&lt;/ -Datenbank benutzerdefinierte Objekte, die msdb&lt;/ -Datenbank geplante Aufträge und die model&lt;/ -Datenbank Änderungen der Standardeinstellungen für Datenbanken enthalten.  
  
###  <a name="Prerequisites"></a> Voraussetzungen  
 Führen Sie die folgenden Aufgaben aus, bevor Sie die Systemdatenbanken neu erstellen, um sicherzustellen, dass Sie die Systemdatenbanken mit ihren aktuellen Einstellungen wiederherstellen können.  
  
1.  Zeichnen Sie alle serverweiten Konfigurationswerte auf.  
  
    ```  
    SELECT * FROM sys.configurations;  
    ```  
  
2.  Zeichnen Sie alle auf die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Instanz angewendeten Service Packs und Hotfixes sowie die aktuelle Sortierung auf. Sie müssen diese Updates erneut ausführen, nachdem Sie die Systemdatenbanken neu erstellt haben.  
  
    ```  
    SELECT  
    SERVERPROPERTY('ProductVersion ') AS ProductVersion,  
    SERVERPROPERTY('ProductLevel') AS ProductLevel,  
    SERVERPROPERTY('ResourceVersion') AS ResourceVersion,  
    SERVERPROPERTY('ResourceLastUpdateDateTime') AS ResourceLastUpdateDateTime,  
    SERVERPROPERTY('Collation') AS Collation;  
    ```  
  
3.  Zeichnen Sie den aktuellen Speicherort aller Daten und Protokolldateien für die Systemdatenbanken auf. Durch die erneute Erstellung der Systemdatenbanken werden alle Systemdatenbanken an ihrem ursprünglichen Speicherort installiert. Wenn Sie Systemdatenbank-Daten oder Protokolldateien an einen anderen Speicherort verschoben haben, müssen Sie die Dateien erneut verschieben.  
  
    ```  
    SELECT name, physical_name AS current_file_location  
    FROM sys.master_files  
    WHERE database_id IN (DB_ID('master'), DB_ID('model'), DB_ID('msdb'), DB_ID('tempdb'));  
    ```  
  
4.  Suchen Sie die aktuelle Sicherung der Datenbanken master, model und msdb.  
  
5.  Wenn die Instanz von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] als Replikationsverteiler konfiguriert ist, suchen Sie die aktuelle Sicherung der Verteilungsdatenbank.  
  
6.  Stellen Sie sicher, dass Sie die geeigneten Berechtigungen haben, um die Systemdatenbanken neu zu erstellen. Um diesen Vorgang ausführen zu können, müssen Sie Mitglied der festen Serverrolle `sysadmin` sein. Weitere Informationen finden Sie unter [Rollen auf Serverebene](../security/authentication-access/server-level-roles.md).  
  
7.  Überprüfen Sie, ob Kopien der Daten und Protokollvorlagendateien der Datenbanken master, model und msdb auf dem lokalen Server vorhanden sind. Der Standardspeicherort für die Vorlagendateien ist C:\Programme\Microsoft SQL Server\MSSQL12.MSSQLSERVER\MSSQL\Binn\Vorlagen. Diese Dateien werden während der Neuerstellung verwendet und müssen vorhanden sein, um Setup erfolgreich ausführen zu können. Wenn sie fehlen, führen Sie die Reparaturfunktion von Setup aus, oder kopieren Sie die Dateien manuell vom Installationsmedium. Um die Dateien auf dem Installationsmedium zu suchen, navigieren Sie zum entsprechenden Plattformverzeichnis (x86 oder x64) und dann zu setup\sql_engine_core_inst_msi\Pfiles\SqlServr\MSSQL.X\MSSQL\Binn\Vorlagen.  
  
##  <a name="RebuildProcedure"></a>Neuerstellen von System Datenbanken  
 Mit der folgenden Vorgehensweise werden die Systemdatenbanken master, model, msdb und tempdb  neu erstellt. Sie können die Systemdatenbanken, die neu erstellt werden sollen, nicht angeben. Für gruppierte Instanzen muss diese Vorgehensweise für den aktiven Knoten ausgeführt werden, und die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Ressource in der entsprechenden Clusteranwendungsgruppe muss zuvor offline geschaltet werden.  
  
 Durch diese Vorgehensweise wird die Ressourcendatenbank nicht neu erstellt. Führen Sie hierzu die Schritte im Abschnitt "Vorgehensweise zum Neuerstellen der resource-Datenbank" weiter unten in diesem Thema aus.  
  
#### <a name="to-rebuild-system-databases-for-an-instance-of-sql-server"></a>So erstellen Sie Systemdatenbanken für eine Instanz von SQL Server neu  
  
1.  Legen Sie das [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] -Installationsmedium in das Laufwerk ein, oder wechseln Sie an einer Eingabeaufforderung zum Speicherort der Datei setup.exe auf dem lokalen Server. Der Standardspeicherort auf dem Server ist C:\Programme\Microsoft SQL Server\120\Setup Bootstrap\Release.  
  
2.  Geben Sie den folgenden Befehl in das Eingabeaufforderungsfenster ein. Die eckigen Klammern zeigen optionale Parameter an. Geben Sie den Befehl ohne die eckigen Klammern ein. Wenn Sie Windows als Betriebssystem verwenden und die Benutzerkontensteuerung aktiviert ist, sind für die Ausführung des Setups erhöhte Rechte erforderlich. Die Eingabeaufforderung muss als Administrator ausgeführt werden.  
  
     `Setup /QUIET /ACTION=REBUILDDATABASE /INSTANCENAME=InstanceName /SQLSYSADMINACCOUNTS=accounts [ /SAPWD= StrongPassword ] [ /SQLCOLLATION=CollationName]`  
  
    |Parametername|BESCHREIBUNG|  
    |--------------------|-----------------|  
    |/QUIET oder /Q|Gibt an, dass Setup ohne Benutzeroberfläche ausgeführt wird.|  
    |/ACTION=REBUILDDATABASE|Gibt an, dass die Systemdatenbanken vom Setup neu erstellt werden.|  
    |/InstanceName =*instanceName*|Der Name der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Instanz. Geben Sie MSSQLSERVER für die Standardinstanz ein.|  
    |/SQLSYSADMINACCOUNTS=*accounts*|Gibt die Windows-Gruppen oder die individuellen Konten an, die der festen Serverrolle `sysadmin` hinzugefügt werden sollen. Wenn Sie mehr als ein Konto angeben, trennen Sie die Konten mit einem Leerzeichen. Geben Sie z.B. **BUILTIN\Administrators MyDomain\MyUser**ein. Wenn Sie ein Konto angeben, dessen Name ein Leerzeichen enthält, setzen Sie den Kontonamen in doppelte Anführungszeichen. Geben Sie z. B. Folgendes ein: `NT AUTHORITY\SYSTEM`.|  
    |[ /SAPWD=*StrongPassword* ]|Gibt das Kennwort für [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] `sa` das Konto an. Dieser Parameter ist erforderlich, wenn die Instanz den gemischten Authentifizierungsmodus ([!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] - und Windows-Authentifizierung) verwendet.<br /><br /> ** \* \* Sicherheits \* Hinweis** Das `sa` Konto ist ein bekanntes [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Konto, das häufig von böswilligen Benutzern betroffen ist. Es ist sehr wichtig, dass Sie ein sicheres Kennwort für die `sa`-Anmeldung verwenden.<br /><br /> Geben Sie diesen Parameter nicht für den Windows-Authentifizierungsmodus an.|  
    |[ /SQLCOLLATION=*CollationName* ]|Gibt eine neue Sortierung auf Serverebene an. Dieser Parameter ist optional. Wenn keine Sortierung angegeben wird, wird die aktuelle Sortierung des Servers verwendet.<br /><br /> ** \* Wichtig \* \* ** Durch das Ändern der Sortierung auf Serverebene wird die Sortierung vorhandener Benutzer Datenbanken nicht geändert. Alle neu erstellten Benutzerdatenbanken verwenden standardmäßig die neue Sortierung.<br /><br /> Weitere Informationen finden Sie unter [Festlegen oder Ändern der Serversortierung](../collations/set-or-change-the-server-collation.md).|  
  
3.  Wenn Setup die Neuerstellung der Systemdatenbanken abgeschlossen hat, wechselt es ohne Meldungen zur Eingabeaufforderung zurück. Lesen Sie die Protokolldatei Summary.txt, um zu überprüfen, ob der Prozess erfolgreich abgeschlossen wurde. Diese Datei befindet sich unter C:\Programme\Microsoft SQL Server\120\Setup Bootstrap\Logs.  
  
## <a name="post-rebuild-tasks"></a>Aufgaben nach der Neuerstellung  
 Nach der Neuerstellung der Datenbank müssen Sie möglicherweise die folgenden zusätzlichen Aufgaben ausführen:  
  
-   Stellen Sie die letzten vollständigen Sicherungen der Datenbanken master, model und msdb wieder her. Weitere Informationen finden Sie unter [Sichern und Wiederherstellen von Systemdatenbanken &#40;SQL Server&#41;](../backup-restore/back-up-and-restore-of-system-databases-sql-server.md).  
  
    > [!IMPORTANT]  
    >  Wenn Sie die Serversortierung geändert haben, stellen Sie die Systemdatenbanken nicht wieder her. Auf diese Weise wird die neue Sortierung durch die vorherige Sortiereinstellung ersetzt.  
  
     Wenn keine Sicherung verfügbar ist oder wenn die wiederhergestellte Sicherung nicht aktuell ist, erstellen Sie alle fehlenden Einträge neu. Erstellen Sie z.B. alle fehlenden Einträge für die Benutzerdatenbanken, Sicherungsmedien, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Anmeldenamen, Endpunkte usw. neu. Die beste Möglichkeit zur Neuerstellung der Einträge besteht darin, die ursprünglichen Skripts auszuführen, mit denen sie erstellt wurden.  
  
> [!IMPORTANT]  
>  Es wird empfohlen, Skripts vor unerlaubtem Zugriff zu schützen. Auf diese Weise können Sie verhindern, dass sie von nicht autorisierten Personen geändert werden.  
  
-   Sie müssen die Verteilungsdatenbank wiederherstellen, wenn die Instanz von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] als Replikationsverteiler konfiguriert ist. Weitere Informationen finden Sie unter [Sichern und Wiederherstellen von replizierten Datenbanken](../replication/administration/back-up-and-restore-replicated-databases.md).  
  
-   Verschieben Sie die Systemdatenbanken an die Speicherorte, die Sie zuvor aufgezeichnet haben. Weitere Informationen finden Sie unter [Verschieben von Systemdatenbanken](system-databases.md).  
  
-   Überprüfen Sie, ob die serverweiten Konfigurationswerte zu den Werten passen, die Sie zuvor aufgezeichnet haben.  
  
##  <a name="Resource"></a>Erneutes Erstellen der Ressourcendatenbank  
 Mit der folgenden Vorgehensweise wird die Ressourcensystemdatenbank neu erstellt. Wenn Sie die Ressourcendatenbank neu erstellen, gehen alle Service Packs und Hotfixes verloren und müssen daher noch einmal angewendet werden.  
  
#### <a name="to-rebuild-the-resource-system-database"></a>So erstellen Sie die Systemdatenbank "resource" neu  
  
1.  Starten Sie von den Installationsmedien das [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] -Setupprogramm (setup.exe).  
  
2.  Klicken Sie im linken Navigationsbereich auf **Wartung**und dann auf **Reparieren**.  
  
3.  Es werden Unterstützungsregeln für Setup und Dateiroutinen ausgeführt, um sicherzustellen, dass die erforderlichen Komponenten auf dem System installiert sind und dass der Computer den Setupüberprüfungsregeln erfüllt. Klicken Sie zum Fortsetzen auf **OK** oder auf **Installieren** .  
  
4.  Wählen Sie auf der Seite Instanz auswählen die zu reparierende Instanz aus, und klicken Sie dann zum auf **Weiter**, um den Vorgang fortzusetzen.  
  
5.  Die Reparaturregeln werden ausgeführt, um den Vorgang zu überprüfen. Klicken Sie auf **Weiter**, um den Vorgang fortzusetzen.  
  
6.  Klicken Sie auf der Seite **Bereit zum Reparieren** auf **Reparieren**. Wenn die Seite Abgeschlossen angezeigt wird, wurde der Vorgang abgeschlossen.  
  
##  <a name="CreateMSDB"></a>Erstellen einer neuen msdb-Datenbank  
 Wenn die `msdb` Datenbank beschädigt ist und Sie nicht über eine Sicherung der- `msdb` Datenbank verfügen, können Sie mit dem `msdb` **instmsdb** -Skript eine neue erstellen.  
  
> [!WARNING]  
>  Durch das `msdb` erneute Erstellen der Datenbank mit dem **instmsdb** -Skript werden alle in `msdb` gespeicherten Informationen, wie z. b. Aufträge, Warnungen, Operatoren, Wartungspläne, Sicherungs Verlauf, Einstellungen der Richtlinien basierten Verwaltung, Datenbank-E-Mail, Leistungs Data Warehouse usw., vermieden.  
  
1.  Beenden Sie alle Dienste, die mit [!INCLUDE[ssDE](../../includes/ssde-md.md)]verbunden sind, einschließlich dem [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Agent, [!INCLUDE[ssRS](../../includes/ssrs.md)], [!INCLUDE[ssIS](../../includes/ssis-md.md)]und allen Anwendungen, die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] als Datenspeicher verwenden.  
  
2.  Starten Sie [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] über die Befehlszeile mit dem Befehl: `NET START MSSQLSERVER /T3608`  
  
     Weitere Informationen finden Sie unter [Starten, Beenden, Anhalten, Fortsetzen und Neustarten von SQL Server-Diensten](../../database-engine/configure-windows/start-stop-pause-resume-restart-sql-server-services.md).  
  
3.  Trennen Sie die `msdb` Datenbank in einem anderen Befehlszeilenfenster, indem Sie den folgenden Befehl ausführen und dabei * \<Servername>* durch die Instanz [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]von ersetzen:`SQLCMD -E -S<servername> -dmaster -Q"EXEC sp_detach_db msdb"`  
  
4.  Benennen Sie die `msdb` Datenbankdateien mithilfe von Windows-Explorer um. Diese befinden sich standardmäßig im Unterordner DATA der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Instanz.  
  
5.  Verwenden Sie den [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Konfigurations-Manager zum Beenden und erneuten Starten des [!INCLUDE[ssDE](../../includes/ssde-md.md)] -Diensts.  
  
6.  Stellen Sie in einem Befehlszeilenfenster eine Verbindung mit [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] her, und führen Sie folgenden Befehl aus: `SQLCMD -E -S<servername> -i"C:\Program Files\Microsoft SQL Server\MSSQL12.MSSQLSERVER\MSSQL\Install\instmsdb.sql" -o" C:\Program Files\Microsoft SQL Server\MSSQL12.MSSQLSERVER\MSSQL\Install\instmsdb.out"`  
  
     Ersetzen * \<Sie Servername>* durch die Instanz von [!INCLUDE[ssDE](../../includes/ssde-md.md)]. Verwenden Sie den Dateisystempfad der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Instanz.  
  
7.  Öffnen Sie die Datei **instmsdb.out** im Windows-Editor, und prüfen Sie, ob die Ausgabe fehlerfrei ist.  
  
8.  Wenden Sie alle installierten Service Packs und Hotfixes auf die Instanz an.  
  
9. Erstellen Sie den in der `msdb` Datenbank gespeicherten Benutzer Inhalt, z. b. Aufträge, Warnungen usw. neu.  
  
10. Sichern Sie die `msdb`-Datenbank.  
  
##  <a name="Troubleshoot"></a>Beheben von Fehlern bei der Neuerstellung  
 Syntaxfehler und andere Laufzeitfehler werden im Eingabeaufforderungsfenster angezeigt. Überprüfen Sie die SETUP-Anweisung auf folgende Syntaxfehler:  
  
-   Fehlender Schrägstrich (/) vor jedem Parameternamen  
  
-   Fehlendes Gleichheitszeichen (=) zwischen dem Parameternamen und dem Parameterwert  
  
-   Leerzeichen zwischen dem Parameternamen und dem Gleichheitszeichen  
  
-   Kommas (,) oder andere Zeichen, die nicht in der Syntax angegeben sind.  
  
 Wenn der Neuerstellungsvorgang abgeschlossen ist, überprüfen Sie die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Protokolle auf Fehler. Der Standardprotokollspeicherort ist C:\Programme\Microsoft SQL Server\120\Setup Bootstrap\Protokolle. Um die Protokolldatei zu suchen, die die Ergebnisse des Neuerstellungsprozesses enthält, wechseln Sie über eine Eingabeaufforderung zum Ordner Protokolle, und führen Sie dann `findstr /s RebuildDatabase summary*.*`aus. Diese Suche führt Sie zu den Protokolldateien, die die Ergebnisse der Neuerstellung der Systemdatenbanken enthalten. Öffnen Sie die Protokolldateien, und untersuchen Sie sie auf relevante Fehlermeldungen.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Systemdatenbanken](system-databases.md)  
  
  
