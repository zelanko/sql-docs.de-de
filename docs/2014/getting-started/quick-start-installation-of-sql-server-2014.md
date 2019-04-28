---
title: Schnellstart-Installation von SQLServer 2014 | Microsoft-Dokumentation
ms.custom: ''
ms.date: 05/25/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- quick start installation [SQL Server]
- installation [SQL Server]
- installing SQL Server, quick start installations
ms.assetid: 672afac9-364d-4946-ad5d-8a2d89cf8d81
author: mightypen
ms.author: genemi
manager: craigg
ms.openlocfilehash: b06f5248152f8a11bf3e46d222df457f5442b6b4
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62837783"
---
# <a name="quick-start-installation-of-sql-server-2014"></a>Schnellstart-Installation von SQL Server 2014
    
## <a name="introduction"></a>Einführung  
 Der Installations-Assistent von [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] basiert auf Windows Installer. Er verfügt über eine einzelne Funktionsstruktur für die Installation der folgenden [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]-Komponenten:  
  
-   [!INCLUDE[ssDE](../includes/ssde-md.md)]  
  
-   [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]  
  
-   [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)]  
  
-   [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)]  
  
-   [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]  
  
-   [!INCLUDE[ssDQSnoversion](../includes/ssdqsnoversion-md.md)]  
  
-   Verwaltungstools  
  
-   Konnektivitätskomponenten  
  
 Sie können jede Komponente einzeln installieren oder eine Kombination der oben aufgelisteten Komponenten auswählen. Die bestmögliche Auswahl unter den Editionen und Komponenten in zur Verfügung stellen [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)], finden Sie unter [Editionen und Komponenten von SQL Server 2014](../sql-server/editions-and-components-of-sql-server-2016.md).  
  
 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] ist als 32- und 64-Bit-Edition verfügbar. Das Setup von [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] unterstützt die folgenden Installationsoptionen:  
  
-   **Installations-Assistent**  
  
     Finden Sie unter [Installieren von SQL Server 2014 vom Installations-Assistenten &#40;Setup&#41; ](../database-engine/install-windows/install-sql-server-from-the-installation-wizard-setup.md) Informationen zur Vorgehensweise beim Installieren von [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] mithilfe des Installations-Assistenten.  
  
-   **Eingabeaufforderung**  
  
     Finden Sie unter [Installieren von SQL Server 2014 über die Eingabeaufforderung](../database-engine/install-windows/install-sql-server-from-the-command-prompt.md) für Beispielparameter Beispielsyntax und Installationsparameter zum Ausführen einer unbeaufsichtigten Installation.  
  
-   **Konfigurationsdatei**  
  
     Finden Sie unter [Installieren von SQL Server 2014 mithilfe einer Konfigurationsdatei](../database-engine/install-windows/install-sql-server-using-a-configuration-file.md) für Beispielparameter Beispielsyntax und Installationsparameter zum Ausführen des Setups mithilfe einer Konfigurationsdatei.  
  
-   **SysPrep**  
  
     Finden Sie unter [installieren SQL Server 2014 mit SysPrep](../database-engine/install-windows/install-sql-server-using-sysprep.md) Informationen zur Vorgehensweise beim Installieren von [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] mithilfe von SysPrep.  
  
-   **Server Core-Installation**  
  
     Finden Sie unter [Installieren von SQL Server 2014 unter Server Core](../database-engine/install-windows/install-sql-server-on-server-core.md) Informationen zur Vorgehensweise beim Installieren von [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] unter Windows Server Core.  
  
-   **[!INCLUDE[ssCurrent](../includes/sscurrent-md.md)] BI-Funktionsinstallation**  
  
     Finden Sie unter [Installieren von SQL Server 2014 BI Features](../sql-server/install/install-sql-server-business-intelligence-features.md) Informationen zum Installieren von Features, die Teil der Microsoft BI Plattform sind, enthalten [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)], [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)], [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)], [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)], und mehrere Clientanwendungen, die zum Erstellen von oder Arbeiten mit analytischen Daten verwendet werden.  
  
