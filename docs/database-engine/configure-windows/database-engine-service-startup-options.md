---
title: Startoptionen für den Datenbank-Engine-Dienst | Microsoft-Dokumentation
ms.custom: ''
ms.date: 05/31/2019
ms.prod: sql
ms.prod_service: high-availability
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
helpviewer_keywords:
- single-user mode [SQL Server], startup option
- overriding default startup options
- minimal configuration mode [SQL Server], startup option
- default startup options
- temporarily override default startup options [SQL Server]
- startup options [SQL Server]
- starting SQL Server, options
- single-user mode [SQL Server], startup parameter
- overriding default startup parameters
- minimal configuration mode [SQL Server], startup parameter
- default startup parameters
- temporarily override default startup parameters [SQL Server]
- startup parameters [SQL Server]
- starting SQL Server, parameters
ms.assetid: d373298b-f6cf-458a-849d-7083ecb54ef5
author: MikeRayMSFT
ms.author: mikeray
manager: jroth
ms.openlocfilehash: 25fb3df76c54042b81a92af3a6fa29706ab9faae
ms.sourcegitcommit: ad2e98972a0e739c0fd2038ef4a030265f0ee788
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 06/07/2019
ms.locfileid: "66767584"
---
# <a name="database-engine-service-startup-options"></a>Startoptionen für den Datenbank-Engine-Dienst

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

