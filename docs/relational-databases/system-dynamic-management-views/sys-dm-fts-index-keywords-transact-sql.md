---
title: sys. dm_fts_index_keywords (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- dm_fts_index_keywords
- sys.dm_fts_index_keywords
- sys.dm_fts_index_keywords_TSQL
- dm_fts_index_keywords_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.dm_fts_index_keywords dynamic management function
- full-text search [SQL Server], viewing keywords
- troubleshooting [SQL Server], full-text search
ms.assetid: fce7b2a1-7e74-4769-86a8-c77c7628decd
author: pmasl
ms.author: pelopes
ms.openlocfilehash: e29fcabeb2f99def9f2e06b1d0b157c8d148002a
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/01/2020
ms.locfileid: "85734544"
---
# <a name="sysdm_fts_index_keywords-transact-sql"></a>sys.dm_fts_index_keywords (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/applies-to-version/sqlserver.md)]

  Gibt Informationen zum Inhalt eines Volltextindex für die angegebene Tabelle zurück.  
  
 **sys. dm_fts_index_keywords** ist eine dynamische Verwaltungsfunktion.  
  
> [!NOTE]  
>  Um Volltextindex Informationen auf niedrigerer Ebene anzuzeigen, verwenden Sie die dynamische Verwaltungsfunktion [sys. dm_fts_index_keywords_by_document](../../relational-databases/system-dynamic-management-views/sys-dm-fts-index-keywords-by-document-transact-sql.md) auf Dokument Ebene.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
sys.dm_fts_index_keywords( DB_ID('database_name'), OBJECT_ID('table_name') )  
```  
  
## <a name="arguments"></a>Argumente  
 DB_ID ('*database_name*')  
 Ein Aufrufder [DB_ID ()](../../t-sql/functions/db-id-transact-sql.md) -Funktion. Diese Funktion akzeptiert einen Datenbanknamen und gibt die Datenbank-ID zurück, die **sys. dm_fts_index_keywords** verwendet, um die angegebene Datenbank zu suchen. Wenn *database_name* nicht angegeben ist, wird die aktuelle Datenbank-ID zurückgegeben.  
  
 object_id ('*table_name*')  
 Ein Aufrufder [object_id ()](../../t-sql/functions/object-id-transact-sql.md) -Funktion. Diese Funktion akzeptiert einen Tabellennamen und gibt die Tabellen-ID der Tabelle zurück, die den zu überprüfenden Volltextindex enthält.  
  
## <a name="table-returned"></a>Zurückgegebene Tabelle  
  
|Spaltenname|Datentyp|BESCHREIBUNG|  
|-----------------|---------------|-----------------|  
|**keyword**|**nvarchar(4000)**|Die hexadezimale Darstellung des Schlüssel Worts, das im Volltextindex gespeichert ist.<br /><br /> Hinweis: OxFF stellt das Sonderzeichen dar, das das Ende einer Datei oder eines Datasets angibt.|  
|**display_term**|**nvarchar(4000)**|Die Klartextform des Schlüsselworts. Dieses Format wird vom Hexadezimalformat abgeleitet.<br /><br /> Hinweis: der **display_term** Wert für OxFF ist "Dateiende".|  
|**column_id**|**int**|Die ID der Spalte für die Volltextindizierung des aktuellen Schlüsselworts.|  
|**document_count**|**int**|Die Anzahl der Dokumente bzw. Zeilen, die den aktuellen Begriff enthalten.|  
  
## <a name="remarks"></a>Hinweise  
 Die Informationen, die von **sys. dm_fts_index_keywords** zurückgegeben werden, sind unter anderem nützlich, um Folgendes zu ermitteln:  
  
-   Ob ein Schlüsselwort ein Teil des Volltextindexes ist  
  
-   Wie viele Dokumente bzw. Zeilen ein gegebenes Schlüsselwort enthalten  
  
-   Das häufigste Schlüsselwort im Volltextindex:  
  
    -   **document_count** der einzelnen *keyword_value* im Vergleich zum Gesamt **document_count**, der Dokument Anzahl von 0xFF.  
  
    -   Häufige oder gemeinsame Schlüsselwörter eignen sich in der Regel für die Deklaration als Stoppwörter.  
  
> [!NOTE]  
>  Der von **sys. dm_fts_index_keywords** zurückgegebene **document_count** kann für ein bestimmtes Dokument weniger genau sein als die von **sys. dm_fts_index_keywords_by_document** oder einer **enthält** -Abfrage zurückgegebene Anzahl. Die mögliche Ungenauigkeit liegt bei ca. 1 %. Diese ingenauigkeit kann auftreten, wenn eine **document_id** zweimal gezählt werden kann, wenn Sie über mehr als eine Zeile im Index Fragment hinweg fortgesetzt wird, oder wenn Sie mehrmals in derselben Zeile angezeigt wird. Um einen genaueren Zähler für ein bestimmtes Dokument zu erhalten, verwenden Sie **sys. dm_fts_index_keywords_by_document** oder eine **enthält** -Abfrage.  
  
## <a name="permissions"></a>Berechtigungen  
 Erfordert die Mitgliedschaft in der festen Server Rolle **sysadmin** .  
  
## <a name="examples"></a>Beispiele  
  
### <a name="a-displaying-high-level-full-text-index-content"></a>A. Anzeigen des Inhalts eines Volltextindex auf hoher Ebene  
 Im folgenden Beispiel werden Informationen über den Inhalt des Volltextindexes auf hoher Ebene in der `HumanResources.JobCandidate`-Tabelle angezeigt.  
  
```  
SELECT * FROM sys.dm_fts_index_keywords(db_id('AdventureWorks2012'), object_id('HumanResources.JobCandidate'))  
GO  
```  
  
## <a name="see-also"></a>Weitere Informationen  
 [Dynamische Verwaltungs Sichten und Funktionen für die voll Text Suche und die semantische Suche &#40;Transact-SQL-&#41;](../../relational-databases/system-dynamic-management-views/full-text-and-semantic-search-dynamic-management-views-functions.md)   
 [Volltextsuche](../../relational-databases/search/full-text-search.md)   
 [sys.dm_fts_index_keywords_by_document &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-fts-index-keywords-by-document-transact-sql.md)  
  
  
