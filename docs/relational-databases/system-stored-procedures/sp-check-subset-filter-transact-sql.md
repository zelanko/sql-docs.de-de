---
title: sp_check_subset_filter (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- sp_check_TSQL
- sp_check_subset_filter
- filter
- subset
- subset_TSQL
- sp_check
- sp_check_subset_filter_TSQL
helpviewer_keywords:
- sp_check_subset_filter
ms.assetid: 525cfcfc-f317-478d-ba84-72e62285f160
author: stevestein
ms.author: sstein
ms.openlocfilehash: 3c1510260a5b381b91a399984121834ca4ce30b5
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/27/2020
ms.locfileid: "68771313"
---
# <a name="sp_check_subset_filter-transact-sql"></a>sp_check_subset_filter (Transact-SQL)
[!INCLUDE[appliesto-ss-asdbmi-xxxx-xxx-md](../../includes/appliesto-ss-asdbmi-xxxx-xxx-md.md)]

  Wird zum Überprüfen einer Filterklausel gegen eine beliebige Tabelle verwendet, um die Gültigkeit der Filterklausel für die Tabelle zu ermitteln. Diese gespeicherte Prozedur gibt Informationen zum bereitgestellten Filter zurück, einschließlich der Angabe, ob der Filter mit vorausberechneten Partitionen verwendet werden kann. Diese gespeicherte Prozedur wird auf dem Verleger für die Datenbank ausgeführt, die die Veröffentlichung enthält.  
  
 ![Symbol für Themenlink](../../database-engine/configure-windows/media/topic-link.gif "Symbol für Themenlink") [Transact-SQL-Syntaxkonventionen](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```  
  
sp_check_subset_filter [ @filtered_table = ] 'filtered_table'  
        , [ @subset_filterclause = ] 'subset_filterclause'  
    [ , [ @has_dynamic_filters = ] has_dynamic_filters OUTPUT ]  
```  
  
## <a name="arguments"></a>Argumente  
`[ @filtered_table = ] 'filtered_table'`Der Name einer gefilterten Tabelle. *filtered_table* ist vom Datentyp **nvarchar (400)** und hat keinen Standardwert.  
  
`[ @subset_filterclause = ] 'subset_filterclause'`Die Filter Klausel, die getestet wird. *subset_filterclause* ist vom Datentyp **nvarchar (1000)** und hat keinen Standardwert.  
  
`[ @has_dynamic_filters = ] has_dynamic_filters`Gibt an, ob die Filter Klausel ein parametrisierter Zeilen Filter ist. *has_dynamic_filters* ist vom Typ **Bit**. der Standardwert ist NULL, und es handelt sich um einen Output-Parameter. Gibt den Wert **1** zurück, wenn die Filter Klausel ein parametrisierter Zeilen Filter ist.  
  
## <a name="result-sets"></a>Resultsets  
  
|Spaltenname|Datentyp|BESCHREIBUNG|  
|-----------------|---------------|-----------------|  
|**can_use_partition_groups**|**bit**|Gibt an, ob die Veröffentlichung für die Verwendung Voraus berechneter Partitionen qualifiziert ist. Dabei bedeutet **1** , dass Voraus berechnete Partitionen verwendet werden können, und **0** bedeutet, dass Sie nicht verwendet werden können.|  
|**has_dynamic_filters**|**bit**|Gibt an, ob die angegebene Filter Klausel mindestens einen parametrisierten Zeilen Filter enthält. wobei **1** bedeutet, dass ein parametrisierter Zeilen Filter verwendet wird, und **0** bedeutet, dass eine solche Funktion nicht verwendet wird.|  
|**dynamic_filters_function_list**|**nvarchar (500)**|Liste der Funktionen in der Filterklausel, die einen Artikel dynamisch filtern, wobei die Funktionen durch Semikolon voneinander getrennt sind.|  
|**uses_host_name**|**bit**|, Wenn die [HOST_NAME ()](../../t-sql/functions/host-name-transact-sql.md) -Funktion in der Filter-Klausel verwendet wird, wobei **1** bedeutet, dass diese Funktion vorhanden ist.|  
|**uses_suser_sname**|**bit**|, Wenn die [SUSER_SNAME ()](../../t-sql/functions/suser-sname-transact-sql.md) -Funktion in der Filter-Klausel verwendet wird, wobei **1** bedeutet, dass diese Funktion vorhanden ist.|  
  
## <a name="return-code-values"></a>Rückgabecodewerte  
 **0** (Erfolg) oder **1** (Fehler)  
  
## <a name="remarks"></a>Bemerkungen  
 **sp_check_subset_filter** wird bei der Mergereplikation verwendet.  
  
 **sp_check_subset_filter** können auch dann für beliebige Tabellen ausgeführt werden, wenn die Tabelle nicht veröffentlicht wird. Mit dieser gespeicherten Prozedur kann eine Filterklausel vor dem Definieren eines gefilterten Artikels überprüft werden.  
  
## <a name="permissions"></a>Berechtigungen  
 Nur Mitglieder der festen Server Rolle **sysadmin** oder der festen Daten Bank Rolle **db_owner** können **sp_check_subset_filter**ausführen.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Optimieren der Leistung parametrisierter Filter mithilfe vorausberechneter Partitionen](../../relational-databases/replication/merge/parameterized-filters-optimize-for-precomputed-partitions.md)  
  
  
