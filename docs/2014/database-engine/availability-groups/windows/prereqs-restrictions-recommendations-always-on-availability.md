---
title: Voraussetzungen, Einschränkungen und Empfehlungen für AlwaysOn-Verfügbarkeitsgruppen (SQLServer) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/14/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
helpviewer_keywords:
- Availability Groups [SQL Server], server instance
- Availability Groups [SQL Server], deploying
- Availability Groups [SQL Server], WSFC clusters
- Availability Groups [SQL Server], about
- Availability Groups [SQL Server], prerequisites and restrictions
- Availability Groups [SQL Server], Failover Cluster Instances
- Availability Groups [SQL Server], databases
- Availability Groups [SQL Server]
ms.assetid: edbab896-42bb-4d17-8d75-e92ca11f7abb
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 047d635be9ff9a9b04770f4ebe3f9e31408ff83d
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "62789867"
---
# <a name="prerequisites-restrictions-and-recommendations-for-alwayson-availability-groups-sql-server"></a>Voraussetzungen, Einschränkungen und Empfehlungen für AlwaysOn-Verfügbarkeitsgruppen (SQL Server)
  In diesem Thema werden Überlegungen zur Bereitstellung von [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)]beschrieben, einschließlich Voraussetzungen, Einschränkungen und Empfehlungen für Hostcomputer, Windows Server Failover Clustering (WSFC)-Cluster, Serverinstanzen und Verfügbarkeitsgruppen. Für alle Komponenten sind Überlegungen zur Sicherheit und ggf. erforderliche Berechtigungen angegeben.  
  
> [!IMPORTANT]  
>  Vor der Bereitstellung von [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)]wird empfohlen, dieses Thema vollständig zu lesen.  
  
 
  
##  <a name="DotNetHotfixes"></a> .NET-Hotfixes, die AlwaysOn-Verfügbarkeitsgruppen unterstützen  
 Abhängig von den [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] -Komponenten und -Funktionen, die Sie mit [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)]verwenden, müssen Sie möglicherweise zusätzliche in der folgenden Tabelle angegebene .NET-Hotfixes installieren. Die Hotfixes können in beliebiger Reihenfolge installiert werden.  
  
