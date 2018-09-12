---
title: Problembehandlung bei SQL Server-Hilfsprogramm | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: f5f47c2a-38ea-40f8-9767-9bc138d14453
caps.latest.revision: 8
author: mashamsft
ms.author: mathoma
manager: craigg
ms.openlocfilehash: d059ac17d901ca7eec0bf451ba7babaecce607a8
ms.sourcegitcommit: 8ae6e6618a7e9186aab3c6a37ea43776aa9a382b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/06/2018
ms.locfileid: "43815746"
---
# <a name="troubleshoot-the-sql-server-utility"></a>Problembehandlung beim SQL Server-Hilfsprogramm
  Die Behebung von Problemen mit dem [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]-Hilfsprogramm kann das Auflösen eines fehlgeschlagenen Vorgangs zur Registrierung einer Instanz von SQL Server mit einem UCP, die Behebung von Fehlern bei Datensammlungen, die zu grauen Symbolen in der Listenansicht der verwalteten Instanzen auf einem UCP führen, die Abhilfe für Leistungsengpässe oder das Beheben von Problemen mit der Ressourcenintegrität umfassen. Weitere Informationen zum Beheben von Problemen mit der ressourcenintegrität identifizierte eine [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] ucp stammen, finden Sie unter [Problembehandlung bei SQL Server-Ressourcenintegrität &#40;SQL Server-Hilfsprogramm&#41;](../relational-databases/manage/troubleshoot-sql-server-resource-health-sql-server-utility.md).  
  
## <a name="failed-operation-to-enroll-an-instance-of-sql-server-into-a-sql-server-utility"></a>Fehlgeschlagener Vorgang, eine Instanz von SQL Server in ein SQL Server-Hilfsprogramm zu registrieren  
 Wenn Sie eine Verbindung mit der Instanz von herstellen [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] die Registrierung über [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Authentifizierung, und Sie ein Proxykonto angeben, die zu einer anderen Active Directory-Domäne als der Domäne gehört, in dem der UCP befindet, instanzüberprüfung erfolgreich, aber die Registrierungsvorgang schlägt mit der folgenden Fehlermeldung fehl:  
  
 Beim Ausführen einer Transact-SQL-Anweisung oder eines Batches ist eine Ausnahme aufgetreten. (Microsoft.SqlServer.ConnectionInfo)  
  
 Weitere Informationen: Konnte keine Informationen zu Windows NT Gruppe/Benutzer abrufen '\<DomainName\AccountName>', Fehlercode 0x5. (Microsoft SQL Server, Fehler: 15404)  
  
 Das Problem tritt im folgenden Beispielszenario auf:  
  
1.  Der UCP ist ein Element von "Domain_1."  
  
2.  Eine unidirektionale Domänenvertrauensstellung ist vorhanden: das heißt, "Domain_1" wird nicht von "Domain_2" vertraut, aber "Domain_2" wird von "Domain_1" vertraut.  
  
3.  Die Instanz von [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)], die in das [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]-Hilfsprogramm registriert werden soll, ist auch ein Element von "Domain_1."  
  
4.  Stellen Sie während des Registrierungsvorgangs eine Verbindung mit der Instanz von [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] her, um sich mit "sa" zu registrieren. Geben Sie ein Proxykonto bei "Domain_2" an.  
  
5.  Die Überprüfung ist erfolgreich, aber die Registrierung schlägt fehl.  
  
 Die Umgehung für dieses Problem besteht darin, eine Verbindung mit der Instanz von [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] herzustellen, um sich in das [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]-Hilfsprogramm mit "sa" zu registrieren und ein Proxykonto bei "Domain_1" bereitzustellen.  
  
## <a name="failed-wmi-validation"></a>Fehlgeschlagene WMI-Überprüfung  
 Wenn WMI nicht ordnungsgemäß auf einer Instanz von [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] konfiguriert wird, zeigen die Vorgänge für das Erstellen des UCPs und die Registrierung verwalteter Instanzen eine Warnung an, der Vorgang wird jedoch nicht blockiert. Darüber hinaus, wenn Sie ändern die [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Agent-Kontokonfiguration, damit [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Agent ist nicht berechtigt, die erforderlichen WMI-Klassen, die Datensammlung in der betroffenen verwalteten Instanz von [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] nicht an den UCP hochgeladen werden. Dies führt im UCP zu grauen Symbolen.  
  
 Die fehlgeschlagene Datensammlung führt in der UCP-Listenansicht für betroffene verwaltete Instanzen von [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] zu grauen Statussymbolen. Der Auftragsverlauf auf der verwalteten Instanz von [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] zeigt an, dass sysutility_mi_collect_and_upload bei Schritt 2 (Phasendaten haben sich von PowerShell-Skript gesammelt) fehlschlägt.  
  
 Die vereinfachten Fehlermeldungen sind:  
  
 Die Befehlsausführung wurde beendet, da die Shellvariable "ErrorActionPreference" auf Beenden festgelegt wurde: Zugriff verweigert.  
  
 Fehler: \<Datum / Uhrzeit (MM/TT/JJJJ hh: mm:) >: hat Ausnahme beim Sammeln von CPU-Eigenschaften abgefangen.  Eine WMI-Abfrage könnte fehlgeschlagen sein.  WARNUNG:  
  
 Um dieses Problem zu beheben, überprüfen Sie die folgenden Konfigurationseinstellungen:  
  
-   Unter Windows Server 2003, SQL Server-Agent-Diensts muss Mitglied der Windows-Leistungsüberwachung-Gruppe auf die verwaltete Instanz von [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)].  
  
-   Der WMI-Dienst muss auf der verwalteten Instanz von [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] aktiviert und konfiguriert sein.  
  
-   Das WMI-Repository ist möglicherweise beschädigt, für die verwaltete Instanz von [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)].  
  
-   Die Leistungsbibliothek möglicherweise fehlt oder ist beschädigt, für die verwaltete Instanz von [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)].  
  
 Um zu überprüfen, ob die angegebene Instanz von [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] ordnungsgemäß für Datenberichte an den UCP konfiguriert ist, überprüfen Sie, ob die folgenden Klassen auf der angegebenen Instanz von [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] verfügbar sind und ob auf sie vom SQL Server-Agent-Dienstkonto zugegriffen werden kann:  
  
