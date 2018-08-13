---
title: external_file_formats (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-data-warehouse, pdw
ms.component: system-catalog-views
ms.reviewer: ''
ms.suite: sql
ms.technology: system-objects
ms.tgt_pltfrm: ''
ms.topic: language-reference
dev_langs:
- TSQL
ms.assetid: a89efb2c-0a3a-4b64-9284-6e93263e29ac
caps.latest.revision: 7
author: stevestein
ms.author: sstein
manager: craigg
monikerRange: '>=aps-pdw-2016||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017'
ms.openlocfilehash: dea0275fbdeea5dc413d4fc69a1da224cd2a6a04
ms.sourcegitcommit: 4cd008a77f456b35204989bbdd31db352716bbe6
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/06/2018
ms.locfileid: "39560520"
---
# <a name="sysexternalfileformats-transact-sql"></a>external_file_formats (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2016-xxxx-asdw-pdw-md](../../includes/tsql-appliesto-ss2016-xxxx-asdw-pdw-md.md)]

  Enthält eine Zeile für jeden externen Dateiformats in der aktuellen Datenbank für [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], [!INCLUDE[ssSDS](../../includes/sssds-md.md)], und [!INCLUDE[ssSDW](../../includes/sssdw-md.md)].  
  
 Enthält eine Zeile für jede externe Dateiformat auf dem Server für [!INCLUDE[ssPDW](../../includes/sspdw-md.md)].  
  
|Spaltenname|Datentyp|Description|Bereich|  
|-----------------|---------------|-----------------|-----------|  
|file_format_id|**int**|Objekt-ID für das externe Dateiformat.||  
|NAME|**sysname**|Der Name des Dateiformats. in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] und [!INCLUDE[ssSDW](../../includes/sssdw-md.md)], dies ist für die Datenbank eindeutig. In [!INCLUDE[ssPDW](../../includes/sspdw-md.md)], dies ist für den Server eindeutig.||  
|format_type|**tinyint**|Der Typ des Datei-Format.|DELIMITEDTEXT, RCFILE, ORC, PARQUET-DATEIEN|  
|Feldabschlusszeichen|**nvarchar(10)**|Für die Format_type = DELIMITEDTEXT, dies ist das Feldabschlusszeichen.||  
|string_delimiter|**nvarchar(10)**|Für die Format_type = DELIMITEDTEXT, dies ist das Zeichenfolgen-Trennzeichen.||  
|date_format|**nvarchar(50)**|Für die Format_type = DELIMITEDTEXT, dies ist das benutzerdefinierte Datums- und Zeitformat.||  
|use_type_default|**bit**|Für die Format_type = TEXT als TRENNZEICHEN, gibt an, wie fehlende Werte behandelt werden, wenn PolyBase Daten aus HDFS-Textdateien in importiert [!INCLUDE[ssSDW](../../includes/sssdw-md.md)].|0 – speichern Sie fehlende Werte als die Zeichenfolge 'NULL'.<br /><br /> 1 – Speichern von fehlenden Werten als der Standardwert der Spalte.|  
|serde_method|**nvarchar(255)**|Für die Format_type = RCFILE-, dies ist die Serialisierung/Deserialisierung-Methode.||  
|Zeilenabschlusszeichen|**nvarchar(10)**|Für die Format_type = DELIMITEDTEXT, dies ist die Zeichenfolge, die jede Zeile in der externen Hadoop-Datei beendet.|Immer '\n'.|  
|Codierung|**nvarchar(10)**|Für die Format_type = DELIMITEDTEXT, dies ist die Codierung Methode für die externen Hadoop-Datei.|Immer "UTF8".|  
|data_compression|**nvarchar(255)**|Die datenkomprimierungsmethode für die externen Daten.|Für die Format_type = DELIMITEDTEXT:<br /><br /> -"org.apache.hadoop.io.compress.DefaultCodec"<br />-"org.apache.Hadoop.IO.Compress.gzipcodec" angewendet.<br /><br /> Für die Format_type = RCFILE:<br /><br /> -"org.apache.hadoop.io.compress.DefaultCodec"<br /><br /> Für die Format_type = ORC:<br /><br /> -"org.apache.hadoop.io.compress.DefaultCodec"<br />-"org.apache.hadoop.io.compress.SnappyCodec"<br /><br /> Für die Format_type = parquet-Dateien:<br /><br /> -"org.apache.Hadoop.IO.Compress.gzipcodec" angewendet.<br />-"org.apache.hadoop.io.compress.SnappyCodec"|  
  
## <a name="permissions"></a>Berechtigungen  
 Die Sichtbarkeit der Metadaten in Katalogsichten ist auf sicherungsfähige Elemente eingeschränkt, bei denen der Benutzer entweder der Besitzer ist oder für die dem Benutzer eine Berechtigung erteilt wurde. Weitere Informationen finden Sie unter [Metadata Visibility Configuration](../../relational-databases/security/metadata-visibility-configuration.md).  
  
## <a name="see-also"></a>Siehe auch  
 [sys.external_data_sources &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-external-data-sources-transact-sql.md)   
 [sys.external_tables &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-external-tables-transact-sql.md)   
 [CREATE EXTERNAL FILE FORMAT &#40;Transact-SQL&#41;](../../t-sql/statements/create-external-file-format-transact-sql.md)  
  
  
