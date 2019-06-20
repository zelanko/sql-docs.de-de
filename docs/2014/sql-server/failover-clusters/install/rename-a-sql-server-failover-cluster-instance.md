---
title: Umbenennen einer SQL Server-Failoverclusterinstanz|Microsoft-Dokumente
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: install
ms.topic: conceptual
helpviewer_keywords:
- clusters [SQL Server], virtual servers
- renaming virtual servers
- virtual servers [SQL Server], failover clustering
- failover clustering [SQL Server], virtual servers
ms.assetid: 2a49d417-25fb-4760-8ae5-5871bfb1e6f3
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 4ce98bacfcc5f3aa8814a9253d1796fd18c4a735
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "63126007"
---
# <a name="rename-a-sql-server-failover-cluster-instance"></a>Umbenennen einer SQL Server-Failoverclusterinstanz
  Wenn eine [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] -Instanz Teil eines Failoverclusters ist, unterscheidet sich der Vorgang des Umbenennens des virtuellen Servers vom Umbenennen einer eigenständigen Instanz. Weitere Informationen finden Sie unter [Umbenennen eines Computers, der eine eigenständige Instanz von SQL Server hostet](../../../database-engine/install-windows/rename-a-computer-that-hosts-a-stand-alone-instance-of-sql-server.md).  
  
 Der Name des virtuellen Servers ist immer mit dem SQL-Netzwerknamen (dem Netzwerknamen des virtuellen Servers mit SQL Server) identisch. Sie können zwar den Namen des virtuellen Servers ändern, nicht jedoch den Instanznamen. Sie können z. B. einen virtuellen Server namens VS1\instance1 in einen anderen Namen ändern, z. B. in SQL35\instance1, der Instanzanteil des Namens, instance1, bleibt jedoch unverändert.  
  
 Bevor Sie den Umbenennungsvorgang beginnen, überprüfen Sie die nachfolgenden Elemente.  
  