-   **Failoverclusterinstallation**  
  
     Finden Sie unter [SQL Server-Failoverclusterinstallation](../sql-server/failover-clusters/install/sql-server-failover-cluster-installation.md) Informationen zur Vorgehensweise beim Installieren von [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] auf eine [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Failovercluster.  
  
 Standardmäßig werden Beispieldatenbanken und Beispielcode nicht als Teil des [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] -Setups installiert. Informationen zum Installieren von Beispieldatenbanken und Beispielcode für andere als Editionen-Editionen von [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] finden Sie auf der [CodePlex-Website](https://go.microsoft.com/fwlink/?LinkId=87843). Supportinformationen zu [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]-Beispieldatenbanken und Beispielcode für [!INCLUDE[ssExpress](../includes/ssexpress-md.md)] finden Sie unter [Databases and Samples Overview](https://go.microsoft.com/fwlink/?LinkId=110391) (Übersicht über Datenbanken und Beispiele).  
  
## <a name="includessnoversionincludesssnoversion-mdmd-installation"></a>[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]-Installation  
 Unabhängig davon, ob Sie die Installation von [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] mithilfe des Installations-Assistenten für [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] oder an der Eingabeaufforderung vornehmen, umfasst das Setup immer mindestens einen der folgenden Schritte:  
  
-   Überprüfen Sie die Installationsanforderungen, Systemkonfigurationsprüfungen und Sicherheitsaspekte für eine [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] -Installation.  Weitere Informationen finden Sie unter [Planen einer SQL Server-Installation](quick-start-installation-of-sql-server-2014.md#BKMK_BeforeYouInstall).  
  
-   Führen Sie [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]-Setup aus, um eine vorhandene Version von [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] auf [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)] zu aktualisieren. Weitere Informationen finden Sie unter [ein Upgrade auf SQL Server 2014](#BKMK_Upgrading).  
  
-   Führen Sie [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]-Setup aus, um eine neue Instanz von [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)] zu installieren. Weitere Informationen finden Sie unter [Installation von SQL Server 2014](#BKMK_Install).  
  
-   Nach der Installation von [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] ist der nächste Schritt die Konfiguration von [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] und den zugehörigen Komponenten. Verwenden Sie [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] -Hilfsprogramme, um [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]zu konfigurieren. Weitere Informationen finden Sie unter [Konfigurieren von SQL Server 2014](#BKMK_Configure).  
  
 Ausführliche Erklärungen dieser Tasks finden Sie im nächsten Abschnitt.  
  
## <a name="related-tasks"></a>Related Tasks  
  
###  <a name="BKMK_BeforeYouInstall"></a> Planen einer [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Installation  
 Vor der Installation von [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)] müssen Sie die Hardware- und Softwareanforderungen, die Netzwerk- und Internetüberlegungen sowie die Sicherheitsüberlegungen für die Installation und Ausführung von [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] überprüfen. Weitere Informationen finden Sie unter [Planen einer SQL Server-Installation](../../2014/sql-server/install/planning-a-sql-server-installation.md) und auch den folgenden Themen:  
  
|Taskbeschreibung|Thema|  
|----------------------|-----------|  
|Überprüfen Sie die -Hardware- und -Softwareanforderungen, die Betriebssystemunterstützung, die Netzwerk- und Internetüberlegungen sowie den erforderlichen Festplattenspeicherplatz.|[Installationsvoraussetzungen](../sql-server/install/hardware-and-software-requirements-for-installing-sql-server.md)|  
|Lesen Sie die Sicherheitsüberlegungen für eine [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]-Installation aufmerksam durch.|[Überlegungen zur Sicherheit](../../2014/sql-server/install/security-considerations-for-a-sql-server-installation.md)|  
|Überprüfen Sie die detaillierten Informationen zu den von verschiedenen [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)]-Versionen unterstützten Funktionen.|[Funktionen und Editionen](features-supported-by-the-editions-of-sql-server-2014.md)|  
|Bestimmen Sie die bestmögliche Auswahl unter den in [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] verfügbaren Editionen und Komponenten.|[Editionen und Komponenten von SQL Server 2014](../sql-server/editions-and-components-of-sql-server-2016.md)|  
|Überprüfen Sie die Hardwarekonfiguration, und erfahren Sie, wie Sie die [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]-Failoverclusterinstallation vorbereiten.|[Vor dem Installieren des Failoverclusterings](../sql-server/failover-clusters/install/before-installing-failover-clustering.md)|  
  
###  <a name="BKMK_Upgrading"></a> Ein Upgrade auf [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)]  
 Sie können vorhandene Instanzen von [!INCLUDE[ssVersion2005](../includes/ssversion2005-md.md)], [!INCLUDE[ssKatmai](../includes/sskatmai-md.md)], [!INCLUDE[ssKilimanjaro](../includes/sskilimanjaro-md.md)] oder [!INCLUDE[ssSQL11](../includes/sssql11-md.md)] auf [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)] aktualisieren. Weitere Informationen finden Sie unter [aktualisieren auf SQL Server 2014](../database-engine/install-windows/upgrade-sql-server.md). Lesen Sie vor der Ausführung des [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]-Setups zur Aktualisierung auf [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)] die folgenden Themen über den Upgradevorgang:  
  
