---
title: Upgrade und Update von Verfügbarkeitsgruppenservern bei minimaler Downtime und minimalem Datenverlust | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
ms.assetid: f670af56-dbcc-4309-9119-f919dcad8a65
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 8e9be78ff13d39b4cdcaf60516ac20b9a85648d6
ms.sourcegitcommit: 334cae1925fa5ac6c140e0b2c38c844c477e3ffb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/13/2018
ms.locfileid: "53357077"
---
# <a name="upgrade-and-update-of-availability-group-servers-with-minimal-downtime-and-data-loss"></a>Upgrade und Update von Verfügbarkeitsgruppenservern bei minimaler Downtime und minimalem Datenverlust
  Wenn Sie für SQL Server 2012-Serverinstanzen ein Update oder Upgrade auf ein Service Pack oder eine neuere Version ausführen, können Sie die Downtime einer Verfügbarkeitsgruppe auf nur einen manuellen Failover begrenzen, indem Sie ein sequenzielles Update oder Upgrade ausführen. Beim Upgrade von SQL Server-Versionen wird dieser Vorgang als paralleles Upgrade und beim Update aktueller SQL Server-Versionen anhand von Hotfixes oder Service Packs als paralleles Update bezeichnet.  
  
 Dieses Thema beschränkt sich auf Upgrades/Updates von SQL Server. Betriebssystembezogene Upgrades/Updates, die hoch verfügbare SQL Server-Instanzen ausgeführt werden, finden Sie unter [clusterübergreifende Migration von AlwaysOn-Verfügbarkeitsgruppen für Betriebssystemupgrade](https://msdn.microsoft.com/library/jj873730.aspx)  
  
## <a name="rolling-upgradeupdate-best-practices-for-alwayson-availability-groups"></a>Bewährte Verfahren für parallele Upgrades/Updates von AlwaysOn-Verfügbarkeitsgruppen  
 Beachten Sie beim Ausführen von Serverupgrades/-updates die folgenden bewährten Verfahren, um die Downtime und Datenverluste für Verfügbarkeitsgruppen zu minimieren:  
  
-   Vor dem Start des parallelen Upgrades/Updates:  
  
    -   Führen Sie zu Übungszwecken ein manuelles Failover für mindestens eines der Replikate mit synchronem Commit aus.  
  
    -   Schützen Sie Ihre Daten, indem Sie eine vollständige Datenbanksicherung für jede Verfügbarkeitsdatenbank ausführen.  
  
    -   Führen Sie DBCC CHECKDB für jede Verfügbarkeitsdatenbank aus.  
  
-   Führen Sie das Upgrade/Update zuerst immer für die sekundären Remotereplikatknoten und dann für die lokalen sekundären Replikatknoten und zuletzt für den primären Replikatknoten aus.  
  
-   Von einer Datenbank, für die gerade ein Upgrade ausgeführt wird, kann keine Sicherung erstellt werden.  Vor dem Aktualisieren der sekundären Replikate konfigurieren Sie die Voreinstellung für die automatisierte Sicherung, um Sicherungen nur auf dem primären Replikat auszuführen.  Vor dem Upgrade des primären Replikats sollten Sie diese Einstellung so ändern, dass nur Sicherungen auf den sekundären Replikaten ausgeführt werden.  
  
-   Damit für die Verfügbarkeitsgruppe während des Upgrades/Updates kein unbeabsichtigter Failover ausgeführt wird, entfernen Sie den Verfügbarkeitsfailover zunächst von allen Replikaten mit synchronem Commit.  
  
-   Führen Sie für den primären Replikatknoten kein Upgrade aus, bevor Sie für die Verfügbarkeitsgruppe kein Failover auf einen aktualisierten Knoten mit sekundärem Replikat ausgeführt haben. Andernfalls kann sich die Downtime von Clientanwendungen während des Upgrades/Updates auf dem primären Replikat verlängern.  
  
-   Führen Sie für die Verfügbarkeitsgruppe immer ein Failover auf den sekundären Replikatknoten mit synchronem Commit aus. Wenn Sie ein Failover auf ein sekundäres Replikat mit asynchronem Commit ausführen, treten in den Datenbanken Datenverluste auf und die Datenverschiebung wird automatisch so lange angehalten, bis der Vorgang manuell fortgesetzt wird.  
  
-   Führen Sie für den primären Replikatknoten kein Upgrade/Upgrade aus, bevor Sie das Upgrade/Update der übrigen sekundären Replikatknoten nicht abgeschlossen haben. Ein primäres Replikat, für das ein Upgrade ausgeführt wurde, kann keine Protokolle mehr an sekundäre Replikate senden, für die noch kein Upgrade auf dieselbe Version ausgeführt wurde. Wenn eine Datenverschiebung zu einem sekundären Replikat angehalten wurde, kann für dieses Replikat kein automatisches Failover ausgeführt werden, und die Verfügbarkeitsdatenbanken sind anfällig für Datenverluste.  
  
-   Bevor Sie ein Failover für eine Verfügbarkeitsgruppe ausführen, sollten Sie überprüfen, ob der Synchronisierungsstatus des Failoverziels SYNCHRONIZED lautet.  
  
## <a name="rolling-upgradeupdate-process"></a>Schritte zur Ausführung des parallelen Upgrades/Updates  
 Die genauen Schritte hängen von Faktoren wie der Bereitstellungstopologie der Verfügbarkeitsgruppen und dem Commitmodus der einzelnen Replikate ab. Im einfachsten Szenario ist ein paralleles Upgrade/Update jedoch ein mehrstufiger Prozess, der aus den folgenden Phasen besteht:  
  
 ![Szenario für ein Upgrade von Verfügbarkeitsgruppen in HADR](../../media/alwaysonupgrade-ag-hadr.gif "Availability Group Upgrade in HADR Scenario")  
  
1.  Deaktivieren des automatischen Failovers für alle Replikate mit synchronem Commit  
  
2.  Ausführen eines Upgrades/Updates für alle Remoteserverinstanzen, auf denen sekundäre Replikate mit asynchronem Commit ausgeführt werden  
  
3.  Ausführen eines Upgrades/Updates für alle lokalen Serverinstanzen, auf denen das primäre Replikat derzeit nicht ausgeführt wird  
  
4.  Ausführen eines manuellen Failovers der Verfügbarkeitsgruppe auf ein sekundäres Replikat mit synchronem Commit  
  
5.  Ausführen eines Upgrades/Updates der Serverinstanz, von der das primäre Replikat zuvor gehostet wurde  
  
6.  Konfigurieren automatischer Failoverpartner nach Bedarf  
  
 Falls erforderlich, können Sie einen zusätzlichen manuellen Failover ausführen, um die ursprüngliche Konfiguration der Verfügbarkeitsgruppe wiederherzustellen.  
  
## <a name="availability-group-with-one-remote-secondary-replica"></a>Verfügbarkeitsgruppe mit einem sekundären Remotereplikat  
 Wenn Sie eine Verfügbarkeitsgruppe ausschließlich zur Notfallwiederherstellung bereitgestellt haben, müssen Sie für die Verfügbarkeitsgruppe u. U. ein Failover auf ein sekundäres Replikat mit asynchronem Commit ausführen. Diese Konfiguration wird in der folgenden Abbildung dargestellt:  
  
 ![Szenario für ein Upgrade von Verfügbarkeitsgruppen in DR](../../media/agupgrade-ag-dr.gif "Availability Group Upgrade in HADR Scenario")  
  
 In diesem Fall müssen Sie für die Verfügbarkeitsgruppe während des parallelen Upgrades/Updates ein Failover auf das sekundäre Replikat mit asynchronem Commit ausführen. Zur Vermeidung von Datenverlusten ändern Sie den Commitmodus in den synchronen Commitmodus und warten mit dem Failover der Verfügbarkeitsgruppe, bis das sekundäre Replikat synchronisiert ist. Das parallele Upgrade/Update kann somit folgende Schritte umfassen:  
  
1.  Upgrade/Update des Remoteservers  
  
2.  Ändern des Commitmodus in den synchronen Commitmodus  
  
3.  Warten, bis der Synchronisierungsstatus SYNCHRONIZED lautet  
  
4.  Ausführen eines Failovers der Verfügbarkeitsgruppe auf den Remotestandort  
  
5.  Upgrade/Update des lokalen Servers (am primären Standort)  
  
6.  Ausführen eines Failovers der Verfügbarkeitsgruppe auf den primären Standort  
  
7.  Ändern des Commitmodus in den asynchronen Commitmodus  
  
 Der synchrone Commitmodus ist für die Datensynchronisierung mit einem Remotestandort nicht zu empfehlen. Nachdem die Einstellung geändert wurde, verzeichnen die Clientanwendungen möglicherweise einen sofortigen Anstieg der Datenbanklatenz. Darüber hinaus führt ein Failover dazu, dass alle unbestätigten Protokollmeldungen verworfen werden. Die Anzahl der verworfenen Protokollmeldungen kann aufgrund hoher Netzwerklatenz zwischen den beiden Standorten deutlich erhöht sein, was auf den Clients zu einer hohen Rate von Transaktionsfehlern führt. Sie können die Auswirkungen auf die Clientanwendungen anhand der folgenden Maßnahmen minimieren:  
  
-   Festlegen des Wartungsfensters auf Zeiten mit geringem Clientdatenverkehr  
  
-   Ändern Sie den Verfügbarkeitsmodus beim Upgrade/Update von SQL Server am primären Standort zurück in den asynchronen Commitmodus, und kehren Sie zu synchronen Commits zurück, wenn Sie wieder bereit für ein Failover auf den primären Standort sind.  
  
## <a name="availability-group-with-failover-cluster-instance-nodes"></a>Verfügbarkeitsgruppe mit Failoverclusterinstanz-Knoten  
 Wenn eine Verfügbarkeitsgruppe Failoverclusterinstanz-Knoten (Failover Cluster Instance, FCI) enthält, sollten Sie ein Upgrade/Update zunächst für die inaktiven und dann erst für die aktiven Knoten ausführen. In der folgenden Abbildung ist ein gängiges Verfügbarkeitsgruppenszenario mit FCIs dargestellt. Es basiert auf FCIs, die auf lokale Hochverfügbarkeit und asynchrone Commits zur Remote-Notfallwiederherstellung ausgelegt sind, und veranschaulicht die Schritte zum Ausführen des Upgrades.  
  
 ![Szenario für ein Upgrade von Verfügbarkeitsgruppen mit FCIs](../../media/agupgrade-ag-fci-dr.gif "Availability Group Upgrade in HADR Scenario")  
  
1.  Upgrade/Update von REMOTE2  
  
2.  Failover von FCI2 auf REMOTE2  
  
3.  Upgrade/Update von REMOTE1  
  
4.  Upgrade/Update von PRIMARY2  
  
5.  Failover von FCI1 auf PRIMARY2  
  
6.  Upgrade/Update von PRIMARY1  
  
## <a name="upgradeupdate-sql-server-instances-with-multiple-availability-groups"></a>Upgrade/Update von SQL Server-Instanzen mit mehreren Verfügbarkeitsgruppen  
 Wenn Sie mehrere Verfügbarkeitsgruppen mit primären Replikaten auf separaten Serverknoten ausführen (Aktiv-/Aktiv-Konfiguration), umfasst das Upgrade/Update mehr Failoverschritte, um Hochverfügbarkeit im Prozess sicherzustellen. Angenommen, Sie führen drei Verfügbarkeitsgruppen auf drei Serverknoten aus (vgl. die folgende Tabelle) und alle sekundären Replikate werden im synchronen Commitmodus ausgeführt.  
  
|Verfügbarkeitsgruppe|Knoten1|Knoten2|Knoten3|  
|------------------------|-----------|-----------|-----------|  
|VG1|Primär|||  
|VG2||Primär||  
|VG3|||Primär|  
  
 In diesem Fall kann es von Vorteil sein, ein lastverteiltes paralleles Upgrade/Update in der folgenden Reihenfolge ausführen:  
  
1.  Failover von VG2 auf Knoten3 (um Knoten2 freizugeben)  
  
2.  Upgrade/Update von Knoten2  
  
3.  Failover von VG1 auf Knoten2 (um Knoten1 freizugeben)  
  
4.  Upgrade/Update von Knoten1  
  
5.  Failover sowohl von VG2 als auch von VG3 auf Knoten1 (um Knoten3 freizugeben)  
  
6.  Upgrade/Update von Knoten3  
  
7.  Failover von VG3 auf Knoten3  
  
 Bei dieser Art von Upgrade/Update beträgt die durchschnittliche Downtime weniger als zwei Failover pro Verfügbarkeitsgruppe. Die resultierende Konfiguration ist in der folgenden Tabelle dargestellt.  
  
|Verfügbarkeitsgruppe|Knoten1|Knoten2|Knoten3|  
|------------------------|-----------|-----------|-----------|  
|VG1||Primär||  
|VG2|Primär|||  
|VG3|||Primär|  
  
 Je nach der vorliegenden Implementierung kann der Upgrade-/Updatepfad abweichen. Das Gleiche gilt für die Downtime der Clientanwendungen.  
  
  
