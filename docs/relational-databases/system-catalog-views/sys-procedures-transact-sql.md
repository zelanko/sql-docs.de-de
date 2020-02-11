---
title: sys. Procedures (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/15/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- procedures
- sys.procedures_TSQL
- sys.procedures
- procedures_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.procedures catalog view
ms.assetid: d17af274-b2dd-464e-9523-ee1f43e1455b
author: stevestein
ms.author: sstein
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: cd7a827c869456b2f4cd97a08b39e7b9be00cb86
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "68068085"
---
# <a name="sysprocedures-transact-sql"></a>sys.procedures (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  Enthält eine Zeile für jedes Objekt, bei dem es sich um eine Prozedur von einer Art handelt, mit **sys. Objects. Type** = P, X, RF und PC.  
  
|Spaltenname|Datentyp|BESCHREIBUNG|  
|-----------------|---------------|-----------------|  
|**\<Von sys. Objects geerbte Spalten>**||Eine Liste der Spalten, die diese Sicht erbt, finden Sie unter [sys. Objects &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-objects-transact-sql.md)|  
|**is_auto_executed**|**bit**|1 = die Prozedur wird beim Serverstart automatisch ausgeführt; andernfalls 0. Kann nur für Prozeduren in der master-Datenbank festgelegt werden.|  
|**is_execution_replicated**|**bit**|Die Ausführung dieser Prozedur wird repliziert.|  
|**is_repl_serializable_only**|**bit**|Die Ausführung der Prozedur wird nur repliziert, wenn die Transaktion serialisiert werden kann.|  
|**skips_repl_constraints**|**bit**|Bei der Ausführung lässt die Prozedur Einschränkungen aus, die als NOT FOR REPLICATION markiert sind.|  
  
## <a name="permissions"></a>Berechtigungen  
 [!INCLUDE[ssCatViewPerm](../../includes/sscatviewperm-md.md)] Weitere Informationen finden Sie unter [Metadata Visibility Configuration](../../relational-databases/security/metadata-visibility-configuration.md).  
  
## <a name="see-also"></a>Weitere Informationen  
 [Objektkatalog Sichten &#40;Transact-SQL-&#41;](../../relational-databases/system-catalog-views/object-catalog-views-transact-sql.md)   
 [Katalogsichten &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/catalog-views-transact-sql.md)  
  
  
