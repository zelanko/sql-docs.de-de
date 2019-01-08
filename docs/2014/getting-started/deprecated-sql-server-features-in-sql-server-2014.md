---
title: Als veraltet markierte SQL Server-Funktionen in SQLServer 2014 | Microsoft-Dokumentation
ms.custom: ''
ms.date: 05/24/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- database-engine
ms.topic: conceptual
ms.assetid: fdc0c778-cc8d-42ab-8833-4deb4329f37a
author: mightypen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 4abd066dd2fc971528468fb7104cb0c11e088150
ms.sourcegitcommit: 334cae1925fa5ac6c140e0b2c38c844c477e3ffb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/13/2018
ms.locfileid: "53348788"
---
# <a name="deprecated-sql-server-features-in-sql-server-2014"></a>Als veraltet markierte SQL Server-Funktionen in SQL Server 2014
  In diesem Thema werden die als veraltet markierten Funktionen beschrieben, die in [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)]noch verfügbar sind. Diese Funktionen werden voraussichtlich in einer zukünftigen Version von [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]entfernt. Als veraltet markierte Funktionen sollten in neuen Anwendungen nicht verwendet werden.  
  
## <a name="features-not-supported-in-the-next-version-of-includessnoversionincludesssnoversion-mdmd"></a>Funktionen, die in der nächsten Version von [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] nicht unterstützt werden  
 Die folgenden [!INCLUDE[ssDEnoversion](../includes/ssdenoversion-md.md)] -Funktionen werden in der nächsten Version von [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]nicht mehr unterstützt. Verwenden Sie diese Funktionen nicht zum Entwickeln neuer Anwendungen, und ändern Sie so bald wie möglich die Anwendungen, in denen diese Funktionen zurzeit verwendet werden. Die Spalte Funktionsname wird in Ablaufverfolgungsereignissen als ObjectName und in Leistungsindikatoren sowie sys.dm_os_performance_counters als instance_name angezeigt. Die Funktions-ID wird in Ablaufverfolgungsereignissen als ObjectId angezeigt.  
  
|Kategorie|Als veraltet markierte Funktion|Ersatz|Feature name|Funktions-ID|  
|--------------|------------------------|-----------------|------------------|----------------|  
|Datenprogrammierbarkeit|[Sys. soap_endpoints &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-soap-endpoints-transact-sql)|Windows Communications Foundation (WCF) oder ASP.NET|Systemeigene XML-Webdienste|22|  
|Datenprogrammierbarkeit|[Sys. endpoint_webmethods &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-endpoint-webmethods-transact-sql)|Windows Communications Foundation (WCF) oder ASP.NET|Systemeigene XML-Webdienste|23|  
  
### <a name="slipstream-functionality"></a>Slipstreamfunktionalität  
 Die Produktupdate-Funktion ersetzt die Slipstreamfunktionalität, die in [!INCLUDE[ssKatmai](../includes/sskatmai-md.md)] PCU1 verfügbar war. Daher sollten die Befehlszeilenparameter, /*PCUSource* und /*CUSource*, die der Slipstreamfunktionalität zugeordnet sind, nicht mehr verwendet werden. Die Parameter funktionieren auch weiterhin, werden jedoch möglicherweise in einer zukünftigen Version des [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] -Setups entfernt. Der /*UpdateSource* -Parameter kombiniert die Funktionalität der Slipstreamparameter, /*PCUSource* und /*CUSource*.  
  
 Weitere Informationen zur slipstreamfunktionalität, die in verfügbar war [!INCLUDE[ssKatmai](../includes/sskatmai-md.md)] PCU1, finden Sie unter [Slipstream-SQL-Serverupdate](https://go.microsoft.com/fwlink/?LinkId=219945) (https://go.microsoft.com/fwlink/?LinkId=219945).  
  
## <a name="see-also"></a>Siehe auch  
 [Abwärtskompatibilität](../../2014/getting-started/backward-compatibility.md)  
  
  
