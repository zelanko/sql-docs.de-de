---
description: sys. dm_fts_index_keywords_position_by_document (Transact-SQL)
title: sys. dm_fts_index_keywords_position_by_document (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sys.dm_fts_index_keywords_position_by_document_TSQL
- dm_fts_index_keywords_position_by_document_TSQL
- dm_fts_index_keywords_position_by_document
- sys.dm_fts_index_keywords_position_by_document
dev_langs:
- TSQL
helpviewer_keywords:
- sys.dm_fts_index_keywords_position_by_document dynamic management view
ms.assetid: 0d70184f-baa2-411b-a32d-a4c5af890edd
author: pmasl
ms.author: pelopes
ms.openlocfilehash: 0b14ccbe7643ed56e18dc79b2a72e27867d63454
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/17/2020
ms.locfileid: "88474951"
---
# <a name="sysdm_fts_index_keywords_position_by_document-transact-sql"></a>sys. dm_fts_index_keywords_position_by_document (Transact-SQL)
[!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

  Gibt Schlüsselwort Positionsinformationen in den indizierten Dokumenten zurück.  
  
## <a name="syntax"></a>Syntax  
  
```  
sys.dm_fts_index_keywords_position_by_document  
(   
    DB_ID('database_name'),   
OBJECT_ID('table_name')   
)  
```  
  
## <a name="arguments"></a>Argumente  
 DB_ID ('*database_name*')  
 Ein Aufrufder [DB_ID ()](../../t-sql/functions/db-id-transact-sql.md) -Funktion. Diese Funktion akzeptiert einen Datenbanknamen und gibt die Datenbank-ID zurück, die sys. dm_fts_index_keywords_position_by_document verwendet, um die angegebene Datenbank zu suchen.  
  
 object_id ('*table_name*')  
 Ein Aufrufder [object_id ()](../../t-sql/functions/object-id-transact-sql.md) -Funktion. Diese Funktion akzeptiert einen Tabellennamen und gibt die Tabellen-ID der Tabelle zurück, die den zu überprüfenden Volltextindex enthält.  
  
## <a name="table-returned"></a>Zurückgegebene Tabelle  
  
|Column|Datentyp|BESCHREIBUNG|  
|------------|---------------|-----------------|  
|Schlüsselwort (keyword)|**varbinary(128)**|Binäre Zeichenfolge, die das Schlüsselwort darstellt.|  
|display_term|**nvarchar(4000)**|Die Klartextform des Schlüsselworts. Dieses Format wird vom internen Format abgeleitet, das im Volltextindex gespeichert ist.|  
|column_id|**int**|Die ID der Spalte für die Volltextindizierung des aktuellen Schlüsselworts.|  
|document_id|**bigint**|Die ID des Dokuments bzw. der Zeile für die Volltextindizierung des aktuellen Ausdrucks. Diese ID entspricht dem Volltextschlüsselwert dieses Dokuments bzw. dieser Zeile.|  
|position|**int**|Die Position des Schlüssel Worts im Dokument.|  
  
## <a name="remarks"></a>Bemerkungen  
 Verwenden Sie die DMV, um den Speicherort von indizierten Wörtern in indizierten Dokumenten zu identifizieren. Diese DMV kann verwendet werden, um Probleme zu beheben, wenn **sys. dm_fts_index_keywords_by_document** angibt, dass sich die Wörter im Volltextindex befinden, aber wenn Sie eine Abfrage mit diesen Wörtern ausführen, wird das Dokument nicht zurückgegeben.  
  
## <a name="permissions"></a>Berechtigungen  
 Erfordert CREATE FULLTEXT CATALOG-Berechtigungen und die SELECT-Berechtigung für die vom Volltextindex abgedeckten Spalten.  
  
## <a name="examples"></a>Beispiele  
 Im folgenden Beispiel werden Schlüsselwörter aus dem Volltextindex der- `Production.Document` Tabelle der- `AdventureWorks` Beispieldatenbank zurückgegeben.  
  
```  
USE AdventureWorks2012;  
GO   
  
SELECT * FROM sys.dm_fts_index_keywords_position_by_document  
(   
    DB_ID('AdventureWorks2012'),  
    OBJECT_ID('AdventureWorks2012.Production.Document')   
);   
GO  
```  
  
 Sie können ein Prädikat auf dem anderen columns_id wie in der folgenden Beispiel Abfrage hinzufügen, um die Speicherorte weiter zu isolieren.  
  
```  
SELECT * FROM sys.dm_fts_index_keywords_position_by_document  
(   
    DB_ID('AdventureWorks2012'),  
    OBJECT_ID('AdventureWorks2012.Production.Document')   
)  
WHERE document_id = 7 AND display_term = 'performance';  
```  
  
## <a name="see-also"></a>Weitere Informationen  
 [Volltextsuche](../../relational-databases/search/full-text-search.md)   
 [Verbessern der Leistung von voll Text Indizes](../../relational-databases/search/improve-the-performance-of-full-text-indexes.md)   
 [Funktionen für die voll Text Suche und die semantische Suche &#40;Transact-SQL-&#41;](../../relational-databases/system-functions/full-text-search-and-semantic-search-functions-transact-sql.md)   
 [Dynamische Verwaltungs Sichten und Funktionen für die voll Text Suche und die semantische Suche &#40;Transact-SQL-&#41;](../../relational-databases/system-dynamic-management-views/full-text-and-semantic-search-dynamic-management-views-functions.md)   
 [Gespeicherte Prozeduren für die voll Text Suche und die semantische Suche &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/full-text-search-and-semantic-search-stored-procedures-transact-sql.md)   
 [Durchsuchen von Dokumenteigenschaften mithilfe von Such Eigenschaften Listen](../../relational-databases/search/search-document-properties-with-search-property-lists.md)   
 [sys.dm_fts_index_keywords_by_document &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-fts-index-keywords-by-document-transact-sql.md)  
  
  
