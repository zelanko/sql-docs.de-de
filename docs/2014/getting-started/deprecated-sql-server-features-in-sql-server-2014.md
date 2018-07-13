---
title: Als veraltet markierte SQL Server-Funktionen in SQLServer 2014 | Microsoft-Dokumentation
ms.custom: ''
ms.date: 05/24/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: fdc0c778-cc8d-42ab-8833-4deb4329f37a
caps.latest.revision: 20
author: mightypen
ms.author: genemi
manager: craigg
ms.openlocfilehash: b7d47249b2263ea3d5523458fd34770e7c009800
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/02/2018
ms.locfileid: "37324730"
---
# <a name="deprecated-sql-server-features-in-sql-server-2014"></a>Als veraltet markierte SQL Server-Funktionen in SQL Server 2014
  In diesem Thema werden die als veraltet markierten Funktionen beschrieben, die in [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)] noch verfügbar sind. Diese Funktionen werden voraussichtlich in einer zukünftigen Version von [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]entfernt. Als veraltet markierte Funktionen sollten in neuen Anwendungen nicht verwendet werden.  
  
## <a name="features-not-supported-in-the-next-version-of-includessnoversionincludesssnoversion-mdmd"></a>Funktionen, die in der nächsten Version von [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] nicht unterstützt werden  
 Die folgenden [!INCLUDE[ssDEnoversion](../includes/ssdenoversion-md.md)] -Funktionen werden in der nächsten Version von [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]nicht mehr unterstützt. Verwenden Sie diese Funktionen nicht zum Entwickeln neuer Anwendungen, und ändern Sie so bald wie möglich die Anwendungen, in denen diese Funktionen zurzeit verwendet werden. Die Spalte Funktionsname wird in Ablaufverfolgungsereignissen als ObjectName und in Leistungsindikatoren sowie sys.dm_os_performance_counters als instance_name angezeigt. Die Funktions-ID wird in Ablaufverfolgungsereignissen als ObjectId angezeigt.  
  
|Kategorie|Als veraltet markierte Funktion|Ersatz|Feature name|Funktions-ID|  
|--------------|------------------------|-----------------|------------------|----------------|  
|Datenprogrammierbarkeit|[Sys. soap_endpoints &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-soap-endpoints-transact-sql)|Windows Communications Foundation (WCF) oder ASP.NET|Systemeigene XML-Webdienste|22|  
|Datenprogrammierbarkeit|[Sys. endpoint_webmethods &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-endpoint-webmethods-transact-sql)|Windows Communications Foundation (WCF) oder ASP.NET|Systemeigene XML-Webdienste|23|  
  
### <a name="slipstream-functionality"></a>Slipstreamfunktionalität  
 Die Produktupdate-Funktion ersetzt die Slipstreamfunktionalität, die in [!INCLUDE[ssKatmai](../includes/sskatmai-md.md)] PCU1 verfügbar war. Daher sollten die Befehlszeilenparameter, /*PCUSource* und /*CUSource*, die der Slipstreamfunktionalität zugeordnet sind, nicht mehr verwendet werden. Die Parameter funktionieren auch weiterhin, werden jedoch möglicherweise in einer zukünftigen Version des [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]-Setups entfernt. Der /*UpdateSource* -Parameter kombiniert die Funktionalität der Slipstreamparameter, /*PCUSource* und /*CUSource*.  
  
 Weitere Informationen zur slipstreamfunktionalität, die in verfügbar war [!INCLUDE[ssKatmai](../includes/sskatmai-md.md)] PCU1, finden Sie unter [Slipstream-SQL-Serverupdate](http://go.microsoft.com/fwlink/?LinkId=219945) (http://go.microsoft.com/fwlink/?LinkId=219945).  
  
## <a name="see-also"></a>Siehe auch  
 [Abwärtskompatibilität](../../2014/getting-started/backward-compatibility.md)  
  
  
