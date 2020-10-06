---
description: sys.fn_hadr_distributed_ag_replica (Transact-SQL)
title: sys.fn_hadr_distributed_ag_replica (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/16/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sys.fn_hadr_distributed_ag_replica
- sys.fn_hadr_distributed_ag_replica_TSQL
- fn_hadr_distributed_ag_replica
- fn_hadr_distributed_ag_replica_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.fn_hadr_distributed_ag_replica
ms.assetid: a1e5f9cb-c350-4bb4-a04f-7394f6f25d62
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 94672892a8d8d3135bbaa48b6e783504e6094eaf
ms.sourcegitcommit: 968969b62bc158b9843aba5034c9d913519bc4a7
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/06/2020
ms.locfileid: "91753652"
---
# <a name="sysfn_hadr_distributed_ag_replica-transact-sql"></a>sys.fn_hadr_distributed_ag_replica (Transact-SQL)
[!INCLUDE [sqlserver2016](../../includes/applies-to-version/sqlserver2016.md)]

  Wird verwendet, um ein Replikat in einer verteilten Verfügbarkeits Gruppe der lokalen Verfügbarkeits Gruppe zuzuordnen.  
  
 ![Symbol für Themenlink](../../database-engine/configure-windows/media/topic-link.gif "Symbol für Themenlink") [Transact-SQL-Syntaxkonventionen](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```  
  
sys.fn_hadr_distributed_ag_replica( lag_Id, replica_id )  
```  
  
## <a name="arguments"></a>Argumente  
 "*lag_Id*"  
 Der Bezeichner der verteilten Verfügbarkeits Gruppe. *lag_Id* ist vom Datentyp **uniqueidentifier**.  
  
 "*replica_id*"  
 Der Bezeichner eines Replikats in der verteilten Verfügbarkeits Gruppe. *replica_id* ist vom Datentyp **uniqueidentifier**.  
  
## <a name="tables-returned"></a>Zurückgegebene Tabellen  
 Gibt die folgenden Informationen zurück.  
  
|Spaltenname|Datentyp|BESCHREIBUNG|  
|-----------------|---------------|-----------------|  
|**group_id**|**uniqueidentifier**|Eindeutiger Bezeichner (GUID) der lokalen Verfügbarkeits Gruppe.|  
  
## <a name="examples"></a>Beispiele  
  
### <a name="using-sysfn_hadr_distributed_ag_replica"></a>Verwenden von sys.fn_hadr_distributed_ag_replica  
 Im folgenden Beispiel wird eine Tabelle mit dem Bezeichner der lokalen Verfügbarkeits Gruppe zurückgegeben, der der angegebenen verteilten Verfügbarkeits Gruppe und dem Replikat zugeordnet ist.  
  
```  
DECLARE @lagId uniqueidentifier = '4A03D1A8-4AE6-B153-E7E9-ED22A546008D'  
DECLARE @replicaId uniqueidentifier = 'D5517513-04A8-FD82-14C6-E684EC913935'  
  
SELECT * FROM sys.fn_hadr_distributed_ag_replica(@lagId, @replicaId)  
GO  
```  
  
## <a name="see-also"></a>Weitere Informationen  
 [AlwaysOn-Verfügbarkeitsgruppen Funktionen &#40;Transact-SQL-&#41;](../../relational-databases/system-functions/always-on-availability-groups-functions-transact-sql.md)   
 [AlwaysOn-Verfügbarkeitsgruppen &#40;SQL Server&#41;](../../database-engine/availability-groups/windows/always-on-availability-groups-sql-server.md)   
 [Verteilte Verfügbarkeits Gruppen &#40;AlwaysOn-Verfügbarkeitsgruppen&#41;](../../database-engine/availability-groups/windows/distributed-availability-groups.md)  
 [CREATE AVAILABILITY GROUP &#40;Transact-SQL&#41;](../../t-sql/statements/create-availability-group-transact-sql.md)   
 [ALTER AVAILABILITY GROUP &#40;Transact-SQL&#41;](../../t-sql/statements/alter-availability-group-transact-sql.md)  
  
