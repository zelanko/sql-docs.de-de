---
title: Routinen (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/15/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- ROUTINES_TSQL
- ROUTINES
dev_langs:
- TSQL
helpviewer_keywords:
- ROUTINES view
- INFORMATION_SCHEMA.ROUTINES view
ms.assetid: c75561b2-c9a1-48a1-9afa-a5896b6454cf
author: CarlRabeler
ms.author: carlrab
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 1ec3836db241320beabfbd4672ffad9b22ccaf58
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "68078525"
---
# <a name="routines-transact-sql"></a>ROUTINES (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  Gibt eine Zeile für jede gespeicherte Prozedur und Funktion zurück, auf die der aktuelle Benutzer in der aktuellen Datenbank zugreifen kann. Die Spalten, die den Rückgabewert beschreiben, sind nur auf Funktionen anwendbar. Für gespeicherte Prozeduren sind diese Spalten NULL.  
  
 Zum Abrufen von Informationen aus diesen Sichten geben Sie den voll qualifizierten Namen INFORMATION_SCHEMA an. *view_name*.  
  
> [!NOTE]  
>  Die ROUTINE_DEFINITION-Spalte enthält die Quellanweisungen, die die Funktion oder die gespeicherte Prozedur erstellt haben. Diese Quellanweisungen enthalten wahrscheinlich eingebettete Wagenrücklaufzeichen. Wenn Sie diese Spalte an eine Anwendung zurückgeben, die die Ergebnisse in einem Textformat anzeigt, beeinflussen die eingebetteten Wagenrücklaufzeichen in den Ergebnissen von ROUTINE_DEFINITION möglicherweise die Formatierung des gesamten Resultsets. Wenn Sie die ROUTINE_DEFINITION-Spalte auswählen, müssen Sie aufgrund der eingebetteten Wagenrücklaufzeichen eine Anpassung vornehmen, indem Sie beispielsweise das Resultset in ein Raster oder die ROUTINE_DEFINITION-Spalte in ein eigenes Textfeld zurückgeben.  
  
|Spaltenname|Datentyp|BESCHREIBUNG|  
|-----------------|---------------|-----------------|  
|SPECIFIC_CATALOG|**nvarchar (** 128 **)**|Spezifischer Name des Katalogs. Dieser Name ist derselbe wie für ROUTINE_CATALOG.|  
|SPECIFIC_SCHEMA|**nvarchar (** 128 **)**|Spezifischer Name des Schemas.<br /><br /> ** \* Wichtig \* \* ** Verwenden Sie INFORMATION_SCHEMA Sichten nicht, um das Schema eines Objekts zu bestimmen. Die einzig zuverlässige Möglichkeit zum Finden des Schemas eines Objekts besteht darin, die sys.objects-Katalogsicht abzufragen.|  
|SPECIFIC_NAME|**nvarchar (** 128 **)**|Spezifischer Name des Katalogs. Dieser Name ist derselbe wie für ROUTINE_NAME.|  
|ROUTINE_CATALOG|**nvarchar (** 128 **)**|Katalogname der Funktion.|  
|ROUTINE_SCHEMA|**nvarchar (** 128 **)**|Name des Schemas, das diese Funktion enthält.<br /><br /> ** \* Wichtig \* \* ** Verwenden Sie INFORMATION_SCHEMA Sichten nicht, um das Schema eines Objekts zu bestimmen. Die einzig zuverlässige Möglichkeit zum Finden des Schemas eines Objekts besteht darin, die sys.objects-Katalogsicht abzufragen.|  
|ROUTINE_NAME|**nvarchar (** 128 **)**|Name der Funktion.|  
|ROUTINE_TYPE|**nvarchar (** 20 **)**|Gibt PROCEDURE für gespeicherte Prozeduren und FUNCTION für Funktionen zurück.|  
|MODULE_CATALOG|**nvarchar (** 128 **)**|NULL. Für die zukünftige Verwendung reserviert.|  
|MODULE_SCHEMA|**nvarchar (** 128 **)**|NULL. Für die zukünftige Verwendung reserviert.|  
|MODULE_NAME|**nvarchar (** 128 **)**|NULL. Für die zukünftige Verwendung reserviert.|  
|UDT_CATALOG|**nvarchar (** 128 **)**|NULL. Für die zukünftige Verwendung reserviert.|  
|UDT_SCHEMA|**nvarchar (** 128 **)**|NULL. Für die zukünftige Verwendung reserviert.|  
|UDT_NAME|**nvarchar (** 128 **)**|NULL. Für die zukünftige Verwendung reserviert.|  
|DATA_TYPE|**nvarchar (** 128 **)**|Datentyp des Rückgabewerts der Funktion. Gibt eine **Tabelle** zurück, wenn eine Tabellenwert Funktion ist.|  
|CHARACTER_MAXIMUM_LENGTH|**int**|Maximale Länge in Zeichen, wenn der Rückgabetyp ein Zeichentyp ist.<br /><br /> -1 für **XML** -Daten und Daten mit umfangreichen Werten.|  
|CHARACTER_OCTET_LENGTH|**int**|Maximale Länge in Bytes, wenn der Rückgabetyp ein Zeichentyp ist.<br /><br /> -1 für **XML** -Daten und Daten mit umfangreichen Werten.|  
|COLLATION_CATALOG|**nvarchar (** 128 **)**|Gibt immer NULL zurück.|  
|COLLATION_SCHEMA|**nvarchar (** 128 **)**|Gibt immer NULL zurück.|  
|COLLATION_NAME|**nvarchar (** 128 **)**|Sortierungsname des Rückgabewerts. Für Nicht-Zeichentypen wird NULL zurückgegeben.|  
|CHARACTER_SET_CATALOG|**nvarchar (** 128 **)**|Gibt immer NULL zurück.|  
|CHARACTER_SET_SCHEMA|**nvarchar (** 128 **)**|Gibt immer NULL zurück.|  
|CHARACTER_SET_NAME|**nvarchar (** 128 **)**|Name des Zeichensatzes des Rückgabewerts. Für Nicht-Zeichentypen wird NULL zurückgegeben.|  
|NUMERIC_PRECISION|**smallint**|Numerische Genauigkeit des Rückgabewerts. Gibt für die nicht numerischen Typen NULL zurück.|  
|NUMERIC_PRECISION_RADIX|**smallint**|Numerische Basis der Genauigkeit des Rückgabewerts. Für nicht-numerische Typen wird NULL zurückgegeben.|  
|NUMERIC_SCALE|**smallint**|Dezimalstellen des Rückgabewerts. Für nicht-numerische Typen wird NULL zurückgegeben.|  
|DATETIME_PRECISION|**smallint**|Bruch Komma Genauigkeit einer Sekunde, wenn der Rückgabewert vom **DateTime**-Datentyp ist. Andernfalls wird NULL zurückgegeben.|  
|INTERVAL_TYPE|**nvarchar (** 30 **)**|NULL. Für die zukünftige Verwendung reserviert.|  
|INTERVAL_PRECISION|**smallint**|NULL. Für die zukünftige Verwendung reserviert.|  
|TYPE_UDT_CATALOG|**nvarchar (** 128 **)**|NULL. Für die zukünftige Verwendung reserviert.|  
|TYPE_UDT_SCHEMA|**nvarchar (** 128 **)**|NULL. Für die zukünftige Verwendung reserviert.|  
|TYPE_UDT_NAME|**nvarchar (** 128 **)**|NULL. Für die zukünftige Verwendung reserviert.|  
|SCOPE_CATALOG|**nvarchar (** 128 **)**|NULL. Für die zukünftige Verwendung reserviert.|  
|SCOPE_SCHEMA|**nvarchar (** 128 **)**|NULL. Für die zukünftige Verwendung reserviert.|  
|SCOPE_NAME|**nvarchar (** 128 **)**|NULL. Für die zukünftige Verwendung reserviert.|  
|MAXIMUM_CARDINALITY|**BIGINT**|NULL. Für die zukünftige Verwendung reserviert.|  
|DTD_IDENTIFIER|**nvarchar (** 128 **)**|NULL. Für die zukünftige Verwendung reserviert.|  
|ROUTINE_BODY|**nvarchar (** 30 **)**|Gibt SQL für eine [!INCLUDE[tsql](../../includes/tsql-md.md)]-Funktion und EXTERNAL für eine extern geschriebene Funktion zurück.<br /><br /> Funktionen sind immer SQL.|  
|ROUTINE_DEFINITION|**nvarchar (** 4000 **)**|Gibt die ersten 4000 Zeichen des Definitionstexts der Funktion oder gespeicherten Prozedur zurück, wenn die Funktion oder gespeicherte Prozedur nicht verschlüsselt ist. Andernfalls wird NULL zurückgegeben.<br /><br /> Um sicherzustellen, dass Sie die gesamte Definition erhalten, Fragen Sie die [OBJECT_DEFINITION](../../t-sql/functions/object-definition-transact-sql.md) -Funktion oder die Definition-Spalte in der [sys. sql_modules](../../relational-databases/system-catalog-views/sys-sql-modules-transact-sql.md) -Katalog Sicht ab.|  
|EXTERNAL_NAME|**nvarchar (** 128 **)**|NULL. Für die zukünftige Verwendung reserviert.|  
|EXTERNAL_LANGUAGE|**nvarchar (** 30 **)**|NULL. Für die zukünftige Verwendung reserviert.|  
|PARAMETER_STYLE|**nvarchar (** 30 **)**|NULL. Für die zukünftige Verwendung reserviert.|  
|IS_DETERMINISTIC|**nvarchar (** 10 **)**|Gibt YES zurück, wenn die Routine deterministisch ist.<br /><br /> Gibt NO zurück, wenn die Routine nicht deterministisch ist.<br /><br /> Für gespeicherte Prozeduren wird immer NO zurückgegeben.|  
|SQL_DATA_ACCESS|**nvarchar (** 30 **)**|Gibt einen der folgenden Werte zurück:<br /><br /> NONE = Die Funktion enthält keine SQL-Anweisungen.<br /><br /> CONTAINS = Die Funktion enthält möglicherweise SQL-Anweisungen.<br /><br /> READS = Die Funktion liest möglicherweise SQL-Daten.<br /><br /> MODIFIES = Die Funktion ändert möglicherweise SQL-Daten.<br /><br /> Gibt für alle Funktionen READS und für alle gespeicherten Prozeduren MODIFIES zurück.|  
|IS_NULL_CALL|**nvarchar (** 10 **)**|Zeigt an, ob die Routine aufgerufen wird, wenn eines der Argumente NULL ist.|  
|SQL_PATH|**nvarchar (** 128 **)**|NULL. Für die zukünftige Verwendung reserviert.|  
|SCHEMA_LEVEL_ROUTINE|**nvarchar (** 10 **)**|Gibt YES zurück, wenn es sich um eine Funktion auf Schemaebene handelt, oder NO, wenn es keine Funktion auf Schemaebene ist.<br /><br /> Es wird immer YES zurückgegeben.|  
|MAX_DYNAMIC_RESULT_SETS|**smallint**|Maximale Anzahl der dynamischen Resultsets, die durch die Routine zurückgegeben werden.<br /><br /> Gibt bei Funktionen 0 zurück.|  
|IS_USER_DEFINED_CAST|**nvarchar (** 10 **)**|Gibt YES zurück, wenn es sich um eine benutzerdefinierte Typumwandlungsfunktion handelt, oder NO, wenn es keine benutzerdefinierte Typumwandlungsfunktion ist.<br /><br /> Es wird immer NO zurückgegeben.|  
|IS_IMPLICITLY_INVOCABLE|**nvarchar (** 10 **)**|Gibt YES zurück, wenn die Routine implizit aufgerufen werden kann, und NO, wenn die Funktion nicht implizit aufgerufen werden kann.<br /><br /> Es wird immer NO zurückgegeben.|  
|CREATED|**datetime**|Zeitpunkt, zu dem die Routine erstellt wurde.|  
|LAST_ALTERED|**datetime**|Zeitpunkt der letzten Änderung der Funktion.|  
  
## <a name="see-also"></a>Weitere Informationen  
 [System Sichten &#40;Transact-SQL-&#41;](https://msdn.microsoft.com/library/35a6161d-7f43-4e00-bcd3-3091f2015e90)   
 [Informations Schema Sichten &#40;Transact-SQL-&#41;](~/relational-databases/system-information-schema-views/system-information-schema-views-transact-sql.md)   
 [sys. Columns &#40;Transact-SQL-&#41;](../../relational-databases/system-catalog-views/sys-columns-transact-sql.md)   
 [sys. Objects &#40;Transact-SQL-&#41;](../../relational-databases/system-catalog-views/sys-objects-transact-sql.md)   
 [sys. Procedures &#40;Transact-SQL-&#41;](../../relational-databases/system-catalog-views/sys-procedures-transact-sql.md)   
 [sys.sql_modules &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-sql-modules-transact-sql.md)  
  
  