-   Win32_MountPoint  
  
-   Win32_PerfRawData_PerfProc_Process  
  
-   Win32_PerfRawData_PerfOS_Processor  
  
-   Win32_Processor  
  
-   Win32_Volume  
  
-   Win32_LogicalDisk  
  
 Sie können das Get-WmiObject PowerShell Cmdlet auf jede der Klassen anwenden, um zu überprüfen, dass auf jede Klasse zugegriffen werden kann. Führen die folgenden Cmdlets für die verwaltete Instanz von [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]:  
  
```  
Get-WmiObject Win32_MountPoint -ErrorAction Stop | Out-Null  
Get-WmiObject Win32_PerfRawData_PerfProc_Process -ErrorAction Stop| Out-Null  
Get-WmiObject Win32_PerfRawData_PerfOS_Processor -ErrorAction Stop | Out-Null  
Get-WmiObject Win32_Processor -ErrorAction Stop | Out-Null  
Get-WmiObject Win32_Volume -ErrorAction Stop | Out-Null  
Get-WmiObject Win32_LogicalDisk -ErrorAction Stop | Out-Null  
```  
  
 Weitere Informationen zum Durchführen einer Problembehandlung für WMI finden Sie unter [Problembehandlung bei WMI](http://go.microsoft.com/fwlink/?LinkId=178250). Beachten Sie, dass Abfragen an diese SQL Server-Hilfsprogrammvorgänge lokal ausgeführt werden, so dass DCOM und Remoteproblembehandlungsinhalte nicht gültig sind.  
  
## <a name="failed-data-collection"></a>Fehlerhafte Datensammlung  
 Wenn [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Datensammlungsereignisse mehr Dienstprogramm ein Fehler auftreten, sollten Sie die folgenden Möglichkeiten:  
  
-   Ändern Sie keine Eigenschaften des Sammlungssatzes "Hilfsprogramminformationen" in einer verwalteten Instanz von [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)], und aktivieren/deaktivieren Sie die Datensammlung nicht manuell, da die Datensammlung von einem Hilfsprogramm-Agentauftrag gesteuert wird.  
  
-   Fehlgeschlagene oder nicht unterstützte WMI-Überprüfung. Weitere Informationen finden Sie im Abschnitt "Fehlgeschlagene WMI-Überprüfung" weiter oben in diesem Thema.  
  
-   Aktualisieren von Daten in die Listenansicht verwalteter Instanzen angezeigt, wenn sich Daten in [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Hilfsprogramm Standpunkte wird nicht automatisch aktualisiert. Um Daten zu aktualisieren, Informationen zu diesem mit der rechten Maustaste die **verwaltete Instanzen** Knoten in der **Hilfsprogramm-Explorer-Navigationsbereich** Bereich, wählen Sie dann **aktualisieren**, oder mit der rechten Maustaste auf die [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Instanzname in der Liste angezeigt, und wählen Sie dann **aktualisieren**. Nachdem eine Instanz von [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] bei einem UCP registriert wurde, kann es bis zu 30 Minuten dauern, bis die ersten Daten im Inhaltsbereich des Hilfsprogramm-Explorers im Dashboard und in den Blickpunkten angezeigt werden.  
  
-   Verwenden Sie SQL Server-Konfigurations-Manager, um zu überprüfen, ob die Instanz von [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] ausgeführt wird.  
  
-   Wenn die Datensammlung oder das Hochladen von Daten aufgrund von Timeoutproblemen scheitern, aktualisieren Sie die Funktion dbo.fn_sysutility_mi_get_collect_script() in der MSDB-Datenbank. Fügen Sie insbesondere in der Funktion "Invoke-BulkCopyCommand()" die folgende Zeile hinzu:  
  
    ```  
    $bulkCopy.BulkCopyTimeout=180  
    ```  
  
     Der Standard-Timeoutwert beträgt 30 Sekunden.  
  
-   Wenn die Instanz von [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] nicht gruppiert ist, überprüfen Sie, ob der [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]-Agent-Dienst ausgeführt wird und ob der Dienst für den automatischen Start auf dem UCP und in der verwalteten Instanz von [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] eingerichtet wurde.  
  
-   Stellen Sie sicher, dass ein gültiges Konto verwendet wird, führen Sie die Datensammlung für die verwaltete Instanz von [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]. Möglicherweise ist das Kennwort z. B. abgelaufen. Wenn das Proxykennwort abgelaufen ist, aktualisieren Sie die Kennwort-Anmeldeinformationen in SSMS wie folgt:  
  
    1.  Erweitern Sie im **Objekt-Explorer**von SSMS den Knoten **Sicherheit** und dann den Knoten **Anmeldeinformationen** .  
  
    2.  Mit der rechten Maustaste auf **UtilityAgentProxyCredential_\<GUID >** , und wählen Sie **Eigenschaften**.  
  
    3.  Aktualisieren Sie im Dialogfeld Eigenschaften für Anmeldeinformationen Anmeldeinformationen nach Bedarf für die **UtilityAgentProxyCredential_\<GUID >** Anmeldeinformationen.  
  
    4.  Klicken Sie auf **OK** , um die Änderung zu bestätigen.  
  
-   TCP/IP muss aktiviert sein, auf dem UCP und in der verwalteten Instanz von [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]. Aktivieren Sie TCP/IP über [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Konfigurations-Manager.  
  
-   Der SQL Server-Browserdienst auf dem UCP sollte gestartet werden und für den automatischen Start konfiguriert sein. Wenn die Verwendung des SQL Server-Browserdiensts in Ihrer Organisation verhindert wird, führen Sie die folgenden Schritte aus, damit eine verwaltete Instanz von [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] eine Verbindung mit dem UCP herstellen kann:  
  
    1.  Klicken Sie auf der Windows-Taskleiste der verwalteten Instanz von [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)], klicken Sie auf **starten**, klicken Sie dann auf **ausführen...** .  
  
    2.  Geben Sie im dafür vorgesehenen Feld **cliconfg.exe**ein, und klicken Sie auf OK.  
  
    3.  Sobald Sie aufgefordert werden, die EXE-Datei für das SQL Server-Clientkonfigurationsprogramm zu starten, klicken Sie auf**Weiter**.  
  
    4.  Wählen Sie im Dialogfeld **SQL Server-Clientkonfigurationsprogramm** die Registerkarte **Alias** aus, und klicken Sie auf **Hinzufügen**.  
  
    5.  Im Dialogfeld **Netzwerkbibliothekskonfiguration hinzufügen** :  
  
    6.  Geben Sie in der Liste der Netzwerkbibliotheken TCP/IP an.  
  
    7.  Geben Sie den **ComputerName\InstanceName** des UCPs im Textfeld Serveralias an.  
  
    8.  Geben Sie den **ComputerName** des UCPs im Textfeld Servername an.  
  
    9. Deaktivieren Sie das Kontrollkästchen **Anschluss dynamisch bestimmen** .  
  
    10. Geben Sie die Nummer des Anschlusses, an dem der UCP lauscht, im Textfeld **Anschlussnummer** an.  
  
    11. Klicken Sie auf **OK** , um die Änderungen zu speichern.  
  
    12. Wiederholen Sie diese Schritte für jede verwaltete Instanz von [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] , verbindet sich mit einem UCP, in dem die SQL Server-Browser-Dienst ist nicht aktiviert.  
  
-   Stellen Sie sicher, dass verwaltete Instanzen von [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] mit dem Netzwerk verbunden sind.  
  
-   Wenn Datenbanken mit dem gleichen Namen, aber unterschiedlichen Einstellungen im Hinblick auf die Berücksichtigung von Groß- und Kleinschreibung für eine verwaltete Instanz von [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] vorhanden sind, kann die Datenauflistung fehlschlagen. Eine Datenbank mit dem Namen "MYDATABASE" könnte z. B. Integritätszustände für eine Datenbank mit dem Namen "MYDATABASE" anzeigen. Bei diesem Szenario wird kein Fehler generiert. Die fehlgeschlagene Datensammlung kann auch für andere im UCP angezeigte Objekte aus Konflikten bei der Groß- und Kleinschreibung im UCP stammen, wie Datenbankdatei- und Dateigruppennamen.  
  
-   Wenn eine verwaltete Instanz von [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] auf einem Windows Server 2003-Computer gehostet wird, muss das [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]-Agent-Dienstkonto der Sicherheitsgruppe Systemmonitorbenutzer oder der lokalen Gruppe Administratoren angehören. Andernfalls meldet die Datensammlung den Fehler, dass der Zugriff verweigert wurde. Hinzufügen einer [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Agent-Dienstkonto der Sicherheitsgruppe Systemmonitorbenutzer, gehen Sie folgendermaßen vor:  
  
    1.  Erweitern Sie unter **Computerverwaltung**den Eintrag **Lokale Benutzer und Gruppen**, und klicken Sie dann auf **Gruppen**.  
  
    2.  Klicken Sie mit der rechten Maustaste auf **Systemmonitorbenutzer** , und wählen Sie **Zur Gruppe hinzufügen**aus.  
  
    3.  Klicken Sie auf **Hinzufügen**.  
  
    4.  Geben Sie das Konto ein, unter dem der SQL Server-Agent-Dienst ausgeführt wird, und klicken Sie dann auf **OK**.  
  
    5.  Wenn die Instanz von [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] bereits beim UCP registriert war, bevor der Benutzer dieser Gruppe hinzugefügt wurde, starten Sie den [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]-Agent-Dienst neu.  
  
## <a name="see-also"></a>Siehe auch  
 [Funktionen und Tasks im SQL Server-Hilfsprogramm](../relational-databases/manage/sql-server-utility-features-and-tasks.md)   
 [Fehlerbehebung für die SQL Server-Ressourcenintegrität &#40;SQL Server-Hilfsprogramm&#41;](../relational-databases/manage/troubleshoot-sql-server-resource-health-sql-server-utility.md)  
  
  
