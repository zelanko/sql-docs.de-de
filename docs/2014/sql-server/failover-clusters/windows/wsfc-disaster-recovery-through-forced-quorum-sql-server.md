---
title: WSFC-Notfallwiederherstellung durch erzwungenes Quorum (SQL Server) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
helpviewer_keywords:
- Availability Groups [SQL Server], WSFC clusters
- quorum [SQL Server], AlwaysOn and WSFC quorum
- failover clustering [SQL Server], AlwaysOn Availability Groups
ms.assetid: 6cefdc18-899e-410c-9ae4-d6080f724046
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 3c170fa1b302ccd0a1edec156b3b30429fc2daf8
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "63224627"
---
# <a name="wsfc-disaster-recovery-through-forced-quorum-sql-server"></a>WSFC-Notfallwiederherstellung durch erzwungenes Quorum (SQL Server)
  Quorumfehler werden normalerweise durch eine systemische Katastrophe, einen persistenten Kommunikationsfehler oder eine fehlerhafte Konfiguration, die mehrere Knoten im WSFC-Cluster betreffen, verursacht.  Zur Beseitigung eines Quorumfehlers ist ein manueller Eingriff erforderlich.  
  
-   Vorbereitungen **:**[Voraussetzungen](#Prerequisites), [Sicherheit](#Security)    
  
-   **Wsfc-Notfall Wiederherstellung durch die erzwungene Quorum Prozedur** [wsfc-Notfall Wiederherstellung durch die Prozedur für erzwungene Quoren](#Main)  
  
-   [Verwandte Aufgaben](#RelatedTasks)  
  
-   [Verwandte Inhalte](#RelatedContent)  
  
##  <a name="BeforeYouBegin"></a>Bevor Sie beginnen  
  
###  <a name="Prerequisites"></a> Voraussetzungen  
 Bei der Prozedur für erzwungene Quoren wird davon ausgegangen, dass vor dem Quorumfehler ein fehlerfreies Quorum vorhanden war.  
  
> [!WARNING]  
>  Der Benutzer sollte mit den Begriffen und Wechselwirkungen von Windows Server Failover Clustering, WSFC-Quorummodellen, [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]und der spezifischen Bereitstellungskonfiguration der Umgebung vertraut sein.  
>   
>  Weitere Informationen finden Sie unter:  [Windows Server Failover Clustering (WSFC) mit SQL Server](https://msdn.microsoft.com/library/hh270278\(v=SQL.110\).aspx), [WSFC-Quorummodi und Abstimmungskonfiguration (SQL Server)](https://msdn.microsoft.com/library/hh270280\(v=SQL.110\).aspx).  
  
###  <a name="Security"></a> Sicherheit  
 Der Benutzer muss einem Domänenkonto entsprechen, das Mitglied der lokalen Administratorgruppe an jedem Knoten des WSFC-Clusters ist.  
  
##  <a name="Main"></a>Wsfc-Notfall Wiederherstellung durch die Prozedur für erzwungene Quoren  
 Vergessen Sie nicht, dass bei einem Quorumfehler alle gruppierten Dienste, SQL Server-Instanzen und [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)]im WSFC-Cluster offline geschaltet werden, da der Cluster in der aktuellen Konfiguration keine Fehlertoleranz auf Knotenebene gewährleisten kann.  Ein Quorumfehler bedeutet, dass fehlerfreie Abstimmungsknoten im WSFC-Cluster nicht mehr dem Quorummodell entsprechen. Einige Knoten sind möglicherweise völlig ausgefallen, und andere haben den WSFC-Dienst möglicherweise nur heruntergefahren und sind, abgesehen vom Verlust der Fähigkeit, mit einem Quorum zu kommunizieren, möglicherweise fehlerfrei.  
  
 Um den WSFC-Cluster wieder online zu schalten, müssen Sie die Ursache für den Quorumfehler in der vorhandenen Konfiguration beheben, die betroffenen Datenbanken nach Bedarf wiederherstellen und die übrigen Knoten im WSFC-Cluster neu konfigurieren, um die verbleibende Clustertopologie widerzuspiegeln.  
  
 Sie können die *erzwungene Quorumprozedur* für einen WSFC-Clusterknoten verwenden, um die Sicherheitskontrollen zu überschreiben, die den Cluster offline geschaltet haben.  Damit wird der Cluster im Endeffekt angewiesen, die Quorumssstimmenprüfungen anzuhalten, und Sie erhalten damit die Möglichkeit, die WSFC-Clusterressourcen und SQL Server auf beliebigen Knoten im Cluster wieder online schalten.  
  
 Dieser Typ von Notfallwiederherstellungsprozess sollte die folgenden Schritte umfassen:  
  
#### <a name="to-recover-from-quorum-failure"></a>So stellen Sie das System nach Quorumfehler wieder her:  
  
1.  **Bestimmen Sie den Fehler Umfang.** Identifizieren Sie, welche Verfügbarkeitsgruppen oder SQL Server-Instanzen nicht mehr reagieren, welche Clusterknoten online sind und zur Verwendung nach der Katastrophe verfügbar sind, und untersuchen Sie die Windows-Ereignisprotokolle und die SQL Server-Systemprotokolle.  Wo praktikabel, sollten Sie forensische Daten und Systemprotokolle für spätere Analysen beibehalten.  
  
    > [!TIP]  
    >  Auf einer reagierenden Instanz von [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)]können Sie Informationen zum Zustand von Verfügbarkeitsgruppen, die auf der lokalen Serverinstanz ein Verfügbarkeitsreplikat besitzen, abrufen, indem Sie die dynamische Verwaltungssicht (DMV, Dynamic Management View) [sys.dm_hadr_availability_group_states](/sql/relational-databases/system-dynamic-management-views/sys-dm-hadr-availability-group-states-transact-sql) abfragen.  
  
2.  **Starten Sie den wsfc-Cluster mit erzwungenem Quorum auf einem einzelnen Knoten.** Identifizieren Sie einen Knoten mit einer minimalen Anzahl von Komponentenfehlern, auf dem der WSFC-Clusterdienst nicht heruntergefahren wurde.  Überprüfen Sie, ob dieser Knoten mit den meisten anderen Knoten kommunizieren kann.  
  
     Versetzen Sie den Cluster von diesem Knoten aus unter Verwendung der erzwungenen Quorumprozedur manuell in den Onlinemodus.  Um potenzielle Datenverluste zu minimieren, wählen Sie einen Knoten aus, der zuletzt ein primäres Replikat der Verfügbarkeitsgruppe gehostet hat.  
  
     Weitere Informationen finden Sie unter:  [Erzwingen des Starts eines Clusters ohne Quorum](https://msdn.microsoft.com/library/hh270275\(v=SQL.110\).aspx)  
  
    > [!NOTE]  
    >  Die erzwungene Quorumeinstellung bewirkt, dass im gesamten Cluster die Quorumüberprüfungen blockiert werden, bis der logische WSFC-Cluster die Mehrheit der Abstimmungsknoten erreicht und automatisch zu einem regulären Quorumbetriebsmodus übergeht.  
  
3.  **Starten Sie den wsfc-Dienst auf jedem ansonsten fehlerfreien Knoten normal.** Sie müssen die erzwungene Quorumoption nicht angeben, wenn Sie den Clusterdienst auf den anderen Knoten starten.  
  
     Sobald der WSFC-Dienst auf den einzelnen Knoten wieder online ist, verhandelt er mit den anderen fehlerfreien Knoten, um den neuen Clusterkonfigurationszustand zu synchronisieren.  Denken Sie daran, diesen Schritt für jeden Knoten getrennt auszuführen, um potenzielle Racebedingungen beim Auflösen des letzten bekannten Clusterstatus zu verhindern.  
  
    > [!WARNING]  
    >  Stellen Sie sicher, dass jeder Knoten, den Sie starten, mit den anderen neu online geschalteten Knoten kommunizieren kann.  Erwägen Sie, den WSFC-Dienst bei den anderen Knoten zu deaktivieren.  Andernfalls laufen Sie Gefahr, mehr als eine Quorumknotengruppe zu erstellen. Das ist ein Split-Brain-Szenario. Wenn Ihre Ermittlungsergebnisse in Schritt 1 richtig waren, sollte dieser Fall nicht eintreten.  
  
4.  **Anwenden der neuen Quorum Modus-und Knoten Abstimmungs Konfiguration.** Wenn durch das Erzwingen des Quorums alle Knoten im Cluster erfolgreich neu gestartet wurden und die Ursache für den Quorumfehler korrigiert wurde, sind keine Änderungen am ursprünglichen Quorummodus und der Knotenabstimmungskonfiguration erforderlich.  
  
     Andernfalls sollten Sie den neu wiederhergestellten Clusterknoten und Verfügbarkeitsreplikattopologie auswerten und bei Bedarf den Quorummodus und die Abstimmungszuweisungen für jeden Knoten ändern. Nicht wiederhergestellte Knoten sollten offline geschaltet werden oder einen Knotenabstimmungswert von 0 (Null) erhalten.  
  
    > [!TIP]  
    >  Zu diesem Zeitpunkt hat es möglicherweise den Anschein, als wären die Knoten und SQL Server-Instanzen im Cluster in ihrem normalen Betriebszustand wiederhergestellt.  Allerdings ist unter Umständen immer noch kein fehlerfreies Quorum vorhanden.  Vergewissern Sie sich mithilfe des Failovercluster-Managers oder des AlwaysOn-Dashboard in SQL Server Management Studio oder der entsprechenden DMVs, dass ein Quorum wiederhergestellt wurde.  
  
5.  **Wiederherstellen von Verfügbarkeits Gruppen-Daten Bank Replikaten** Datenbanken, die mit keiner Verfügbarkeitsgruppe verknüpft sind, sollten im Rahmen des regulären SQL Server-Startprozess von allein wiederhergestellt und online geschaltet werden.  
  
     Sie können potenzielle Datenverluste und den Zeitaufwand des Wiederherstellungsvorgangs für die Verfügbarkeitsgruppenreplikate minimieren, indem Sie diese in der folgenden Reihenfolge wieder online schalten: primäres Replikat, synchrone sekundäre Replikate, asynchrone sekundäre Replikate.  
  
6.  **Reparieren oder ersetzen Sie fehlerhafte Komponenten, und überprüfen Sie den Cluster neu.** Nachdem Sie das System nach dem Auftreten der ursprünglichen Katastrophe und des Quorumfehlers wiederhergestellt haben, sollten Sie die fehlerhaften Knoten reparieren oder austauschen und die zugehörigen WSFC- und AlwaysOn-Konfigurationen entsprechend anpassen.  Hierzu kann es erforderlich sein, Verfügbarkeitsgruppenreplikate zu löschen, Knoten aus dem Cluster zu entfernen oder die Software eines Knotens zu vereinfachen oder neu zu installieren.  
  
     Sie müssen alle fehlerhaften Verfügbarkeitsreplikate reparieren oder entfernen.  
  [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] schneidet das Transaktionsprotokoll nicht am letzten bekannten Punkt des Verfügbarkeitsreplikats mit den am weitesten zurückliegenden Daten ab.   Wenn ein fehlerhaftes Replikat nicht repariert oder aus der Verfügbarkeitsgruppe entfernt wird, wachsen die Transaktionsprotokolle, und es besteht das Risiko, dass nicht mehr ausreichend Speicherplatz für die Transaktionsprotokolle der anderen Replikate verfügbar ist.  
  
    > [!NOTE]  
    >  Wenn Sie den WSFC-Konfigurationsüberprüfungs-Assistenten ausführen, wenn im WSFC-Cluster ein Verfügbarkeitsgruppenlistener vorhanden ist, generiert der Assistent die folgende falsche Warnmeldung:  
    >   
    >  „Die RegisterAllProviderIP-Eigenschaft für Netzwerkname 'Name:&lt;Netzwerkname' ist auf 1 festgelegt. Für die aktuelle Clusterkonfiguration muss dieser Wert auf 0 festgelegt werden.“  
    >   
    >  Ignorieren Sie diese Meldung.  
  
7.  **Wiederholen Sie Schritt 4 nach Bedarf.** Das Ziel besteht darin, erneut das für einen fehlerfreien Betrieb angemessene Maß an Fehlertoleranz und Hochverfügbarkeit wiederherzustellen.  
  
8.  **Führt eine RPO/RTO-Analyse durch.** Sie sollten SQL Server-Systemprotokolle, Datenbank-Timestamps und Windows-Ereignisprotokolle analysieren, um die Fehlerursache zu bestimmen und die tatsächlichen Wiederherstellungspunkt- und Wiederherstellungszeitdaten zu dokumentieren.  
  
##  <a name="RelatedTasks"></a> Verwandte Aufgaben  
  
-   [Erzwingen des Starts eines Clusters ohne Quorum](force-a-wsfc-cluster-to-start-without-a-quorum.md)  
  
-   [Ausführen eines erzwungenen manuellen Failovers einer Verfügbarkeitsgruppe &#40;SQL Server&#41;](../../../database-engine/availability-groups/windows/perform-a-forced-manual-failover-of-an-availability-group-sql-server.md)  
  
-   [Anzeigen von Cluster-Quorum-NodeWeight-Einstellungen](view-cluster-quorum-nodeweight-settings.md)  
  
-   [Konfigurieren von Cluster-Quorum-NodeWeight-Einstellungen](configure-cluster-quorum-nodeweight-settings.md)  
  
-   [Verwenden Sie das AlwaysOn-Dashboard &#40;SQL Server Management Studio&#41;](../../../database-engine/availability-groups/windows/use-the-always-on-dashboard-sql-server-management-studio.md) 
  
##  <a name="RelatedContent"></a> Verwandte Inhalte  
  
-   [Anzeigen von Ereignissen und Protokollen für einen Failovercluster](https://technet.microsoft.com/library/cc772342\(WS.10\).aspx)  
  
-   [Get-CLUSTERLOG-Failovercluster-Cmdlet](https://technet.microsoft.com/library/ee461045.aspx)  
  
## <a name="see-also"></a>Weitere Informationen  
 [Windows Server-Failoverclustering &#40;WSFC&#41; mit SQL Server](windows-server-failover-clustering-wsfc-with-sql-server.md)  
  
  
