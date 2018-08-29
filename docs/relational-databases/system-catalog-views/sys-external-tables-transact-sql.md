---
title: Sys.external_tables (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql
ms.technology: system-objects
ms.tgt_pltfrm: ''
ms.topic: language-reference
dev_langs:
- TSQL
ms.assetid: fac4720c-b679-4ab2-864b-ff7810a9b559
caps.latest.revision: 7
author: stevestein
ms.author: sstein
manager: craigg
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: ceaaa2c3a5005b9adec32fecd3b8a63600416652
ms.sourcegitcommit: 4183dc18999ad243c40c907ce736f0b7b7f98235
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/27/2018
ms.locfileid: "43094627"
---
# <a name="sysexternaltables-transact-sql"></a>Sys.external_tables (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2016-all-md](../../includes/tsql-appliesto-ss2016-all-md.md)]

  Enthält eine Zeile für jede externe Tabelle in der aktuellen Datenbank.  
  
|Spaltenname|Datentyp|Description|Bereich|  
|-----------------|---------------|-----------------|-----------|  
|\<geerbte Spalten >||Eine Liste der Spalten, die in dieser Ansicht erbt, finden Sie unter [sys.objects &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-objects-transact-sql.md).||  
|max_column_id_used|**int**|Höchste Spalten-ID für diese Tabelle hat Sie bisher verwendet.||  
|uses_ansi_nulls|**bit**|Beim Erstellen der Tabelle war die Datenbankoption SET ANSI_NULLS auf ON festgelegt.||  
|data_source_id|**int**|Objekt-ID für die externe Datenquelle.||  
|file_format_id|**int**|Für externe Tabellen über eine externe Datenquelle HADOOP ist dies die Objekt-ID für das externe Dateiformat.||  
|location|**nvarchar(4000)**|Für externe Tabellen über eine externe Datenquelle HADOOP ist dies der Pfad der externen Daten in HDFS.||  
|reject_type|**tinyint**|Für externe Tabellen über eine externe Datenquelle HADOOP ist dies die Möglichkeit, abgelehnte Zeilen gezählt werden, wenn externe Daten Abfragen.|Wert: die Anzahl der abgelehnten Zeilen.<br /><br /> Prozentsatz – der Prozentsatz der abgelehnten Zeilen.|  
|reject_value|**float**|Für externe Tabellen über eine externe Datenquelle HADOOP:<br /><br /> Für *Reject_type =* Wert, dies ist die Anzahl der ablehnungen von Zeile zu ermöglichen, bevor die Abfrage fehlschlägt.<br /><br /> Für *Reject_type* = Prozentsatz, dies ist der Prozentsatz von Zeilen ablehnungen zu ermöglichen, bevor die Abfrage fehlschlägt.||  
|reject_sample_value|**int**|Für *Reject_type* = Prozentsatz, dies ist die Anzahl der Zeilen an, entweder erfolgreich oder erfolglos, laden, bevor Sie den Prozentsatz der abgelehnten Zeilen zu berechnen.|NULL, wenn Reject_type = Wert.|  
|distribution_type|**int**|Für externe Tabellen über eine externe Datenquelle für SHARD_MAP_MANAGER ist dies die Verteilung der Daten der Zeilen in der zugrunde liegenden Basistabellen.|0 – Sharded<br /><br /> 1 – repliziert<br /><br /> 2 – Roundrobin|  
|distribution_desc|**nvarchar(120)**|Für externe Tabellen über eine externe Datenquelle für SHARD_MAP_MANAGER ist dies den Verteilungstyp, die als Zeichenfolge angezeigt.||  
|sharding_column_id|**int**|Für externe Tabellen über eine externe Datenquelle für SHARD_MAP_MANAGER und sharded-Verteilung ist dies die Spalten-ID der Spalte, die die Sharding-Schlüsselwerte enthält.||  
|remote_schema_name|**sysname**|Für externe Tabellen über eine externe Datenquelle für SHARD_MAP_MANAGER ist dies das Schema, in denen die Basistabelle in den Remotedatenbanken (falls abweichend aus dem Schema, in die externe Tabelle definiert ist) befindet.||  
|remote_object_name|**sysname**|Für externe Tabellen über eine externe Datenquelle für SHARD_MAP_MANAGER ist dies der Name der Basistabelle in den Remotedatenbanken (falls abweichend vom Namen der externen Tabelle).||  
  
## <a name="permissions"></a>Berechtigungen  
 Die Sichtbarkeit der Metadaten in Katalogsichten ist auf sicherungsfähige Elemente eingeschränkt, bei denen der Benutzer entweder der Besitzer ist oder für die dem Benutzer eine Berechtigung erteilt wurde. Weitere Informationen finden Sie unter [Metadata Visibility Configuration](../../relational-databases/security/metadata-visibility-configuration.md).  
  
## <a name="see-also"></a>Siehe auch  
 [external_file_formats &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-external-file-formats-transact-sql.md)   
 [sys.external_data_sources &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-external-data-sources-transact-sql.md)   
 [CREATE EXTERNAL TABLE &#40;Transact-SQL&#41;](../../t-sql/statements/create-external-table-transact-sql.md)  
  
  
