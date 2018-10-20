---
title: Sys.Periods (Transact-SQL) | Microsoft-Dokumentation
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
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 6e018e33ffa76fb162fd2020ba8ff043f295aa16
ms.sourcegitcommit: 3cd6068f3baf434a4a8074ba67223899e77a690b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/19/2018
ms.locfileid: "49461926"
---
# <a name="sysperiods-transact-sql"></a>Sys.Periods (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2016-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2016-xxxx-xxxx-xxx-md.md)]

  Gibt eine Zeile für jede Tabelle, die für die Zeiträume definiert wurden.  
  
|Spaltenkopfzeile|Datentyp|Description|  
|-------------------|---------------|-----------------|  
|NAME|**sysname**|Name des Zeitraums|  
|period_type|**tinyint**|Der numerische Wert, der den Typ des Zeitraums darstellt:<br /><br /> 1 = der Zeitraum der Systemzeit|  
|period_type_desc|**nvarchar(60)**|Die Beschreibung des Typs der Spalte:<br /><br /> SYSTEM_TIME_PERIOD|  
|object_id|**int**|Die Id der Tabelle mit der Period_type-Spalte|  
|start_column_id|**int**|Die Id der Spalte, die die untere Grenze für Zeitraum definiert.|  
|end_column_id|**int**|Die Id der Spalte, die die Obergrenze des Zeitraums definiert.|  
  
## <a name="permissions"></a>Berechtigungen  
 [!INCLUDE[ssCatViewPerm](../../includes/sscatviewperm-md.md)] Weitere Informationen finden Sie unter [Metadata Visibility Configuration](../../relational-databases/security/metadata-visibility-configuration.md).  
  
## <a name="see-also"></a>Siehe auch  
 [Systemsichten &#40;Transact-SQL&#41;](http://msdn.microsoft.com/library/35a6161d-7f43-4e00-bcd3-3091f2015e90)   
 [Katalogsichten für Objekte &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/object-catalog-views-transact-sql.md)   
 [Katalogsichten &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/catalog-views-transact-sql.md)   
 [sys.all_columns &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-all-columns-transact-sql.md)   
 [sys.system_columns &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-system-columns-transact-sql.md)   
 [Abfragen des Systemkatalogs von SQL Server – häufig gestellte Fragen](../../relational-databases/system-catalog-views/querying-the-sql-server-system-catalog-faq.md)   
 [Temporale Tabellen](../../relational-databases/tables/temporal-tables.md)  
  
  
