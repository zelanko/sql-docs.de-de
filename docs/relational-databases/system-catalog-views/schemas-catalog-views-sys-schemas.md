---
description: Schemas-Katalog Sichten-sys. Schemas
title: sys. Schemas (Transact-SQL) | Microsoft-Dokumentation
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
author: CarlRabeler
ms.author: carlrab
monikerRange: '>=aps-pdw-2016||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: a8a48cbf6a2c50bafab98638c94dce8d5b833012
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/17/2020
ms.locfileid: "88486558"
---
# <a name="schemas-catalog-views---sysschemas"></a>Schemas-Katalog Sichten-sys. Schemas
[!INCLUDE [sql-asdbmi-asa-pdw](../../includes/applies-to-version/sql-asdbmi-asa-pdw.md)]

  Enthält eine Zeile für jedes Datenbankschema.  
  
> [!NOTE]  
>  Datenbankschemas unterscheiden sich von XML-Schemas, die verwendet werden, um das Inhaltsmodell von XML-Dokumenten zu definieren.  
  
|Spaltenname|Datentyp|BESCHREIBUNG|  
|-----------------|---------------|-----------------|  
|**name**|**sysname**|Name des Schemas. Ist in der Datenbank eindeutig.|  
|**schema_id**|**int**|Die ID des Schemas. Ist in der Datenbank eindeutig.|  
|**principal_id**|**int**|Die ID des Prinzipals, der das Schema besitzt.|  
  
## <a name="remarks"></a>Bemerkungen  
Datenbankschemas dienen als Namespaces oder Container für Objekte, wie z. B. Tabellen, Sichten, Prozeduren und Funktionen, die in der Katalogsicht **sys.objects** zu finden sind.  

Jedes Schema weist einen Besitzer auf. Der Besitzer ist ein Sicherheits [Prinzipal](../../relational-databases/security/authentication-access/principals-database-engine.md).
  
## <a name="permissions"></a>Berechtigungen  
 Erfordert die Mitgliedschaft in der **public** -Rolle. Weitere Informationen finden Sie unter [Metadata Visibility Configuration](../../relational-databases/security/metadata-visibility-configuration.md).  
  
## <a name="see-also"></a>Weitere Informationen  
[Principals](../../relational-databases/security/authentication-access/principals-database-engine.md)

[Katalogsichten &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/catalog-views-transact-sql.md)   

[Schemas-Katalog Sichten &#40;Transact-SQL-&#41;](https://msdn.microsoft.com/library/c516fb1c-b6ed-48ae-99c7-a78bc4336c8e)   

[sys.objects &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-objects-transact-sql.md)  
  
  
