---
title: Problembehandlung bei SQL Server-Hilfsprogramm | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
ms.assetid: f5f47c2a-38ea-40f8-9767-9bc138d14453
author: mashamsft
ms.author: mathoma
manager: craigg
ms.openlocfilehash: ed71e0fb889b0cff71937e78245bef1453e13a10
ms.sourcegitcommit: 334cae1925fa5ac6c140e0b2c38c844c477e3ffb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/13/2018
ms.locfileid: "53371062"
---
# <a name="troubleshoot-the-sql-server-utility"></a>Problembehandlung beim SQL Server-Hilfsprogramm
  Die Behebung von Problemen mit dem [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] -Hilfsprogramm kann das Auflösen eines fehlgeschlagenen Vorgangs zur Registrierung einer Instanz von SQL Server mit einem UCP, die Behebung von Fehlern bei Datensammlungen, die zu grauen Symbolen in der Listenansicht der verwalteten Instanzen auf einem UCP führen, die Abhilfe für Leistungsengpässe oder das Beheben von Problemen mit der Ressourcenintegrität umfassen. Weitere Informationen zum Beheben von Problemen mit der ressourcenintegrität identifizierte eine [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] ucp stammen, finden Sie unter [Problembehandlung bei SQL Server-Ressourcenintegrität &#40;SQL Server-Hilfsprogramm&#41;](../relational-databases/manage/troubleshoot-sql-server-resource-health-sql-server-utility.md).  
  
## <a name="failed-operation-to-enroll-an-instance-of-sql-server-into-a-sql-server-utility"></a>Fehlgeschlagener Vorgang, eine Instanz von SQL Server in ein SQL Server-Hilfsprogramm zu registrieren  
 Wenn Sie die [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] -Authentifizierung für die Verbindung mit der Instanz von [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] für die Registrierung verwenden, und Sie geben ein Proxykonto an, das zu einer anderen Active Directory-Domäne gehört als die Domäne, wo sich der UCP befindet, ist die Instanzüberprüfung erfolgreich, aber der Registrierungsvorgang schlägt mit der folgenden Fehlermeldung fehl:  
  
 Beim Ausführen einer Transact-SQL-Anweisung oder eines Batches ist eine Ausnahme aufgetreten. (Microsoft.SqlServer.ConnectionInfo)  
  
 Zusätzliche Informationen:  Informationen zu Windows NT-Gruppe oder-Benutzer konnten nicht abgerufen "\<DomainName\AccountName >', Fehlercode 0 x 5. (Microsoft SQL Server, Fehler: -2)" 15404)  
  
 Das Problem tritt im folgenden Beispielszenario auf:  
  
1.  Der UCP ist ein Element von "Domain_1."  
  
2.  Eine unidirektionale Domänenvertrauensstellung ist vorhanden: das heißt, "Domain_1" wird nicht von "Domain_2" vertraut, aber "Domain_2" wird von "Domain_1" vertraut.  
  
3.  Die Instanz von [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] , die in das [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] -Hilfsprogramm registriert werden soll, ist auch ein Element von "Domain_1."  
  
4.  Während des Registrierungsvorgangs eine Verbindung mit der Instanz [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] , mit "sa" zu registrieren. Geben Sie ein Proxykonto bei "Domain_2" an.  
  