Startoptionen legen bestimmte während des Starts benötigte Speicherorte fest und legen einige Bedingungen fest, die für den gesamten Server gelten. Die meisten Benutzer müssen keine Startoptionen angeben, es sei denn, Sie führen Fehlerbehebungen für [!INCLUDE[ssDE](../../includes/ssde-md.md)] durch oder es liegt ein ein außergewöhnliches Problem vor, und und Sie werden vom [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Produktsupport aufgefordert, eine Startoption zu verwenden.  
  
> [!WARNING]  
>  Die falsche Verwendung von Startoptionen kann die Serverleistung beeinträchtigen und verhindern, dass [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] startet.  
>
>  Starten Sie SQL Server unter Linux mit dem Benutzer „MSSQL“, um zukünftige Startprobleme zu vermeiden. Beispiel: `sudo -u mssql /opt/mssql/bin/sqlservr [STARTUP OPTIONS]` 
  
## <a name="about-startup-options"></a>Informationen zu Startoptionen  
 Wenn Sie [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]installieren, schreibt Setup eine Reihe von Standardstartoptionen in die [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows-Registrierung. Sie können die folgenden Startoptionen verwenden, um eine andere master-Datenbankdatei, eine andere Protokolldatei der master-Datenbank oder eine andere Fehlerprotokolldatei anzugeben. Wenn [!INCLUDE[ssDE](../../includes/ssde-md.md)] die notwendigen Dateien nicht finden kann, startet [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] nicht.  
  
 Startoptionen können mithilfe des [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Konfigurations-Managers festgelegt werden. Weitere Informationen finden Sie unter [Konfigurieren von Serverstartoptionen &#40;SQL Server-Konfigurations-Manager&#41;](../../database-engine/configure-windows/scm-services-configure-server-startup-options.md).  
  
## <a name="list-of-startup-options"></a>Liste von Startoptionen  
### <a name="default-startup-options"></a>Standardstartoptionen  

|enthalten|und Beschreibung|  
|-----------------------------|-----------------|  
|**-d**  *master_file_path*|Der vollqualifizierte Pfad der master-Datenbankdatei (in der Regel C:\Programme\Microsoft SQL Server\MSSQL.*n*\MSSQL\Data\master.mdf). Wenn diese Option nicht bereitgestellt wird, werden die vorhandenen Registrierungsparameter verwendet.|  
|**-e**  *error_log_path*|Der vollqualifizierte Pfad der Fehlerprotokolldatei (in der Regel C:\Programme\Microsoft SQL Server\MSSQL.*n*\MSSQL\LOG\ERRORLOG). Wenn diese Option nicht bereitgestellt wird, werden die vorhandenen Registrierungsparameter verwendet.|  
|**-l**  *master_log_path*|Der vollqualifizierte Pfad der master-Datenbankdatei (in der Regel C:\Programme\Microsoft SQL Server\MSSQL.*n*\MSSQL\Data\mastlog.ldf). Wenn diese Option nicht angegeben wird, werden die vorhandenen Registrierungsparameter verwendet.|  
  
### <a name="other-startup-options"></a>Sonstige Startoptionen   

|enthalten |und Beschreibung|   
|---------------------------|-----------------|  
|**-c**|Verkürzt die Startzeit, wenn [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] an der Eingabeaufforderung gestartet wird. In der Regel wird [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] als Dienst gestartet, indem der Dienstkontroll-Manager aufgerufen wird. Da [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] nicht als Dienst gestartet wird, wenn die Anwendung an der Eingabeaufforderung gestartet wird, sollten Sie diesen Schritt mithilfe von **-c** überspringen.|  
|**-f**|Startet eine [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Instanz mit Minimalkonfiguration. Dies ist hilfreich, wenn der Server aufgrund der Einstellung eines Konfigurationswerts (z. B. aufgrund von Arbeitsspeichermangel) nicht gestartet werden kann. Wenn [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] im minimalen Konfigurationsmodus gestartet wird, befindet sich [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] im Einzelbenutzermodus. Weitere Informationen finden Sie in der weiter unten folgenden Beschreibung für **-m** .|  
|**-kDecimalNumber**| Dieser Startparameter begrenzt die Anzahl der E/A-Anforderungen für Prüfpunkte pro Sekunde, während **DecimalNumber** die Prüfpunktgeschwindigkeit in MB pro Sekunde angibt.  Beachten Sie, dass eine Änderung dieses Wertes sich darauf auswirken kann, wie schnell Sicherungen erstellt werden oder der Wiederherstellungsprozess ausgeführt wird. Hier sollte also vorsichtig gehandelt werden. Weitere Informationen zu diesem Startparameter finden Sie in dem Hotfix, in dem der Parameter [-k](https://support.microsoft.com/en-us/help/929240/fix-i-o-requests-that-are-generated-by-the-checkpoint-process-may-caus) vorgestellt wurde.| 
|**-m**|Startet eine Instanz von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] im Einzelbenutzermodus. Wenn Sie eine Instanz von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] im Einzelbenutzermodus starten, kann nur ein einziger Benutzer eine Verbindung herstellen, und der CHECKPOINT-Prozess wird nicht gestartet. Durch CHECKPOINT wird sichergestellt, dass die abgeschlossenen Transaktionen regelmäßig vom Datenträgercache auf das Datenbankmedium geschrieben werden. (In der Regel verwenden Sie diese Option bei Problemen mit Systemdatenbanken, die repariert werden sollten.) Diese Option aktiviert die Option „sp_configure allow updates“ (Updates zulassen). Standardmäßig ist allow updates deaktiviert. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] im Einzelbenutzermodus zu starten, ermöglicht einem beliebigen Mitglied der lokalen Administratorengruppe des Computers, eine Verbindung mit der Instanz von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] als Mitglied der festen Serverrolle "sysadmin" herzustellen. Weitere Informationen finden Sie unter [Herstellen einer Verbindung mit SQL Server, wenn Systemadministratoren gesperrt sind](../../database-engine/configure-windows/connect-to-sql-server-when-system-administrators-are-locked-out.md). Weitere Informationen zum Einzelbenutzermodus finden Sie unter [Starten von SQL Server im Einzelbenutzermodus](../../database-engine/configure-windows/start-sql-server-in-single-user-mode.md).|  
|**-mName der Clientanwendung**|Beschränkt die Verbindungen auf eine angegebene Clientanwendung. `-mSQLCMD`  beschränkt Verbindungen z. B. auf eine einzelne Verbindung, und diese Verbindung muss sich als SQLCMD-Clientprogramm identifizieren. Verwenden Sie diese Option, wenn Sie [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] im Einzelbenutzermodus starten und eine unbekannte Clientanwendung die einzige verfügbare Verbindung belegt. Verwenden Sie `"Microsoft SQL Server Management Studio - Query"` , um eine Verbindung mit dem SSMS Abfrage-Editor herzustellen. Die Option „SSMS Abfrage-Editor“ kann nicht über [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)] -Konfigurations-Manager konfiguriert werden, weil sie den Bindestrich enthält, der vom Tool abgelehnt wird.<br /><br /> Beim Clientanwendungsnamen wird zwischen Groß- und Kleinschreibung unterschieden. Doppelte Anführungszeichen sind erforderlich, wenn der Anwendungsname Leerzeichen oder Sonderzeichen enthält.<br /><br />**Beispiele für ein Starten von der Befehlszeile aus:**<br /><br />`C:\Program Files\Microsoft SQL Server\MSSQL13.MSSQLSERVER\MSSQL\Binn\sqlservr -s MSSQLSERVER -m"Microsoft SQL Server Management Studio - Query"` <br /><br />`C:\Program Files\Microsoft SQL Server\MSSQL13.MSSQLSERVER\MSSQL\Binn\sqlservr -s MSSQLSERVER -mSQLCMD` <br /><br /> **Sicherheitshinweis:** Verwenden Sie diese Option nicht als Sicherheitsfunktion. Die Clientanwendung gibt den Clientanwendungsnamen an und kann als Teil der Verbindungszeichenfolge einen falschen Namen angeben.|  
|**-n**|Zeichnet keine [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Ereignisse mithilfe des Windows-Anwendungsprotokolls auf. Wenn Sie eine [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Instanz mit der Option **-n**starten, sollten Sie auch die Startoption **-e** verwenden. Andernfalls werden keine [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Ereignisse protokolliert.|  
|**-s**|Ermöglicht es Ihnen, eine benannte [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Instanz zu starten. Wenn der **-s** -Parameter nicht festgelegt wurde, wird versucht, die Standardinstanz zu starten. Sie müssen an der Eingabeaufforderung in das entsprechende BINN-Verzeichnis für die Instanz wechseln, bevor Sie **sqlservr.exe**starten. Wenn beispielsweise Instanz1 `\mssql$Instance1` für die zugehörigen Binärdateien verwendet, muss sich der Benutzer im Verzeichnis `\mssql$Instance1\binn` befinden, um **sqlservr.exe -s instance1** zu starten.|  
|**-T**  *trace#*|Gibt an, dass eine [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Instanz so gestartet werden soll, dass ein bestimmtes Ablaufverfolgungsflag (*trace#* ) wirksam wird. Ablaufverfolgungsflags werden verwendet, um den Server mit nicht standardmäßigem Verhalten zu starten. Weitere Informationen finden Sie unter [Ablaufverfolgungsflags &#40;Transact-SQL&#41;](../../t-sql/database-console-commands/dbcc-traceon-trace-flags-transact-sql.md).<br /><br /> **Wichtig:** Wenn Sie ein Ablaufverfolgungsflag mit der Option **-T** angeben, sollten Sie ein „T“ in Großbuchstaben verwenden, um die Nummer des Ablaufverfolgungsflags zu übergeben. Ein "t" in Kleinbuchstaben wird von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] akzeptiert, doch werden dadurch andere interne Ablaufverfolgungsflags festgelegt, die nur von Supporttechnikern für [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] benötigt werden. (Startparameter, die über die Anwendung Dienste in der Systemsteuerung angegeben werden, werden nicht gelesen.)|  
|**-x**|Deaktiviert die folgenden Überwachungsfunktionen:<br /> - [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Leistungsindikatoren<br /> – Beibehalten der Statistiken zu CPU-Zeit und zur Cachetrefferquote<br /> – Sammeln von Informationen für den Befehl „DBCC SQLPERF“<br /> – Sammeln von Informationen für einige dynamische Verwaltungssichten<br /> – viele Ereignispunkte für erweiterte Ereignisse<br /><br /> **Warnung:** Wenn Sie die Startoption **-x** verwenden, werden die Informationen, die Ihnen zum Diagnostizieren von Leistungs- und Funktionsproblemen in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] zur Verfügung stehen, erheblich reduziert.|  
|**-E**|Erhöht die Anzahl der Blöcke, die jeder Datei in einer Dateigruppe zugeordnet werden. Diese Option ist möglicherweise bei Data Warehouse-Anwendungen nützlich, bei denen nur eine eingeschränkte Anzahl von Benutzern Index- oder Datenscans ausführen. Sie sollte bei anderen Anwendungen nicht verwendet werden, da sie sich möglicherweise negativ auf die Leistung auswirkt. Diese Option wird in 32-Bit-Versionen von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]nicht unterstützt.|  
  
## <a name="using-startup-options-for-troubleshooting"></a>Verwenden von Startoptionen für die Problembehandlung  
 Manche Startoptionen, z. B. der Einzelbenutzermodus und der Minimalkonfigurationsmodus, werden in erster Linie für die Problembehandlung verwendet. Zum Starten des Servers für die Problembehandlung mit den Optionen **-m** oder **-f** verwenden Sie am besten die Befehlszeile und starten „sqlservr.exe“ manuell.  
  
> [!NOTE]  
>  Beim Starten von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] mithilfe von **net start**wird ein Schrägstrich (/) anstelle eines Bindestrichs (-) für die Startoptionen verwendet.  
  
## <a name="using-startup-options-during-normal-operations"></a>Verwenden von Startoptionen im normalen Betrieb  
 Sie können Startoptionen bei jedem Start von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]verwenden. Für diese Optionen, z.B. das Starten mit einem Ablaufverfolgungsflag, konfigurieren Sie die Startparameter am besten mit dem [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Konfigurations-Manager. Dieses Tool speichert die Startoptionen als Registrierungsschlüssel, sodass [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] stets mit den Startoptionen gestartet werden kann.  
  
## <a name="compatibility-support"></a>Kompatibilitätsunterstützung  
 Der **-h**  -Parameter wird in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]nicht unterstützt. Dieser Parameter wurde in früheren Versionen der 32-Bit-Instanzen von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] verwendet, um virtuellen Adressraum für Metadaten zum Hinzufügen von Speicher im laufenden Systembetrieb (Hot Add Memory) zu reservieren, wenn AWE aktiviert ist. Weitere Informationen finden Sie unter [Nicht mehr unterstützte SQL Server-Funktionen in SQL Server 2016](https://msdn.microsoft.com/library/0678bfbc-5d3f-44f4-89c0-13e8e52404da).  
  
## <a name="related-tasks"></a>Related Tasks  
[Konfigurieren der Serverkonfigurationsoption Startprozeduren suchen](../../database-engine/configure-windows/configure-the-scan-for-startup-procs-server-configuration-option.md)  
[Starten, Beenden, Anhalten, Fortsetzen und Neustarten der Datenbank-Engine, von SQL Server Agent oder des SQL Server-Browserdiensts](../../database-engine/configure-windows/start-stop-pause-resume-restart-sql-server-services.md)
[Konfigurieren von Serverstartoptionen &#40;SQL Server-Konfigurations-Manager&#41;](../../database-engine/configure-windows/scm-services-configure-server-startup-options.md)
  
## <a name="see-also"></a>Weitere Informationen  
 [CHECKPOINT &#40;Transact-SQL&#41;](../../t-sql/language-elements/checkpoint-transact-sql.md)   
 [sqlservr (Anwendung)](../../tools/sqlservr-application.md)  
  
  