-   [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] unterstützt nicht das Umbenennen von Servern, die an der Replikation beteiligt sind. Eine Ausnahme stellt die Verwendung von Protokollversand mit Replikation dar. Der sekundäre Server beim Protokollversand kann umbenannt werden, wenn der primäre Server dauerhaft verloren ist. Weitere Informationen finden Sie unter [Protokollversand und Replikation &#40;SQL Server&#41;](../../../database-engine/log-shipping/log-shipping-and-replication-sql-server.md).  
  
-   Wenn Sie einen virtuellen Server umbenennen, der für die Verwendung von Datenbankspiegelung konfiguriert ist, müssen Sie die Datenbankspiegelung vor dem Umbenennungsvorgang deaktivieren und die Datenbankspiegelung mit dem neuen Namen des virtuellen Servers anschließend neu einrichten. Die Metadaten für die Datenbankspiegelung werden nicht automatisch aktualisiert, um den neuen Namen des virtuellen Servers widerzuspiegeln.  
  
### <a name="to-rename-a-virtual-server"></a>So benennen Sie einen virtuellen Server um:  
  
1.  Ändern Sie mithilfe der Clusterverwaltung den SQL-Netzwerknamen in den neuen Namen.  
  
2.  Schalten Sie die Netzwerknamenressource offline. Durch diesen Vorgang werden die [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] -Ressource und andere abhängige Ressourcen ebenfalls offline geschaltet.  
  
3.  Schalten Sie die [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] -Ressource erneut online.  
  
## <a name="verify-the-renaming-operation"></a>Überprüfen des Umbenennungsvorgangs  
 Nachdem ein virtueller Server umbenannt wurde, müssen alle Verbindungen, die den alten Namen verwendet haben, nun Verbindungen mithilfe des neuen Namens herstellen.  
  
 Um zu überprüfen, ob der Umbenennungsvorgang abgeschlossen wurde, wählen Sie Informationen aus `@@servername` oder `sys.servers` aus. Die `@@servername`-Funktion gibt den neuen Namen des virtuellen Servers zurück, und die `sys.servers`-Tabelle zeigt den neuen Namen des virtuellen Servers an. Um zu überprüfen, ob der Failoverprozess ordnungsgemäß mit dem neuen Namen arbeitet, sollte der Benutzer außerdem versuchen, ein Failover der [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] -Ressource auf die anderen Knoten auszuführen.  
  
 Für Verbindungen von einem beliebigen Knoten im Cluster kann der neue Name fast sofort verwendet werden. Für Verbindungen, die den neuen Namen von einem Clientcomputer aus verwenden, kann der neue Name jedoch erst zum Herstellen einer Verbindung zum Server verwendet werden, nachdem der neue Name für den betreffenden Clientcomputer sichtbar ist. Die Zeitspanne, die zum Weitergeben des neuen Namens über ein Netzwerk benötigt wird, kann abhängig von der Netzwerkkonfiguration zwischen einigen Sekunden bis hin zu 3 bis 5 Minuten betragen; zusätzliche Zeit ist möglicherweise erforderlich, bis der alte Name des virtuellen Servers nicht mehr im Netzwerk sichtbar ist.  
  
 Um die Verzögerung der Netzwerkweitergabe des Umbenennungsvorgangs eines virtuellen Servers zu minimieren, führen Sie die folgenden Schritte aus:  
  
#### <a name="to-minimize-network-propagation-delay"></a>So minimieren Sie die Verzögerung der Netzwerkweitergabe:  
  
1.  Geben Sie an einer Eingabeaufforderung auf dem Serverknoten die folgenden Befehle aus:  
  
    ```  
    ipconfig /flushdns  
    ipconfig /registerdns  
    nbtstat -RR  
    ```  
  
## <a name="additional-considerations-after-the-renaming-operation"></a>Weitere Überlegungen nach dem Umbenennungsvorgang  
 Nachdem der Netzwerkname des Failoverclusters geändert wurde, müssen die folgenden Anweisungen überprüft und ausgeführt werden, damit alle Szenarien in [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Agent und [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]funktionieren.  
  
 **[!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]:** Nach dem Ändern der Netzwerkname des eine [!INCLUDE[ssASCurrent](../../../includes/ssascurrent-md.md)] Failover cluster-Instanz, die mit Windows-Clusterverwaltungstool umbenannt, Upgrade- oder Deinstallationsvorgang schlägt möglicherweise fehl. Um dieses Problem beheben, Aktualisieren der **ClusterName** -Registrierungseintrag entsprechend die Anweisungen im Abschnitt "Lösung" [dies](https://go.microsoft.com/fwlink/?LinkId=244002) (https://go.microsoft.com/fwlink/?LinkId=244002).  
  
 **[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Agent-Dienst:** Stellen Sie sicher, und führen Sie die unten genannten zusätzlichen Aktionen für [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] -Agent-Dienst:  
  
-   Korrigieren Sie die Registrierungseinstellungen, wenn SQL Agent für die Ereignisweiterleitung konfiguriert ist. Weitere Informationen finden Sie unter [Bestimmen eines Ereignisweiterleitungsservers &#40;SQL Server Management Studio&#41;](../../../ssms/agent/designate-an-events-forwarding-server-sql-server-management-studio.md).  
  
-   Korrigieren Sie die Instanznamen von Masterserver (MSX) und Zielservern (TSX), wenn der Netzwerkname von Computern/Cluster umbenannt wird. Weitere Informationen finden Sie unter den folgenden Themen:  
  
    -   [Vollziehen des Austritts mehrerer Zielserver aus einem Masterserver](../../../ssms/agent/defect-multiple-target-servers-from-a-master-server.md)  
  
    -   [Erstellen einer Multiserverumgebung](../../../ssms/agent/create-a-multiserver-environment.md)  
  
-   Konfigurieren Sie den Protokollversand neu, damit der aktualisierte Servername für die Sicherungs- und Wiederherstellungsprotokolle verwendet wird. Weitere Informationen finden Sie unter den folgenden Themen:  
  
    -   [Konfigurieren des Protokollversands &#40;SQL Server&#41;](../../../database-engine/log-shipping/configure-log-shipping-sql-server.md)  
  
    -   [Entfernen des Protokollversands &#40;SQL Server&#41;](../../../database-engine/log-shipping/remove-log-shipping-sql-server.md)  
  
-   Aktualisieren Sie die Auftragsschritte, die vom Servernamen abhängen. Weitere Informationen finden Sie unter [Manage Job Steps](../../../ssms/agent/manage-job-steps.md).  
  
## <a name="see-also"></a>Siehe auch  
 [Umbenennen eines Computers, der eine eigenständige Instanz von SQL Server hostet](../../../database-engine/install-windows/rename-a-computer-that-hosts-a-stand-alone-instance-of-sql-server.md)  
  
  
