---
title: CHANGE_TRACKING_MIN_VALID_VERSION (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 08/08/2016
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- CHANGE_TRACKING_CLEANUP_VERSION
- CHANGE_TRACKING_CLEANUP_VERSION_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- CHANGE_TRACKING_MIN_VALID_VERSION
- change tracking [SQL Server], CHANGE_TRACKING_MIN_VALID_VERSION
ms.assetid: 5a43d23f-adcf-4c0b-95ad-07cee03c1f9d
author: rothja
ms.author: jroth
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: 5bb0baec2284d17d84c7a8c3dddd13de3fa69510
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "68042944"
---
# <a name="change_tracking_min_valid_version-transact-sql"></a>CHANGE_TRACKING_MIN_VALID_VERSION (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  Gibt die minimale Version auf dem Client zurück, die zum Abrufen von Änderungs nach Verfolgungs Informationen aus der angegebenen Tabelle gültig ist, wenn Sie die [CHANGETABLE](../../relational-databases/system-functions/changetable-transact-sql.md) -Funktion verwenden.  
    
 ![Symbol für Themenlink](../../database-engine/configure-windows/media/topic-link.gif "Symbol für Themenlink") [Transact-SQL-Syntaxkonventionen](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```  
  
CHANGE_TRACKING_MIN_VALID_VERSION ( table_object_id )  
```  
  
## <a name="arguments"></a>Argumente  
 *table_object_id*  
 Die Objekt-ID der Tabelle. *table_object_id* ist vom Datentyp **int**.  
  
## <a name="return-type"></a>Rückgabetyp  
 **BIGINT**  
  
## <a name="remarks"></a>Bemerkungen  
 Verwenden Sie diese Funktion, um den Wert des *last_sync_version* -Parameters für CHANGETABLE zu validieren. Wenn *last_sync_version* kleiner ist als der Wert, der von dieser Funktion gemeldet wird, sind die Ergebnisse, die von einem späteren CHANGETABLE-Befehl zurückgegeben werden, möglicherweise nicht gültig.  
  
 CHANGE_TRACKING_MIN_VALID_VERSION verwendet die folgenden Informationen, um den Rückgabewert zu bestimmen:  
  
-   Wenn für die Tabelle die Änderungsnachverfolgung aktiviert ist.  
  
-   Wenn der Cleanuptask im Hintergrund ausgeführt wurde, um Änderungsnachverfolgungsinformationen zu entfernen, die älter als die für die Datenbank angegebene Beibehaltungsdauer sind.  
  
-   Wenn die Tabelle abgeschnitten wurde. Dadurch werden alle Änderungsnachverfolgungsinformationen entfernt, die der Tabelle zugeordnet sind.  
  
 Die Funktion gibt einen NULL-Fehler zurück, wenn eine der folgenden Bedingungen zutrifft:  
  
-   Die Änderungsnachverfolgung ist für die Datenbank nicht aktiviert.  
  
-   Die angegebene Tabellen-Objekt-ID ist für die aktuelle Datenbank nicht gültig.  
  
-   Es sind keine ausreichenden Berechtigungen für die von der Objekt-ID angegebene Tabelle vorhanden.  
  
## <a name="examples"></a>Beispiele  
 Im folgenden Beispiel wird ermittelt, ob eine angegebene Version eine gültige Version ist. In diesem Beispiel wird die minimal gültige Version für die Tabelle `dbo.Employees` abgerufen, und dieser Wert wird mit dem Wert der Variable `@last_sync_version` verglichen. Wenn der Wert von `@last_sync_version` kleiner als der Wert von `@min_valid_version` ist, dann ist die Liste der geänderten Zeilen nicht gültig.  
  
> [!NOTE]  
>  Normalerweise wird der Wert aus einer Tabelle oder aus einem anderen Speicherort abgerufen, in der bzw. in dem die letzte Versionsnummer gespeichert wurde, die zum Synchronisieren von Daten verwendet wurde.  
  
```  
-- The tracked change is tagged with the specified context   
DECLARE @min_valid_version bigint, @last_sync_version bigint;  
  
SET @min_valid_version =   
CHANGE_TRACKING_MIN_VALID_VERSION(OBJECT_ID('dbo.Employees'));  
  
SET @last_sync_version = 11  
IF (@last_sync_version < @min_valid_version)  
-- Error � do not obtain changes  
ELSE  
-- Obtain changes using CHANGETABLE(CHANGES ...)  
```  
  
## <a name="see-also"></a>Weitere Informationen  
 [Änderungsnachverfolgungsfunktionen &#40;Transact-SQL&#41;](../../relational-databases/system-functions/change-tracking-functions-transact-sql.md)   
 [sys.change_tracking_tables &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/change-tracking-catalog-views-sys-change-tracking-tables.md)  
  
  
