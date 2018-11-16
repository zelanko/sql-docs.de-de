---
title: Sys.Schemas (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/15/2017
ms.prod: sql
ms.prod_service: database-engine, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- schemas_TSQL
- sys.schemas_TSQL
- schemas
- sys.schemas
dev_langs:
- TSQL
helpviewer_keywords:
- sys.schemas catalog view
ms.assetid: 29af5ce5-2af7-4103-8f08-3ec92603ba05
author: stevestein
ms.author: sstein
manager: craigg
monikerRange: '>=aps-pdw-2016||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 9a676eb3e9bf67d14e45ebc9973f5be7998e19cf
ms.sourcegitcommit: 9c6a37175296144464ffea815f371c024fce7032
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/15/2018
ms.locfileid: "51665789"
---
# <a name="schemas-catalog-views---sysschemas"></a>Schemas Katalogsichten – sys.schemas
[!INCLUDE[tsql-appliesto-ss2008-xxxx-asdw-pdw-md](../../includes/tsql-appliesto-ss2008-xxxx-asdw-pdw-md.md)]

  Enthält eine Zeile für jedes Datenbankschema.  
  
> [!NOTE]  
>  Datenbankschemas unterscheiden sich von XML-Schemas, die verwendet werden, um das Inhaltsmodell von XML-Dokumenten zu definieren.  
  
|Spaltenname|Datentyp|Description|  
|-----------------|---------------|-----------------|  
|**name**|**sysname**|Der Name des Schemas. Ist in der Datenbank eindeutig.|  
|**schema_id**|**int**|Die ID des Schemas. Ist in der Datenbank eindeutig.|  
|**principal_id**|**int**|Die ID des Prinzipals, der das Schema besitzt.|  
  
## <a name="remarks"></a>Hinweise  
 Datenbankschemas dienen als Namespaces oder Container für Objekte, wie z. B. Tabellen, Sichten, Prozeduren und Funktionen, die in der Katalogsicht **sys.objects** zu finden sind.  
  
## <a name="permissions"></a>Berechtigungen  
 Erfordert die Mitgliedschaft in der **public** -Rolle. Weitere Informationen finden Sie unter [Metadata Visibility Configuration](../../relational-databases/security/metadata-visibility-configuration.md).  
  
## <a name="see-also"></a>Siehe auch  
 [Katalogsichten &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/catalog-views-transact-sql.md)   
 [Katalogsichten für Schemas &#40;Transact-SQL&#41;](https://msdn.microsoft.com/library/c516fb1c-b6ed-48ae-99c7-a78bc4336c8e)   
 [sys.objects &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-objects-transact-sql.md)  
  
  