||Abhängige Funktion|Hotfix|Link|  
|------|-----------------------|------------|----------|  
|![Kontrollkästchen](../../media/checkboxemptycenterxtraspacetopandright.gif "Kontrollkästchen")|[!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)]|Hotfix für .NET 3.5 SP1 fügt dem SQL-Client Unterstützung für die AlwaysOn-Funktionen "Read-intent", "readonly" und "multisubnetfailover" hinzu. Der Hotfix muss auf allen [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] -Berichtsservern installiert werden.|KB 2654347: [Hotfix für .net 3.5 SP1 zur Unterstützung für AlwaysOn-Funktionen](https://go.microsoft.com/fwlink/?LinkId=242896)|  
  
##  <a name="SystemReqsForAOAG"></a> Windows-Systemanforderungen und -Empfehlungen  
  
  
###  <a name="SystemRequirements"></a> Prüfliste: Anforderungen (Windows-System)  
 Zur Unterstützung der Funktion [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] muss gewährleistet sein, dass jeder Computer, der an mindestens einer Verfügbarkeitsgruppe teilnehmen soll, die folgenden wesentlichen Anforderungen erfüllt:  
  
||Anforderung|Link|  
|------|-----------------|----------|  
|![Kontrollkästchen](../../media/checkboxemptycenterxtraspacetopandright.gif "Kontrollkästchen")|Stellen Sie sicher, dass es sich bei diesem System nicht um einen Domänencontroller handelt.|Verfügbarkeitsgruppen werden nicht auf Domänencontrollern unterstützt.|  
|![Kontrollkästchen](../../media/checkboxemptycenterxtraspacetopandright.gif "Kontrollkästchen")|Stellen Sie sicher, dass auf jedem Computer x86 (Nicht-WOW64) oder x64 Windows Server 2008 oder höhere Versionen ausgeführt werden.|WOW64 (Windows-32-Bit unter Windows-64-Bit) unterstützt [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)]nicht.|  
|![Kontrollkästchen](../../media/checkboxemptycenterxtraspacetopandright.gif "Kontrollkästchen")|Stellen Sie sicher, dass es sich bei jedem Computer um einen Knoten in einem Windows Server Failover Clustering (WSFC)-Cluster handelt.|[Windows Server-Failoverclustering &#40;WSFC&#41; mit SQL Server](../../../sql-server/failover-clusters/windows/windows-server-failover-clustering-wsfc-with-sql-server.md)|  
|![Kontrollkästchen](../../media/checkboxemptycenterxtraspacetopandright.gif "Kontrollkästchen")|Stellen Sie sicher, dass der WSFC-Cluster ausreichend Knoten enthält, um die Verfügbarkeitsgruppenkonfigurationen zu unterstützen.|Ein WSF-Knoten kann nur ein Verfügbarkeitsreplikat für eine bestimmte Verfügbarkeitsgruppe hosten. In einem angegebenen WSFC-Knoten kann mindestens eine Instanz von [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Verfügbarkeitsreplikate für viele Verfügbarkeitsgruppen hosten.<br /><br /> Fragen Sie die Datenbankadministratoren, wie viele WSFC-Knoten erforderlich sind, um die Verfügbarkeitsreplikate der geplanten Verfügbarkeitsgruppen zu unterstützen.<br /><br /> [Übersicht über AlwaysOn-Verfügbarkeitsgruppen &#40;SQL Server&#41;](overview-of-always-on-availability-groups-sql-server.md).|  
|![Kontrollkästchen](../../media/checkboxemptycenterxtraspacetopandright.gif "Kontrollkästchen")|Es müssen alle Windows-Hotfixes auf allen Knoten im WSFC-Cluster installiert sein.|**\*\* Wichtige \* \***  einige Hotfixes sind erforderlich oder empfohlen, für die Knoten eines wsfc-, auf dem Clusters [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] bereitgestellt wird. Weitere Informationen finden Sie weiter unten in diesem Abschnitt unter [Windows-Hotfixes, die AlwaysOn-Verfügbarkeitsgruppen unterstützen (Windows-System)](#WinHotfixes).|  
  
> [!IMPORTANT]  
>  Stellen Sie zudem sicher, dass Ihre Umgebung ordnungsgemäß zum Herstellen einer Verbindung mit einer Verfügbarkeitsgruppe konfiguriert wird. Weitere Informationen finden Sie unter [AlwaysOn-Clientkonnektivität (SQL Server)](always-on-client-connectivity-sql-server.md).  
  
####  <a name="WinHotfixes"></a> Windows-Hotfixes, die Unterstützung von AlwaysOn-Verfügbarkeitsgruppen (Windows-System)  
 Abhängig von der Clustertopologie sind möglicherweise einige zusätzliche Windows Server 2008 Service Pack (SP2)- oder Windows Server R2-Hotfixes zur Unterstützung von [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)]anwendbar. In der folgenden Tabelle sind diese Hotfixes angegeben. Die Hotfixes können in beliebiger Reihenfolge installiert werden.  
  
||Gilt für Windows 2008 SP2|Gilt für Windows 2008 R2 SP1|Im Lieferumfang von Windows 2012 enthalten|Zur Unterstützung von...|Hotfix|Link|  
|------|---------------------------------|------------------------------------|------------------------------|-----------------|------------|----------|  
|![Kontrollkästchen](../../media/checkboxemptycenterxtraspacetopandright.gif "Kontrollkästchen")|Ja|Ja|Ja|**Konfigurieren der optimalen WSFC-Quorums**|Stellen Sie in jedem WSFC-Knoten sicher, dass der im Knowledge Base-Artikel 2494036 beschriebene Hotfix installiert ist.<br /><br /> Dieser Hotfix unterstützt das Konfigurieren eines optimalen Quorums mit nicht automatischen Failoverzielen. Diese Funktionalität verbessert Cluster mit mehreren Standorten, indem sie Ihnen die Auswahl der Abstimmungsknoten ermöglicht.|KB 2494036:  [Ein Hotfix ist verfügbar, mit dem sich ein Clusterknoten konfigurieren, der keine quorumabstimmung in Windows Server 2008 und in Windows Server 2008 R2 verfügt](https://support.microsoft.com/kb/2494036)<br /><br /> Informationen zu Quorumabstimmungen finden Sie unter [WSFC-Quorummodi und Abstimmungskonfiguration &#40;SQL Server&#41;](../../../sql-server/failover-clusters/windows/wsfc-quorum-modes-and-voting-configuration-sql-server.md)|  
|![Kontrollkästchen](../../media/checkboxemptycenterxtraspacetopandright.gif "Kontrollkästchen")|Ja|Ja|Ja|**Eine effizientere Nutzung der Netzwerkbandbreite**|Stellen Sie in jedem WSFC-Knoten sicher, dass der im Knowledge Base-Artikel 2616514 beschriebene Hotfix installiert ist.<br /><br /> Ohne diesen Hotfix sendet der Cluster unnötige Registrierungsbenachrichtigungen an die Clusterknoten. Dies stellt ein ernsthaftes Problem für [!INCLUDE[ssHADRc](../../../includes/sshadrc-md.md)]dar, weil die Netzwerkbandbreite durch dieses Verhalten eingeschränkt wird.|KB 2616514:  [Der Clusterdienst sendet unnötige änderungsbenachrichtigungen zu Clusterknoten in Windows Server 2008 oder Windows Server 2008 R2](https://support.microsoft.com/kb/2616514)|  
|![Kontrollkästchen](../../media/checkboxemptycenterxtraspacetopandright.gif "Kontrollkästchen")||Ja|Nicht verfügbar|**VPD-Speichertests auf Datenträgern, die nicht für alle WSFC-Knoten verfügbar sind.**|Falls auf einem WSFC-Knoten Windows Server 2008 R2 Service Pack 1 (SP1) ausgeführt wird und der Speichertest "VPD (Vital Product Data) des SCSI-Geräts überprüfen" einen Fehler verursacht, nachdem er fälschlicherweise auf Datenträgern ausgeführt wurde, die online sind und nicht für alle Knoten im WSFC-Cluster verfügbar sind, installieren Sie den im Knowledge Base-Artikel 2531907 beschriebenen Hotfix.<br /><br /> Dieser Hotfix verhindert falsche Warnungen oder Fehler im Überprüfungsbericht, wenn Datenträger online sind.|KB 2531907:  [Überprüfen der SCSI VITAL Product Geräts Daten () Test schlägt fehl, nach der Installation von Windows Server 2008 R2 SP1](https://support.microsoft.com/kb/2531907)|  
|![Kontrollkästchen](../../media/checkboxemptycenterxtraspacetopandright.gif "Kontrollkästchen")||Ja|Ja|**Schnelleres Failover auf lokale Replikate**|Wenn in einem WSFC-Knoten Windows Server 2008 R2 Service Pack 1 (SP1) ausgeführt wird, stellen Sie sicher, dass der in Knowledge Base-Artikel 2687741 beschriebene Hotfix installiert ist.<br /><br /> Dieser Hotfix verbessert die Leistung des [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] -Failovers auf lokale Replikate.|KB 2687741:  [Es ist ein Hotfix die Leistung der "AlwaysOn-Verfügbarkeitsgruppen"-Funktion in SQL Server 2012 verbessert für Windows Server 2008 R2 verfügbar](https://support.microsoft.com/KB/2687741)|  
|![Kontrollkästchen](../../media/checkboxemptycenterxtraspacetopandright.gif "Kontrollkästchen")|Ja|Ja|Ja|**Asymmetrischer Speicher – für Failoverclusterinstanzen (FCIs)**|Installieren Sie das Windows Server 2008-Hotfix 976097, wenn eine Failoverclusterinstanz (FCI) für [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)]aktiviert wird.<br /><br /> Dieser Hotfix aktiviert das Failover Cluster Management Microsoft Management Console (MMC)-Snap-in zur Unterstützung von asymmetrischen Speicher freigegebenen Datenträgern, die nur auf einigen WSFC-Knoten verfügbar sind.|KB 976097:  [Hotfix zum Hinzufügen der Unterstützung für asymmetrische Speicher zum MMC-Failovercluster-Verwaltungs-Snap-in für einen Failovercluster, auf denen Windows Server 2008 oder Windows Server 2008 R2 ausgeführt wird](https://support.microsoft.com/kb/976097)<br /><br /> [AlwaysOn-Architekturhandbuch: Erstellen einer Lösung für Hochverfügbarkeit und Notfallwiederherstellung unter Verwendung von Failoverclusterinstanzen und Verfügbarkeitsgruppen](https://technet.microsoft.com/library/jj215886.aspx)|  
|![Kontrollkästchen](../../media/checkboxemptycenterxtraspacetopandright.gif "Kontrollkästchen")|Ja|Ja|Nicht verfügbar|**Internet Protocol Security (IPsec)**|Wenn in Ihrer Umgebung IPsec-Verbindungen verwendet werden, kann eine lange Verzögerung (von ca. zwei oder drei Minuten) eintreten, wenn ein Clientcomputer die IPsec-Verbindung mit dem Namen eines virtuellen Netzwerks erneut herstellt (in diesem Kontext, um eine Verbindung mit dem Verfügbarkeitsgruppenlistener herzustellen). Wenn Sie IPsec-Verbindungen verwenden, wird empfohlen, dass Sie sich über die im Knowledge Base-Artikel (KB 980915) aufgeführten speziellen Szenarien informieren.|KB 980915:  [Eine lange Verzögerung tritt auf, wenn Sie eine IPSec-Verbindung von einem Computer verbinden, auf denen Windows Server 2003, Windows Vista, Windows Server 2008, Windows 7 oder Windows Server 2008 R2 ausgeführt wird](https://support.microsoft.com/kb/980915)|  
|![Kontrollkästchen](../../media/checkboxemptycenterxtraspacetopandright.gif "Kontrollkästchen")|Ja|Ja|Ja|**IPv6**|Bei Verwendung von IPv6 wird empfohlen, die zum jeweiligen Windows Server-Betriebssystem passenden Informationen zu spezifischen Szenarien in Knowledge Base-Artikel 2578103 oder 2578113 zu lesen.<br /><br /> Wenn für die Windows Server-Topologie IPv6 (IP Version 6) verwendet wird, benötigt der WSFC-Clusterdienst ungefähr 30 Sekunden, um ein Failover auf die IPv6-IP-Adresse auszuführen. Dies führt dazu, dass Clients ungefähr 30 Sekunden warten müssen, um erneut eine Verbindung mit der IPv6-IP-Adresse herzustellen.|KB 2578103 (Windows Server 2008):  [Der Clusterdienst dauert ungefähr 30 Sekunden zum Failover von IPv6-IP-Adressen in Windows Server 2008](https://support.microsoft.com/kb/2578103)<br /><br /> KB 2578113 (Windows Server 2008 R2):  **Windows Server 2008 R2:** [Der Clusterdienst dauert ungefähr 30 Sekunden zum Failover von IPv6-IP-Adressen in Windows Server 2008 R2](https://support.microsoft.com/kb/2578113)|  
|![Kontrollkästchen](../../media/checkboxemptycenterxtraspacetopandright.gif "Kontrollkästchen")|Ja|Ja|Ja|**Kein Router zwischen Cluster und Anwendung-server**|Falls zwischen dem Failovercluster und dem Anwendungsserver kein Router vorhanden ist, führt der Clusterdienst ein Failover der netzwerkbezogenen Ressourcen langsam aus. Dadurch werden erneute Clientverbindungen nach dem Failover einer Verfügbarkeitsgruppe verzögert. Wenn kein Router vorhanden ist, wird empfohlen, die spezifischen Szenarien in Knowledge Base-Artikel 2582281 zu lesen und den Hotfix zu installieren, sofern dieser für Ihre Umgebung geeignet ist.|KB 2582281:  [Langsamer Failovervorgang, wenn kein Router zwischen dem Cluster und einem Anwendungsserver vorhanden ist](https://support.microsoft.com/kb/2582281)|  
  
###  <a name="ComputerRecommendations"></a> Empfehlungen für Computer, die Verfügbarkeitsreplikate (Windows-System) hosten  
  
-   **Vergleichbare Systeme:**  Für eine bestimmte Verfügbarkeitsgruppe sollten alle Verfügbarkeitsreplikate auf vergleichbaren Systemen ausgeführt werden, die identische Arbeitslasten bewältigen können.  
  
-   **Dedizierte Netzwerkadapter:**  Für eine optimale Leistung sollten Sie einen dedizierten Netzwerkadapter (NIC, Network Interface Card, Netzwerkschnittstellenkarte) für [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] verwenden.  
  
-   **Genügend freien Speicherplatz:**  Jeder Computer, auf dem eine Serverinstanz ein Verfügbarkeitsreplikat hostet, muss über ausreichend Speicherplatz für alle Datenbanken in der Verfügbarkeitsgruppe verfügen. Bedenken Sie, dass sekundäre Datenbanken in gleichem Maße zunehmen wie ihre entsprechenden primären Datenbanken.  
  
###  <a name="PermissionsWindows"></a> Berechtigungen (Windows-System)  
 Zur Verwaltung eines WSFC-Clusters muss der Benutzer Systemadministrator auf jedem Clusterknoten sein.  
  
 Weitere Informationen über das Konto zum Verwalten des Clusters finden Sie unter [Appendix A: Failover Cluster Requirements (Anhang A: Failoverclusteranforderungen)](https://technet.microsoft.com/library/dd197454\(WS.10\).aspx).  
  
###  <a name="RelatedTasksWindows"></a> Verwandte Aufgaben (Windows-System)  
  
|Aufgabe|Link|  
|----------|----------|  
|Legen Sie den HostRecordTTL-Wert fest.|[Ändern des HostRecordTTL (Verwenden von Windows PowerShell)](#ChangeHostRecordTTLps)|  
  
####  <a name="ChangeHostRecordTTLps"></a> Ändern des HostRecordTTL (Verwenden von Windows PowerShell)  
  
1.  Öffnen Sie das PowerShell-Fenster über **Als Administrator ausführen**.  
  
2.  Importieren Sie das FailoverClusters-Modul.  
  
3.  Verwenden Sie das `Get-ClusterResource`-Cmdlet, um die Netzwerknamenressource zu suchen. Verwenden Sie dann `Set-ClusterParameter`-Cmdlet, um den `HostRecordTTL`-Wert folgendermaßen festzulegen:  
  
     Get-ClusterResource „ *\<Netzwerkressourcenname>* “ | Set-ClusterParameter-HostRecordTTL *\<Zeit_in_Sekunden>*  
  
     Im folgenden PowerShell-Beispiel wird der HostRecordTTL für eine Netzwerknamenressource mit dem Namen "`SQL Network Name (SQL35)`" auf 300 Sekunden festgelegt.  
  
    ```  
    Import-Module FailoverClusters  
  
    $nameResource = "SQL Network Name (SQL35)"  
    Get-ClusterResource $nameResource | Set-ClusterParameter ClusterParameter HostRecordTTL 300  
    ```  
  
    > [!TIP]  
    >  Bei jedem Öffnen eines neuen PowerShell-Fensters müssen Sie das `FailoverClusters`-Modul importieren.  
  
##### <a name="related-content-powershell"></a>Verwandte Inhalte (PowerShell)  
  
-   [Clustering and High-Availability](https://blogs.msdn.com/b/clustering/archive/2009/05/23/9636665.aspx) (Clustering und hohe Verfügbarkeit) (Failoverclustering und Netzwerklastenausgleichs-Teamblog)  
  
-   [Erste Schritte mit Windows PowerShell auf einem Failovercluster](https://technet.microsoft.com/library/ee619762\(WS.10\).aspx)  
  
-   [Clusterressourcenbefehle und entsprechende Windows PowerShell-Cmdlets](https://msdn.microsoft.com/library/ee619744.aspx#BKMK_resource)  
  
###  <a name="RelatedContentWS"></a> Verwandte Inhalte (Windows-System)  
  
-   [Konfigurieren von DNS-Einstellungen in einem Failovercluster für mehrere Standorte](https://technet.microsoft.com/library/dd197562\(WS.10\).aspx)  
  
-   [DNS-Registrierung mit Netzwerknamenressource](https://blogs.msdn.com/b/clustering/archive/2009/07/17/9836756.aspx)  
  
-   [Windows 2008 R2 Failover Multisite Clustering](https://kiruba4u.blogspot.com/2012/03/failover-clustering-in-windows-server.html)  
  
##  <a name="ServerInstance"></a> Voraussetzungen und Einschränkungen für SQL Server-Instanzen  
 Jede Verfügbarkeitsgruppe erfordert einen Satz Failoverpartner, die als *Verfügbarkeitsreplikate*bezeichnet und von Instanzen von [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]gehostet werden. Bei einer angegebenen Serverinstanz kann es sich um eine *eigenständige Instanz* oder eine [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]*Failovercluster-Instanz* (FCI) handeln.  
  
 
  
###  <a name="PrerequisitesSI"></a> Prüfliste: Voraussetzungen (Serverinstanz)  
  
||Voraussetzung|Links|  
|-|------------------|-----------|  
|![Kontrollkästchen](../../media/checkboxemptycenterxtraspacetopandright.gif "Kontrollkästchen")|Beim Hostcomputer muss es sich um einen WSFC-Knoten (Windows Server Failover Clustering) handeln. Die Instanzen von [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] , die Verfügbarkeitsreplikate für eine angegebene Verfügbarkeitsgruppe hosten, müssen sich jeweils in einem separaten Knoten eines einzelnen WSFC-Clusters befinden. Die einzige Ausnahme besteht darin, dass sich eine Verfügbarkeitsgruppe während der Migration zu einem anderen WSFC-Cluster vorübergehend auf zwei Cluster erstrecken kann.|[Windows Server-Failoverclustering &#40;WSFC&#41; mit SQL Server](../../../sql-server/failover-clusters/windows/windows-server-failover-clustering-wsfc-with-sql-server.md)<br /><br /> [Failoverclustering und AlwaysOn-Verfügbarkeitsgruppen &#40;SQLServer&#41;](failover-clustering-and-always-on-availability-groups-sql-server.md)|  
|![Kontrollkästchen](../../media/checkboxemptycenterxtraspacetopandright.gif "Kontrollkästchen")|Wenn eine Verfügbarkeitsgruppe mit Kerberos verwendet werden soll:<br /><br /> Alle Serverinstanzen, die ein Verfügbarkeitsreplikat für die Verfügbarkeitsgruppe hosten, müssen das gleiche SQL Server-Dienstkonto verwenden.<br /><br /> Der Domänenadministrator muss manuell einen Dienstprinzipalnamen (SPN) für Active Directory auf dem SQL Server-Dienstkonto beim virtuellen Netzwerknamen (VNN) des Verfügbarkeitsgruppenlisteners registrieren. Wenn der SPN auf keinem SQL Server-Dienstkonto registriert wird, treten bei der Authentifizierung Fehler auf.<br /><br /> **\*\* Wichtig \*\*** : Wenn Sie das SQL Server-Dienstkonto ändern, muss der Domänenadministrator den SPN erneut manuell registrieren.|[Registrieren eines Dienstprinzipalnamens für Kerberos-Verbindungen](../../configure-windows/register-a-service-principal-name-for-kerberos-connections.md)<br /><br /> **Kurze Erklärung:**<br /><br /> Kerberos und SPNs erzwingen die gegenseitige Authentifizierung. Dem Windows-Konto, das die SQL Server-Dienste startet, wird der SPN zugeordnet. Wenn die Registrierung des SPNs nicht richtig erfolgt oder dabei ein Fehler aufgetreten ist, kann die Windows-Sicherheitsschicht nicht das Konto bestimmen, das dem Dienstprinzipalname zugewiesen ist. Das bedeutet, die Kerberos-Authentifizierung kann nicht verwendet werden.<br /><br /> Hinweis: Bei NTLM gibt es diese Anforderung nicht.|  
|![Kontrollkästchen](../../media/checkboxemptycenterxtraspacetopandright.gif "Kontrollkästchen")|Wenn Sie planen, eine [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] -Failoverclusterinstanz (FCI) zu verwenden, um ein Verfügbarkeitsreplikat zu hosten, muss gewährleistet sein, dass Sie die FCI-Einschränkungen verstehen und dass die FCI-Anforderungen erfüllt werden.|[Voraussetzungen und Anforderungen zum Hosten eines Verfügbarkeitsreplikats mithilfe einer SQL Server-Failoverclusterinstanz (FCI)](#FciArLimitations) (später in diesem Thema)|  
|![Kontrollkästchen](../../media/checkboxemptycenterxtraspacetopandright.gif "Kontrollkästchen")|Auf jeder Serverinstanz muss die Enterprise Edition von [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)]ausgeführt werden.|[Von den SQL Server 2014-Editionen unterstützte Funktionen](../../../getting-started/features-supported-by-the-editions-of-sql-server-2014.md)|  
|![Kontrollkästchen](../../media/checkboxemptycenterxtraspacetopandright.gif "Kontrollkästchen")|Alle Serverinstanzen, die Verfügbarkeitsreplikate für eine Verfügbarkeitsgruppe hosten, müssen die gleiche [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] -Sortierung verwenden.|[Festlegen oder Ändern der Serversortierung](../../../relational-databases/collations/set-or-change-the-server-collation.md)|  
|![Kontrollkästchen](../../media/checkboxemptycenterxtraspacetopandright.gif "Kontrollkästchen")|Aktivieren Sie die Funktion [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] auf jeder Serverinstanz, die ein Verfügbarkeitsreplikat für jede Verfügbarkeitsgruppe hostet. Auf einem angegebenen Computer können Sie so viele Serverinstanzen für [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] aktivieren, wie Ihre [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] -Installation unterstützt.|[Aktivieren und Deaktivieren von Always On-Verfügbarkeitsgruppen &#40;SQL Server&#41;](enable-and-disable-always-on-availability-groups-sql-server.md)<br /><br /> **\*\* Wichtig \*\*** : Wenn Sie einen WSFC-Cluster löschen und neu erstellen, müssen Sie die Funktion [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] auf jeder Serverinstanz, die auf dem ursprünglichen WSFC-Cluster für [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] aktiviert war, deaktivieren und erneut aktivieren.|  
|![Kontrollkästchen](../../media/checkboxemptycenterxtraspacetopandright.gif "Kontrollkästchen")|Jede Serverinstanz erfordert einen Datenbankspiegelungs-Endpunkt. Beachten Sie, dass dieser Endpunkt von allen Verfügbarkeitsreplikaten, Datenbank-Spiegelungspartnern und Zeugen auf der Serverinstanz gemeinsam verwendet wird.<br /><br /> Wenn eine Serverinstanz, die Sie zum Hosten eines Verfügbarkeitsreplikats auswählen, unter einem Domänenbenutzerkonto ausgeführt wird und noch keinen Datenbankspiegelungs-Endpunkt aufweist, kann der [Assistent für neue Verfügbarkeitsgruppen](use-the-availability-group-wizard-sql-server-management-studio.md) (oder [Assistent zum Hinzufügen von Replikaten zu Verfügbarkeitsgruppen](use-the-add-replica-to-availability-group-wizard-sql-server-management-studio.md)) den Endpunkt erstellen und dem Dienstkonto der Serverinstanz die CONNECT-Berechtigung erteilen. Wenn der [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] -Dienst jedoch als integriertes Konto, z. B. Lokales System, Lokaler Dienst oder Netzwerkdienst, oder als Nichtdomänenkonto ausgeführt wird, müssen Sie Zertifikate zur Endpunktauthentifizierung verwenden, und der Assistent kann keinen Datenbankspiegelungs-Endpunkt auf der Serverinstanz erstellen. In diesem Fall empfiehlt es sich, dass Sie die Datenbankspiegelungs-Endpunkte manuell erstellen, bevor Sie den Assistenten starten.<br /><br /> **\*\* Sicherheitshinweis \*\*** : Die Transportsicherheit für [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] entspricht derjenigen der Datenbankspiegelung.|[Der Datenbankspiegelungs-Endpunkt &#40;SQL Server&#41;](../../database-mirroring/the-database-mirroring-endpoint-sql-server.md)<br /><br /> [Transportsicherheit für Datenbankspiegelung und AlwaysOn-Verfügbarkeitsgruppen &#40;SQLServer&#41;](../../database-mirroring/transport-security-database-mirroring-always-on-availability.md)|  
|![Kontrollkästchen](../../media/checkboxemptycenterxtraspacetopandright.gif "Kontrollkästchen")|Bevor Datenbanken, die FILESTREAM verwenden, zu einer Verfügbarkeitsgruppe hinzugefügt werden, stellen Sie sicher, dass FILESTREAM auf jeder Serverinstanz, die ein Verfügbarkeitsreplikat für die Verfügbarkeitsgruppe hostet, aktiviert worden ist.|[Aktivieren und Konfigurieren von FILESTREAM](../../../relational-databases/blob/enable-and-configure-filestream.md)|  
|![Kontrollkästchen](../../media/checkboxemptycenterxtraspacetopandright.gif "Kontrollkästchen")|Bevor eigenständige Datenbanken einer Verfügbarkeitsgruppe hinzugefügt werden, muss gewährleistet sein, dass die Serveroption `contained database authentication` auf jeder Serverinstanz, die ein Verfügbarkeitsreplikat für die Verfügbarkeitsgruppe hostet, auf `1` festgelegt wurde.|[Contained Database Authentication (Serverkonfigurationsoption)](../../configure-windows/contained-database-authentication-server-configuration-option.md)<br /><br /> [Serverkonfigurationsoptionen &#40;SQL Server&#41;](../../configure-windows/server-configuration-options-sql-server.md)|  
  
###  <a name="ThreadUsage"></a> Threadverwendung durch Verfügbarkeitsgruppen  
 [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] stellt die folgenden Anforderungen an Arbeitsthreads:  
  
-   Auf einer [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]-Instanz im Leerlauf verwendet [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] 0 Threads.  
  
-   Die maximale Anzahl der von Verfügbarkeitsgruppen verwendeten Threads entspricht der Einstellung, die als maximale Anzahl von Serverthreads ('`max worker threads`') minus 40 konfiguriert wurde.  
  
-   Die auf einer bestimmten Serverinstanz gehosteten Verfügbarkeitsreplikate verwenden einen gemeinsamen Threadpool.  
  
     Threads werden bedarfsgesteuert wie folgt freigegeben:  
  
    -   In der Regel gibt es 3 bis 10 freigegebene Threads, diese Zahl kann sich jedoch abhängig von der Arbeitsauslastung des primären Replikats erhöhen.  
  
    -   Wenn ein bestimmter Thread eine Zeit lang im Leerlauf ist, wird er wieder im allgemeinen [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] -Threadpool freigegeben. Normalerweise wird ein inaktiver Thread nach ~ 15 Sekunden Inaktivität freigegeben. Abhängig von der letzten Aktivität kann ein Thread jedoch länger im Leerlauf gehalten werden.  
  
-   Darüber hinaus verwenden Verfügbarkeitsgruppen nicht freigegebene Threads wie folgt:  
  
    -   Jedes primäre Replikat verwendet einen Protokollaufzeichnungsthread für jede primäre Datenbank. Außerdem verwendet es einen Protokollsendethread für jede sekundäre Datenbank. Protokollsendethreads werden nach ~ 15 Sekunden Inaktivität freigegeben.  
  
    -   Jedes sekundäre Replikat verwendet einen Wiederholungsthread für jede sekundäre Datenbank. Wiederholungsthreads werden nach ~ 15 Sekunden Inaktivität freigegeben.  
  
    -   Von einer Sicherung auf einem sekundären Replikat wird ein Thread auf dem primären Replikat für die Dauer des Sicherungsvorgangs beibehalten.  
  
 Weitere Informationen finden Sie unter [AlwaysON - HADRON-Lernreihe: Worker Pool Usage for HADRON Enabled Databases (Always On – HADRON-Lernreihe: Nutzung des Arbeitspools für HADRON-fähige Datenbanken)](https://blogs.msdn.com/b/psssql/archive/2012/05/17/alwayson-hadron-learning-series-worker-pool-usage-for-hadron-enabled-databases.aspx) (ein CSS-[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]-Engineer-Blogbeitrag).  
  
###  <a name="PermissionsSI"></a> Berechtigungen (Serverinstanz)  
  
|Aufgabe|Erforderliche Berechtigungen|  
|----------|--------------------------|  
|Erstellen des Endpunktes für die Datenbankspiegelung|Erfordert die CREATE ENDPOINT-Berechtigung oder die Mitgliedschaft in der festen Serverrolle **sysadmin** .  Erfordert zudem die CONTROL ON ENDPOINT-Berechtigung. Weitere Informationen finden Sie unter [GRANT (Endpunktberechtigungen) &#40;Transact-SQL&#41;](/sql/t-sql/statements/grant-endpoint-permissions-transact-sql).|  
|Aktivieren von [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)]|Erfordert auf dem lokalen Computer die Mitgliedschaft in der Gruppe **Administrator** und Vollzugriff auf den WSFC-Cluster.|  
  
###  <a name="RelatedTasksSI"></a> Verwandte Aufgaben (Serverinstanz)  
  
|Aufgabe|Thema|  
|----------|-----------|  
|Bestimmen, ob ein Datenbankspiegelungs-Endpunkt vorhanden ist|[sys.database_mirroring_endpoints &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-database-mirroring-endpoints-transact-sql)|  
|Erstellen des Datenbankspiegelungs-Endpunkts (falls noch nicht vorhanden)|[Erstellen eines Endpunkts der Datenbankspiegelung für Windows-Authentifizierung &#40;Transact-SQL&#41;](../../database-mirroring/create-a-database-mirroring-endpoint-for-windows-authentication-transact-sql.md)<br /><br /> [Verwenden von Zertifikaten für einen Datenbankspiegelungs-Endpunkt &#40;Transact-SQL&#41;](../../database-mirroring/use-certificates-for-a-database-mirroring-endpoint-transact-sql.md)<br /><br /> [Erstellen Sie eine Datenbank mit dem Datenbankspiegelungs-Endpunkts für AlwaysOn-Verfügbarkeitsgruppen &#40;SQL Server PowerShell&#41;](database-mirroring-always-on-availability-groups-powershell.md)|  
|Aktivieren der AlwaysOn-Verfügbarkeitsgruppen|[Aktivieren und Deaktivieren von Always On-Verfügbarkeitsgruppen &#40;SQL Server&#41;](enable-and-disable-always-on-availability-groups-sql-server.md)|  
  
###  <a name="RelatedContentSI"></a> Verwandte Inhalte (Serverinstanz)  
  
-   [AlwaysON - HADRON-Lernreihe: Worker Pool Usage for HADRON Enabled Databases (Always On – HADRON-Lernreihe: Nutzung des Arbeitspools für HADRON-fähige Datenbanken)](https://blogs.msdn.com/b/psssql/archive/2012/05/17/alwayson-hadron-learning-series-worker-pool-usage-for-hadron-enabled-databases.aspx)  
  
##  <a name="NetworkConnect"></a> Empfehlungen zur Netzwerkkonnektivität  
 Es wird dringend empfohlen, für die Kommunikation zwischen WSFC-Clusterelementen die gleichen Netzwerkverbindungen zu verwenden wie für die Kommunikation zwischen Verfügbarkeitsreplikaten.  Bei Verwendung separater Netzwerkverbindungen kann ein unerwartetes Verhalten auftreten, wenn einige Verbindungen (wenn auch nur vorübergehend) ausfallen.  
  
 Damit eine Verfügbarkeitsgruppe automatisches Failover unterstützt, muss das sekundäre Replikat, das dem automatischen Failoverpartner entspricht, beispielsweise den Status SYNCHRONIZED aufweisen. Wenn bei der Netzwerkverbindung mit dem sekundären Replikat (wenn auch nur vorübergehend) ein Fehler auftritt, wechselt das Replikat in den Status UNSYNCHRONIZED und wird erst nach Wiederherstellen der Verbindung erneut synchronisiert. Wenn der WSFC-Cluster ein automatisches Failover anfordert, während das sekundäre Replikat nicht synchronisiert ist, findet kein automatisches Failover statt.  
  
##  <a name="ClientConnSupport"></a> Unterstützung für Clientkonnektivität  
 Informationen zu [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] -Unterstützung für Clientkonnektivität, finden Sie unter [AlwaysOn-Clientkonnektivität (SQL Server)](always-on-client-connectivity-sql-server.md).  
  
##  <a name="FciArLimitations"></a> Voraussetzungen und Einschränkungen zum Hosten eines Verfügbarkeitsreplikats mithilfe einer SQL Server-Failoverclusterinstanz (FCI)  
 
  
###  <a name="RestrictionsFCI"></a> Einschränkungen (FCIs)  
  
> [!NOTE]  
>  Ab [!INCLUDE[ssSQL14](../../../includes/sssql14-md.md)]unterstützen AlwaysOn-Failoverclusterinstanzen sowohl in [!INCLUDE[winserver2008r2](../../../includes/winserver2008r2-md.md)] als auch in [!INCLUDE[win8srv](../../../includes/win8srv-md.md)]freigegebene Clustervolumes (Cluster Shared Volumes, CSVs). Weitere Informationen zu CSVs finden Sie unter [Grundlegendes zu freigegebenen Clustervolumes in einem Failovercluster](https://technet.microsoft.com/library/dd759255.aspx).  
  
-   **Ein FCI-Clusterknoten kann nur ein Replikat für eine bestimmte Verfügbarkeitsgruppe hosten:**  Wenn Sie ein verfügbarkeitsreplikat auf einer FCI hinzufügen, können nicht in die WSFC-Clusterknoten, die mögliche FCI-Besitzer sind ein anderes Replikat für dieselbe verfügbarkeitsgruppe hosten.  
  
     Weiter muss jedes andere Replikat von einer SQL Server 2012-Instanz gehostet werden, die sich unter einem anderen WSFC-Knoten desselben WSFC-Clusters befindet. Die einzige Ausnahme besteht darin, dass sich eine Verfügbarkeitsgruppe während der Migration zu einem anderen WSFC-Cluster vorübergehend auf zwei Cluster erstrecken kann.  
  
-   **FCIs unterstützen kein automatisches Failover durch Verfügbarkeitsgruppen:**  FCIs unterstützen kein automatisches Always On-Failover durch Verfügbarkeitsgruppen. Daher können die Verfügbarkeitsreplikate, die von einer FCI gehostet werden, ausschließlich für manuelle Failovers konfiguriert werden.  
  
-   **Ändern des FCI-Netzwerknamens:**  Falls Sie den Netzwerknamen einer FCI ändern müssen, die ein Verfügbarkeitsreplikat hostet, müssen Sie das Replikat aus seiner Verfügbarkeitsgruppe entfernen und das Replikat dann wieder der Verfügbarkeitsgruppe hinzufügen. Sie können das primäre Replikat nicht entfernen. Wenn Sie daher eine FCI umbenennen, die das primäre Replikat hostet, sollten Sie ein Failover zu einem sekundären Replikat ausführen und dann das vorherige primäre Replikat entfernen und wieder hinzufügen. Beachten Sie, dass durch Umbenennen einer FCI möglicherweise die URL ihres Datenbankspiegelungs-Endpunkts geändert wird. Stellen Sie beim Hinzufügen des Replikats sicher, dass Sie die aktuelle Endpunkt-URL angeben.  
  
###  <a name="PrerequisitesFCI"></a>Prüfliste: Voraussetzungen (FCIs)  
  
||Voraussetzung|Link|  
|-|------------------|----------|  
|![Kontrollkästchen](../../media/checkboxemptycenterxtraspacetopandright.gif "Kontrollkästchen")|Bevor Sie ein Verfügbarkeitsreplikat mithilfe einer FCI hosten, muss gewährleistet sein, dass der Systemadministrator das im Knowledge Base-Artikel KB 976097 beschriebene Windows Server 2008-Hotfix installiert hat. Dieser Hotfix aktiviert das Failover Cluster Management Microsoft Management Console (MMC)-Snap-in zur Unterstützung von asymmetrischen Speicher freigegebenen Datenträgern, die nur auf einigen WSFC-Knoten verfügbar sind.|KB 976097:  [Hotfix zum Hinzufügen der Unterstützung für asymmetrische Speicher zum MMC-Failovercluster-Verwaltungs-Snap-in für einen Failovercluster, auf denen Windows Server 2008 oder Windows Server 2008 R2 ausgeführt wird](https://support.microsoft.com/kb/976097)|  
|![Kontrollkästchen](../../media/checkboxemptycenterxtraspacetopandright.gif "Kontrollkästchen")|Stellen Sie sicher, dass jede SQL Server-Failoverclusterinstanz (FCI) den erforderlichen gemeinsam verwendeten Speicher laut Standardinstallation der SQL Server-Failoverclusterinstanz besitzt.||  
  
###  <a name="RelatedTasksFCIs"></a> Verwandte Aufgaben (FCIs)  
  
|Aufgabe|Thema|  
|----------|-----------|  
|Installieren eines SQL Server-Failoverclusters|[Erstellen eines neuen SQL Server-Failoverclusters &#40;Setup&#41;](../../../sql-server/failover-clusters/install/create-a-new-sql-server-failover-cluster-setup.md)|  
|Direktes Upgrade des vorhandenen SQL Server-Failoverclusters|[Aktualisieren einer SQL Server-Failoverclusterinstanz &#40;Setup&#41;](../../../sql-server/failover-clusters/windows/upgrade-a-sql-server-failover-cluster-instance-setup.md)|  
|Beibehalten des vorhandenen SQL Server-Failoverclusters|[Hinzufügen oder Entfernen von Knoten in einem SQL Server-Failovercluster &#40;Setup&#41;](../../../sql-server/failover-clusters/install/add-or-remove-nodes-in-a-sql-server-failover-cluster-setup.md)|  
  
###  <a name="RelatedContentFCIs"></a> Verwandte Inhalte (FCIs)  
  
-   [Failoverclustering und AlwaysOn-Verfügbarkeitsgruppen &#40;SQLServer&#41;](failover-clustering-and-always-on-availability-groups-sql-server.md)  
  
-   [AlwaysOn-Architekturhandbuch: Erstellen einer Lösung für Hochverfügbarkeit und Notfallwiederherstellung unter Verwendung von Failoverclusterinstanzen und Verfügbarkeitsgruppen](https://technet.microsoft.com/library/jj215886.aspx)  
  
##  <a name="PrerequisitesForAGs"></a> Voraussetzungen und Einschränkungen für Verfügbarkeitsdatenbanken  

  
###  <a name="RestrictionsAG"></a> Einschränkungen (Verfügbarkeitsgruppen)  
  
-   **Verfügbarkeitsreplikate müssen von verschiedenen Knoten eines WSFC-Clusters gehostet werden:**  Für eine bestimmte verfügbarkeitsgruppe müssen verfügbarkeitsreplikate von Serverinstanzen, die auf verschiedenen Knoten desselben WSFC-Clusters gehostet werden. Die einzige Ausnahme besteht darin, dass sich eine Verfügbarkeitsgruppe während der Migration zu einem anderen WSFC-Cluster vorübergehend auf zwei Cluster erstrecken kann.  
  
    > [!NOTE]  
    >  Virtuelle Computer können auf demselben physischen Computer jeweils ein Verfügbarkeitsreplikat für dieselbe Verfügbarkeitsgruppe hosten, da jeder virtuelle Computer als separater Computer fungiert.  
  
-   **Eindeutiger Name der Verfügbarkeitsgruppe:**  Jeder verfügbarkeitsgruppenname muss auf dem WSFC-Cluster eindeutig sein. Die maximale Länge eines Verfügbarkeitsgruppennamens beträgt 128 Zeichen.  
  
-   **Verfügbarkeitsreplikate:**  Jede Verfügbarkeitsgruppe unterstützt ein primäres Replikat und bis zu acht sekundäre Replikate. Alle Replikate können im Modus für asynchrone Commits ausgeführt werden. Alternativ können bis zu drei Replikate im Modus für synchrone Commits ausgeführt werden (ein primäres Replikat mit zwei synchronen sekundären Replikaten).  
  
-   **Maximale Anzahl von Verfügbarkeitsgruppen und Verfügbarkeitsdatenbanken pro Computer:** Die tatsächliche Anzahl der auf einem Computer (virtuell oder physisch) ausführbaren Datenbanken und Verfügbarkeitsgruppen richtet sich nach der Hardware und Workload, es gibt jedoch keine maximale Vorgabe. Microsoft hat umfangreiche Testreihen mit 10 Verfügbarkeitsgruppen und 100 Datenbanken pro physischem Computer durchgeführt. Anzeichen für eine Systemüberlastung könnten u. a. zu wenige Arbeitsthreads, langsame Antwortzeiten für AlwaysOn-Systemsichten und DMVs und/oder Systemspeicherabbilder bei angehaltenem Verteiler sein. Es wird empfohlen, die Umgebung unter produktionsähnlichen Bedingungen eingehend zu testen, um zu gewährleisten, dass das System maximale Arbeitsauslastungen im Rahmen Ihrer Anwendungs-SLAs bewältigen kann. Im Hinblick auf SLAs sollten sowohl die Auslastung unter Fehlerbedingungen als auch die erwarteten Antwortzeiten abgewogen werden.  
  
-   **Verwenden Sie den Failovercluster-Manager nicht, um Verfügbarkeitsgruppen zu bearbeiten:**  
  
     Zum Beispiel:  
  
    -   Ändern Sie keine Verfügbarkeitsgruppeneigenschaften, z. B. die möglichen Besitzer.  
  
    -   Verwenden Sie den Failovercluster-Manager nicht, um Failover für Verfügbarkeitsgruppen auszuführen. Sie müssen [!INCLUDE[tsql](../../../includes/tsql-md.md)] oder [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)]verwenden.  
  
###  <a name="RequirementsAG"></a> Voraussetzungen (Verfügbarkeitsgruppen)  
 Beim Erstellen oder Neukonfigurieren einer Verfügbarkeitsgruppenkonfiguration müssen Sie folgende Anforderungen einhalten.  
  
||Voraussetzung|Beschreibung|  
|-|------------------|-----------------|  
|![Kontrollkästchen](../../media/checkboxemptycenterxtraspacetopandright.gif "Kontrollkästchen")|Wenn Sie planen, eine [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] -Failoverclusterinstanz (FCI) zu verwenden, um ein Verfügbarkeitsreplikat zu hosten, muss gewährleistet sein, dass Sie die FCI-Einschränkungen verstehen und dass die FCI-Anforderungen erfüllt werden.|[Voraussetzungen und Einschränkungen zum Hosten eines Verfügbarkeitsreplikats mithilfe einer SQL Server-Failoverclusterinstanz (FCI)](#FciArLimitations) (früher in diesem Thema)|  
  
###  <a name="SecurityAG"></a> Sicherheit (Verfügbarkeitsgruppen)  
  
-   Die Sicherheit wird vom Windows Server-Failoverclustering (WSFC)-Cluster geerbt. WSFC stellt zwei Benutzersicherheitsebenen mit der Granularität gesamter WSFC-Cluster-APIs bereit:  
  
    -   Schreibgeschützter Zugriff  
  
    -   Vollzugriff  
  
         [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] benötigt Vollzugriff. Durch Aktivieren von [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] auf einer Instanz von [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] wird der Vollzugriff auf den WSFC-Cluster erteilt (über Dienst-SID).  
  
         Sie können im WSFC-Failovercluster-Manager die Sicherheit für eine Serverinstanz nicht direkt hinzufügen oder entfernen. Um WSFC-Sicherheitssitzungen zu verwalten, verwenden Sie den [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] -Konfigurations-Manager oder die WMI-Entsprechung von [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].  
  
-   Jede Instanz von [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] muss über Berechtigungen zum Zugreifen auf die Registrierung, den Cluster usw. verfügen.  
  
-   Es wird empfohlen, dass Sie eine Verschlüsselung für Verbindungen zwischen Serverinstanzen verwenden, die [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] -Verfügbarkeitsreplikate hosten.  
  
#### <a name="permissions-availability-groups"></a>Berechtigungen (Verfügbarkeitsgruppen)  
  
|Aufgabe|Erforderliche Berechtigungen|  
|----------|--------------------------|  
|Erstellen einer Verfügbarkeitsgruppe|Erfordert die Mitgliedschaft in der festen **sysadmin** -Serverrolle und die CREATE AVAILABILITY GROUP-Serverberechtigung, ALTER ANY AVAILABILITY GROUP-Berechtigung oder CONTROL SERVER-Berechtigung.|  
|Ändern einer Verfügbarkeitsgruppe|Erfordert die ALTER AVAILABILITY GROUP-Berechtigung für die Verfügbarkeitsgruppe, die CONTROL AVAILABILITY GROUP-Berechtigung, die ALTER ANY AVAILABILITY GROUP-Berechtigung oder die CONTROL SERVER-Berechtigung.<br /><br /> Außerdem erfordert das Verknüpfen einer Datenbank mit einer Verfügbarkeitsgruppe die Mitgliedschaft in der festen **db_owner** -Datenbankrolle.|  
|Löschen einer Verfügbarkeitsgruppe|Erfordert die ALTER AVAILABILITY GROUP-Berechtigung für die Verfügbarkeitsgruppe, die CONTROL AVAILABILITY GROUP-Berechtigung, die ALTER ANY AVAILABILITY GROUP-Berechtigung oder die CONTROL SERVER-Berechtigung. Um eine Verfügbarkeitsgruppe zu löschen, die nicht am lokalen Replikatspeicherort gehostet wird, benötigen Sie die CONTROL SERVER-Berechtigung oder die CONTROL-Berechtigung für diese Verfügbarkeitsgruppe.|  
  
###  <a name="RelatedTasksAGs"></a> Verwandte Aufgaben (Verfügbarkeitsgruppen)  
  
|Aufgabe|Thema|  
|----------|-----------|  
|Erstellen einer Verfügbarkeitsgruppe|[Verwenden der Verfügbarkeitsgruppe (Assistent für neue Verfügbarkeitsgruppen)](use-the-availability-group-wizard-sql-server-management-studio.md)<br /><br /> [Erstellen einer Verfügbarkeitsgruppe (Transact-SQL)](create-an-availability-group-transact-sql.md)<br /><br /> [Erstellen einer Verfügbarkeitsgruppe (SQL Server PowerShell)](../../../powershell/sql-server-powershell.md)<br /><br /> [Angeben der Endpunkt-URL beim Hinzufügen oder Ändern eines Verfügbarkeitsreplikats &#40;SQL Server&#41;](specify-endpoint-url-adding-or-modifying-availability-replica.md)|  
|Ändern der Anzahl der Verfügbarkeitsreplikate|[Hinzufügen eines sekundären Replikats zu einer Verfügbarkeitsgruppe &#40;SQL Server&#41;](add-a-secondary-replica-to-an-availability-group-sql-server.md)<br /><br /> [Verknüpfen eines sekundären Replikats mit einer Verfügbarkeitsgruppe &#40;SQL Server&#41;](join-a-secondary-replica-to-an-availability-group-sql-server.md)<br /><br /> [Entfernen einer sekundären Replikats aus einer Verfügbarkeitsgruppe &#40;SQL Server&#41;](remove-a-secondary-replica-from-an-availability-group-sql-server.md)|  
|Erstellen eines Verfügbarkeitsgruppenlisteners|[Erstellen oder Konfigurieren eines Verfügbarkeitsgruppenlisteners &#40;SQL Server&#41;](create-or-configure-an-availability-group-listener-sql-server.md)|  
|Löschen einer Verfügbarkeitsgruppe|[Entfernen einer Verfügbarkeitsgruppe &#40;SQL Server&#41;](remove-an-availability-group-sql-server.md)|  
  
##  <a name="PrerequisitesForDbs"></a> Voraussetzungen und Einschränkungen für Verfügbarkeitsdatenbanken  
 Damit einer Verfügbarkeitsgruppe eine Datenbank hinzugefügt werden kann, muss sie folgenden Voraussetzungen und Einschränkungen entsprechen:  
  
 
  
###  <a name="RequirementsDb"></a> Prüfliste: Anforderungen (Verfügbarkeitsdatenbanken)  
 Damit eine Datenbank einer Verfügbarkeitsgruppe hinzugefügt zu werden, müssen folgende Bedingungen für die Datenbank zutreffen:  
  
||Anforderungen|Link|  
|-|------------------|----------|  
|![Kontrollkästchen](../../media/checkboxemptycenterxtraspacetopandright.gif "Kontrollkästchen")|Die Datenbank muss eine Benutzerdatenbank sein. Systemdatenbanken können nicht zu einer Verfügbarkeitsgruppe gehören.||  
|![Kontrollkästchen](../../media/checkboxemptycenterxtraspacetopandright.gif "Kontrollkästchen")|Die Datenbank muss sich auf der Instanz von [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] , auf der Sie die Verfügbarkeitsgruppe erstellen, und die Serverinstanz muss darauf zugreifen können.||  
|![Kontrollkästchen](../../media/checkboxemptycenterxtraspacetopandright.gif "Kontrollkästchen")|Die Datenbank muss eine Datenbank mit Lese-/Schreibzugriff sein. Schreibgeschützte Datenbanken können nicht zu einer Verfügbarkeitsgruppe hinzugefügt werden.|[sys.databases](/sql/relational-databases/system-catalog-views/sys-databases-transact-sql) (**is_read_only** = 0)|  
|![Kontrollkästchen](../../media/checkboxemptycenterxtraspacetopandright.gif "Kontrollkästchen")|Die Datenbank muss eine Mehrbenutzerdatenbank sein.|[sys.databases](/sql/relational-databases/system-catalog-views/sys-databases-transact-sql) (**user_access** = 0)|  
|![Kontrollkästchen](../../media/checkboxemptycenterxtraspacetopandright.gif "Kontrollkästchen")|Verwenden Sie nicht AUTO_CLOSE.|[sys.Databases](/sql/relational-databases/system-catalog-views/sys-databases-transact-sql) (**is_auto_close_on** = 0)|  
|![Kontrollkästchen](../../media/checkboxemptycenterxtraspacetopandright.gif "Kontrollkästchen")|Verwenden Sie das vollständige Wiederherstellungsmodell (auch bekannt als der vollständige Wiederherstellungsmodus).|[sys.Databases](/sql/relational-databases/system-catalog-views/sys-databases-transact-sql) (**recovery_model** = 1)|  
|![Kontrollkästchen](../../media/checkboxemptycenterxtraspacetopandright.gif "Kontrollkästchen")|Die Datenbank muss mindestens über eine vollständige Datenbanksicherung verfügen.<br /><br /> Hinweis: Eine vollständige Sicherung ist erforderlich, um die volle Protokollkette für eine vollständige Wiederherstellung auszulösen, nachdem eine Datenbank auf den vollständigen Wiederherstellungsmodus festgelegt wurde.|[Erstellen einer vollständigen Datenbanksicherung &#40;SQL Server&#41;](../../../relational-databases/backup-restore/create-a-full-database-backup-sql-server.md)|  
|![Kontrollkästchen](../../media/checkboxemptycenterxtraspacetopandright.gif "Kontrollkästchen")|Sie darf zu keiner vorhandenen Verfügbarkeitsgruppe gehören.|[sys.Databases](/sql/relational-databases/system-catalog-views/sys-databases-transact-sql) (**group_database_id** = NULL)|  
|![Kontrollkästchen](../../media/checkboxemptycenterxtraspacetopandright.gif "Kontrollkästchen")|Die Datenbank darf nicht für die Datenbankspiegelung konfiguriert sein.|[sys.database_mirroring](/sql/relational-databases/system-catalog-views/sys-database-mirroring-transact-sql) (Wenn die Datenbank nicht an der Spiegelung beteiligt ist, haben alle Spalten mit dem Präfix „mirroring_“ den Wert NULL.)|  
|![Kontrollkästchen](../../media/checkboxemptycenterxtraspacetopandright.gif "Kontrollkästchen")|Bevor Sie eine Datenbank, die FILESTREAM verwendet, zu einer Verfügbarkeitsgruppe hinzufügen, muss gewährleistet sein, dass FILESTREAM auf jeder Serverinstanz aktiviert ist, die ein Verfügbarkeitsreplikat für die Verfügbarkeitsgruppe hostet oder hosten wird.|[Aktivieren und Konfigurieren von FILESTREAM](../../../relational-databases/blob/enable-and-configure-filestream.md)|  
|![Kontrollkästchen](../../media/checkboxemptycenterxtraspacetopandright.gif "Kontrollkästchen")|Vor dem Hinzufügen einer eigenständigen Datenbank zu einer Verfügbarkeitsgruppe muss gewährleistet sein, dass die Serveroption `contained database authentication` auf jeder Serverinstanz, die ein Verfügbarkeitsreplikat für die Verfügbarkeitsgruppe hostet oder hosten wird, auf `1` gesetzt ist.|[Contained Database Authentication (Serverkonfigurationsoption)](../../configure-windows/contained-database-authentication-server-configuration-option.md)<br /><br /> [Serverkonfigurationsoptionen &#40;SQL Server&#41;](../../configure-windows/server-configuration-options-sql-server.md)|  
  
> [!NOTE]  
>  [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] funktioniert mit jedem unterstützten Datenbank-Kompatibilitätsgrad.  
  
###  <a name="RestrictionsDb"></a> Einschränkungen (Verfügbarkeitsdatenbanken)  
  
-   Falls sich der Dateipfad (einschließlich des Laufwerkbuchstabens) einer sekundären Datenbank vom Pfad der entsprechenden primären Datenbank unterscheidet, gelten folgende Einschränkungen.  
  
    -   **[!INCLUDE[ssAoNewAgWiz](../../../includes/ssaonewagwiz-md.md)]/[!INCLUDE[ssAoAddDbWiz](../../../includes/ssaoadddbwiz-md.md)]:**  Die Option **Vollständig** wird nicht unterstützt (auf der Seite [Anfängliche Datensynchronisierung auswählen](select-initial-data-synchronization-page-always-on-availability-group-wizards.md)).  
  
    -   **RESTORE WITH MOVE:**  Zum Erstellen der sekundären Datenbanken müssen die Datenbankdateien auf jeder Instanz von [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], die ein sekundäres Replikat hostet, auf RESTORED WITH MOVE festgelegt sein.  
  
    -   **Auswirkungen auf add-file-Vorgänge:**  Ein späterer add-file-Vorgang auf dem primären Replikat schlägt auf den sekundären Datenbanken möglicherweise fehl. Dieser Fehler kann bewirken, dass die sekundären Datenbanken angehalten werden. Dies bewirkt dann, dass die sekundären Replikate den Status NOT SYNCHRONIZING erhalten.  
  
        > [!NOTE]  
        >  Informationen zum Reagieren auf einen Dateihinzufügungsvorgang, bei dem ein Fehler aufgetreten ist, finden Sie unter [Problembehandlung bei einem fehlgeschlagenen Vorgang zum Hinzufügen einer Datei &#40;AlwaysOn-Verfügbarkeitsgruppen&#41;](troubleshoot-a-failed-add-file-operation-always-on-availability-groups.md).  
  
-   Sie können keine Datenbank löschen, die aktuell einer Verfügbarkeitsgruppe angehört.  
  
###  <a name="TDEdbs"></a> Nachverfolgung für TDE-geschützte Datenbanken  
 Wenn Sie die transparente Datenverschlüsselung (TDE) verwenden, muss das Zertifikat oder der asymmetrische Schlüssel zum Erstellen und Entschlüsseln weiterer Schlüssel auf jeder Serverinstanz, die ein Verfügbarkeitsreplikat für die Verfügbarkeitsgruppe hostet, identisch sein. Weitere Informationen finden Sie unter [Verschieben einer TDE-geschützten Datenbank auf einen anderen SQL-Server](../../../relational-databases/security/encryption/move-a-tde-protected-database-to-another-sql-server.md).  
  
###  <a name="PermissionsDbs"></a> Berechtigungen (Verfügbarkeitsdatenbanken)  
 Erfordert die ALTER-Berechtigung für die Datenbank.  
  
###  <a name="RelatedTasksADb"></a> Verwandte Aufgaben (Verfügbarkeitsdatenbanken)  
  
|Aufgabe|Thema|  
|----------|-----------|  
|Vorbereiten einer sekundären Datenbank (manuell)|[Manuelles Vorbereiten einer sekundären Datenbank auf eine Verfügbarkeitsgruppe &#40;SQL Server&#41;](manually-prepare-a-secondary-database-for-an-availability-group-sql-server.md)|  
|Verknüpfen einer sekundären Datenbank mit einer Verfügbarkeitsgruppe (manuell)|[Verknüpfen einer sekundären Datenbank mit einer Verfügbarkeitsgruppe &#40;SQL Server&#41;](join-a-secondary-database-to-an-availability-group-sql-server.md)|  
|Ändern der Anzahl der Verfügbarkeitsdatenbanken|[Hinzufügen einer Datenbank zu einer Verfügbarkeitsgruppe &#40;SQL Server&#41;](availability-group-add-a-database.md)<br /><br /> [Entfernen einer sekundären Datenbank aus einer Verfügbarkeitsgruppe &#40;SQL Server&#41;](remove-a-secondary-database-from-an-availability-group-sql-server.md)<br /><br /> [Entfernen einer primären Datenbank aus einer Verfügbarkeitsgruppe &#40;SQL Server&#41;](remove-a-primary-database-from-an-availability-group-sql-server.md)|  
  
##  <a name="RelatedContent"></a> Verwandte Inhalte  
  
-   [Microsoft SQL Server AlwaysOn-Lösungshandbuch für hohe Verfügbarkeit und Notfallwiederherstellung](https://go.microsoft.com/fwlink/?LinkId=227600)  
  
-   [SQL Server AlwaysOn-Teamblog: Der offizielle SQL Server AlwaysOn-Teamblog](https://blogs.msdn.com/b/sqlalwayson/)  
  
-   [AlwaysON - HADRON-Lernreihe: Worker Pool Usage for HADRON Enabled Databases (Always On – HADRON-Lernreihe: Nutzung des Arbeitspools für HADRON-fähige Datenbanken)](https://blogs.msdn.com/b/psssql/archive/2012/05/17/alwayson-hadron-learning-series-worker-pool-usage-for-hadron-enabled-databases.aspx)  
  
## <a name="see-also"></a>Siehe auch  
 [Übersicht über AlwaysOn-Verfügbarkeitsgruppen &#40;SQLServer&#41;](overview-of-always-on-availability-groups-sql-server.md)   
 [Failoverclustering und AlwaysOn-Verfügbarkeitsgruppen &#40;SQLServer&#41;](failover-clustering-and-always-on-availability-groups-sql-server.md)   
 [AlwaysOn-Clientkonnektivität (SQLServer)](always-on-client-connectivity-sql-server.md)  
  
  
