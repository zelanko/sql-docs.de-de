---
title: Wichtige Änderungen an Funktionen der Verwaltungstools in SQLServer 2014 | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology: ssms
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: 3ff3fad8-b569-4516-bd58-5a3efeb537e2
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: f206da123659c750f955d2132142dcae76df6a46
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/02/2018
ms.locfileid: "37165351"
---
# <a name="breaking-changes-to-management-tools-features-in-sql-server-2014"></a>Wichtige Änderungen an Funktionen der Verwaltungstools in SQL Server 2014
  In diesem Thema werden aktuelle Änderungen an Funktionen der Verwaltungstools beschrieben. Diese Änderungen können u. U. zur Funktionsunfähigkeit von Anwendungen, Skripts oder Funktionen führen, die auf früheren Versionen von [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]basieren. Diese Probleme können nach einem Upgrade auftreten. Weitere Informationen finden Sie unter [Use Upgrade Advisor to Prepare for Upgrades](../../2014/sql-server/install/use-upgrade-advisor-to-prepare-for-upgrades.md).  
  
## <a name="breaking-changes-in-includesssql14includessssql14-mdmd"></a>Wichtige Änderungen in [!INCLUDE[ssSQL14](../includes/sssql14-md.md)]  
 Informationen werden später bereitgestellt.  
  
## <a name="breaking-changes-in-includesssql11includessssql11-mdmd"></a>Wichtige Änderungen in [!INCLUDE[ssSQL11](../includes/sssql11-md.md)]  
  
### <a name="you-cannot-use-includesssql11includessssql11-mdmd-management-tools-to-create-a-utility-control-point-on-a-includesskilimanjaroincludessskilimanjaro-mdmd-instance-of-sql-server"></a>Sie können keine [!INCLUDE[ssSQL11](../includes/sssql11-md.md)] -Verwaltungstools zum Erstellen eines Steuerungspunkts für das Hilfsprogramm auf einer [!INCLUDE[ssKilimanjaro](../includes/sskilimanjaro-md.md)] -Instanz von SQL Server verwenden.  
 Verwenden Sie [!INCLUDE[ssKilimanjaro](../includes/sskilimanjaro-md.md)]-Verwaltungstools, um auf einer Instanz von [!INCLUDE[ssKilimanjaro](../includes/sskilimanjaro-md.md)] einen Steuerungspunkt für das Hilfsprogramm zu erstellen.  
  
### <a name="smo-has-been-reversioned-in-includesssql11includessssql11-mdmd"></a>SMO wurde geändert in [!INCLUDE[ssSQL11](../includes/sssql11-md.md)]  
 Mit SMO aus [!INCLUDE[ssKilimanjaro](../includes/sskilimanjaro-md.md)] oder früheren Versionen entwickelter Code kann nicht ohne kleinere Änderungen für [!INCLUDE[ssSQL11](../includes/sssql11-md.md)] erstellt werden. Weitere Informationen finden Sie unter [Backward Compatibility in SMO](../relational-databases/server-management-objects-smo/backward-compatibility-in-smo.md).  
  
## <a name="see-also"></a>Siehe auch  
 [Abwärtskompatibilität](../../2014/getting-started/backward-compatibility.md)  
  
  
