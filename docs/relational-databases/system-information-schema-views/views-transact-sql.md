---
description: VIEWS (Transact-SQL)
title: Sichten (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/15/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- VIEWS_TSQL
- VIEWS
dev_langs:
- TSQL
helpviewer_keywords:
- VIEWS view
- INFORMATION_SCHEMA.VIEWS view
ms.assetid: 6119bc94-0b22-45d4-a34b-967afd810a9d
author: markingmyname
ms.author: maghan
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: c2e09f62858865c9ae1420efff17b0a3a0de9736
ms.sourcegitcommit: 1a544cf4dd2720b124c3697d1e62ae7741db757c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/14/2020
ms.locfileid: "97482435"
---
# <a name="views-transact-sql"></a>VIEWS (Transact-SQL)
[!INCLUDE [sql-asdb-asdbmi-asa-pdw](../../includes/applies-to-version/sql-asdb-asdbmi-asa-pdw.md)]

  Gibt eine Zeile für Sichten zurück, auf die der aktuelle Benutzer in der aktuellen Datenbank zugreifen kann.  
  
 Zum Abrufen von Informationen aus diesen Sichten geben Sie den voll qualifizierten Namen **INFORMATION_SCHEMA an.** _view_name_.  
  
|Spaltenname|Datentyp|Beschreibung|  
|-----------------|---------------|-----------------|  
|**TABLE_CATALOG**|**nvarchar (** 128 **)**|Sichtqualifizierer|  
|**TABLE_SCHEMA**|**nvarchar (** 128 **)**|Der Name des Schemas, das die Sicht enthält.<br /><br /> **&#42;&#42; wichtig &#42;&#42;**  nur eine zuverlässige Möglichkeit, das Schema eines-Objekts zu finden, besteht darin, die sys. Objects-Katalog Sicht abzufragen.|  
|**TABLE_NAME**|**nvarchar (** 128 **)**|Ansichtsname.|  
|**VIEW_DEFINITION**|**nvarchar (** 4000 **)**|Wenn die Länge der Definition größer als **nvarchar (** 4000 **)** ist, ist diese Spalte NULL. Andernfalls enthält diese Spalte den Text der Sichtdefinition.|  
|**CHECK_OPTION**|**varchar (** 7 **)**|WITH CHECK OPTION-Typ. Wenn die Originalsicht mit WITH CHECK OPTION erstellt wurde, wird CASCADE zurückgegeben. Andernfalls wird NONE zurückgegeben.|  
|**IS_UPDATABLE**|**varchar (** 2 **)**|Gibt an, ob die Sicht aktualisierbar ist. Es wird immer NO zurückgegeben.|  
  
## <a name="see-also"></a>Weitere Informationen  
 [System Sichten &#40;Transact-SQL-&#41;](../../t-sql/language-reference.md)   
 [Informations Schema Sichten &#40;Transact-SQL-&#41;](~/relational-databases/system-information-schema-views/system-information-schema-views-transact-sql.md)   
 [sys.sql_modules &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-sql-modules-transact-sql.md)   
 [sys.views &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-views-transact-sql.md)  
  
