---
title: Installieren von SQLServer 2014 | Microsoft Docs
ms.custom: ''
ms.date: 09/09/2016
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- installing SQL Server, preparing to install
- installation [SQL Server]
ms.assetid: 0300e777-d56b-4d10-9c33-c9ebd2489ee5
caps.latest.revision: 40
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: bf415bef00710562247bcfd9fa310e2c0728497f
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/19/2018
ms.locfileid: "36150234"
---
# <a name="install-sql-server-2014"></a>Installieren von SQL Server 2014
## <a name="-download-sql-server-2014-express-httpwwwhanselmancomblogdownloadsqlserverexpressaspx"></a>[ Herunterladen von SQL Server 2014 Express ](http://www.hanselman.com/blog/DownloadSQLServerExpress.aspx)
  **Vielen Dank, [Scott Hanselman](http://www.hanselman.com/) für alle Verknüpfungen Installer-Paket an einem Ort gesammelt.**
  
 Dieses Thema bietet eine Übersicht über andere Installationsoptionen, die zur Installation von [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] zur Verfügung stehen. Weitere Informationen zu den verschiedenen [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Komponenten, die installiert werden können, sowie zum Installationsvorgang finden Sie unter [Installation für SQL Server 2014](installation-for-sql-server.md).  
> **Hinweis:** [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] in 32-Bit und 64-Bit-Editionen verfügbar ist. Die 64-Bit- und 32-Bit-Edition von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] werden entweder über den Installations-Assistenten oder von der Eingabeaufforderung aus installiert. Weitere Informationen zu [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Komponenten, finden Sie unter [Editionen und Komponenten von SQL Server 2014](../../sql-server/editions-and-components-of-sql-server-2016.md) und [von den Editionen von SQL Server 2014 unterstützte Funktionen](../../getting-started/features-supported-by-the-editions-of-sql-server-2014.md).  
  
 Standardmäßig werden Beispieldatenbanken und Beispielcode nicht als Teil des [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Setups installiert. Informationen zum Installieren von Beispieldatenbanken und Beispielcode für andere als Editionen-Editionen von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] finden Sie auf der [CodePlex-Website](http://go.microsoft.com/fwlink/?LinkId=87843). Supportinformationen zu [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Beispieldatenbanken und Beispielcode für [!INCLUDE[ssExpress](../../includes/ssexpress-md.md)] finden Sie unter [Databases and Samples Overview](http://go.microsoft.com/fwlink/?LinkId=110391) (Übersicht über Datenbanken und Beispiele).  
  
 Vor der Installation von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] sollten Sie die Installationsanforderungen, Systemkonfigurationsprüfungen und Sicherheitsaspekte überprüfen. Weitere Informationen finden Sie unter [Planen einer SQL Server-Installation](../../sql-server/install/planning-a-sql-server-installation.md). Überprüfen Sie die Themen im nächsten Abschnitt, um Informationen zu den verschiedenen Installationsszenarien für [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] zu erhalten.  
  
  
## <a name="install-includesscurrentincludessscurrent-mdmd-components"></a>Installieren Sie [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] Komponenten  
  
|Thema|Description|  
|-----------|-----------------|  
|[Über das SQL Server-Datenbankmodul](../sql-server-database-engine-overview.md)|Beschreibt, wie Sie [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]installieren und konfigurieren.|  
|[Installieren der SQL Server-Replikation](install-sql-server-replication.md)|Beschreibt, wie Sie die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Replikation installieren und konfigurieren.|  
|[Installieren von Distributed Replay](../../tools/distributed-replay/install-distributed-replay-overview.md)|Enthält eine Auflistung der Themen zur Installation der Distributed Replay-Funktion.|  
|[Installieren der SQL Server-Verwaltungstools](../../sql-server/install/install-sql-server-management-tools.md)|Beschreibt, wie Sie die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Verwaltungstools installieren und konfigurieren.|  
|[Installieren von SQL Server PowerShell](install-sql-server-powershell.md)|Beschreibt die Überlegungen zum Installieren von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] PowerShell-Komponenten.|  
  
## <a name="how-to-install-includesscurrentincludessscurrent-mdmd"></a>Gewusst wie: Installieren [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]  
  
|Titel|Description|  
|-----------|-----------------|  
|[Themen zu Vorgehensweisen für die Installation](../../sql-server/install/installation-how-to-topics.md)|Enthält Links zu verfahrensspezifischen Themen für die Installation von [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] mit dem Installations-Assistenten, über die Eingabeaufforderung, unter Verwendung von Konfigurationsdateien sowie mithilfe von "SysPrep".|  
|[Installieren von SQL Server 2014 unter Server Core](install-sql-server-on-server-core.md)|Lesen Sie dieses Thema, wenn Sie [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] unter Windows Server Core installieren möchten.|  
|[Überprüfen einer SQL Server-Installation](validate-a-sql-server-installation.md)|Informieren Sie sich darüber, wie Sie mithilfe des SQL-Ermittlungsberichts die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Version sowie die auf dem Computer installierten [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Funktionen überprüfen.|  
|[Überprüfen der Parameter für die Systemkonfigurationsprüfung](check-parameters-for-the-system-configuration-checker.md)|Erläutert die Funktion der Systemkonfigurationsprüfung (System Configuration Checker, SCC).|  
  
## <a name="configuration"></a>Konfiguration  
  
|Thema|Description|  
|-----------|-----------------|  
|[Konfigurieren der Windows-Firewall für den SQL Server-Zugriff](../../sql-server/install/configure-the-windows-firewall-to-allow-sql-server-access.md)|Dieses Thema bietet einen Überblick über die Firewallkonfiguration und wie Windows-Firewall konfiguriert wird.|  
|[Konfigurieren eines mehrfach vernetzten Computers für SQL Server-Zugriff](../../sql-server/install/configure-a-multi-homed-computer-for-sql-server-access.md)|In diesem Thema wird beschrieben, wie [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] und Windows-Firewall mit erweiterter Sicherheit konfiguriert werden, um Netzwerkverbindungen zu einer Instanz von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] in einer mehrfach vernetzten Umgebung bereitzustellen.|  
|[Konfigurieren der Windows-Firewall, um den Zugriff auf Analysis Services zuzulassen](../../analysis-services/instances/configure-the-windows-firewall-to-allow-analysis-services-access.md)|Sie können die in diesem Thema beschriebenen Schritte zur Konfiguration von Port- und Firewalleinstellungen ausführen, um den Zugriff auf [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] oder PowerPivot für SharePoint zuzulassen.|  
  
## <a name="related-sections"></a>Verwandte Abschnitte  
 [Installieren von SQL Server 2014-BI-Funktionen](../../sql-server/install/install-sql-server-business-intelligence-features.md)  
 Zu den [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Funktionen, die Teil der [!INCLUDE[msCoName](../../includes/msconame-md.md)] BI-Plattform sind, zählen [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)], [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)], [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)], [!INCLUDE[ssDQSnoversion](../../includes/ssdqsnoversion-md.md)] sowie mehrere Clientanwendungen, die zum Erstellen von oder Arbeiten mit analytischen Daten verwendet werden. Dieser Abschnitt der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Setupdokumentation erklärt, wie [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)], [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)], [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)], [!INCLUDE[ssDQSnoversion](../../includes/ssdqsnoversion-md.md)] und [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] installiert werden.  
  
 [SQL Server-Failoverclusterinstallation](../../sql-server/failover-clusters/install/sql-server-failover-cluster-installation.md)  
 In diesem Abschnitt der Dokumentation zum [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Setup wird die Installation und Konfiguration von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Failoverclustern beschrieben.  
  
## <a name="see-also"></a>Siehe auch  
 [Planen einer SQL Server-Installation](../../sql-server/install/planning-a-sql-server-installation.md)   
 [Aktualisieren auf SQLServer 2014](upgrade-sql-server.md)   
 [Deinstallieren von SQLServer 2014](../../sql-server/install/uninstall-sql-server.md)   
 [Lösungen mit hoher Verfügbarkeit &#40;SQL Server&#41;](../../sql-server/failover-clusters/high-availability-solutions-sql-server.md)  
  
  