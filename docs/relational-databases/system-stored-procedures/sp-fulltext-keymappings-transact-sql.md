---
description: sp_fulltext_keymappings (Transact-SQL)
title: sp_fulltext_keymappings (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, pdw
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_fulltext_keymappings_TSQL
- sp_fulltext_keymappings
dev_langs:
- TSQL
helpviewer_keywords:
- full-text indexes [SQL Server], key column
- sp_fulltext_keymappings
- full-text indexes [SQL Server], troubleshooting
ms.assetid: 2818fa42-072d-4664-a2f7-7ec363b51d81
author: markingmyname
ms.author: maghan
monikerRange: '>=aps-pdw-2016||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: cfac86a5cb8000203873f2434212bf2b50749a6d
ms.sourcegitcommit: 04cf7905fa32e0a9a44575a6f9641d9a2e5ac0f8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/07/2020
ms.locfileid: "91810096"
---
# <a name="sp_fulltext_keymappings-transact-sql"></a>sp_fulltext_keymappings (Transact-SQL)
[!INCLUDE [sql-asdbmi-pdw](../../includes/applies-to-version/sql-asdbmi-pdw.md)]

  Gibt Zuordnungen zwischen Dokumentbezeichnern (DocIds) und Volltextschlüsselwerten zurück. Die DocId-Spalte enthält Werte für eine **bigint** -Ganzzahl, die einem bestimmten voll Text Schlüsselwert in einer voll Text indizierten Tabelle zugeordnet ist. DocId-Werte, die eine Suchbedingung erfüllen, werden von der Volltext-Engine an die Datenbank-Engine übergeben. Dort werden sie Volltextschlüsselwerten aus der abgefragten Basistabelle zugeordnet. Die Volltextschlüsselspalte ist ein eindeutiger Index, der in einer Spalte der Tabelle erforderlich ist.  
  
 ![Symbol für Themenlink](../../database-engine/configure-windows/media/topic-link.gif "Symbol für Themenlink") [Transact-SQL-Syntaxkonventionen](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```  
  
sp_fulltext_keymappings { table_id | table_id, docid | table_id, NULL, key }  
```  
  
#### <a name="parameters"></a>Parameter  
 *table_id*  
 Ist die Objekt-ID der volltextindizierten Tabelle. Wenn Sie einen ungültigen *table_id*angeben, wird ein Fehler zurückgegeben. Informationen zum Abrufen der Objekt-ID einer Tabelle finden Sie unter [object_id &#40;Transact-SQL-&#41;](../../t-sql/functions/object-id-transact-sql.md).  
  
 *docid*  
 Ein interner Dokumentbezeichner (DocId), der dem Schlüsselwert entspricht. Ein ungültiger *docid* -Wert gibt keine Ergebnisse zurück.  
  
 *key*  
 Der Wert des Volltextschlüssels aus der angegebenen Tabelle. Ein ungültiger *key* -Wert gibt keine Ergebnisse zurück. Weitere Informationen zu voll Text Schlüsselwerten finden Sie unter [Verwalten von Volltextindizes](../search/create-and-manage-full-text-indexes.md).  
  
> [!IMPORTANT]  
>  Informationen zur Verwendung von einem, zwei oder drei Parametern finden Sie unter "Hinweise" später in diesem Thema.  
  
## <a name="return-code-values"></a>Rückgabecodewerte  
 Keine.  
  
## <a name="result-sets"></a>Resultsets  
  
|Spaltenname|Datentyp|Beschreibung|  
|-----------------|---------------|-----------------|  
|DocId|**bigint**|Eine interne Dokumentbezeichnerspalte (DocId), die dem Schlüsselwert entspricht.|  
|Key|*|Der Wert des Volltextschlüssels aus der angegebenen Tabelle.<br /><br /> Wenn in der Zuordnungstabelle keine Volltextschlüssel vorhanden sind, wird ein leeres Rowset zurückgegeben.|  
  
 <sup>*</sup> Der Datentyp für Key ist identisch mit dem Datentyp der voll Text Schlüssel Spalte in der Basistabelle.  
  
## <a name="permissions"></a>Berechtigungen  
 Diese Funktion ist öffentlich und erfordert keine besonderen Berechtigungen.  
  
## <a name="remarks"></a>Hinweise  
 In der folgenden Tabelle sind die Auswirkungen beschrieben, die sich ergeben, wenn ein, zwei oder drei Parameter verwendet werden.  
  
|Diese Parameterliste...|Hat dieses Ergebnis...|  
|--------------------------|----------------------|  
|*table_id*|Wenn nur mit dem *table_id* -Parameter aufgerufen wird, gibt sp_fulltext_keymappings alle voll Text Schlüsselwerte (Key) aus der angegebenen Basistabelle sowie die DocId zurück, die jedem Schlüssel entspricht. Dies schließt auch Schlüssel mit ein, für die ein Löschvorgang aussteht.<br /><br /> Diese Funktion ist hilfreich zur Behebung zahlreicher Probleme. Insbesondere bietet sie sich zum Anzeigen des Inhalts des Volltextindex an, wenn der ausgewählte Volltextschlüssel keinen ganzzahligen Datentyp aufweist. Dies umfasst das beitreten der Ergebnisse sp_fulltext_keymappings mit den Ergebnissen **sys.dm_fts_index_keywords_by_document**. Weitere Informationen finden Sie unter [sys.dm_fts_index_keywords_by_document &#40;Transact-SQL-&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-fts-index-keywords-by-document-transact-sql.md).<br /><br /> Im Allgemeinen sollten Sie jedoch , falls möglich, sp_fulltext_keymappings mit Parametern ausführen, die einen bestimmten Volltextschlüssel oder DocId angeben. Dies ist erheblich effizienter als eine gesamte Schlüsselzuordnung zurückzugeben, insbesondere für eine sehr große Tabelle, für die die Leistungskosten der Rückgabe der gesamten Schlüsselzuordnung erheblich sein könnten.|  
|*table_id*, *docid*|Wenn nur die *table_id* und die *docid* angegeben werden, muss *docid* nicht NULL sein und in der angegebenen Tabelle eine gültige docid angeben. Diese Funktion ist hilfreich, um den benutzerdefinierten Volltextschlüssel aus der Basistabelle zu isolieren, die der DocId eines bestimmten Volltextindex entspricht.|  
|*table_id*, NULL, *Schlüssel*|Wenn drei Parameter vorhanden sind, muss der zweite Parameter NULL sein, und der *Schlüssel* darf nicht NULL sein, und es muss ein gültiger Volltext-Schlüsselwert aus der angegebenen Tabelle angegeben werden. Diese Funktion ist hilfreich, um die DocID zu isolieren, die einem bestimmten Volltextschlüssel aus der Basistabelle entspricht.|  
  
 Wenn eine der folgenden Bedingungen zutrifft, wird ein Fehler zurückgegeben:  
  
-   Sie geben einen ungültigen *table_id*an.  
  
-   Die Tabelle ist nicht volltextindiziert.  
  
-   NULL tritt für einen Parameter auf, der möglicherweise ungleich NULL ist  
  
## <a name="examples"></a>Beispiele  
  
> [!NOTE]  
>  Die Beispiele in diesem Abschnitt verwenden die `Production.ProductReview` -Tabelle der [!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal-md.md)] -Beispieldatenbank. Sie können diesen Index erstellen, indem Sie das Beispiel ausführen, das für die- `ProductReview` Tabelle in [CREATE FULLTEXT Index &#40;Transact-SQL-&#41;](../../t-sql/statements/create-fulltext-index-transact-sql.md)bereitgestellt wird.  
  
### <a name="a-obtaining-all-the-key-and-docid-values"></a>A. Abrufen aller Schlüssel- und DocId-Werte  
 Im folgenden Beispiel wird eine [Declare](../../t-sql/language-elements/declare-local-variable-transact-sql.md) -Anweisung verwendet, um eine lokale Variable zu erstellen `@table_id` und die ID der `ProductReview` Tabelle als Wert zuzuweisen. Im Beispiel wird **sp_fulltext_keymappings** , `@table_id` der für den *table_id* -Parameter angibt, ausgeführt.  
  
> [!NOTE]  
>  Die Verwendung von **sp_fulltext_keymappings** nur mit dem Parameter *table_id* eignet sich für kleine Tabellen.  
  
```  
USE AdventureWorks2012;  
GO  
DECLARE @table_id int = OBJECT_ID(N'Production.ProductReview');  
EXEC sp_fulltext_keymappings @table_id;  
GO  
  
```  
  
 In diesem Beispiel werden alle DocIds und Volltextschlüssel folgendermaßen von der Tabelle zurückgegeben:  
  
| TABLE | docid | Schlüssel |
| ----- | ----- | --- |
|`1`|`1`|`1`|  
|`2`|`2`|`2`|  
|`3`|`3`|`3`|  
|`4`|`4`|`4`|  
  
### <a name="b-obtaining-the-docid-value-for-a-specific-key-value"></a>B. Abrufen des DocId-Werts für einen bestimmten Schlüsselwert  
 Im folgenden Beispiel wird eine DECLARE-Anweisung verwendet, um die lokale Variable `@table_id`zu erstellen und ihr die ID der `ProductReview` -Tabelle als Wert zuzuweisen. Das Beispiel führt **sp_fulltext_keymappings** aus `@table_id` , die für den Parameter *table_id* angeben, NULL für den *docid* -Parameter und 4 für den *Key* -Parameter.  
  
> [!NOTE]  
>  Die Verwendung von **sp_fulltext_keymappings** nur mit dem *table_id* parameterist für kleine Tabellen geeignet.  
  
```  
USE AdventureWorks2012;  
GO  
DECLARE @table_id int = OBJECT_ID(N'Production.ProductReview');  
EXEC sp_fulltext_keymappings @table_id, NULL, 4;  
GO  
  
```  
  
 Dieses Beispiel gibt die folgenden Ergebnisse zurück:  
  
| TABLE | docid | Schlüssel |
| ----- | ----- | --- |
|`4`|`4`|`4`|  
  
## <a name="see-also"></a>Weitere Informationen  
 [Gespeicherte Prozeduren für die voll Text Suche und die semantische Suche &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/full-text-search-and-semantic-search-stored-procedures-transact-sql.md)  
  
