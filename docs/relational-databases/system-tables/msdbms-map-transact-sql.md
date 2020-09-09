---
description: MSdbms_map (Transact-SQL)
title: MSdbms_map (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- MSdbms_map
- MSdbms_map_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- MSdbms_map system table
ms.assetid: df67e691-3a50-450a-99c5-8c4a041749ae
author: markingmyname
ms.author: maghan
ms.openlocfilehash: 66896c98c0d02dbb7cf9276f512420688b14be0f
ms.sourcegitcommit: dd36d1cbe32cd5a65c6638e8f252b0bd8145e165
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/08/2020
ms.locfileid: "89551010"
---
# <a name="msdbms_map-transact-sql"></a>MSdbms_map (Transact-SQL)
[!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

  Die **MSdbms_map** Tabelle enthält Informationen zum Quell Datentyp sowie einen Link zu den standardmäßigen Ziel Datentyp Informationen für die Quell-und Ziel-DBMS-Paare. Diese Tabelle wird in der **msdb** -Datenbank gespeichert und wird für die heterogene Veröffentlichung verwendet.  
  
|Spaltenname|Datentyp|BESCHREIBUNG|  
|-----------------|---------------|-----------------|  
|**map_id**|**int**|Identifiziert eine Datentypzuordnung eindeutig.|  
|**src_dbms_id**|**int**|Identifiziert das Quell-DBMS durch Angabe seines **dbms_id** in der [MSdbms](../../relational-databases/system-tables/msdbms-transact-sql.md) -Tabelle.|  
|**dest_dbms_id**|**int**|Identifiziert das Ziel-DBMS durch Angabe seines **dbms_id** in der [MSdbms](../../relational-databases/system-tables/msdbms-transact-sql.md) -Tabelle.|  
|**src_datatype_id**|**int**|Identifiziert die **datatype_id** aus der [MSdbms_datatype](../../relational-databases/system-tables/msdbms-datatype-transact-sql.md) Tabelle für den Quell Datentyp.|  
|**src_len_min**|**bigint**|Die Mindestlänge des Datentyps im Quell-DBMS, wobei der Wert NULL angibt, dass die Länge nicht verwendet wird.|  
|**src_len_max**|**bigint**|Die maximale Länge des Datentyps im Quell-DBMS, wobei der Wert NULL angibt, dass die Länge nicht verwendet wird.|  
|**src_prec_min**|**bigint**|Die Mindestgenauigkeit des Datentyps im Quell-DBMS, wobei der Wert NULL angibt, dass die Genauigkeit nicht verwendet wird.|  
|**src_prec_max**|**bigint**|Die maximale Genauigkeit des Datentyps im Quell-DBMS, wobei der Wert NULL angibt, dass die Genauigkeit nicht verwendet wird.|  
|**src_scale_min**|**int**|Die Mindestdezimalstellen des Datentyps im Quell-DBMS, wobei der Wert NULL angibt, dass die Dezimalstellen nicht verwendet werden.|  
|**src_scale_max**|**int**|Die maximalen Dezimalstellen des Datentyps im Quell-DBMS, wobei der Wert NULL angibt, dass die Dezimalstellen nicht verwendet werden.|  
|**src_nullable**|**bit**|Gibt an, ob die Zielspalte in der Zuordnung NULL-Werte zulässt. Ein Wert von NULL bedeutet, dass diese Definition nicht erforderlich ist.|  
|**default_datatype_mapping_id**|**int**|Identifiziert die standardmäßige Datentyp Zuordnung durch Angeben der **map_id** in Table [MSdbms_datatype_mapping](../../relational-databases/system-tables/msdbms-datatype-mapping-transact-sql.md).|  
  
## <a name="see-also"></a>Weitere Informationen  
 [Heterogene Datenbankreplikation](../../relational-databases/replication/non-sql/heterogeneous-database-replication.md)   
 [Angeben von Datentyp Zuordnungen für einen Oracle-Verleger](../../relational-databases/replication/publish/specify-data-type-mappings-for-an-oracle-publisher.md)   
 [Replikations Tabellen &#40;Transact-SQL-&#41;](../../relational-databases/system-tables/replication-tables-transact-sql.md)   
 [Replikationssichten &#40;Transact-SQL&#41;](../../relational-databases/system-views/replication-views-transact-sql.md)  
  
  
