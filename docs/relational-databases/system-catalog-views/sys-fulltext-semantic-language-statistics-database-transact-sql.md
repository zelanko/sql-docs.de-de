---
title: sys. fulltext_semantic_language_statistics_database (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.prod_service: database-engine
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sys.fulltext_semantic_language_statistics_database_TSQL
- fulltext_semantic_language_statistics_database_TSQL
- fulltext_semantic_language_statistics_database
- sys.fulltext_semantic_language_statistics_database
dev_langs:
- TSQL
helpviewer_keywords:
- sys.fulltext_semantic_language_statistics_database catalog view
ms.assetid: 32e95614-ed88-4068-8c37-1e21544717bc
author: pmasl
ms.author: pelopes
ms.reviewer: mikeray
ms.openlocfilehash: 0decfac8cf28727a3ba3f4bf5ad54e8f9ff8bee9
ms.sourcegitcommit: f7ac1976d4bfa224332edd9ef2f4377a4d55a2c9
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/02/2020
ms.locfileid: "85902184"
---
# <a name="sysfulltext_semantic_language_statistics_database-transact-sql"></a>sys.fulltext_semantic_language_statistics_database (Transact-SQL)
[!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

  Gibt eine Zeile zur semantischen Sprachstatistikdatenbank zurück, die in der aktuellen Instanz von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] installiert ist.  
  
 Sie können diese Sicht abfragen, um Informationen über die semantische Sprachstatistikkomponente zu erhalten, die für die semantische Verarbeitung erforderlich ist.  
   
  
||||  
|-|-|-|  
|**Spaltenname**|**Type**|**Beschreibung**|  
|**database_id**|**int**|ID der Datenbank und innerhalb einer [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Instanz eindeutig.|  
|**register_date**|**datetime**|Datum, an dem die Datenbank für die semantische Verarbeitung registriert wurde.|  
|**registered_by**|**int**|ID des Serverprinzipals, der die Datenbank für die semantische Verarbeitung registriert hat.|  
|**version**|**nvarchar(128)**|Die neuesten Versionsinformationen spezifisch für die semantische Sprachstatistikdatenbank.|  
  
## <a name="general-remarks"></a>Allgemeine Hinweise  
 Weitere Informationen finden Sie unter [Installieren und Konfigurieren der semantischen Suche](../../relational-databases/search/install-and-configure-semantic-search.md).  
  
## <a name="metadata"></a>Metadaten  
 Informationen zu den Sprachen, die für die semantische Indizierung unterstützt werden, finden Sie in der Katalog Sicht [sys. fulltext_semantic_languages &#40;Transact-SQL-&#41;](../../relational-databases/system-catalog-views/sys-fulltext-semantic-languages-transact-sql.md).  
  
## <a name="security"></a>Sicherheit  
  
### <a name="permissions"></a>Berechtigungen  
 Die Sichtbarkeit der Metadaten in Katalogsichten ist auf sicherungsfähige Elemente eingeschränkt, bei denen der Benutzer entweder der Besitzer ist oder für die dem Benutzer eine Berechtigung erteilt wurde.  
  
## <a name="examples"></a>Beispiele  
 Im folgenden Beispiel wird gezeigt, wie **sys. fulltext_semantic_language_statistics_database** abgefragt wird, um Informationen über die semantische sprach Statistik Datenbank zu erhalten, die für die aktuelle Instanz von registriert ist [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
```  
SELECT * FROM sys.fulltext_semantic_language_statistics_database;  
GO  
```  
  
## <a name="see-also"></a>Weitere Informationen  
 [Installieren und Konfigurieren der semantischen Suche](../../relational-databases/search/install-and-configure-semantic-search.md)  
  
  
