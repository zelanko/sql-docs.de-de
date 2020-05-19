---
title: sys. fn_hadr_is_primary_replica (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/17/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sys.fn_hadr_is_primary_replica
- fn_hadr_is_primary_replica_TSQL
- fn_hadr_is_primary_replica
- sys.fn_hadr_is_primary_replica_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- fn_hadr_is_primary_replica
- sys.fn_hadr_is_primary_replica
ms.assetid: c9b1969f-be1d-4dfb-a33d-551f380b9e27
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 5a030bbcd292ade6e52f71f523d60dfccbdf6c79
ms.sourcegitcommit: bfb5e79586fd08d8e48e9df0e9c76d1f6c2004e9
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/29/2020
ms.locfileid: "82262116"
---
# <a name="sysfn_hadr_is_primary_replica-transact-sql"></a>sys.fn_hadr_is_primary_replica (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2014-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2014-xxxx-xxxx-xxx-md.md)]

  Dient zum Ermitteln, ob das aktuelle Replikat das primäre Replikat ist.  
  
 ![Symbol für Themenlink](../../database-engine/configure-windows/media/topic-link.gif "Symbol für Themenlink") [Transact-SQL-Syntaxkonventionen](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```  
  
sys.fn_hadr_is_primary_replica ( 'dbname' )  
```  
  
## <a name="arguments"></a>Argumente  
 "*dbname*"  
 Der Name der Datenbank. *dbname* ist vom Typ sysname.  
  
## <a name="returns"></a>Gibt zurück  
 Gibt den Datentyp **bool**: 1 zurück, wenn die Datenbank auf der aktuellen Instanz das primäre Replikat ist; andernfalls 0.  
  
## <a name="remarks"></a>Bemerkungen  
 Verwenden Sie diese Funktion, um leicht zu bestimmen, ob die lokale Instanz das primäre Replikat der angegebenen Verfügbarkeitsdatenbank hostet. Beispielcode kann sich wie folgt zusammensetzen.  
  
```  
If sys.fn_hadr_is_primary_replica ( @dbname ) <> 1   
BEGIN  
-- If this is not the primary replica, exit (probably without error).  
END  
-- If this is the primary replica, continue to do the backup.  
  
```  
  
## <a name="examples"></a>Beispiele  
  
### <a name="a-using-sysfn_hadr_is_primary_replica"></a>A. Verwenden von sys.fn_hadr_is_primary_replica  
 Im folgenden Beispiel wird 1 zurückgegeben, wenn die angegebene Datenbank auf der lokalen Instanz das primäre Replikat ist.  
  
```  
SELECT sys.fn_hadr_is_primary_replica ('TestDB');  
GO  
```    
  
## <a name="security"></a>Sicherheit  
  
### <a name="permissions"></a>Berechtigungen  
 Erfordert die VIEW SERVER STATE-Berechtigung auf dem Server.  
  
## <a name="see-also"></a>Weitere Informationen  
 [AlwaysOn-Verfügbarkeitsgruppen Funktionen &#40;Transact-SQL-&#41;](../../relational-databases/system-functions/always-on-availability-groups-functions-transact-sql.md)   
 [sys. dm_hadr_database_replica_states &#40;Transact-SQL&#41;](../..//relational-databases/system-dynamic-management-views/sys-dm-hadr-database-replica-states-transact-sql.md) [AlwaysOn-Verfügbarkeitsgruppen &#40;](../../database-engine/availability-groups/windows/always-on-availability-groups-sql-server.md) SQL Server&#41;   
 [Erstellen einer Verfügbarkeits Gruppe &#40;Transact-SQL-&#41;](../../t-sql/statements/create-availability-group-transact-sql.md)   
 [ALTER AVAILABILITY GROUP &#40;Transact-SQL&#41;](../../t-sql/statements/alter-availability-group-transact-sql.md)   
 [AlwaysOn-Verfügbarkeitsgruppen Katalog Sichten &#40;Transact-SQL-&#41;](../../relational-databases/system-catalog-views/always-on-availability-groups-catalog-views-transact-sql.md)     
  
  