|Description|Thema|  
|-----------------|-----------|  
|Dokumentiert unterstützte Upgradepfade zu [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)].|[Unterstützte Upgrades](../database-engine/install-windows/supported-version-and-edition-upgrades.md)|  
|Beschreibt den Upgrade Advisor, ein Tool, das Instanzen von [!INCLUDE[ssVersion2005](../includes/ssversion2005-md.md)], [!INCLUDE[ssKatmai](../includes/sskatmai-md.md)], [!INCLUDE[ssKilimanjaro](../includes/sskilimanjaro-md.md)] und [!INCLUDE[ssSQL11](../includes/sssql11-md.md)] analysiert, um bekannte Probleme beim Upgrade zu identifizieren.|[Verwenden von Upgrade Advisor zur Vorbereitung auf Upgrades](../../2014/sql-server/install/use-upgrade-advisor-to-prepare-for-upgrades.md)|  
|Beschreibt das Distributed Replay Utility, ein Tool, das Ablaufverfolgungsdaten mithilfe mehrerer Computern wiedergeben und eine unternehmenswichtige Arbeitsauslastung simulieren kann. Durch Ausführen einer Wiedergabe auf einem Testserver vor und nach einem [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]-Upgrade können Sie Leistungsunterschiede messen und nach Inkompatibilitäten der Anwendung suchen, die möglicherweise durch das Upgrade verursacht werden.|[Vorbereiten von Upgrades mit dem Distributed Replay-Hilfsprogramm](../../2014/sql-server/install/use-the-distributed-replay-utility-to-prepare-for-upgrades.md)|  
|Listet wichtige Änderungen auf, die sich auf die Anwendungen auswirken können, nachdem Sie auf [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)] aktualisieren.|[Abwärtskompatibilität](backward-compatibility.md)|  
|Das Thema mit Anleitungen zum Aktualisieren einer eigenständigen Instanz von [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] auf [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)].|[Aktualisieren auf SQL Server 2014 mithilfe des Installations-Assistenten &#40;Setup&#41;](../database-engine/install-windows/upgrade-sql-server-using-the-installation-wizard-setup.md)|  
|Das Thema mit Anleitungen zum Aktualisieren einer Edition von [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)] auf eine andere Edition. Weitere Informationen finden Sie unter [Unterstützte Versions- und Editionsupgrades](../database-engine/install-windows/supported-version-and-edition-upgrades.md).|[Upgrade auf eine andere Edition von SQLServer 2014 &#40;Setup&#41;](../database-engine/install-windows/upgrade-to-a-different-edition-of-sql-server-setup.md)|  
|[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] unterstützt ein separates Upgrade von [!INCLUDE[ssDE](../includes/ssde-md.md)] und [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] auf allen Failoverclusterknoten unter [!INCLUDE[ssVersion2005](../includes/ssversion2005-md.md)], [!INCLUDE[ssKatmai](../includes/sskatmai-md.md)], [!INCLUDE[ssKilimanjaro](../includes/sskilimanjaro-md.md)] oder  [!INCLUDE[ssSQL11](../includes/sssql11-md.md)] auf [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)]-Failovercluster. Weitere Informationen finden Sie in diesem Thema.|[Upgraden eines SQL Server-Failoverclusters](../sql-server/failover-clusters/windows/upgrade-a-sql-server-failover-cluster-instance.md)|  
  
###  <a name="BKMK_Install"></a> Installieren von [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)]  
 Informationen zu verschiedenen Installationsszenarien für [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)] finden Sie in den folgenden Themen.  
  
