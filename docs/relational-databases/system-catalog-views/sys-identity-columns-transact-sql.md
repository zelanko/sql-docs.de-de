---
description: sys.identity_columns (Transact-SQL)
title: sys.identity_columns (Transact-SQL) | Microsoft-Dokumentation
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
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 195768c830e13f2cb61f04bff9fe67f6eefe6dc4
ms.sourcegitcommit: 1a544cf4dd2720b124c3697d1e62ae7741db757c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/14/2020
ms.locfileid: "97484762"
---
# <a name="sysidentity_columns-transact-sql"></a>sys.identity_columns (Transact-SQL)
[!INCLUDE [sql-asdb-asdbmi-asa-pdw](../../includes/applies-to-version/sql-asdb-asdbmi-asa-pdw.md)]

  Enthält eine Zeile für jede Spalte, bei der es sich um eine Identitätsspalte handelt.  
  
 Die **sys.identity_columns** Sicht erbt Zeilen aus der **sys. Columns** -Sicht. Die **sys.identity_columns** Sicht gibt die Spalten in der **sys. Columns** -Sicht sowie die Spalten **seed_value**, **increment_value**, **LAST_VALUE** und **is_not_for_replication** zurück. Weitere Informationen finden Sie unter [Katalogsichten &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/catalog-views-transact-sql.md).  
  
|Spaltenname|Datentyp|Beschreibung|  
|-----------------|---------------|-----------------|  
|**\<columns inherited from sys.columns>**||In der **sys.identity_columns** Sicht werden alle Spalten in der **sys. Columns** -Sicht zurückgegeben. Darüber hinaus werden die unten beschriebenen, zusätzlichen Spalten zurückgegeben. Eine Beschreibung der Spalten, die die **sys.identity_columns** Sicht von **sys. Columns** erbt, finden Sie unter [sys. Columns &#40;Transact-SQL-&#41;](../../relational-databases/system-catalog-views/sys-columns-transact-sql.md).|  
|**seed_value**|**sql_variant**|Der Ausgangswert für diese Identitätsspalte. Der Datentyp des Ausgangswerts ist der gleiche wie der Datentyp der Spalte selbst.|  
|**increment_value**|**sql_variant**|Der inkrementelle Wert für diese Identitätsspalte. Der Datentyp des Ausgangswerts ist der gleiche wie der Datentyp der Spalte selbst.|  
|**last_value**|**sql_variant**|Der Wert, der zuletzt für diese Identitätsspalte generiert wurde. Der Datentyp des Ausgangswerts ist der gleiche wie der Datentyp der Spalte selbst.|  
|**is_not_for_replication**|**bit**|Die Identitätsspalte wird als NOT FOR REPLICATION deklariert. **Hinweis:** Diese Spalte gilt nicht für Azure-Synapse-Analysen.|  
  
> [!NOTE]  
>  Weitere Informationen zu einer automatisch inkrementierten Zahl, die in mehreren Tabellen verwendet oder aus Anwendungen aufgerufen werden kann, ohne dass auf eine Tabelle verwiesen wird, finden Sie unter [Sequenznummern](../../relational-databases/sequence-numbers/sequence-numbers.md).  
  
## <a name="permissions"></a>Berechtigungen  
 [!INCLUDE[ssCatViewPerm](../../includes/sscatviewperm-md.md)] Weitere Informationen finden Sie unter [Metadata Visibility Configuration](../../relational-databases/security/metadata-visibility-configuration.md).  
  
## <a name="see-also"></a>Weitere Informationen  
 [Katalogsichten für Objekte &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/object-catalog-views-transact-sql.md)   
 [Katalogsichten &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/catalog-views-transact-sql.md)   
 [FAQ: Abfragen des SQL Server-Systemkatalogs](../../relational-databases/system-catalog-views/querying-the-sql-server-system-catalog-faq.md)  
  
  