5.  Die Überprüfung ist erfolgreich, aber die Registrierung schlägt fehl.  
  
 Die problemumgehung für dieses Problem, das im Beispiel oben besteht darin, für die Verbindung mit der Instanz von [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Sie beim Registrieren der [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] -Hilfsprogramm mit "sa", und geben Sie ein Proxykonto an, von "Domain_1."  
  
## <a name="failed-wmi-validation"></a>Fehlgeschlagene WMI-Überprüfung  
 Wenn WMI nicht ordnungsgemäß auf einer Instanz von [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]konfiguriert wird, zeigen die Vorgänge für das Erstellen des UCPs und die Registrierung verwalteter Instanzen eine Warnung an, der Vorgang wird jedoch nicht blockiert. Wenn Sie die [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] -Agent-Kontokonfiguration ändern, sodass der [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] -Agent nicht über die Berechtigung für die erforderlichen WMI-Klassen verfügt, lädt die Datensammlung auf der betroffenen verwalteten Instanz von [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] nicht zum UCP hoch. Dies führt im UCP zu grauen Symbolen.  
  
 Die fehlgeschlagene Datensammlung führt in der UCP-Listenansicht für betroffene verwaltete Instanzen von [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]zu grauen Statussymbolen. Der Auftragsverlauf auf der verwalteten Instanz von [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] zeigt an, dass sysutility_mi_collect_and_upload bei Schritt 2 (Phasendaten haben sich von PowerShell-Skript gesammelt) fehlschlägt.  
  
 Die vereinfachten Fehlermeldungen sind:  
  
 Die Ausführung des Befehls wurde beendet, da die Shellvariable "ErrorActionPreference" auf "Stop" festgelegt ist: Zugriff verweigert.  
  
 FEHLER: \<Datum und Uhrzeit (MM/TT/JJJJ hh: mm:) >: Beim Sammeln von CPU-Eigenschaften wurde eine Ausnahme abgefangen.  Eine WMI-Abfrage könnte fehlgeschlagen sein.  WARNUNG:  
  
 Um dieses Problem zu beheben, überprüfen Sie die folgenden Konfigurationseinstellungen:  
  
-   Unter Windows Server 2003 muss der SQL Server-Agent-Dienst Teil der Gruppe der Systemmonitorbenutzer auf der verwalteten Instanz von [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]sein.  
  
-   Der WMI-Dienst muss auf der verwalteten Instanz von [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]aktiviert und konfiguriert sein.  
  
-   Das WMI-Repository könnte auf der verwalteten Instanz von [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]fehlerhaft sein.  
  
-   Die Leistungsbibliothek könnte fehlen oder auf der verwalteten Instanz von [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]beschädigt sein.  
  
 Um zu überprüfen, ob die angegebene Instanz von [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] ordnungsgemäß für Datenberichte an den UCP konfiguriert ist, überprüfen Sie, ob die folgenden Klassen auf der angegebenen Instanz von [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]verfügbar sind und ob auf sie vom SQL Server-Agent-Dienstkonto zugegriffen werden kann:  
  
-   Win32_MountPoint  
  
-   Win32_PerfRawData_PerfProc_Process  
  
-   Win32_PerfRawData_PerfOS_Processor  
  
-   Win32_Processor  
  
-   Win32_Volume  
  
-   Win32_LogicalDisk  
  
 Sie können das Get-WmiObject PowerShell Cmdlet auf jede der Klassen anwenden, um zu überprüfen, dass auf jede Klasse zugegriffen werden kann. Führen Sie die folgenden Cmdlets auf der verwalteten Instanz von [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]aus:  
  
```  
Get-WmiObject Win32_MountPoint -ErrorAction Stop | Out-Null  
Get-WmiObject Win32_PerfRawData_PerfProc_Process -ErrorAction Stop| Out-Null  
Get-WmiObject Win32_PerfRawData_PerfOS_Processor -ErrorAction Stop | Out-Null  
Get-WmiObject Win32_Processor -ErrorAction Stop | Out-Null  
Get-WmiObject Win32_Volume -ErrorAction Stop | Out-Null  
Get-WmiObject Win32_LogicalDisk -ErrorAction Stop | Out-Null  
```  
  
 Weitere Informationen zum Durchführen einer Problembehandlung für WMI finden Sie unter [Problembehandlung bei WMI](https://go.microsoft.com/fwlink/?LinkId=178250). Beachten Sie, dass Abfragen an diese SQL Server-Hilfsprogrammvorgänge lokal ausgeführt werden, so dass DCOM und Remoteproblembehandlungsinhalte nicht gültig sind.  
  
## <a name="failed-data-collection"></a>Fehlerhafte Datensammlung  
 Wenn bei Datensammlungsereignissen des [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] -Hilfsprogramms ein Fehler auftritt, sollten Sie folgende Möglichkeiten in Betracht ziehen:  
  
-   Ändern Sie keine Eigenschaften des Sammlungssatzes „Hilfsprogramminformationen“ in einer verwalteten Instanz von [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)], und aktivieren/deaktivieren Sie die Datensammlung nicht manuell, da die Datensammlung von einem Hilfsprogramm-Agentauftrag gesteuert wird.  
  
-   Fehlgeschlagene oder nicht unterstützte WMI-Überprüfung. Weitere Informationen finden Sie im Abschnitt "Fehlgeschlagene WMI-Überprüfung" weiter oben in diesem Thema.  
  
-   Aktualisieren Sie Daten in der Listenansicht verwalteter Instanzen, da die Daten in den Blickpunkten des [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] -Hilfsprogramms nicht automatisch aktualisiert werden. Um Daten zu aktualisieren, klicken Sie mit der rechten Maustaste auf den Knoten **Verwaltete Instanzen** im **Hilfsprogramm-Explorer** -Navigationsbereich und wählen dann **Aktualisieren**aus. Alternativ klicken Sie mit der rechten Maustaste in der Listenansicht auf den [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] -Instanznamen und wählen dann **Aktualisieren**aus. Nachdem eine Instanz von [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] bei einem UCP registriert wurde, kann es bis zu 30 Minuten dauern, bis die ersten Daten im Inhaltsbereich des Hilfsprogramm-Explorers im Dashboard und in den Blickpunkten angezeigt werden.  
  
-   Verwenden Sie den SQL Server-Konfigurations-Manager, um zu überprüfen, ob die Instanz von [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] ausgeführt wird.  
  
-   Wenn die Datensammlung oder das Hochladen von Daten aufgrund von Timeoutproblemen scheitern, aktualisieren Sie die Funktion dbo.fn_sysutility_mi_get_collect_script() in der MSDB-Datenbank. Fügen Sie insbesondere in der Funktion "Invoke-BulkCopyCommand()" die folgende Zeile hinzu:  
  
    ```  
    $bulkCopy.BulkCopyTimeout=180  
    ```  
  
     Der Standard-Timeoutwert beträgt 30 Sekunden.  
  
-   Wenn die Instanz von [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] nicht gruppiert ist, überprüfen Sie, ob der [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] -Agent-Dienst ausgeführt wird und ob der Dienst für den automatischen Start auf dem UCP und in der verwalteten Instanz von [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]eingerichtet wurde.  
  
-   Überprüfen Sie, ob ein gültiges Konto verwendet wird, um die Datensammlung für die verwaltete Instanz von [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]auszuführen. Möglicherweise ist das Kennwort z. B. abgelaufen. Wenn das Proxykennwort abgelaufen ist, aktualisieren Sie die Kennwort-Anmeldeinformationen in SSMS wie folgt:  
  
    1.  Erweitern Sie im **Objekt-Explorer**von SSMS den Knoten **Sicherheit** und dann den Knoten **Anmeldeinformationen** .  
  
    2.  Mit der rechten Maustaste auf **UtilityAgentProxyCredential_\<GUID >** , und wählen Sie **Eigenschaften**.  
  
    3.  Aktualisieren Sie im Dialogfeld Eigenschaften für Anmeldeinformationen Anmeldeinformationen nach Bedarf für die **UtilityAgentProxyCredential_\<GUID >** Anmeldeinformationen.  
  
    4.  Klicken Sie auf **OK** , um die Änderung zu bestätigen.  
  
-   TCP/IP muss für den UCP und die verwaltete Instanz von [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]aktiviert sein. Aktivieren Sie TCP/IP über den [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] -Konfigurations-Manager.  
  
-   Der SQL Server-Browserdienst auf dem UCP sollte gestartet werden und für den automatischen Start konfiguriert sein. Wenn die Verwendung des SQL Server-Browserdiensts in Ihrer Organisation verhindert wird, führen Sie die folgenden Schritte aus, damit eine verwaltete Instanz von [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] eine Verbindung mit dem UCP herstellen kann:  
  
    1.  Klicken Sie auf der Windows-Taskleiste der verwalteten Instanz von [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)], klicken Sie auf **starten**, klicken Sie dann auf **ausführen...** .  
  
    2.  Geben Sie im dafür vorgesehenen Feld **cliconfg.exe**ein, und klicken Sie auf OK.  
  
    3.  Sobald Sie aufgefordert werden, die EXE-Datei für das SQL Server-Clientkonfigurationsprogramm zu starten, klicken Sie auf**Weiter**.  
  
    4.  Auf der **SQL Server-Clientkonfigurationsprogramm** wählen Sie im Dialogfeld die **Alias** Registerkarte, und klicken Sie dann **hinzufügen...** .  
  
    5.  Im Dialogfeld **Netzwerkbibliothekskonfiguration hinzufügen** :  
  
    6.  Geben Sie in der Liste der Netzwerkbibliotheken TCP/IP an.  
  
    7.  Geben Sie den **ComputerName\InstanceName** des UCPs im Textfeld Serveralias an.  
  
    8.  Geben Sie den **ComputerName** des UCPs im Textfeld Servername an.  
  
    9. Deaktivieren Sie das Kontrollkästchen **Anschluss dynamisch bestimmen** .  
  
    10. Geben Sie die Nummer des Anschlusses, an dem der UCP lauscht, im Textfeld **Anschlussnummer** an.  
  
    11. Klicken Sie auf **OK** , um die Änderungen zu speichern.  
  
    12. Wiederholen Sie diese Schritte für jede verwaltete Instanz von [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] , die eine Verbindung mit einem UCP herstellt, auf dem der SQL Server-Browserdienst nicht aktiviert ist.  
  
