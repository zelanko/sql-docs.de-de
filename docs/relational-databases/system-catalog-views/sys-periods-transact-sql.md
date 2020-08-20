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
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: a7f084571472f1f37a1e825ae2067e51a817ff35
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/17/2020
ms.locfileid: "88475287"
---
# <a name="sysperiods-transact-sql"></a>sys. Zeiträume (Transact-SQL)
[!INCLUDE [sqlserver2016](../../includes/applies-to-version/sqlserver2016.md)]

  Gibt eine Zeile für jede Tabelle zurück, für die Zeiträume definiert wurden.  
  
|Spaltenkopfzeile|Datentyp|BESCHREIBUNG|  
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
 [System Sichten &#40;Transact-SQL-&#41;](https://msdn.microsoft.com/library/35a6161d-7f43-4e00-bcd3-3091f2015e90)   
 [Katalogsichten für Objekte &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/object-catalog-views-transact-sql.md)   
 [Katalogsichten &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/catalog-views-transact-sql.md)   
 [sys. ALL_COLUMNS &#40;Transact-SQL-&#41;](../../relational-databases/system-catalog-views/sys-all-columns-transact-sql.md)   
 [sys.system_columns &#40;Transact-SQL-&#41;](../../relational-databases/system-catalog-views/sys-system-columns-transact-sql.md)   
 [Abfragen der SQL Server System Katalog-FAQ](../../relational-databases/system-catalog-views/querying-the-sql-server-system-catalog-faq.md)   
 [Temporale Tabellen](../../relational-databases/tables/temporal-tables.md)  
  
  
