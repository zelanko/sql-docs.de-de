---
title: sys. identity_columns (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/15/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- identity_columns
- sys.identity_columns
- sys.identity_columns_TSQL
- identity_columns_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.identity_columns catalog view
ms.assetid: 97ee01e6-9c9e-4fd9-884b-68b4084669d5
author: VanMSFT
ms.author: vanto
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 49684671c25ea83fa7554bec7f80d0b16c30d4eb
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/27/2020
ms.locfileid: "68122718"
---
# <a name="sysidentity_columns-transact-sql"></a>sys.identity_columns (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  Enthält eine Zeile für jede Spalte, bei der es sich um eine Identitätsspalte handelt.  
  
 Die **sys. identity_columns** -Sicht erbt Zeilen aus der **sys. Columns** -Sicht. Die **sys. identity_columns** -Sicht gibt die Spalten in der **sys. Columns** -Sicht sowie die Spalten **seed_value**, **increment_value**, **LAST_VALUE**und **is_not_for_replication** zurück. Weitere Informationen finden Sie unter [Katalogsichten &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/catalog-views-transact-sql.md).  
  
|Spaltenname|Datentyp|BESCHREIBUNG|  
|-----------------|---------------|-----------------|  
|**\<von sys. Columns geerbte Spalten>**||Die **sys. identity_columns** -Sicht gibt alle Spalten in der **sys. Columns** -Sicht zurück. Darüber hinaus werden die unten beschriebenen, zusätzlichen Spalten zurückgegeben. Eine Beschreibung der Spalten, die die **sys. identity_columns** -Sicht von **sys. Columns**erbt, finden Sie unter [sys. Columns &#40;Transact-SQL-&#41;](../../relational-databases/system-catalog-views/sys-columns-transact-sql.md).|  
|**seed_value**|**sql_variant**|Der Ausgangswert für diese Identitätsspalte. Der Datentyp des Ausgangswerts ist der gleiche wie der Datentyp der Spalte selbst.|  
|**increment_value**|**sql_variant**|Der inkrementelle Wert für diese Identitätsspalte. Der Datentyp des Ausgangswerts ist der gleiche wie der Datentyp der Spalte selbst.|  
|**last_value**|**sql_variant**|Der Wert, der zuletzt für diese Identitätsspalte generiert wurde. Der Datentyp des Ausgangswerts ist der gleiche wie der Datentyp der Spalte selbst.|  
|**is_not_for_replication**|**bit**|Die Identitätsspalte wird als NOT FOR REPLICATION deklariert.|  
  
> [!NOTE]  
>  Weitere Informationen zu einer automatisch inkrementierten Zahl, die in mehreren Tabellen verwendet oder aus Anwendungen aufgerufen werden kann, ohne dass auf eine Tabelle verwiesen wird, finden Sie unter [Sequenznummern](../../relational-databases/sequence-numbers/sequence-numbers.md).  
  
## <a name="permissions"></a>Berechtigungen  
 [!INCLUDE[ssCatViewPerm](../../includes/sscatviewperm-md.md)] Weitere Informationen finden Sie unter [Metadata Visibility Configuration](../../relational-databases/security/metadata-visibility-configuration.md).  
  
## <a name="see-also"></a>Weitere Informationen  
 [Objektkatalog Sichten &#40;Transact-SQL-&#41;](../../relational-databases/system-catalog-views/object-catalog-views-transact-sql.md)   
 [Katalog Sichten &#40;Transact-SQL-&#41;](../../relational-databases/system-catalog-views/catalog-views-transact-sql.md)   
 [FAQ: Abfragen des SQL Server-Systemkatalogs](../../relational-databases/system-catalog-views/querying-the-sql-server-system-catalog-faq.md)  
  
  
