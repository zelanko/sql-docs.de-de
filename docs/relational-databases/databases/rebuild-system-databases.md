---
description: Neuerstellen von Systemdatenbanken
title: Neuerstellen von Systemdatenbanken | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/06/2016
ms.prod: sql
ms.prod_service: database-engine
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
ms.openlocfilehash: 2365440fd87789a30e67c8c5effcbf0e85b8bc24
ms.sourcegitcommit: 544706f6725ec6cdca59da3a0ead12b99accb2cc
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/27/2020
ms.locfileid: "92638993"
---
# <a name="rebuild-system-databases"></a>Neuerstellen von Systemdatenbanken
 [!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]
  Systemdatenbanken müssen neu erstellt werden, um Beschädigungen der Systemdatenbanken [master](../../relational-databases/databases/master-database.md), [model](../../relational-databases/databases/model-database.md), [msdb](../../relational-databases/databases/msdb-database.md)oder [resource](../../relational-databases/databases/resource-database.md) zu beheben oder die Standardsortierung auf Serverebene zu ändern. Dieses Thema enthält schrittweise Anweisungen für die Neuerstellung von Systemdatenbanken in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].  
  
 **In diesem Thema**  
  
   - **Vorbereitungen:**  
  
     [Einschränkungen](#Restrictions)  
  
     [Voraussetzungen](#Prerequisites)  
  
   - **Vorgehensweisen:**  
  
     [Neuerstellen von Systemdatenbanken](#RebuildProcedure)  
  
     [Neuerstellen der resource-Datenbank](#Resource)  
  
     [Erstellen einer neuen msdb-Datenbank](#CreateMSDB) 

     [Neuerstellen der tempdb-Datenbank](#RebuildTempdb)  
  
   - **Nachverfolgung:**  
  
     [Problembehandlung von Fehlern bei der Neuerstellung](#Troubleshoot)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> Vorbereitungen  
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> Einschränkungen  
 Bei der Neuerstellung der Systemdatenbanken master, model, msdb und tempdb werden die Datenbanken abgelegt und an ihrem ursprünglichen Speicherort neu erstellt. Wenn in der REBUILD-Anweisung eine neue Sortierung angegeben wird, werden die Systemdatenbanken unter Verwendung dieser Sortiereinstellung erstellt. Alle Benutzeränderungen an diesen Datenbanken gehen verloren. Beispielsweise kann die master&lt;/ -Datenbank benutzerdefinierte Objekte, die msdb&lt;/ -Datenbank geplante Aufträge und die model&lt;/ -Datenbank Änderungen der Standardeinstellungen für Datenbanken enthalten.  
  
###  <a name="prerequisites"></a><a name="Prerequisites"></a> Voraussetzungen  
 Führen Sie die folgenden Aufgaben aus, bevor Sie die Systemdatenbanken neu erstellen, um sicherzustellen, dass Sie die Systemdatenbanken mit ihren aktuellen Einstellungen wiederherstellen können.  
  
1. Zeichnen Sie alle serverweiten Konfigurationswerte auf.  
  
    ```SQL  
    SELECT * FROM sys.configurations;  
    ```  
  
2.  Zeichnen Sie alle Hotfixes auf, die auf die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Instanz und die aktuelle Sortierung angewendet wurden. Sie müssen diese Hotfixes erneut anwenden, nachdem Sie die Systemdatenbanken neu erstellt haben.  
  
    ```SQL  
    SELECT  
    SERVERPROPERTY('ProductVersion ') AS ProductVersion,  
    SERVERPROPERTY('ProductLevel') AS ProductLevel,  
    SERVERPROPERTY('ResourceVersion') AS ResourceVersion,  
    SERVERPROPERTY('ResourceLastUpdateDateTime') AS ResourceLastUpdateDateTime,  
    SERVERPROPERTY('Collation') AS Collation;  
    ```  
  
3.  Zeichnen Sie den aktuellen Speicherort aller Daten und Protokolldateien für die Systemdatenbanken auf. Durch die erneute Erstellung der Systemdatenbanken werden alle Systemdatenbanken an ihrem ursprünglichen Speicherort installiert. Wenn Sie Systemdatenbank-Daten oder Protokolldateien an einen anderen Speicherort verschoben haben, müssen Sie die Dateien erneut verschieben.  
  
    ```SQL  
    SELECT name, physical_name AS current_file_location  
    FROM sys.master_files  
    WHERE database_id IN (DB_ID('master'), DB_ID('model'), DB_ID('msdb'), DB_ID('tempdb'));  
    ```  
  
4.  Suchen Sie die aktuelle Sicherung der Datenbanken master, model und msdb.  
  
5.  Wenn die Instanz von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] als Replikationsverteiler konfiguriert ist, suchen Sie die aktuelle Sicherung der Verteilungsdatenbank.  
  
6.  Stellen Sie sicher, dass Sie die geeigneten Berechtigungen haben, um die Systemdatenbanken neu zu erstellen. Um diesen Vorgang ausführen zu können, müssen Sie Mitglied der festen Serverrolle **sysadmin** sein. Weitere Informationen finden Sie unter [Rollen auf Serverebene](../../relational-databases/security/authentication-access/server-level-roles.md).  
  
7.  Überprüfen Sie, ob Kopien der Daten und Protokollvorlagendateien der Datenbanken master, model und msdb auf dem lokalen Server vorhanden sind. Der Standardspeicherort für die Vorlagendateien ist „C:\Programme\Microsoft SQL Server\MSSQL13.MSSQLSERVER\MSSQL\Binn\Templates“. Diese Dateien werden während der Neuerstellung verwendet und müssen vorhanden sein, um Setup erfolgreich ausführen zu können. Wenn sie fehlen, führen Sie die Reparaturfunktion von Setup aus, oder kopieren Sie die Dateien manuell vom Installationsmedium. Um die Dateien auf dem Installationsmedium zu suchen, navigieren Sie zum entsprechenden Plattformverzeichnis (x86 oder x64) und dann zu setup\sql_engine_core_inst_msi\Pfiles\SqlServr\MSSQL.X\MSSQL\Binn\Vorlagen.  
  
##  <a name="rebuild-system-databases"></a><a name="RebuildProcedure"></a> Neuerstellen von Systemdatenbanken  
 Mit der folgenden Vorgehensweise werden die Systemdatenbanken master, model, msdb und tempdb  neu erstellt. Sie können die Systemdatenbanken, die neu erstellt werden sollen, nicht angeben. Für gruppierte Instanzen muss diese Vorgehensweise für den aktiven Knoten ausgeführt werden, und die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Ressource in der entsprechenden Clusteranwendungsgruppe muss zuvor offline geschaltet werden.  
  
 Durch diese Vorgehensweise wird die Ressourcendatenbank nicht neu erstellt. Führen Sie hierzu die Schritte im Abschnitt "Vorgehensweise zum Neuerstellen der resource-Datenbank" weiter unten in diesem Thema aus.  
  
#### <a name="to-rebuild-system-databases-for-an-instance-of-sql-server"></a>So erstellen Sie Systemdatenbanken für eine Instanz von SQL Server neu  
  
1.  Legen Sie das [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] -Installationsmedium in das Laufwerk ein, oder wechseln Sie an einer Eingabeaufforderung zum Speicherort der Datei setup.exe auf dem lokalen Server. Der Standardspeicherort auf dem Server ist C:\Programme\Microsoft SQL Server\130\Setup Bootstrap\SQLServer2016.  
  
2.  Geben Sie den folgenden Befehl in das Eingabeaufforderungsfenster ein. Die eckigen Klammern zeigen optionale Parameter an. Geben Sie den Befehl ohne die eckigen Klammern ein. Wenn Sie Windows als Betriebssystem verwenden und die Benutzerkontensteuerung aktiviert ist, sind für die Ausführung des Setups erhöhte Rechte erforderlich. Die Eingabeaufforderung muss als Administrator ausgeführt werden.  
  
     **Setup /QUIET /ACTION=REBUILDDATABASE /INSTANCENAME=InstanceName /SQLSYSADMINACCOUNTS=accounts [ /SAPWD= StrongPassword ] [ /SQLCOLLATION=CollationName]**  
  
    |Parametername|BESCHREIBUNG|  
    |--------------------|-----------------|  
    |/QUIET oder /Q|Gibt an, dass Setup ohne Benutzeroberfläche ausgeführt wird.|  
    |/ACTION=REBUILDDATABASE|Gibt an, dass die Systemdatenbanken vom Setup neu erstellt werden.|  
    |/INSTANCENAME= *InstanceName*|Der Name der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Instanz. Geben Sie MSSQLSERVER für die Standardinstanz ein.|  
    |/SQLSYSADMINACCOUNTS= *accounts*|Gibt die Windows-Gruppen oder die individuellen Konten an, die der festen Serverrolle **sysadmin** hinzugefügt werden sollen. Wenn Sie mehr als ein Konto angeben, trennen Sie die Konten mit einem Leerzeichen. Geben Sie z.B. **BUILTIN\Administrators MyDomain\MyUser** ein. Wenn Sie ein Konto angeben, dessen Name ein Leerzeichen enthält, setzen Sie den Kontonamen in doppelte Anführungszeichen. Geben Sie beispielsweise **NT AUTHORITY\SYSTEM** ein.|  
    |[ /SAPWD= *StrongPassword* ]|Legt das Kennwort für das **sa** -Konto für [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] fest. Dieser Parameter ist erforderlich, wenn die Instanz den gemischten Authentifizierungsmodus ([!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] - und Windows-Authentifizierung) verwendet.<br /><br /> **&#42;&#42; Sicherheitshinweis &#42;&#42;** Das Konto **sa** ist ein bekanntes [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Konto und oft das Ziel böswilliger Benutzer. Es ist sehr wichtig, dass Sie für die **sa** -Anmeldung ein sicheres Kennwort verwenden.<br /><br /> Geben Sie diesen Parameter nicht für den Windows-Authentifizierungsmodus an.|  
    |[ /SQLCOLLATION= *CollationName* ]|Gibt eine neue Sortierung auf Serverebene an. Dieser Parameter ist optional. Wenn keine Sortierung angegeben wird, wird die aktuelle Sortierung des Servers verwendet.<br /><br /> **\*\* Wichtig \*\*** Die Änderung der Sortierung auf Serverebene ändert nicht die Sortierung vorhandener Benutzerdatenbanken. Alle neu erstellten Benutzerdatenbanken verwenden standardmäßig die neue Sortierung.<br /><br /> Weitere Informationen finden Sie unter [Festlegen oder Ändern der Serversortierung](../../relational-databases/collations/set-or-change-the-server-collation.md).|  
    |[ /SQLTEMPDBFILECOUNT=NumberOfFiles ]|Gibt die Anzahl von tempdb-Datendateien an. Dieser Wert kann auf bis zu 8 bzw. auf die Anzahl von Kernen erhöht werden, je nachdem, welcher Wert größer ist.<br /><br /> Standardwert: 8 oder die Anzahl von Kernen, je nachdem, welcher Wert niedriger ist.|  
    |[ /SQLTEMPDBFILESIZE=FileSizeInMB ]|Gibt die Anfangsgröße jeder tempdb-Datendatei in MB an. Das Setup ermöglicht eine Größe von bis zu 1024 MB.<br /><br /> Standardwert: 8|  
    |[ /SQLTEMPDBFILEGROWTH=FileSizeInMB ]|Gibt das Dateivergrößerungsinkrement jeder tempdb-Datendatei in MB an. Der Wert 0 zeigt an, dass die automatische Vergrößerung deaktiviert ist und kein zusätzlicher Platz zulässig ist. Das Setup ermöglicht eine Größe von bis zu 1024 MB.<br /><br /> Standardwert: 64|  
    |[ /SQLTEMPDBLOGFILESIZE=FileSizeInMB ]|Gibt die Anfangsgröße einer tempdb-Protokolldatei in MB an. Das Setup ermöglicht eine Größe von bis zu 1024 MB.<br /><br /> Standardwert: 8.<br /><br /> Zulässiger Bereich: Min. = 8, max. = 1024.|  
    |[ /SQLTEMPDBLOGFILEGROWTH=FileSizeInMB ]|Gibt das Dateivergrößerungsinkrement jeder tempdb-Protokolldatei in MB an. Der Wert 0 zeigt an, dass die automatische Vergrößerung deaktiviert ist und kein zusätzlicher Platz zulässig ist. Das Setup ermöglicht eine Größe von bis zu 1024 MB.<br /><br /> Standardwert: 64<br /><br /> Zulässiger Bereich: Min. = 8, max. = 1024.|  
    |[ /SQLTEMPDBDIR=Directories ]|Gibt die Verzeichnisse für tempdb-Datendateien an. Wenn Sie mehr als ein Verzeichnis angeben, trennen Sie die Verzeichnisse mit einem Leerzeichen. Wenn mehrere Verzeichnisse angegeben sind, werden die tempdb-Datendateien auf die Verzeichnisse im Rahmen eines Roundrobinverfahrens verteilt.<br /><br /> Standardwert: Systemdatenverzeichnis|  
    |[ /SQLTEMPDBLOGDIR=Directory ]|Gibt das Verzeichnis für die tempdb-Protokolldatei an.<br /><br /> Standardwert: Systemdatenverzeichnis|  
  
3.  Wenn Setup die Neuerstellung der Systemdatenbanken abgeschlossen hat, wechselt es ohne Meldungen zur Eingabeaufforderung zurück. Lesen Sie die Protokolldatei Summary.txt, um zu überprüfen, ob der Prozess erfolgreich abgeschlossen wurde. Diese Datei befindet sich unter „C:\Programme\Microsoft SQL Server\130\Setup Bootstrap\Logs“.  
  
4.  Das RebuildDatabase-Szenario löscht Systemdatenbanken und installiert diese neu in fehlerfreiem Zustand. Da die Einstellung der Anzahl von tempdb-Dateien nicht beibehalten wird, ist der Wert der Anzahl von tempdb-Dateien während des Setups nicht bekannt. Daher weiß das RebuildDatabase-Szenario nicht, wie viele tempdb-Dateien wieder hinzugefügt werden müssen. Sie können den Wert der Anzahl von tempdb-Dateien mit dem SQLTEMPDBFILECOUNT-Parameter erneut bereitstellen. Wenn der Parameter nicht bereitgestellt wird, fügt RebuildDatabase eine Standardanzahl von tempdb-Dateien hinzu. Diese Standardanzahl ist die Anzahl von CPUs oder 8, je nachdem, welche Anzahl niedriger ist.  
  
## <a name="post-rebuild-tasks"></a>Aufgaben nach der Neuerstellung  
 Nach der Neuerstellung der Datenbank müssen Sie möglicherweise die folgenden zusätzlichen Aufgaben ausführen:  
  
-   Stellen Sie die letzten vollständigen Sicherungen der Datenbanken master, model und msdb wieder her. Weitere Informationen finden Sie unter [Sichern und Wiederherstellen von Systemdatenbanken &#40;SQL Server&#41;](../../relational-databases/backup-restore/back-up-and-restore-of-system-databases-sql-server.md).  
  
    > [!IMPORTANT]  
    >  Wenn Sie die Serversortierung geändert haben, stellen Sie die Systemdatenbanken nicht wieder her. Auf diese Weise wird die neue Sortierung durch die vorherige Sortiereinstellung ersetzt.  
  
     Wenn keine Sicherung verfügbar ist oder wenn die wiederhergestellte Sicherung nicht aktuell ist, erstellen Sie alle fehlenden Einträge neu. Erstellen Sie z.B. alle fehlenden Einträge für die Benutzerdatenbanken, Sicherungsmedien, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Anmeldenamen, Endpunkte usw. neu. Die beste Möglichkeit zur Neuerstellung der Einträge besteht darin, die ursprünglichen Skripts auszuführen, mit denen sie erstellt wurden.  
  
> [!IMPORTANT]  
>  Es wird empfohlen, Skripts vor unerlaubtem Zugriff zu schützen. Auf diese Weise können Sie verhindern, dass sie von nicht autorisierten Personen geändert werden.  
  
-   Sie müssen die Verteilungsdatenbank wiederherstellen, wenn die Instanz von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] als Replikationsverteiler konfiguriert ist. Weitere Informationen finden Sie unter [Sichern und Wiederherstellen von replizierten Datenbanken](../../relational-databases/replication/administration/back-up-and-restore-replicated-databases.md).  
  
-   Verschieben Sie die Systemdatenbanken an die Speicherorte, die Sie zuvor aufgezeichnet haben. Weitere Informationen finden Sie unter [Verschieben von Systemdatenbanken](../../relational-databases/databases/move-system-databases.md).  
  
-   Überprüfen Sie, ob die serverweiten Konfigurationswerte zu den Werten passen, die Sie zuvor aufgezeichnet haben.  
  
##  <a name="rebuild-the-resource-database"></a><a name="Resource"></a> Neuerstellen der resource-Datenbank  
 Mit der folgenden Vorgehensweise wird die Ressourcensystemdatenbank neu erstellt. Wenn Sie die Ressourcendatenbank neu erstellen, gehen alle Hotfixes verloren. Daher müssen sie noch mal angewendet werden.  
  
#### <a name="to-rebuild-the-resource-system-database"></a>So erstellen Sie die Systemdatenbank "resource" neu  
  
1.  Starten Sie von den Installationsmedien das [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] -Setupprogramm (setup.exe).  
  
2.  Klicken Sie im linken Navigationsbereich auf **Wartung** und dann auf **Reparieren** .  
  
3.  Es werden Unterstützungsregeln für Setup und Dateiroutinen ausgeführt, um sicherzustellen, dass die erforderlichen Komponenten auf dem System installiert sind und dass der Computer den Setupüberprüfungsregeln erfüllt. Klicken Sie zum Fortsetzen auf **OK** oder auf **Installieren** .  
  
4.  Wählen Sie auf der Seite Instanz auswählen die zu reparierende Instanz aus, und klicken Sie dann zum auf **Weiter** , um den Vorgang fortzusetzen.  
  
5.  Die Reparaturregeln werden ausgeführt, um den Vorgang zu überprüfen. Klicken Sie auf **Weiter** , um den Vorgang fortzusetzen.  
  
6.  Klicken Sie auf der Seite **Bereit zum Reparieren** auf **Reparieren** . Wenn die Seite Abgeschlossen angezeigt wird, wurde der Vorgang abgeschlossen.  
  
##  <a name="create-a-new-msdb-database"></a><a name="CreateMSDB"></a> Erstellen einer neuen msdb-Datenbank  

 Wenn die **msdb** -Datenbank beschädigt ist und Sie keine Sicherung der **msdb** -Datenbank erstellt haben, können Sie mit dem Skript **instmsdb** eine neue **msdb** -Datenbank erstellen.  
  
> [!WARNING]  
>  Beim Neuerstellen der **msdb** -Datenbank mit dem **instmsdb** -Skript werden alle in der **msdb** -Datenbank gespeicherten Informationen wie Aufträge, Warnungen, Operatoren, Wartungspläne, Sicherungsverläufe, Einstellungen für die richtlinienbasierte Verwaltung, Datenbank-E-Mail, Leistungs-Data Warehouse usw. gelöscht.  
  
1.  Beenden Sie alle Dienste, die mit [!INCLUDE[ssDE](../../includes/ssde-md.md)]verbunden sind, einschließlich dem [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Agent, [!INCLUDE[ssRS](../../includes/ssrs.md)], [!INCLUDE[ssIS](../../includes/ssis-md.md)]und allen Anwendungen, die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] als Datenspeicher verwenden.  
  
2.  Starten Sie [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] über die Befehlszeile mit dem Befehl: `NET START MSSQLSERVER /T3608`  
  
     Weitere Informationen finden Sie unter [Starten, Beenden, Anhalten, Fortsetzen und Neustarten von SQL Server-Diensten](../../database-engine/configure-windows/start-stop-pause-resume-restart-sql-server-services.md).  
  
3.  Trennen Sie in einem weiteren Befehlszeilenfenster die **msdb** -Datenbank, indem Sie den folgenden Befehl ausführen und dabei *\<servername>* durch die Instanz von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ersetzen: `SQLCMD -E -S<servername> -dmaster -Q"EXEC sp_detach_db msdb"`.  
  
4.  Benennen Sie in Windows Explorer die **msdb** -Datenbankdateien um. Diese befinden sich standardmäßig im Unterordner DATA der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Instanz.  
  
5.  Verwenden Sie den [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Konfigurations-Manager zum Beenden und erneuten Starten des [!INCLUDE[ssDE](../../includes/ssde-md.md)] -Diensts.  
  
6.  Stellen Sie in einem Befehlszeilenfenster eine Verbindung mit [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] her, und führen Sie folgenden Befehl aus: `SQLCMD -E -S<servername> -i"C:\Program Files\Microsoft SQL Server\MSSQL13.MSSQLSERVER\MSSQL\Install\instmsdb.sql" -o"C:\Program Files\Microsoft SQL Server\MSSQL13.MSSQLSERVER\MSSQL\Install\instmsdb.out"`  
  
     Ersetzen Sie *\<servername>* durch die Instanz von [!INCLUDE[ssDE](../../includes/ssde-md.md)]. Verwenden Sie den Dateisystempfad der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Instanz.  
  
7.  Öffnen Sie die Datei **instmsdb.out** im Windows-Editor, und prüfen Sie, ob die Ausgabe fehlerfrei ist.  
  
8.  Wenden Sie alle Hotfixes noch mal auf die Instanz an.  
  
9. Legen Sie die in der **msdb** -Datenbank gespeicherten Benutzerinhalte wie Aufträge, Warnungen usw. erneut an.  
  
10. Sichern Sie die **msdb** -Datenbank.  

##  <a name="rebuild-the-tempdb-database"></a><a name="RebuildTempdb"></a> Neuerstellen der tempdb-Datenbank  

Wenn die **tempdb** -Datenbank beschädigt ist und die Datenbank-Engine nicht startet, können Sie **tempdb** neu erstellen, ohne alle Systemdatenbanken neu erstellen zu müssen.
  
1. Benennen Sie die aktuellen Dateien „tempdb.mdf“ und „templog.ldf“ um, falls sie vorhanden sind. 
1. Starten Sie [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] von einer Eingabeaufforderung aus mithilfe des folgenden Befehls. 

   ```sql
   sqlservr -c -f -T3608 -T4022 -s <instance> -mSQLCMD
   ```

   Für einen Standardinstanznamen verwenden Sie MSSQLSERVER, für eine benannte Instanz verwenden Sie MSSQL$<Instanzname>. Ablaufverfolgungsflag 4022 deaktiviert die Ausführung von gespeicherten Startprozeduren. Durch „-mSQLCMD“ wird nur [sqlcmd.exe](../../ssms/scripting/sqlcmd-use-the-utility.md) gestattet, eine Verbindung mit dem Server herzustellen (siehe [Weitere Startoptionen](../../database-engine/configure-windows/database-engine-service-startup-options.md#other-startup-options))

   > [!Note] 
   > Stellen Sie sicher, dass das Eingabeaufforderungsfenster nach dem Start von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] geöffnet bleibt. Das Schließen des Eingabeaufforderungsfensters beendet den Prozess.

1. Stellen Sie mithilfe von **sqlcmd** eine Verbindung mit dem Server her, und verwenden Sie dann die folgende gespeicherte Prozedur, um den Status der tempdb-Datenbank zurückzusetzen.

   ```sql
   exec master..sp_resetstatus tempdb
   ```

1. Fahren Sie den Server herunter, indem Sie im Eingabeaufforderungsfenster STRG+C drücken.

1. Starten Sie den [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Dienst neu. Dadurch wird ein neuer Satz von tempdb-Datenbankdateien erstellt und die tempdb-Datenbank wiederhergestellt.

  
##  <a name="troubleshoot-rebuild-errors"></a><a name="Troubleshoot"></a> Problembehandlung von Fehlern bei der Neuerstellung  
 Syntaxfehler und andere Laufzeitfehler werden im Eingabeaufforderungsfenster angezeigt. Überprüfen Sie die SETUP-Anweisung auf folgende Syntaxfehler:  
  
-   Fehlender Schrägstrich (/) vor jedem Parameternamen  
  
-   Fehlendes Gleichheitszeichen (=) zwischen dem Parameternamen und dem Parameterwert  
  
-   Leerzeichen zwischen dem Parameternamen und dem Gleichheitszeichen  
  
-   Kommas (,) oder andere Zeichen, die nicht in der Syntax angegeben sind.  
  
 Wenn der Neuerstellungsvorgang abgeschlossen ist, überprüfen Sie die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Protokolle auf Fehler. Der Standardprotokollspeicherort ist „C:\Programme\Microsoft SQL Server\130\Setup Bootstrap\Logs“. Um die Protokolldatei zu suchen, die die Ergebnisse des Neuerstellungsprozesses enthält, wechseln Sie über eine Eingabeaufforderung zum Ordner Protokolle, und führen Sie dann `findstr /s RebuildDatabase summary*.*`aus. Diese Suche führt Sie zu den Protokolldateien, die die Ergebnisse der Neuerstellung der Systemdatenbanken enthalten. Öffnen Sie die Protokolldateien, und untersuchen Sie sie auf relevante Fehlermeldungen.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Systemdatenbanken](../../relational-databases/databases/system-databases.md)  
  
  
