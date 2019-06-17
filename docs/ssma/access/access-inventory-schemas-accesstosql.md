---
title: Zugriff auf Inventory Schemas (AccessToSQL) | Microsoft-Dokumentation
ms.prod: sql
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.technology: ssma
ms.topic: conceptual
helpviewer_keywords:
- columns table
- databases table
- exported metadata
- exporting, schemas of exported metadata
- foreign keys table
- forms table
- indexes, table
- inventory schemas
- macros table
- modules table
- queries table
- reference, inventory schemas
- reports table
- schemas of exported metadata
- schemas, exported metadata
- SSMA_Access_InventoryColumns
- SSMA_Access_InventoryDatabases
- SSMA_Access_InventoryForeignKeys
- SSMA_Access_InventoryForms
- SSMA_Access_InventoryIndexes
- SSMA_Access_InventoryMacros
- SSMA_Access_InventoryModules
- SSMA_Access_InventoryQueries
- SSMA_Access_InventoryReports
- SSMA_Access_InventoryTables
- tables, inventory
ms.assetid: fdd3cff2-4d62-4395-8acf-71ea8f17f524
author: Shamikg
ms.author: Shamikg
manager: craigg
ms.openlocfilehash: 71a52a619ba2a3c16c372021181b90bae72ccfe7
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "62759706"
---
# <a name="access-inventory-schemas-accesstosql"></a>Access Inventory Schemas (AccessToSQL)
Die folgenden Abschnitte beschreiben die Tabellen, die vom SSMA, beim Exportieren von Schemas Zugriff erstellt werden [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
## <a name="databases"></a>Datenbanken  
Datenbank-Metadaten exportiert wird, um die **SSMA_Access_InventoryDatabases** Tabelle. Diese Tabelle enthält die folgenden Spalten:  
  
|Spaltenname|Datentyp|Description|  
|---------------|-------------|---------------|  
|**DatabaseId**|**uniqueidentifier**|Eine GUID, die jede Datenbank eindeutig identifiziert. Diese Spalte wird auch der primäre Schlüssel für die Tabelle.|  
|**DatabaseName**|**nvarchar(4000)**|Der Name der Access-Datenbank.|  
|**ExportTime**|**datetime**|Das Datum und Uhrzeit, die diese Metadaten von SSMA erstellt wurde.|  
|**FilePath**|**nvarchar(4000)**|Der vollständige Pfad und Name der Access-Datenbank.|  
|**FileSize**|**bigint**|Die Größe der Access-Datenbank in KB.|  
|**FileOwner**|**nvarchar(4000)**|Das Windows-Konto, das als Besitzer der Access-Datenbank angegeben ist.|  
|**DateCreated**|**datetime**|Das Datum und Uhrzeit der Erstellung die Access-Datenbank.|  
|**DateModified**|**datetime**|Das Datum und Uhrzeit der letzten die Access-Datenbank Änderung.|  
|**TablesCount**|**int**|Die Anzahl der Tabellen in der Access-Datenbank.|  
|**QueriesCount**|**int**|Die Anzahl der Abfragen in der Access-Datenbank.|  
|**FormsCount**|**int**|Die Anzahl der Formulare in der Access-Datenbank.|  
|**ModulesCount**|**int**|Die Anzahl der Module in der Access-Datenbank.|  
|**ReportsCount**|**int**|Die Anzahl der Berichte in der Access-Datenbank.|  
|**MacrosCount**|**int**|Die Anzahl von Makros in der Access-Datenbank.|  
|**AccessVersion**|**nvarchar(4000)**|Die Access-Version der Datenbank.|  
|**Sortierung**|**nvarchar(4000)**|Die Sortierung der Access-Datenbank. Sortierungen bestimmen, wie eine Datenbank sortiert und vergleicht Zeichenfolgen.|  
|**JetVersion**|**nvarchar(4000)**|Die Jet-Datenbank-Engine-Version. Access-Datenbanken verwenden die zugrunde liegenden Jet-Datenbank-Engine.|  
|**IsUpdatable**|**bit**|Gibt an, wenn die Datenbank aktualisiert werden kann. Wenn der Wert 1 ist, kann die Datenbank aktualisiert werden. Wenn der Wert 0 ist, ist die Datenbank schreibgeschützt.|  
|**QueryTimeout**|**int**|Konfigurierte ODBC-Wert für das Abfragetimeout für die Datenbank, in Sekunden. Der Standardwert ist 60 Sekunden.|  
  
## <a name="tables"></a>Tabellen  
Tabellenmetadaten exportiert wird, um die **SSMA_Access_InventoryTables** Tabelle. Diese Tabelle enthält die folgenden Spalten:  
  
|Spaltenname|Datentyp|Description|  
|---------------|-------------|---------------|  
|**DatabaseId**|**uniqueidentifier**|Identifiziert die Datenbank, die diese Tabelle enthält.|  
|**TableId**|**uniqueidentifier**|Eine GUID, die in der Tabelle eindeutig identifiziert. Diese Spalte wird auch der primäre Schlüssel für die Tabelle.|  
|**TableName**|**nvarchar(4000)**|Der Name der Tabelle.|  
|**RowsCount**|**int**|Anzahl der Zeilen in der Tabelle.|  
|**ValidationRule**|**nvarchar(4000)**|Die Regel, die gültige Eingabe für die Tabelle definiert. Wenn keine Gültigkeitsprüfungsregel vorhanden ist, wird das Feld eine leere Zeichenfolge enthalten.|  
|**LinkedTable**|**nvarchar(4000)**|Eine andere Tabelle, sofern vorhanden, die mit der Tabelle verknüpft ist. Verknüpfen von Tabellen kann Hinzufügungen, löschungen und Updates für die andere Tabelle mit dieser Tabelle.|  
|**ExternalSource**|**nvarchar(4000)**|Die Datenquelle ist ggf., die der Tabelle zugeordnet. Wenn es sich bei eine Tabelle verknüpft ist, hat dies eine externe Datenquelle, die in diesem Feld angegeben.|  
  
## <a name="columns"></a>Spalte  
In Metadaten exportiert die **SSMA_Access_InventoryColumns** Tabelle. Diese Tabelle enthält die folgenden Spalten:  
  
|Spaltenname|Datentyp|Description|  
|---------------|-------------|---------------|  
|**DatabaseId**|**uniqueidentifier**|Identifiziert die Datenbank, die diese Spalte enthält.|  
|**TableId**|**uniqueidentifier**|Identifiziert die Tabelle, die diese Spalte enthält.|  
|**ColumnId**|**int**|Inkrementelle eine ganze Zahl, die die Spalte identifiziert. **ColumnId** ist der Primärschlüssel für die Tabelle.|  
|**ColumnName**|**nvarchar(4000)**|Name der Spalte.|  
|**IsNullable**|**bit**|Gibt an, wenn die Spalte null-Werte enthalten kann. Wenn der Wert 1 ist, kann die Spalte null-Werte enthalten. Wenn der Wert 0 ist, kann nicht in die Spalte null-Werte enthalten. Beachten Sie, dass die Validierungsregel auch verwendet werden kann, um zu verhindern, dass null-Werte.|  
|**DataType**|**nvarchar(4000)**|Der Access-Datentyp der Spalte, wie z. B. **Text** oder **lange**.|  
|**IsAutoIncrement**|**bit**|Gibt an, ob es sich bei ganzzahligen Werten in der Spalte automatisch erhöht wird. Wenn der Wert 1 ist, werden die ganzen Zahlen automatisch inkrementiert.|  
|**Ordinal**|**smallint**|Die Reihenfolge der Spalte in der Tabelle, beginnend mit 0 (null).|  
|**DefaultValue**|**nvarchar(4000)**|Der Standardwert für die Spalte.|  
|**ValidationRule**|**nvarchar(4000)**|Die Regel, die zum Überprüfen von Daten, die hinzugefügt oder aktualisiert werden, in der Spalte verwendet wird.|  
  
## <a name="indexes"></a>Indizes  
Exportierten Metadaten für den Index der **SSMA_Access_InventoryIndexes** Tabelle. Diese Tabelle enthält die folgenden Spalten:  
  
|Spaltenname|Datentyp|Description|  
|---------------|-------------|---------------|  
|**DatabaseId**|**uniqueidentifier**|Identifiziert die Datenbank, die diesen Index enthält.|  
|**TableId**|**uniqueidentifier**|Identifiziert die Tabelle, die diesen Index enthält.|  
|**IndexId**|**int**|Inkrementelle eine ganze Zahl, die im Index. Diese Spalte ist der primäre Schlüssel für die Tabelle.|  
|**IndexName**|**nvarchar(4000)**|Der Name des Index.|  
|**ColumnsIncluded**|**nvarchar(4000)**|Listet die Spalten, die im Index enthalten sind. Die Spaltennamen werden durch ein Semikolon getrennt.|  
|**IsUnique**|**bit**|Gibt an, wenn jedes Element im Index eindeutig sein muss. Für einen mehrspaltigen Index muss die Kombination der Werte eindeutig sein. Wenn der Wert 1 ist, erzwingt der Index eindeutige Werte.|  
|**IsPK**|**bit**|Gibt an, wenn der Index automatisch als Teil der Definition des primären Schlüssels erstellt wurde.|  
|**IsClustered**|**bit**|Gibt an, wenn der Index gruppiert ist. Ein gruppierter Index sortiert die physische Speicherung von Daten. Eine Tabelle kann nur ein gruppierten Index aufweisen.|  
  
## <a name="foreign-keys"></a>Fremdschlüssel  
Foreign Key-Metadaten exportiert wird, um die **SSMA_Access_InventoryForeignKeys** Tabelle. Diese Tabelle enthält die folgenden Spalten:  
  
|Spaltenname|Datentyp|Description|  
|---------------|-------------|---------------|  
|**DatabaseId**|**uniqueidentifier**|Identifiziert die Datenbank, die diese Fremdschlüssel enthält.|  
|**TableId**|**uniqueidentifier**|Identifiziert die Tabelle, die diese Fremdschlüssel enthält.|  
|**ForeignKeyId**|**int**|Inkrementelle eine ganze Zahl, die den Fremdschlüssel identifiziert. Diese Spalte ist der primäre Schlüssel für die Tabelle.|  
|**ForeignKeyName**|**nvarchar(4000)**|Der Name des Index.|  
|**ReferencedTableId**|**uniqueidentifier**|Identifiziert die Tabelle, die Quellspalten enthält.|  
|**SourceColumns**|**nvarchar(4000)**|Listet die foreign Key-Spalte oder Spalten.|  
|**ReferencedColumns**|**nvarchar(4000)**|Listet die Primärschlüsselspalte oder der Spalten, die vom Fremdschlüssel verwiesen werden.|  
|**IsCascadeForUpdate**|**bit**|Gibt an, wenn der Primärschlüsselwert aktualisiert wird, auch alle Zeilen, die auf, Schlüssel-Wert verweisen aktualisiert werden.|  
|**IsCascadeForDelete**|**bit**|Gibt an, wenn der Primärschlüsselwert gelöscht wird, werden alle Zeilen, die auf diese Schlüssel-Wert verweisen ebenfalls gelöscht.|  
|**IsEnforced**|**bit**|Gibt an, dass foreign Key-Einschränkung erzwungen wird.|  
  
## <a name="queries"></a>Abfragen  
Abfragen von Metadaten exportiert wird, um die **SSMA_Access_InventoryQueries** Tabelle. Diese Tabelle enthält die folgenden Spalten:  
  
|Spaltenname|Datentyp|Beschreibung|  
|---------------|-------------|---------------|  
|**DatabaseId**|**uniqueidentifier**|Identifiziert die Datenbank, die diese Abfrage enthält.|  
|**QueryId**|**int**|Inkrementelle eine ganze Zahl, die die Abfrage identifiziert. Diese Spalte ist der primäre Schlüssel für die Tabelle.|  
|**QueryName**|**nvarchar(4000)**|Der Name der Abfrage.|  
|**QueryText**|**nvarchar(4000)**|SQL-Abfrage-Code, z. B. eine SELECT-Anweisung.|  
|**IsUpdateable**|**bit**|Gibt an, wenn die Abfrage aktualisierbar oder schreibgeschützt ist.|  
|**QueryType**|**nvarchar(4000)**|Gibt den Typ der Abfrage, z. B. **wählen** oder **SetOperation**.|  
|**ExternalSource**|**nvarchar(4000)**|Wenn die Abfrage eine externen Datenquelle verweist, ist dies die Verbindungszeichenfolge, die von der Abfrage verwendet.|  
  
## <a name="forms"></a>Formulare  
In von Formularmetadaten exportiert die **SSMA_Access_InventoryForms** Tabelle. Diese Tabelle enthält die folgenden Spalten:  
  
|Spaltenname|Datentyp|Description|  
|---------------|-------------|---------------|  
|**DatabaseId**|**uniqueidentifier**|Identifiziert die Datenbank, die dieses Formular enthält.|  
|**FormId**|**int**|Inkrementelle eine ganze Zahl, die die Form identifiziert. Diese Spalte ist der primäre Schlüssel für die Tabelle.|  
|**FormName**|**nvarchar(4000)**|Der Name des Formulars.|  
  
## <a name="macros"></a>Makros  
Makro Metadaten exportiert wird, um die **SSMA_Access_InventoryMacros** Tabelle. Diese Tabelle enthält die folgenden Spalten:  
  
|Spaltenname|Datentyp|Beschreibung|  
|---------------|-------------|---------------|  
|**DatabaseId**|**uniqueidentifier**|Identifiziert die Datenbank, die das Makro enthält.|  
|**MacroId**|**int**|Inkrementelle eine ganze Zahl, die das Makro identifiziert. Diese Spalte ist der primäre Schlüssel für die Tabelle.|  
|**MacroName**|**nvarchar(4000)**|Der Name des Makros.|  
  
## <a name="reports"></a>Berichte  
Berichtsmetadaten exportiert wird, um die **SSMA_Access_InventoryReports** Tabelle. Diese Tabelle enthält die folgenden Spalten:  
  
|Spaltenname|Datentyp|Description|  
|---------------|-------------|---------------|  
|**DatabaseId**|**uniqueidentifier**|Identifiziert die Datenbank mit dem Bericht.|  
|**ReportId**|**int**|Inkrementelle eine ganze Zahl, die den Bericht identifiziert. Diese Spalte ist der primäre Schlüssel für die Tabelle.|  
|**Berichtsname**|**nvarchar(4000)**|Der Berichtsname.|  
  
## <a name="modules"></a>Module  
Metadaten des Moduls exportiert wird, um die **SSMA_Access_InventoryModules** Tabelle. Diese Tabelle enthält die folgenden Spalten:  
  
|Spaltenname|Datentyp|Description|  
|---------------|-------------|---------------|  
|**DatabaseId**|**uniqueidentifier**|Identifiziert die Datenbank, die das Modul enthält.|  
|**ModuleId**|**int**|Inkrementelle eine ganze Zahl, die das Modul identifiziert. Diese Spalte ist der primäre Schlüssel für die Tabelle.|  
|**ModuleName**|**nvarchar(4000)**|Der Name des Moduls.|  
  
## <a name="see-also"></a>Siehe auch  
[Exporting an Access Inventory (Exportieren eines Access-Inventars)](exporting-an-access-inventory-accesstosql.md)  
  
