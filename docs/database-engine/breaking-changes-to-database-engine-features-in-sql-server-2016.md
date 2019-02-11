---
title: Wichtige Änderungen an Funktionen der Datenbank-Engine in SQL Server 2016 | Microsoft-Dokumentation
ms.custom: ''
ms.date: 11/27/2016
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
manager: craigg
ms.openlocfilehash: 03827d700e268baf2695c23d9c9ea3021ebb74e2
ms.sourcegitcommit: 7c052fc969d0f2c99ad574f99076dc1200d118c3
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/01/2019
ms.locfileid: "55570683"
---
# <a name="breaking-changes-to-database-engine-features-in-sql-server-2016"></a>Fehlerhafte Änderungen an Funktionen der Datenbank-Engine in SQL Server 2016
[!INCLUDE[tsql-appliesto-ss2016-xxxx-xxxx-xxx-md](../includes/tsql-appliesto-ss2016-xxxx-xxxx-xxx-md.md)]

  In diesem Thema werden wichtige Änderungen in [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)] [!INCLUDE[ssDE](../includes/ssde-md.md)] und den früheren Versionen von [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] beschrieben. Diese Änderungen können u. U. zur Funktionsunfähigkeit von Anwendungen, Skripts oder Funktionen führen, die auf früheren Versionen von [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]basieren. Diese Probleme können nach einem Upgrade auftreten.  
  
##  <a name="SQL15"></a> Wichtige Änderungen in [!INCLUDE[ssSQL15](../includes/sssql15-md.md)]  
  
-   Die Spalte *sample_ms* von `sys.dm_io_virtual_file_stats` wurde aus einem **int**- zu einem **bigint**-Datentyp erweitert.  
  
-   Die Spalte *TimeStamp* von `sys.fn_virtualfilestats` wurde aus einem **int**- zu einem **bigint**-Datentyp erweitert.  

-   Die MD2-, MD4-, MD5-, SHA- und SHA1-Algorithmen sind bei einem niedrigeren Kompatibilitätsgrad als 130 nicht verfügbar. Die Verwendung der Hashalgorithmen MD2, MD4, MD5, SHA oder SHA1 **wird nicht empfohlen**, kann aber erreicht werden, indem der Datenbankkompatibilitätsgrad auf einen niedrigeren Wert als 130 festgelegt wird.  

-   Unter dem Datenbankkompatibilitätsgrad 130 ergibt sich bei einer impliziten Konvertierung aus dem Datentyp **datetime** in den Datentyp **datetime2** eine verbesserte Genauigkeit, indem die Bruchteile von Millisekunden berücksichtigt werden, wodurch sich unterschiedliche konvertierte Werte ergeben. Verwenden Sie explizite Umwandlung in den Datentyp „datetime2“, wenn ein Vergleich so gestaltet ist, dass zwischen den Datentypen „datetime“ und „datetime2“ verglichen wird. Weitere Informationen finden Sie im folgenden [Microsoft-Supportartikel](https://support.microsoft.com/help/4010261).

-   Bei einem niedrigeren Datenbankkompatibilitätsgrad als 130 weisen Vorgänge, die implizite Konvertierungen zwischen bestimmten numerischen und „datetime“-Datentypen durchführen, eine verbesserte Genauigkeit auf und können zu unterschiedlichen konvertierten Werten führen. Dies schließt die Verwendung von Funktionen ein, die Berechnungen wie z. B. `DATEDIFF` und `ROUND` erfordern. Weitere Informationen finden Sie im folgenden [Microsoft-Supportartikel](https://support.microsoft.com/help/4010261).

## <a name="previous-versions"></a> Vorgängerversionen  

Informationen zu Breaking Changes in [!INCLUDE[ssSQL14](../includes/sssql14-md.md)] und in einigen Vorgängerversionen finden Sie unter [Breaking Changes bei Funktionen der Datenbank-Engine in SQL Server 2014](../database-engine/breaking-changes-to-database-engine-features-in-sql-server-2016.md#SQL14).

#### <a name="archived-documentation-for-very-old-versions-of-sql-server"></a>Archivierte Dokumentationen von sehr alten Versionen von SQL Server

[!INCLUDE[Archived documentation for very old versions of SQL Server](../includes/paragraph-content/previous-versions-archive-documentation-sql-server.md)]

## <a name="see-also"></a>Weitere Informationen  
 [Als veraltet markierte Funktionen der Datenbank-Engine in SQL Server 2016](../database-engine/deprecated-database-engine-features-in-sql-server-2016.md)   
 [Nicht mehr unterstützte Datenbank-Engine-Funktionalität in SQL Server 2016](../database-engine/discontinued-database-engine-functionality-in-sql-server-2016.md)   
 [Abwärtskompatibilität der SQL Server-Datenbank-Engine](../database-engine/sql-server-database-engine-backward-compatibility.md)   
 [ALTER DATABASE-Kompatibilitätsgrad &#40;Transact-SQL&#41;](../t-sql/statements/alter-database-transact-sql-compatibility-level.md)   
 [SQL Server 2016 or SQL Server 2017 on Windows improvements in handling some data types and uncommon operations (Verbesserungen der Verarbeitung einiger Datentypen und ungewöhnlicher Vorgänge für SQL Server 2016 oder SQL Server 2017 unter Windows)](https://support.microsoft.com/help/4010261).   
  
  
