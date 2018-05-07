---
title: Sys. fulltext_document_types (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.component: system-catalog-views
ms.reviewer: ''
ms.suite: sql
ms.technology: system-objects
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- sys.fulltext_document_types_TSQL
- fulltext_document_types
- fulltext_document_types_TSQL
- sys.fulltext_document_types
dev_langs:
- TSQL
helpviewer_keywords:
- sys.fulltext_document_types catalog view
ms.assetid: 156fcfa4-7304-4a5c-b96f-1c3e061e5df0
caps.latest.revision: 19
author: douglaslMS
ms.author: douglasl
manager: craigg
monikerRange: = azuresqldb-current || >= sql-server-2016 || = sqlallproducts-allversions
ms.openlocfilehash: 12ffa574d72bd2ee901015f5714eeb228524579c
ms.sourcegitcommit: f1caaa156db2b16e817e0a3884394e7b30fb642f
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/04/2018
---
# <a name="sysfulltextdocumenttypes-transact-sql"></a>sys.fulltext_document_types (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  Gibt eine Zeile für jeden für Volltextindizierungen verfügbaren Dokumenttyp zurück. Jede Zeile stellt eine in der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Instanz registrierte IFilter-Schnittstelle dar.  
  
 
|Spaltenname|Datentyp|Description|  
|-----------------|---------------|-----------------|  
|**document_type**|**sysname**|Die Dateierweiterung des unterstützten Dokumenttyps.<br /><br /> Dieser Wert kann verwendet werden, zum Identifizieren des Filters, der verwendet wird, während der Volltextindizierung von Spalten vom Typ **varbinary(max)** oder **Image**.|  
|**class_id**|**uniqueidentifier**|GUID der IFilter-Klasse, die die Dateierweiterung unterstützt.|  
|**path**|**nvarchar(260)**|Der Pfad zur IFilter-DLL. Der Pfad ist nur für Mitglieder der festen Serverrolle **serveradmin** sichtbar.|  
|**version**|**sysname**|Version der IFilter-DLL.|  
|**Hersteller**|**sysname**|Name des IFilter-Herstellers.<br /><br /> Hinweis: Nur Dokumente zurück mit dem Hersteller als [!INCLUDE[msCoName](../../includes/msconame-md.md)] werden unterstützt, auf [!INCLUDE[ssSDS](../../includes/sssds-md.md)].|  
  
## <a name="permissions"></a>Berechtigungen  
 [!INCLUDE[ssCatViewPerm](../../includes/sscatviewperm-md.md)]  
  
## <a name="see-also"></a>Siehe auch  
 [Katalogsichten &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/catalog-views-transact-sql.md)  
  
  