|Description|Thema|  
|-----------------|-----------|  
|Stellt Links zu Themen über die Installation verschiedener Komponenten von [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)] und zu Themen mit Anleitungen für die Installation von [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)] bereit.|[Installieren von SQL Server 2014](../database-engine/install-windows/install-sql-server.md)|  
|Lesen Sie dieses Thema, wenn Sie [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)] unter Windows Server Core installieren möchten.|[Installieren von SQL Server 2014 unter Server Core](../database-engine/install-windows/install-sql-server-on-server-core.md)|  
|Lesen Sie dieses Thema, um einer vorhandenen Instanz von [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)] einzelne Funktionen hinzuzufügen.|[Hinzufügen von Funktionen zu einer Instanz von SQLServer 2014 &#40;Setup&#41;](../database-engine/install-windows/add-features-to-an-instance-of-sql-server-setup.md)|  
|Lesen Sie dieses Thema, um eine neue [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]-Failoverclusterinstanz zu erstellen.|[Erstellen eines neuen SQL Server-Failoverclusters &#40;Setup&#41;](../sql-server/failover-clusters/install/create-a-new-sql-server-failover-cluster-setup.md)|  
|Verwenden Sie dieses Thema zum Verwalten von Knoten in einem vorhandenen [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Failoverclusterinstanz.|[Hinzufügen oder Entfernen von Knoten in einem SQL Server-Failovercluster &#40;Setup&#41;](../sql-server/failover-clusters/install/add-or-remove-nodes-in-a-sql-server-failover-cluster-setup.md)|  
|Dieses Thema enthält Informationen darüber, wie Sie [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]-Clienttools auf einem Failovercluster installieren.|[Installieren von Clienttools auf einem SQL Server-Failovercluster](../sql-server/failover-clusters/install/install-client-tools-on-a-sql-server-failover-cluster.md)|  
|Informieren Sie sich darüber, wie Sie mithilfe des SQL-Ermittlungsberichts die [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] -Version sowie die auf dem Computer installierten [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] -Funktionen überprüfen.|[Überprüfen einer SQL Server-Installation](../database-engine/install-windows/validate-a-sql-server-installation.md)|  
|Enthält Links zu verfahrensspezifischen Themen für die Installation von [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)] mit dem Installations-Assistenten, über die Eingabeaufforderung, unter Verwendung von Konfigurationsdateien sowie mithilfe von "SysPrep".|[Themen zu Vorgehensweisen für die Installation](../../2014/sql-server/install/installation-how-to-topics.md)|  
  
## <a name="related-content"></a>Verwandte Inhalte  
 Dieser Abschnitt enthält Informationen zur Konfiguration und Deinstallation von [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)].  
  
###  <a name="BKMK_Configure"></a> Konfigurieren von [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)]  
 Nachdem die Installation von [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] abgeschlossen ist, können Sie [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] mithilfe der grafischen und der Eingabeaufforderungs-Hilfsprogramme weiter konfigurieren. Folgende Themen enthalten weitere Informationen, wenn Sie [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] zum ersten Mal konfigurieren:  
  
|Description|Thema|  
|-----------------|-----------|  
|Anhand der Informationen in diesem Thema können Sie feststellen, ob Sie die Blockierung von Ports in einer Firewall aufheben müssen, um den Zugriff auf [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] oder PowerPivot für SharePoint zuzulassen. Sie können die Schritte in diesem Thema befolgen, um Port- und Firewalleinstellungen zu konfigurieren.|[Konfigurieren der Windows-Firewall, um den Zugriff auf Analysis Services zuzulassen](../analysis-services/instances/configure-the-windows-firewall-to-allow-analysis-services-access.md)|  
|Dieses Thema bietet einen Überblick über die Firewallkonfiguration und fasst Informationen zusammen, die für einen [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] -Administrator interessant sind.|[Konfigurieren der Windows-Firewall für den SQL Server-Zugriff](../../2014/sql-server/install/configure-the-windows-firewall-to-allow-sql-server-access.md)|  
|In diesem Thema wird beschrieben, wie [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] und Windows-Firewall mit erweiterter Sicherheit konfiguriert werden, um Netzwerkverbindungen zu einer Instanz von [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] in einer mehrfach vernetzten Umgebung bereitzustellen.|[Konfigurieren eines mehrfach vernetzten Computers für SQL Server-Zugriff](../../2014/sql-server/install/configure-a-multi-homed-computer-for-sql-server-access.md)|  
  
###  <a name="BKMK_Uninstalling"></a> Deinstallieren von [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)]  
 In den folgenden Themen wird beschrieben, wie Sie eine eigenständige Instanz und eine Failoverclusterinstanz von [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] manuell deinstallieren:  
  
|Description|Thema|  
|-----------------|-----------|  
|In diesem Thema wird beschrieben, wie Sie eine eigenständige Instanz von [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]manuell deinstallieren.|[Deinstallieren von SQL Server 2014](../sql-server/install/uninstall-sql-server.md)|  
|In diesem Thema wird beschrieben, wie Sie eine [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]-Failoverclusterinstanz deinstallieren.|[Entfernen einer SQL Server-Failoverclusterinstanz &#40;Setup&#41;](../sql-server/failover-clusters/install/remove-a-sql-server-failover-cluster-instance-setup.md)|  
|In diesem Thema wird erläutert, wie [!INCLUDE[ssDQSnoversion](../includes/ssdqsnoversion-md.md)]-Objekte (DQS) nach der Deinstallation von [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] oder lediglich von DQS-Server manuell entfernt werden.|[Entfernen von Data Quality Server-Objekten](../../2014/sql-server/install/remove-data-quality-server-objects.md)|  
  
## <a name="see-also"></a>Siehe auch  
 [Produktspezifikationen für SQLServer 2014](sql-server-2014-product-specifications.md)   
 [Erste Schritte mit SQLServer-Produktdokumentation in](../2014-toc/books-online-for-sql-server-2014.md) [Abwärtskompatibilität](backward-compatibility.md)  
  
  
