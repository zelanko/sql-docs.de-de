---
description: sys.fulltext_stopwords (Transact-SQL)
title: sys.fulltext_stopwords (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- fulltext_stopwords_TSQL
- fulltext_stopwords
- sys.fulltext_stopwords
- sys.fulltext_stopwords_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- stoplists [full-text search]
- full-text search [SQL Server], stopwords
- sys.fulltext_stopwords catalog view
- stopwords [full-text search]
ms.assetid: 79787bb7-d729-448e-b56a-0a467bbb304f
author: pmasl
ms.author: pelopes
ms.reviewer: mikeray
monikerRange: =azuresqldb-current||>=sql-server-2016||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: 409de2d07425c2c39f983a3f1c1f6cb32bce631b
ms.sourcegitcommit: 1a544cf4dd2720b124c3697d1e62ae7741db757c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/14/2020
ms.locfileid: "97461631"
---
# <a name="sysfulltext_stopwords-transact-sql"></a>sys.fulltext_stopwords (Transact-SQL)
[!INCLUDE [SQL Server SQL Database](../../includes/applies-to-version/sql-asdb.md)]

  Enthält eine Zeile pro Stoppwort für alle Stopplisten in der Datenbank.  
 
|Spaltenname|Datentyp|Beschreibung|  
|-----------------|---------------|-----------------|  
|**stoplist_id**|**int**|ID der Stoppliste, zu der das **stopword** gehört. Diese ID ist innerhalb der Datenbank eindeutig.|  
|**Stoppwort**|**nvarchar (64)**|Der Ausdruck, der für eine Stoppwortübereinstimmung berücksichtigt werden muss.|  
|**language**|**sysname**|Ist entweder der Wert des Alias in [sys.fulltext_languages](../../relational-databases/system-catalog-views/sys-fulltext-languages-transact-sql.md)der dem Wert des Gebiets Schema Bezeichners (Locale Identifier,**LCID**) entspricht, oder ist die Zeichen folgen Darstellung der numerischen LCID.|  
|**language_id**|**int**|Die für die Wörtertrennung verwendete LCID.|  
  
## <a name="permissions"></a>Berechtigungen  
 [!INCLUDE[ssCatViewPerm](../../includes/sscatviewperm-md.md)]  
  
## <a name="see-also"></a>Weitere Informationen  
 [Katalogsichten &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/catalog-views-transact-sql.md)   
 [Katalogsichten für Objekte &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/object-catalog-views-transact-sql.md)   
 [Konfigurieren und Verwalten von Stoppwörtern und Stopplisten für Volltextsuche](../../relational-databases/search/configure-and-manage-stopwords-and-stoplists-for-full-text-search.md)   
 [sys.fulltext_stoplists &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-fulltext-stoplists-transact-sql.md)   
 [sys.fulltext_system_stopwords &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-fulltext-system-stopwords-transact-sql.md)  
  
  
