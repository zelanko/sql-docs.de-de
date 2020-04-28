---
title: sys.database_service_objectives
titleSuffix: Azure SQL Database
ms.custom: seo-dt-2019
ms.date: 03/21/2018
ms.service: sql-database
ms.prod_service: sql-database, sql-data-warehouse
ms.reviewer: ''
ms.topic: conceptual
keywords:
- elastischer Pool
- Pool für elastische Datenbanken, Verwaltung
f1_keywords:
- DATABASE_SERVICE_OBJECTIVES_TSQL
ms.assetid: cecd8c31-06c0-4aa7-85d3-ac590e6874fa
author: stevestein
ms.author: sstein
monikerRange: = azuresqldb-current || = azure-sqldw-latest || = sqlallproducts-allversions
ms.openlocfilehash: 465416e87966ba3a80c8e98394c0b1f2009f591b
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/27/2020
ms.locfileid: "73844461"
---
# <a name="sysdatabase_service_objectives-azure-sql-database"></a>sys.database_service_objectives (Azure SQL-Datenbank)
[!INCLUDE[tsql-appliesto-xxxxxx-asdb-asdw-xxx-md](../../includes/tsql-appliesto-xxxxxx-asdb-asdw-xxx-md.md)]

Gibt ggf. die Edition (Dienst Ebene), das Dienst Ziel (Tarif) und den Namen des elastischen Pools für eine Azure SQL-Datenbank oder eine Azure SQL Data Warehouse zurück. Wenn eine Anmeldung an der Masterdatenbank in einem Azure SQL-Datenbank-Server besteht, werden Informationen zu allen Datenbanken zurückgegeben. Für Azure SQL Data Warehouse müssen Sie über eine Verbindung mit der Masterdatenbank verfügen.  
  
  
 Informationen zu den Preisen finden Sie unter [SQL-Daten Bankoptionen und-Leistung: Preis](https://azure.microsoft.com/pricing/details/sql-database/) -und [SQL Data Warehouse Preise](https://azure.microsoft.com/pricing/details/sql-data-warehouse/)für SQL-Datenbank.  
  
 Informationen zum Ändern der Dienst Einstellungen finden Sie unter [ALTER DATABASE (Azure SQL-Datenbank)](../../t-sql/statements/alter-database-azure-sql-database.md) und [ALTER DATABASE (Azure SQL Data Warehouse)](https://docs.microsoft.com/sql/t-sql/statements/alter-database-transact-sql?view=azure-sqldw-latest).  
  
 Die sys. database_service_objectives-Sicht enthält die folgenden Spalten.  
  
|Spaltenname|Datentyp|BESCHREIBUNG|  
|-----------------|---------------|-----------------|  
|database_id|INT|Die ID der Datenbank, die innerhalb einer Instanz von Azure SQL-Datenbankserver eindeutig ist. Joinfähig mit [sys.-Datenbanken &#40;Transact-SQL-&#41;](../../relational-databases/system-catalog-views/sys-databases-transact-sql.md).|  
|Edition|sysname|Die Dienst Ebene für die Datenbank oder Data Warehouse: **Basic**, **Standard**, **Premium** oder **Data Warehouse**.|  
|service_objective|sysname|Der Tarif der Datenbank. Wenn sich die Datenbank in einem Pool für elastische Datenbanken befindet, wird **elasticpool**zurückgegeben.<br /><br /> Auf dem **Basic** -Level gibt **Basic**zurück.<br /><br /> Eine **einzelne Datenbank in einer Standard Dienst Ebene** gibt eine der folgenden zurück: S0, S1, S2, S3, S4, S6, S7, S9 oder S12.<br /><br /> **Eine Einzel Datenbank in einem Premium** -Tarif gibt Folgendes zurück: P1, P2, P4, P6, P11 oder P15.<br /><br /> **SQL Data Warehouse** gibt DW100 bis DW30000c zurück.<br /><br /> Weitere Informationen finden Sie unter [Einzel Datenbanken](/azure/sql-database/sql-database-dtu-resource-limits-single-databases/), [Pools für elastische](/azure/sql-database/sql-database-dtu-resource-limits-elastic-pools/)Datenbanken, [Data](/azure/sql-data-warehouse/what-is-a-data-warehouse-unit-dwu-cdwu/) Warehouse|  
|elastic_pool_name|sysname|Der Name des [Pools für elastische](https://azure.microsoft.com/documentation/articles/sql-database-elastic-pool/) Datenbanken, zu dem die Datenbank gehört. Gibt **null** zurück, wenn die Datenbank eine einzelne Datenbank oder ein Datenlager ist.|  
  
## <a name="permissions"></a>Berechtigungen  
 Erfordert die **DBManager** -Berechtigung für die Master-Datenbank.  Auf Datenbankebene muss der Benutzer der Ersteller oder Besitzer sein.  
  
## <a name="examples"></a>Beispiele  
 Dieses Beispiel kann in der Master-Datenbank oder in Azure SQL-Datenbank-Benutzer Datenbanken ausgeführt werden. Die Abfrage gibt die Informationen zu Name, Dienst und Leistungs Ebene der Datenbank (en) zurück.  
  
```sql  
SELECT  d.name,   
     slo.*    
FROM sys.databases d   
JOIN sys.database_service_objectives slo    
ON d.database_id = slo.database_id;  
  
```  
  
  
