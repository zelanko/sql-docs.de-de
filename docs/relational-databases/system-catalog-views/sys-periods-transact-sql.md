---
description: sys. Zeiträume (Transact-SQL)
title: sys. Zeiträume (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
dev_langs:
- TSQL
ms.assetid: 25e66ed3-2270-4c5c-9f5a-2c0f165a57ca
author: markingmyname
ms.author: maghan
ms.openlocfilehash: c091649234826080054de942ed96272055a1b595
ms.sourcegitcommit: 04cf7905fa32e0a9a44575a6f9641d9a2e5ac0f8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/07/2020
ms.locfileid: "91810320"
---
# <a name="sysperiods-transact-sql"></a>sys. Zeiträume (Transact-SQL)
[!INCLUDE [sqlserver2016](../../includes/applies-to-version/sqlserver2016.md)]

  Gibt eine Zeile für jede Tabelle zurück, für die Zeiträume definiert wurden.  
  
|Spaltenkopfzeile|Datentyp|Beschreibung|  
|-------------------|---------------|-----------------|  
|name|**sysname**|Der Name des Zeitraums.|  
|period_type|**tinyint**|Der numerische Wert, der den Typ des Zeitraums darstellt:<br /><br /> 1 = System Zeitraum|  
|period_type_desc|**nvarchar(60)**|Die Textbeschreibung des Spalten Typs:<br /><br /> SYSTEM_TIME_PERIOD|  
|object_id|**int**|Die ID der Tabelle, die die period_type Spalte enthält.|  
|start_column_id|**int**|Die ID der Spalte, die die Grenze für den unteren Zeitraum definiert.|  
|end_column_id|**int**|Die ID der Spalte, die die Grenze für den oberen Zeitraum definiert.|  
  
## <a name="permissions"></a>Berechtigungen  
 [!INCLUDE[ssCatViewPerm](../../includes/sscatviewperm-md.md)] Weitere Informationen finden Sie unter [Metadata Visibility Configuration](../../relational-databases/security/metadata-visibility-configuration.md).  
  
## <a name="see-also"></a>Weitere Informationen  
 [System Sichten &#40;Transact-SQL-&#41;](../../t-sql/language-reference.md)   
 [Katalogsichten für Objekte &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/object-catalog-views-transact-sql.md)   
 [Katalogsichten &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/catalog-views-transact-sql.md)   
 [sys.ALL_COLUMNS &#40;Transact-SQL-&#41;](../../relational-databases/system-catalog-views/sys-all-columns-transact-sql.md)   
 [sys.system_columns &#40;Transact-SQL-&#41;](../../relational-databases/system-catalog-views/sys-system-columns-transact-sql.md)   
 [Abfragen der SQL Server System Katalog-FAQ](../../relational-databases/system-catalog-views/querying-the-sql-server-system-catalog-faq.md)   
 [Temporale Tabellen](../../relational-databases/tables/temporal-tables.md)  
  
