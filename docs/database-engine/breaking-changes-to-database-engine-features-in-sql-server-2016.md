---
title: 'Datenbank-Engine: Breaking Changes | Microsoft-Dokumentation'
titleSuffix: SQL Server 2016
description: Breaking Changes an Features der Datenbank-Engine in SQL Server 2016
ms.custom: seo-lt-2019
ms.date: 12/13/2019
ms.prod: sql
ms.prod_service: high-availability
ms.reviewer: ''
ms.technology: release-landing
ms.topic: conceptual
helpviewer_keywords:
- Database Engine [SQL Server], what's new
- breaking changes [SQL Server]
ms.assetid: 47edefbd-a09b-4087-937a-453cd5c6e061
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 67a37dd07810facf3e18e94dc0f9e552ea05778a
ms.sourcegitcommit: 792c7548e9a07b5cd166e0007d06f64241a161f8
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 12/19/2019
ms.locfileid: "75244723"
---
# <a name="breaking-changes-to-database-engine-features-in-sql-server-2016"></a>Breaking Changes an Features der Datenbank-Engine in SQL Server 2016

[!INCLUDE[tsql-appliesto-ss2016-xxxx-xxxx-xxx-md](../includes/tsql-appliesto-ss2016-xxxx-xxxx-xxx-md.md)]

  In diesem Thema werden Breaking Changes in [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)] [!INCLUDE[ssDE](../includes/ssde-md.md)] und den früheren Versionen von [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] beschrieben. Diese Änderungen können u. U. zur Funktionsunfähigkeit von Anwendungen, Skripts oder Funktionen führen, die auf früheren Versionen von [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]basieren. Diese Probleme können nach einem Upgrade auftreten.  
  
##  <a name="SQL15"></a> Wichtige Änderungen in [!INCLUDE[ssSQL15](../includes/sssql15-md.md)]  
  
-   Die Spalte *sample_ms* von `sys.dm_io_virtual_file_stats` wurde aus einem **int**- zu einem **bigint**-Datentyp erweitert.  
  
-   Die Spalte *TimeStamp* von `sys.fn_virtualfilestats` wurde aus einem **int**- zu einem **bigint**-Datentyp erweitert.  

-   Unter dem Datenbankkompatibilitätsgrad 130 ergibt sich bei einer impliziten Konvertierung aus dem Datentyp **datetime** in den Datentyp **datetime2** eine verbesserte Genauigkeit, indem die Bruchteile von Millisekunden berücksichtigt werden, wodurch sich unterschiedliche konvertierte Werte ergeben. Verwenden Sie explizite Umwandlung in den Datentyp „datetime2“, wenn ein Vergleich so gestaltet ist, dass zwischen den Datentypen „datetime“ und „datetime2“ verglichen wird. Weitere Informationen finden Sie im folgenden [Microsoft-Supportartikel](https://support.microsoft.com/help/4010261).

-   Bei einem niedrigeren Datenbankkompatibilitätsgrad als 130 weisen Vorgänge, die implizite Konvertierungen zwischen bestimmten numerischen und „datetime“-Datentypen durchführen, eine verbesserte Genauigkeit auf und können zu unterschiedlichen konvertierten Werten führen. Dies schließt die Verwendung von Funktionen ein, die Berechnungen wie z. B. `DATEDIFF` und `ROUND` erfordern. Weitere Informationen finden Sie im folgenden [Microsoft-Supportartikel](https://support.microsoft.com/help/4010261).

## <a name="previous-versions"></a> Vorgängerversionen  

Informationen zu Breaking Changes in [!INCLUDE[ssSQL14](../includes/sssql14-md.md)] und in einigen Vorgängerversionen finden Sie unter [Breaking Changes bei Funktionen der Datenbank-Engine in SQL Server 2014](../database-engine/breaking-changes-to-database-engine-features-in-sql-server-2016.md?view=sql-server-2014).

#### <a name="archived-documentation-for-very-old-versions-of-sql-server"></a>Archivierte Dokumentationen von sehr alten Versionen von SQL Server

[!INCLUDE[Archived documentation for very old versions of SQL Server](../includes/paragraph-content/previous-versions-archive-documentation-sql-server.md)]

## <a name="see-also"></a>Weitere Informationen  
 [Als veraltet markierte Funktionen der Datenbank-Engine in SQL Server 2016](../database-engine/deprecated-database-engine-features-in-sql-server-2016.md)   
 [Nicht mehr unterstützte Datenbank-Engine-Funktionalität in SQL Server 2016](../database-engine/discontinued-database-engine-functionality-in-sql-server-2016.md)   
 [Abwärtskompatibilität der SQL Server-Datenbank-Engine](../database-engine/sql-server-database-engine-backward-compatibility.md)   
 [ALTER DATABASE-Kompatibilitätsgrad &#40;Transact-SQL&#41;](../t-sql/statements/alter-database-transact-sql-compatibility-level.md)   
 [SQL Server 2016 or SQL Server 2017 on Windows improvements in handling some data types and uncommon operations (Verbesserungen der Verarbeitung einiger Datentypen und ungewöhnlicher Vorgänge für SQL Server 2016 oder SQL Server 2017 unter Windows)](https://support.microsoft.com/help/4010261).   
