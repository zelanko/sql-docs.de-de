---
description: sp_check_dynamic_filters (Transact-SQL)
title: sp_check_dynamic_filters (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- dynamic_filters_TSQL
- sp_check_TSQL
- check
- sp_check_dynamic filter
- check_TSQL
- filters_TSQL
- check_dynamic_filters_TSQL
- dynamic filters
- filters
- check dynamic filters
- sp_check_dynamic filter_TSQL
- sp_check_for_sync_trigger_TSQL
- sp_check
helpviewer_keywords:
- sp_check_dynamic_filters
ms.assetid: dd7760db-a3a5-460f-bd97-b8d436015e19
author: markingmyname
ms.author: maghan
ms.openlocfilehash: 323740799308f19a15dd4c8ccede8bcfe106465f
ms.sourcegitcommit: dd36d1cbe32cd5a65c6638e8f252b0bd8145e165
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/08/2020
ms.locfileid: "89539105"
---
# <a name="sp_check_dynamic_filters-transact-sql"></a>sp_check_dynamic_filters (Transact-SQL)
[!INCLUDE [SQL Server SQL MI](../../includes/applies-to-version/sql-asdbmi.md)]

  Zeigt Informationen zu parametrisierten Zeilenfiltereigenschaften für eine Veröffentlichung an, insbesondere die Funktionen, die zum Generieren einer gefilterten Datenpartition für eine Veröffentlichung verwendet werden, und ob die Veröffentlichung vorausberechnete Partitionen verwenden kann. Diese gespeicherte Prozedur wird auf dem Verleger für die Veröffentlichungs Datenbank ausgeführt.  
  
 ![Symbol für Themenlink](../../database-engine/configure-windows/media/topic-link.gif "Symbol für Themenlink") [Transact-SQL-Syntaxkonventionen](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```  
  
sp_check_dynamic_filters [ @publication = ] 'publication'  
```  
  
## <a name="arguments"></a>Argumente  
`[ @publication = ] 'publication'` Der Name der Veröffentlichung. *Publication* ist vom **Datentyp vom Datentyp sysname**und hat keinen Standardwert.  
  
## <a name="result-sets"></a>Resultsets  
  
|Spaltenname|Datentyp|BESCHREIBUNG|  
|-----------------|---------------|-----------------|  
|**can_use_partition_groups**|**bit**|Gibt an, ob die Veröffentlichung für die Verwendung Voraus berechneter Partitionen qualifiziert ist. Dabei bedeutet **1** , dass Voraus berechnete Partitionen verwendet werden können, und **0** bedeutet, dass Sie nicht verwendet werden können.|  
|**has_dynamic_filters**|**bit**|Gibt an, ob mindestens ein parametrisierter Zeilen Filter in der Veröffentlichung definiert wurde. **1** bedeutet, dass mindestens ein parametrisierter Zeilen Filter vorhanden ist, und **0** bedeutet, dass keine dynamischen Filter vorhanden sind.|  
|**dynamic_filters_function_list**|**nvarchar (500)**|Die Liste der Funktionen, die zum Filtern von Artikeln in einer Veröffentlichung verwendet werden. Die einzelnen Funktionen werden hierbei durch ein Semikolon getrennt.|  
|**validate_subscriber_info**|**nvarchar (500)**|Die Liste der Funktionen, die zum Filtern von Artikeln in einer Veröffentlichung verwendet werden. Die einzelnen Funktionen werden hierbei durch ein Pluszeichen (+) getrennt.|  
|**uses_host_name**|**bit**|, Wenn die [HOST_NAME ()](../../t-sql/functions/host-name-transact-sql.md) -Funktion in parametrisierten Zeilen filtern verwendet wird, wobei **1** bedeutet, dass diese Funktion für das dynamische Filtern verwendet wird.|  
|**uses_suser_sname**|**bit**|, Wenn die [SUSER_SNAME ()](../../t-sql/functions/suser-sname-transact-sql.md) -Funktion in parametrisierten Zeilen filtern verwendet wird, wobei **1** bedeutet, dass diese Funktion für das dynamische Filtern verwendet wird.|  
  
## <a name="return-code-values"></a>Rückgabecodewerte  
 **0** (Erfolg) oder **1** (Fehler)  
  
## <a name="remarks"></a>Hinweise  
 **sp_check_dynamic_filters** wird bei der Mergereplikation verwendet.  
  
 Wenn eine Veröffentlichung für die Verwendung Voraus berechneter Partitionen definiert wurde, prüft **sp_check_dynamic_filters** auf Verstöße gegen die Einschränkungen Voraus berechneter Partitionen. Ist dies der Fall, wird ein Fehler zurückgegeben. Weitere Informationen finden Sie unter [Optimieren Parametrisierter Filter-Leistung mit Vorausberechneten Partitionen ](../../relational-databases/replication/merge/parameterized-filters-optimize-for-precomputed-partitions.md).  
  
 Wenn eine Veröffentlichung laut Definition über parametrisierte Zeilenfilter verfügt, jedoch keine parametrisierten Zeilenfilter gefunden werden, wird ein Fehler zurückgegeben.  
  
## <a name="permissions"></a>Berechtigungen  
 Nur Mitglieder der festen Server Rolle **sysadmin** oder der festen Daten Bank Rolle **db_owner** können **sp_check_dynamic_filters**ausführen.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Verwalten von Partitionen für eine Mergeveröffentlichung mit parametrisierten Filtern](../../relational-databases/replication/publish/manage-partitions-for-a-merge-publication-with-parameterized-filters.md)   
 [sp_check_join_filter &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/sp-check-join-filter-transact-sql.md)   
 [sp_check_subset_filter &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/sp-check-subset-filter-transact-sql.md)  
  
  
