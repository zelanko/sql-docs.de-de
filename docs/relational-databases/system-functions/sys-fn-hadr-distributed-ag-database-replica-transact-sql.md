---
title: sys. fn_hadr_distributed_ag_database_replica (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/14/2016
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sys.fn_hadr_distributed_ag_database_replica
- sys.fn_hadr_distributed_ag_database_replica_TSQL
- fn_hadr_distributed_ag_database_replica
- fn_hadr_distributed_ag_database_replica_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.fn_hadr_distributed_ag_database_replica
ms.assetid: 0e6202a1-e872-4f53-99d7-c16b6f712efc
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 2acff9f5d78549fe1e00397d566053ec19f628a8
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "68120242"
---
# <a name="sysfn_hadr_distributed_ag_database_replica-transact-sql"></a>sys. fn_hadr_distributed_ag_database_replica (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2016-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2016-xxxx-xxxx-xxx-md.md)]

  Wird verwendet, um eine Datenbank in einer verteilten Verfügbarkeits Gruppe der-Datenbank in der lokalen Verfügbarkeits Gruppe zuzuordnen.  
   
 ![Symbol für Themenlink](../../database-engine/configure-windows/media/topic-link.gif "Symbol für Themenlink") [Transact-SQL-Syntaxkonventionen](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```  
  
sys.fn_hadr_distributed_ag_database_replica( lag_Id, database_id )  
```  
  
## <a name="arguments"></a>Argumente  
 "*lag_Id*"  
 Der Bezeichner der verteilten Verfügbarkeits Gruppe. *lag_Id* ist vom Datentyp **uniqueidentifier**.  
  
 "*database_id*"  
 Der Bezeichner der Datenbank in einer verteilten Verfügbarkeits Gruppe. *database_id* ist vom Datentyp **uniqueidentifier**.  
  
## <a name="tables-returned"></a>Zurückgegebene Tabellen  
 Gibt die folgenden Informationen zurück.  
  
|Spaltenname|Datentyp|BESCHREIBUNG|  
|-----------------|---------------|-----------------|  
|**group_database_id**|**uniqueidentifier**|ID der Datenbank in der lokalen Verfügbarkeits Gruppe.|  
  
## <a name="examples"></a>Beispiele  
  
### <a name="using-sysfn_hadr_distributed_ag_database_replica"></a>Verwenden von sys. fn_hadr_distributed_ag_database_replica  
 Im folgenden Beispiel wird die Datenbank-ID in einer verteilten Verfügbarkeits Gruppe weitergegeben. Es wird eine Tabelle mit der Datenbank-ID zurückgegeben, die der lokalen Verfügbarkeits Gruppe zugeordnet ist.  
  
```  
DECLARE @lagId uniqueidentifier = '4A03D1A8-4AE6-B153-E7E9-ED22A546008D'  
DECLARE @databaseId uniqueidentifier = '3FFA882A-C4C3-5B9E-A203-8F44BD9659F7'  
  
SELECT * FROM sys.fn_hadr_distributed_ag_database_replica(@lagId, @databaseId)  
GO  
```  
  
## <a name="see-also"></a>Weitere Informationen  
 [Always on-Verfügbarkeits Gruppenfunktionen &#40;Transact-SQL-&#41;](../../relational-databases/system-functions/always-on-availability-groups-functions-transact-sql.md)   
 [Always On-Verfügbarkeitsgruppen &#40;SQL Server&#41;](../../database-engine/availability-groups/windows/always-on-availability-groups-sql-server.md)   
 [Verteilte Verfügbarkeits Gruppen &#40;Always on Verfügbarkeits Gruppen&#41;](../../database-engine/availability-groups/windows/distributed-availability-groups-always-on-availability-groups.md)   
 [CREATE AVAILABILITY GROUP &#40;Transact-SQL&#41;](../../t-sql/statements/create-availability-group-transact-sql.md)   
 [ALTER AVAILABILITY GROUP &#40;Transact-SQL&#41;](../../t-sql/statements/alter-availability-group-transact-sql.md)  
  
  
