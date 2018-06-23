---
title: Hochverfügbarkeitslösungen (SQL Server) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dbe-high-availability
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- high availability [SQL Server], solutions
- Database Engine [SQL Server], availability
- database availability [SQL Server]
- availability [SQL Server]
- server availability [SQL Server]
ms.assetid: b2eda634-0f8e-4703-801b-7ba895544ff5
caps.latest.revision: 80
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 061606f86a28216e78409e6521c78cc301d4c738
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/19/2018
ms.locfileid: "36163070"
---
# <a name="high-availability-solutions-sql-server"></a>Lösungen mit hoher Verfügbarkeit (SQL Server)
  In diesem Thema werden mehrere Hochverfügbarkeitslösungen von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] vorgestellt, die die Verfügbarkeit von Servern oder Datenbanken verbessern. Eine Lösung mit hoher Verfügbarkeit unterdrückt die Auswirkungen eines Hardware- oder Softwarefehlers und hält die Verfügbarkeit von Anwendungen aufrecht, damit die Ausfallzeiten für Benutzer so gering wie möglich gehalten werden.  
  
> [!NOTE]  
>  Informationen dazu, welche [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Editionen eine bestimmte Lösung mit Hochverfügbarkeit unterstützen, finden Sie im Artikel [Von den SQL Server 2014-Editionen unterstützte Funktionen](../../getting-started/features-supported-by-the-editions-of-sql-server-2014.md) im Abschnitt „Hochverfügbarkeit (Always On)“.  
(#RecommendedSolutions)  
  
##  <a name="TermsAndDefinitions"></a> Übersicht über SQL Server-Hochverfügbarkeitslösungen  
 In [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] sind mehrere Optionen zum Einrichten von Hochverfügbarkeit für einen Server oder eine Datenbank verfügbar. Die Hochverfügbarkeitsoptionen umfassen Folgendes:  
  
 AlwaysOn-Failoverclusterinstanzen  
 Als Teil des [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] AlwaysOn-Angebots nutzen AlwaysOn-Failoverclusterinstanzen die Funktionalität Windows Server-Failoverclustering (WSFC), um lokale Hochverfügbarkeit durch Redundanz auf Serverinstanzebene (eine *Failoverclusterinstanz* (FCI)) zu bieten. Eine FCI ist eine einzelne Instanz von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . Diese ist auf Windows Server-Failoverclustering-Knoten (WSFC) und möglicherweise auf mehreren Subnetzen installiert. In einem Netzwerk wird eine FCI als eine Instanz von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] angezeigt, die auf einem einzelnen Computer ausgeführt wird. Die FCI bietet jedoch die Möglichkeit zur Failoverbereitstellung von einem WSFC-Knoten zu einem anderen, wenn der aktuelle Knoten nicht verfügbar ist.  
  
 Weitere Informationen finden Sie unter [ AlwaysOn-Failoverclusterinstanzen (SQL Server)](windows/always-on-failover-cluster-instances-sql-server.md).  
  
 [!INCLUDE[ssHADR](../../includes/sshadr-md.md)]  
 [!INCLUDE[ssHADR](../../includes/sshadr-md.md)] ist eine Hochverfügbarkeits- und Notfallwiederherstellungslösung auf Unternehmensebene, die in [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] eingeführt wurde und die Maximierung der Verfügbarkeit für mindestens eine Benutzerdatenbank ermöglicht. [!INCLUDE[ssHADR](../../includes/sshadr-md.md)] erfordert, dass sich die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Instanzen auf Windows Server-Failoverclusteringknoten (WSFC) befinden. Weitere Informationen finden Sie unter [ AlwaysOn-Verfügbarkeitsgruppen (SQL Server)](../../database-engine/availability-groups/windows/always-on-availability-groups-sql-server.md).  
  
> [!NOTE]  
>  Eine FCI kann [!INCLUDE[ssHADR](../../includes/sshadr-md.md)] nutzen, um die Remotewiederherstellung im Notfall auf Datenbankebene bereitzustellen. Weitere Informationen finden Sie unter [Failoverclustering und AlwaysOn-Verfügbarkeitsgruppen &#40;SQL Server&#41;](../../database-engine/availability-groups/windows/failover-clustering-and-always-on-availability-groups-sql-server.md).  
  
 Datenbankspiegelung  
 > [!NOTE]  
>  [!INCLUDE[ssNoteDepFutureAvoid](../../includes/ssnotedepfutureavoid-md.md)] Stattdessen wird die Verwendung von [!INCLUDE[ssHADR](../../includes/sshadr-md.md)] empfohlen.  
  
 Die Datenbankspiegelung stellt eine Softwarelösung dar, mit der die Verfügbarkeit einer Datenbank erhöht wird, indem ein fast sofortiges Failover unterstützt wird. Mit der Datenbankspiegelung kann eine einzelne Datenbank, die sich im Standbymodus befindet, eine so genannte *Spiegeldatenbank*, für eine entsprechende Produktionsdatenbank, eine so genannte *Prinzipaldatenbank*, verwaltet werden. Weitere Informationen finden Sie unter [Datenbankspiegelung &#40;SQL Server&#41;](../../database-engine/database-mirroring/database-mirroring-sql-server.md).  
  
 Protokollversand  
 Wie die [!INCLUDE[ssHADR](../../includes/sshadr-md.md)] - und Datenbankspiegelung arbeitet auch der Protokollversand auf Datenbankebene. Sie können den Protokollversand verwenden, um eine oder mehrere Datenbanken im betriebsbereiten Standbymodus (*sekundäre Datenbanken*) für eine einzelne Produktionsdatenbank (*primäre Datenbank*) zu verwalten. Weitere Informationen zum Protokollversand finden Sie unter [Informationen zum Protokollversand &#40;SQL Server&#41;](../../database-engine/log-shipping/about-log-shipping-sql-server.md).  
  
##  <a name="RecommendedSolutions"></a> Empfohlene Lösungen zum Verwenden von SQL Server für das Schützen von Daten  
 Unsere Empfehlung zum Bereitstellen von Datenschutz für die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Umgebung lautet:  
  
-   Für den Datenschutz über eine freigegebene Datenträgerlösung (ein SAN) eines Drittanbieters empfiehlt es sich, dass Sie AlwaysOn-Failoverclusterinstanzen verwenden.  
  
-   Für den Datenschutz über [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]sollten Sie [!INCLUDE[ssHADR](../../includes/sshadr-md.md)]verwenden.  
  
    > [!NOTE]  
    >  Wenn Sie eine Edition von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ausführen, der [!INCLUDE[ssHADR](../../includes/sshadr-md.md)]nicht unterstützt, sollten Sie den Protokollversand verwenden. Informationen dazu, welche [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Editionen [!INCLUDE[ssHADR](../../includes/sshadr-md.md)] unterstützen, finden Sie im Artikel [Von den SQL Server 2014-Editionen unterstützte Funktionen](../../getting-started/features-supported-by-the-editions-of-sql-server-2014.md) im Abschnitt „Hohe Verfügbarkeit (Always On)“.  
  
## <a name="see-also"></a>Siehe auch  
 [Windows Server-Failoverclustering &#40;WSFC&#41; mit SQL Server](windows/windows-server-failover-clustering-wsfc-with-sql-server.md)   
 [Datenbankspiegelung: Interoperabilität und Koexistenz &#40;SQL Server&#41;](../../database-engine/database-mirroring/database-mirroring-interoperability-and-coexistence-sql-server.md)   
 [Als veraltet markierte Features der Datenbank-Engine in SQL Server 2014](../../database-engine/deprecated-database-engine-features-in-sql-server-2016.md)  
  
  