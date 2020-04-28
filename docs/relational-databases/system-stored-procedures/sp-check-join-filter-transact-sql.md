---
title: sp_check_join_filter (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- filter_TSQL
- sp_check_TSQL
- sp_check_join_filter
- sp_check_join_filter_TSQL
- join
- join_TSQL
- filter
- sp_check
helpviewer_keywords:
- sp_check_join_filter
ms.assetid: e9699d59-c8c9-45f6-a561-f7f95084a540
author: stevestein
ms.author: sstein
ms.openlocfilehash: 28589be83c62f705457e990b328be98e88905568
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/27/2020
ms.locfileid: "68771275"
---
# <a name="sp_check_join_filter-transact-sql"></a>sp_check_join_filter (Transact-SQL)
[!INCLUDE[appliesto-ss-asdbmi-xxxx-xxx-md](../../includes/appliesto-ss-asdbmi-xxxx-xxx-md.md)]

  Wird dazu verwendet, einen Joinfilter zwischen zwei Tabellen zu überprüfen, um festzustellen, ob die Joinfilterklausel gültig ist. Diese gespeicherte Prozedur gibt außerdem Informationen zum angegebenen Joinfilter zurück, u. a. mit dem Hinweis, ob der Filter für die angegebene Tabelle zusammen mit vorausberechneten Partitionen verwendet werden kann. Diese gespeicherte Prozedur wird auf dem Verleger für die Veröffentlichung ausgeführt. Weitere Informationen finden Sie unter [Optimieren Parametrisierter Filter-Leistung mit Vorausberechneten Partitionen ](../../relational-databases/replication/merge/parameterized-filters-optimize-for-precomputed-partitions.md).  
  
 ![Symbol für Themenlink](../../database-engine/configure-windows/media/topic-link.gif "Symbol für Themenlink") [Transact-SQL-Syntaxkonventionen](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```  
  
sp_check_join_filter [ @filtered_table = ] 'filtered_table'  
        , [@join_table = ] 'join_table'  
        , [ @join_filterclause = ] 'join_filterclause'  
```  
  
## <a name="arguments"></a>Argumente  
`[ @filtered_table = ] 'filtered_table'`Der Name einer gefilterten Tabelle. *filtered_table* ist vom Datentyp **nvarchar (400)** und hat keinen Standardwert.  
  
`[ @join_table = ] 'join_table'`Der Name einer Tabelle, der *filtered_table*hinzugefügt wird. *join_table* ist vom Datentyp **nvarchar (400)** und hat keinen Standardwert.  
  
`[ @join_filterclause = ] 'join_filterclause'`Die joinfilterklausel, die getestet wird. *join_filterclause* ist vom Datentyp **nvarchar (1000)** und hat keinen Standardwert.  
  
## <a name="result-sets"></a>Resultsets  
  
|Spaltenname|Datentyp|BESCHREIBUNG|  
|-----------------|---------------|-----------------|  
|**can_use_partition_groups**|**bit**|Gibt an, ob die Veröffentlichung für Voraus berechnete Partitionen qualifiziert ist. wobei **1** bedeutet, dass vorab komprimierte Partitionen verwendet werden können, **0** bedeutet, dass Sie nicht verwendet werden können.|  
|**has_dynamic_filters**|**bit**|Gibt an, ob die angegebene Filter Klausel mindestens eine parametrisierte Filterfunktion enthält. wobei **1** bedeutet, dass eine parametrisierte Filterfunktion verwendet wird, und **0** bedeutet, dass eine solche Funktion nicht verwendet wird.|  
|**dynamic_filters_function_list**|**nvarchar (500)**|Liste der Funktionen in der Filterklausel, die einen parametrisierten Filter für einen Artikel definieren. Dabei sind die einzelnen Funktionen durch ein Semikolon voneinander getrennt.|  
|**uses_host_name**|**bit**|, Wenn die [HOST_NAME ()](../../t-sql/functions/host-name-transact-sql.md) -Funktion in der Filter-Klausel verwendet wird, wobei **1** bedeutet, dass diese Funktion vorhanden ist.|  
|**uses_suser_sname**|**bit**|, Wenn die [SUSER_SNAME ()](../../t-sql/functions/suser-sname-transact-sql.md) -Funktion in der Filter-Klausel verwendet wird, wobei **1** bedeutet, dass diese Funktion vorhanden ist.|  
  
## <a name="return-code-values"></a>Rückgabecodewerte  
 **0** (Erfolg) oder **1** (Fehler)  
  
## <a name="remarks"></a>Bemerkungen  
 **sp_check_join_filter** wird bei der Mergereplikation verwendet.  
  
 **sp_check_join_filter** können für alle verknüpften Tabellen ausgeführt werden, auch wenn Sie nicht veröffentlicht werden. Mit dieser gespeicherten Prozedur kann eine Joinfilterklausel überprüft werden, bevor ein Joinfilter zwischen zwei Artikeln definiert wird.  
  
## <a name="permissions"></a>Berechtigungen  
 Nur Mitglieder der festen Server Rolle **sysadmin** oder der festen Daten Bank Rolle **db_owner** können **sp_check_join_filter**ausführen.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Gespeicherte Automatisierungsprozeduren &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/replication-stored-procedures-transact-sql.md)  
  
  
