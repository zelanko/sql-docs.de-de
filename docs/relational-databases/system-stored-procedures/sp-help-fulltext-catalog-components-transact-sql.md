---
description: sp_help_fulltext_catalog_components (Transact-SQL)
title: sp_help_fulltext_catalog_components (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_help_fulltext_catalog_components_TSQL
- sp_help_fulltext_catalog_components
dev_langs:
- TSQL
helpviewer_keywords:
- sp_help_fulltext_catalog_components
ms.assetid: fbd6a3d4-6a4c-42a2-bff8-2a5eb0745e47
author: markingmyname
ms.author: maghan
ms.openlocfilehash: 2884cda986a99f23c88c71c8960d25a467de0663
ms.sourcegitcommit: dd36d1cbe32cd5a65c6638e8f252b0bd8145e165
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/08/2020
ms.locfileid: "89548028"
---
# <a name="sp_help_fulltext_catalog_components-transact-sql"></a>sp_help_fulltext_catalog_components (Transact-SQL)
[!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

  Gibt eine Liste aller Komponenten (Filter, Wörtertrennung und Protokollhandler) zurück, die für alle Volltextkataloge in der aktuellen Datenbank verwendet werden.  
  
> [!NOTE]  
>  [!INCLUDE[ssNoteDepFutureDontUse](../../includes/ssnotedepfuturedontuse-md.md)]  
  
 ![Symbol für Themenlink](../../database-engine/configure-windows/media/topic-link.gif "Symbol für Themenlink") [Transact-SQL-Syntaxkonventionen](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```  
  
sp_help_fulltext_catalog_components  
```  
  
## <a name="result-sets"></a>Resultsets  
  
|Spaltenname|Datentyp|BESCHREIBUNG|  
|-----------------|---------------|-----------------|  
|**Name des voll Text Katalogs**|**int**|Name des Volltextkatalogs.|  
|**voll Text Katalog-ID**|**sysname**|ID des Volltextkatalogs.|  
|**componenttype**|**sysname**|Typ der Komponente. Einer der folgenden:<br /><br /> Filter<br /><br /> Protokollhandler<br /><br /> Wörtertrennung|  
|**componentname**|**sysname**|Der Name der Komponente.|  
|**CLSID**|**uniqueidentifier**|Klassenbezeichner der Komponente.|  
|**FullPath**|**nvarchar(256)**|Pfad zum Speicherort der Komponente.<br /><br /> NULL = Aufrufer ist kein Mitglied der festen Serverrolle **serveradmin** .|  
|**version**|**nvarchar(30)**|Version der Komponente.|  
|**Hersteller**|**sysname**|Name des Herstellers der Komponente.|  
  
## <a name="permissions"></a>Berechtigungen  
 Erfordert die Mitgliedschaft in der **public** -Rolle.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Gespeicherte Prozeduren für die voll Text Suche und die semantische Suche &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/full-text-search-and-semantic-search-stored-procedures-transact-sql.md)   
 [sys.fulltext_catalogs &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-fulltext-catalogs-transact-sql.md)   
 [sp_help_fulltext_system_components &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/sp-help-fulltext-system-components-transact-sql.md)   
 [Volltextsuche](../../relational-databases/search/full-text-search.md)  
  
  
