---
title: Wichtige Änderungen an Funktionen der Verwaltungs Tools in SQL Server 2014 | Microsoft-Dokumentation
ms.custom: ''
ms.date: 11/27/2018
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
ms.assetid: 3ff3fad8-b569-4516-bd58-5a3efeb537e2
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 73e2c6ecb4ae2f829c02897ed5c6ab5d84f1ba4b
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "62787014"
---
# <a name="breaking-changes-to-management-tools-features-in-sql-server-2014"></a>Wichtige Änderungen an Funktionen der Verwaltungstools in SQL Server 2014
  In diesem Thema werden aktuelle Änderungen an Funktionen der Verwaltungstools beschrieben. Diese Änderungen können u. U. zur Funktionsunfähigkeit von Anwendungen, Skripts oder Funktionen führen, die auf früheren Versionen von [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]basieren. Diese Probleme können nach einem Upgrade auftreten. Weitere Informationen finden Sie unter [Use Upgrade Advisor to Prepare for Upgrades](../../2014/sql-server/install/use-upgrade-advisor-to-prepare-for-upgrades.md).  
  
## <a name="breaking-changes-in-includesssql14includessssql14-mdmd"></a>Wichtige Änderungen in [!INCLUDE[ssSQL14](../includes/sssql14-md.md)]  
 Informationen werden später bereitgestellt.  
  
## <a name="breaking-changes-in-includesssql11includessssql11-mdmd"></a>Wichtige Änderungen in [!INCLUDE[ssSQL11](../includes/sssql11-md.md)]  
  
### <a name="you-cannot-use-includesssql11includessssql11-mdmd-management-tools-to-create-a-utility-control-point-on-a-includesskilimanjaroincludessskilimanjaro-mdmd-instance-of-sql-server"></a>Sie können keine [!INCLUDE[ssSQL11](../includes/sssql11-md.md)] -Verwaltungstools zum Erstellen eines Steuerungspunkts für das Hilfsprogramm auf einer [!INCLUDE[ssKilimanjaro](../includes/sskilimanjaro-md.md)] -Instanz von SQL Server verwenden.  
 Verwenden Sie [!INCLUDE[ssKilimanjaro](../includes/sskilimanjaro-md.md)]-Verwaltungstools, um auf einer Instanz von [!INCLUDE[ssKilimanjaro](../includes/sskilimanjaro-md.md)] einen Steuerungspunkt für das Hilfsprogramm zu erstellen.  
  
### <a name="smo-has-been-reversioned-in-includesssql11includessssql11-mdmd"></a>SMO liegt in [!INCLUDE[ssSQL11](../includes/sssql11-md.md)] in einer neuen Version vor.  
 Mit SMO aus [!INCLUDE[ssKilimanjaro](../includes/sskilimanjaro-md.md)] oder früheren Versionen entwickelter Code kann nicht ohne kleinere Änderungen für [!INCLUDE[ssSQL11](../includes/sssql11-md.md)] erstellt werden. Weitere Informationen finden Sie unter [Backward Compatibility in SMO](../relational-databases/server-management-objects-smo/backward-compatibility-in-smo.md).  

## <a name="previous-versions"></a>Wichtige Änderungen in SQL Server 2005  

[!INCLUDE[Archived documentation for very old versions of SQL Server](../includes/paragraph-content/previous-versions-archive-documentation-sql-server.md)]

## <a name="see-also"></a>Weitere Informationen  
 [Abwärtskompatibilität](../../2014/getting-started/backward-compatibility.md)  
 [Weitere Informationen zu wichtigen Änderungen an Funktionen der Verwaltungs Tools in SQL Server 2014](breaking-changes-to-database-engine-features-in-sql-server-2016.md?view=sql-server-2014)  
  
  
