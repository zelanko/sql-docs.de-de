---
title: Installationsoptionen für SQL Server-Failovercluster | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: install
ms.topic: conceptual
ms.assetid: c0e75a7c-85c5-423c-a218-77247bf071aa
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 49fce70b4fc01f77fe7ca54e3951f0372ba18489
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "63067646"
---
# <a name="sql-server-failover-cluster-installation"></a>SQL Server-Failoverclusterinstallation
  Zum Installieren eines [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] -Failoverclusters müssen Sie eine Failoverclusterinstanz erstellen und konfigurieren, indem Sie das [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] -Setup ausführen.  
  
## <a name="installing-a-failover-cluster"></a>Installieren eines Failoverclusters  
 Zum Installieren eines Failoverclusters müssen Sie ein Domänenkonto mit lokalen Administratorrechten sowie Berechtigungen zum Anmelden als Dienst und Agieren als Teil des Betriebssystems auf allen Knoten des Failoverclusters verwenden. Führen Sie zum Installieren eines Failoverclusters mithilfe des [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] -Setupprogramms folgende Schritte aus:  
  
1.  Verwenden Sie [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] -Setup, um ein [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] -Failovercluster zu installieren, zu konfigurieren und zu verwalten.  
  
    -   Identifizieren Sie die erforderlichen Informationen zum Erstellen der Failoverclusterinstanz (z. B. Cluster-Datenträgerressource, IP-Adressen und Netzwerkname) und der Knoten, die für ein Failover verfügbar sind. Weitere Informationen finden Sie unter:  
  
        -   [Vor dem Installieren des Failoverclusterings](before-installing-failover-clustering.md)  
  
        -   [Überlegungen zur Sicherheit bei SQL Server-Installationen](../../install/security-considerations-for-a-sql-server-installation.md)  
  
    -   Die Konfigurationsschritte müssen ausgeführt werden, bevor Sie das [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Setup Programm ausführen. Verwenden Sie den Windows-Cluster Administrator, um Sie auszuführen. Sie müssen über eine wsfc-Gruppe für jede Failoverclusterinstanz verfügen, die Sie konfigurieren möchten.  
  
    -   Sie müssen sicherstellen, dass das System die Mindestanforderungen erfüllt. Weitere Informationen zu speziellen Anforderungen für einen [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] -Failovercluster finden Sie unter [Vor dem Installieren des Failoverclusterings](before-installing-failover-clustering.md).  
  
2.  Fügen Sie Knoten aus der Konfiguration eines Failoverclusters hinzu, oder entfernen Sie diese, ohne dass sich dies auf andere Clusterknoten auswirkt. Weitere Informationen finden Sie unter [Hinzufügen oder Entfernen von Knoten in einem SQL Server-Failovercluster &#40;Setup&#41;](add-or-remove-nodes-in-a-sql-server-failover-cluster-setup.md).  
  
    -   Alle Knoten in einem Failovercluster müssen auf der gleichen Plattform, entweder 32-Bit oder 64-Bit, und unter der gleichen Betriebssystemversion ausgeführt werden. Darüber hinaus müssen 64-Bit-Editionen von [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] auf 64-Bit-Hardware installiert sein, auf der die 64-Bit-Versionen der Windows-Betriebssysteme ausgeführt werden. Es gibt keine WOW64-Unterstützung für das Failoverclustering in dieser Version.  
  
3.  Geben Sie für jede Failoverclusterinstanz mehrere IP-Adressen an. Sie können mehrere IP-Adressen für jedes Subnetz angeben. Wenn sich die IP-Adressen im gleichen Subnetz befinden, wird die Abhängigkeit vom Setup für [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] auf AND festgelegt. Wenn Sie Knoten für mehrere Subnetze gruppieren, wird die Abhängigkeit vom Setup für [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] auf OR festgelegt.  
  
## <a name="includessnoversionincludesssnoversion-mdmd-failover-cluster-installation-options"></a>
  [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] -Failovercluster  
  
##### <a name="option-1-integrated-installation-with-add-node"></a>Option 1: Integrierte Installation mithilfe der Funktion zum Hinzufügen eines Knotens  
 
  [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] besteht aus zwei Schritten:  
  
1.  Erstellen und konfigurieren Sie eine [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] -Failoverclusterinstanz mit einem einzelnen Knoten. Beim Abschluss einer erfolgreichen Konfiguration des Knotens verfügen Sie über eine voll funktionsfähige Failoverclusterinstanz. Zu diesem Zeitpunkt verfügt diese noch nicht über eine hohe Verfügbarkeit, da nur ein Knoten im Failovercluster vorhanden ist.  
  
2.  Führen Sie für jeden Knoten, der dem [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] -Failovercluster hinzufügt werden soll, Setup mithilfe der Funktion Knoten hinzufügen aus.  
  
##### <a name="option-2-advancedenterprise-installation"></a>Option 2: Erweiterte bzw. Enterprise-Installation  
 
  [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Die erweiterte bzw. Enterprise-Installation eines Failoverclusters besteht aus zwei Schritten:  
  
1.  Führen Sie für jeden Knoten, der Teil des [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] -Failoverclusters sein soll, Setup mithilfe der Funktion zum Vorbereiten des Failoverclusters aus. Mit diesem Schritt werden die Knoten für die Gruppierung vorbereitet. Nach diesem Schritt ist jedoch keine funktionstüchtige [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] -Instanz vorhanden.  
  
2.  Nachdem die Knoten für die Gruppierung vorbereitet sind, führen Sie Setup mithilfe der Funktion zum Abschließen eines Failoverclusters für den Knoten aus, der über den freigegebenen Datenträger verfügt. Durch diesen Schritt wird die Failoverclusterinstanz konfiguriert und abgeschlossen. Nach diesem Schritt verfügen Sie über eine funktionstüchtige [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] -Failoverclusterinstanz.  
  
    > [!NOTE]  
    >  Beide Installationsoptionen ermöglichen eine [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] -Failoverclusterinstallation mit mehreren Knoten. Die Funktion Knoten hinzufügen kann bei beiden Optionen dazu verwendet werden, um nach Erstellen eines [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] -Failoverclusters zusätzliche Knoten hinzuzufügen.  
  
    > [!IMPORTANT]  
    >  Der Laufwerkbuchstabe des Betriebssystems für [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] -Installationsverzeichnisse muss auf allen Knoten übereinstimmen, die dem [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] -Failovercluster hinzugefügt werden.  
  
#### <a name="ip-address-configuration-during-setup"></a>Konfigurieren von IP-Adressen während des Setups  
 
  [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] können Sie die IP-Adressabhängigkeit im Zusammenhang mit folgenden Aktionen festlegen oder ändern:  
  
-   Integrierte Installation: [Erstellen eines neuen SQL Server-Failoverclusters &#40;Setup&#41;](create-a-new-sql-server-failover-cluster-setup.md)  
  
-   Vollständiger Failovercluster (erweiterte Installation): [Erstellen eines neuen SQL Server-Failoverclusters &#40;Setup&#41;](create-a-new-sql-server-failover-cluster-setup.md)  
  
-   Knoten hinzufügen: [Hinzufügen oder Entfernen von Knoten in einem SQL Server-Failovercluster &#40;Setup&#41;](add-or-remove-nodes-in-a-sql-server-failover-cluster-setup.md)  
  
-   Knoten entfernen: [Hinzufügen oder Entfernen von Knoten in einem SQL Server-Failovercluster &#40;Setup&#41;](add-or-remove-nodes-in-a-sql-server-failover-cluster-setup.md)  
  
 **Hinweis** IPv6-IP-Adressen werden unterstützt.  IPV4 und IPV6 werden bei paralleler Konfiguration als unterschiedliche Subnetze eingestuft, und IPV6 soll zuerst online geschaltet werden.  
  
##### <a name="includessnoversionincludesssnoversion-mdmd-multi-subnet-failover-cluster"></a>
  [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] -Multisubnetz-Failovercluster  
 Sie können OR-Abhängigkeiten festlegen, wenn sich die Knoten im Cluster in unterschiedlichen Subnetzen befinden. Jeder Knoten im [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] -Multisubnetz-Failovercluster muss jedoch möglicher Besitzer mindestens einer angegebenen IP-Adresse sein.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Vor dem Installieren des Failoverclustering](before-installing-failover-clustering.md)   
 [Erstellen eines neuen SQL Server-Failoverclusters &#40;Setup&#41;](create-a-new-sql-server-failover-cluster-setup.md)   
 [Installieren von SQL Server 2014 von der Eingabeaufforderung](../../../database-engine/install-windows/install-sql-server-from-the-command-prompt.md)   
 [Aktualisieren eines SQL Server-Failoverclusters](../windows/upgrade-a-sql-server-failover-cluster-instance.md)  
  
  
