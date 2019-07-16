---
title: computed_columns (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/15/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sys.computed_columns_TSQL
- sys.computed_columns
- computed_columns_TSQL
- computed_columns
dev_langs:
- TSQL
helpviewer_keywords:
- sys.computed_columns catalog view
ms.assetid: c962c619-e18f-4315-9251-8d9862462299
author: stevestein
ms.author: sstein
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 9e55274d1e6dfa34a3cfb92317bb4f205cfdd964
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "68109576"
---
# <a name="syscomputedcolumns-transact-sql"></a>sys.computed_columns (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  Enthält eine Zeile für jede Spalte in **sys.columns** , einer berechneten Spalte.  
  
|Spaltenname|Datentyp|Beschreibung|  
|-----------------|---------------|-----------------|  
|**\<geerbte Spalten >**||Die **computed_columns** Ansicht gibt alle Spalten in der **sys.columns** anzeigen. Darüber hinaus werden die unten beschriebenen, zusätzlichen Spalten zurückgegeben. Eine Beschreibung der Spalten, die die **computed_columns** Ansicht erbt von **sys.columns**, finden Sie unter [sys.columns &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-columns-transact-sql.md). Der Wert des der **Is_computed** Spalte immer auf 1 festgelegt ist die **computed_columns** anzeigen.|  
|**definition**|**nvarchar(max)**|SQL-Text, der diese berechnete Spalte definiert.|  
|**uses_database_collation**|**bit**|1 = Die Spaltendefinition hängt von der richtigen Auswertung der Standardsortierung der Datenbank ab, andernfalls ist der Wert 0. Durch diese Abhängigkeit wird verhindert, dass die Standardsortierung der Datenbank geändert wird.|  
|**is_persisted**|**bit**|Die berechnete Spalte ist persistent.|  
  
## <a name="permissions"></a>Berechtigungen  
 [!INCLUDE[ssCatViewPerm](../../includes/sscatviewperm-md.md)] Weitere Informationen finden Sie unter [Metadata Visibility Configuration](../../relational-databases/security/metadata-visibility-configuration.md).  
  
## <a name="see-also"></a>Siehe auch  
 [Katalogsichten für Objekte &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/object-catalog-views-transact-sql.md)   
 [Katalogsichten &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/catalog-views-transact-sql.md)  
  
  