-   Stellen Sie sicher, dass verwaltete Instanzen von [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] mit dem Netzwerk verbunden sind.  
  
-   Wenn Datenbanken mit dem gleichen Namen, aber unterschiedlichen Einstellungen im Hinblick auf die Berücksichtigung von Groß- und Kleinschreibung für eine verwaltete Instanz von [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]vorhanden sind, kann die Datenauflistung fehlschlagen. Eine Datenbank mit dem Namen "MYDATABASE" könnte z. B. Integritätszustände für eine Datenbank mit dem Namen "MYDATABASE" anzeigen. Bei diesem Szenario wird kein Fehler generiert. Die fehlgeschlagene Datensammlung kann auch für andere im UCP angezeigte Objekte aus Konflikten bei der Groß- und Kleinschreibung im UCP stammen, wie Datenbankdatei- und Dateigruppennamen.  
  
-   Wenn eine verwaltete Instanz von [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] auf einem Windows Server 2003-Computer gehostet wird, muss das [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] -Agent-Dienstkonto der Sicherheitsgruppe Systemmonitorbenutzer oder der lokalen Gruppe Administratoren angehören. Andernfalls meldet die Datensammlung den Fehler, dass der Zugriff verweigert wurde. Um der Sicherheitsgruppe der Systemmonitorbenutzer ein [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] -Agent-Dienstkonto hinzuzufügen, führen Sie die folgenden Schritte aus:  
  
    1.  Erweitern Sie unter **Computerverwaltung**den Eintrag **Lokale Benutzer und Gruppen**, und klicken Sie dann auf **Gruppen**.  
  
    2.  Klicken Sie mit der rechten Maustaste auf **Systemmonitorbenutzer** , und wählen Sie **Zur Gruppe hinzufügen**aus.  
  
    3.  Klicken Sie auf **Hinzufügen**.  
  
    4.  Geben Sie das Konto ein, unter dem der SQL Server-Agent-Dienst ausgeführt wird, und klicken Sie dann auf **OK**.  
  
    5.  Wenn die Instanz von [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] bereits beim UCP registriert war, bevor der Benutzer dieser Gruppe hinzugefügt wurde, starten Sie den [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] -Agent-Dienst neu.  
  
## <a name="see-also"></a>Siehe auch  
 [Funktionen und Tasks im SQL Server-Hilfsprogramm](../relational-databases/manage/sql-server-utility-features-and-tasks.md)   
 [Fehlerbehebung für die SQL Server-Ressourcenintegrität &#40;SQL Server-Hilfsprogramm&#41;](../relational-databases/manage/troubleshoot-sql-server-resource-health-sql-server-utility.md)  
  
  
