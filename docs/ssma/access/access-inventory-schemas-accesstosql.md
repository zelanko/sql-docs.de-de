---
description: Zugreifen auf Inventur Schemas (Access Token-SQL)
title: Zugreifen auf Inventur Schemas (Access Token) | Microsoft-Dokumentation
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
author: nahk-ivanov
ms.author: alexiva
ms.openlocfilehash: 593c36c193b95d1484f3d478018992ea130d5417
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/17/2020
ms.locfileid: "88418636"
---
# <a name="access-inventory-schemas-accesstosql"></a>Zugreifen auf Inventur Schemas (Access Token-SQL)
In den folgenden Abschnitten werden die Tabellen beschrieben, die von SSMA beim Exportieren von Zugriffs Schemas in erstellt werden [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
## <a name="databases"></a>Datenbanken  
Daten Bank Metadaten werden in die **SSMA_Access_InventoryDatabases** Tabelle exportiert. Diese Tabelle enthält die folgenden Spalten:  
  
|Spaltenname|Datentyp|Beschreibung|  
|---------------|-------------|---------------|  
|**DatabaseID**|**uniqueidentifier**|Eine GUID, die jede Datenbank eindeutig identifiziert. Diese Spalte ist auch der Primärschlüssel für die Tabelle.|  
|**DatabaseName**|**nvarchar(4000)**|Der Name der Access-Datenbank.|  
|**Export Zeit**|**datetime**|Das Datum und die Uhrzeit, zu denen diese Metadaten von SSMA erstellt wurden.|  
|**FilePath**|**nvarchar(4000)**|Der vollständige Pfad und der Dateiname der Access-Datenbank.|  
|**Filesize**|**bigint**|Die Größe der Access-Datenbank in KB.|  
|**Dateibesitzer**|**nvarchar(4000)**|Das Windows-Konto, das als Besitzer der Access-Datenbank angegeben wird.|  
|**DateCreated**|**datetime**|Das Datum und die Uhrzeit der Erstellung der Access-Datenbank.|  
|**DateModified**|**datetime**|Das Datum und die Uhrzeit der letzten Änderung der Access-Datenbank.|  
|**Tabellen Anzahl**|**int**|Die Anzahl der Tabellen in der Access-Datenbank.|  
|**Queriescount**|**int**|Die Anzahl der Abfragen in der Access-Datenbank.|  
|**Formscount**|**int**|Die Anzahl der Formulare in der Access-Datenbank.|  
|**Modulescount**|**int**|Die Anzahl der Module in der Access-Datenbank.|  
|**Reportscount**|**int**|Die Anzahl der Berichte in der Access-Datenbank.|  
|**Macroscount**|**int**|Die Anzahl der Makros in der Access-Datenbank.|  
|**AccessVersion**|**nvarchar(4000)**|Die Zugriffs Version der Datenbank.|  
|**Sortierung**|**nvarchar(4000)**|Die Sortierung der Access-Datenbank. Sortierungen bestimmen, wie eine Datenbank Zeichen folgen sortiert und vergleicht.|  
|**Jetversion**|**nvarchar(4000)**|Die Jet-Datenbank-Engine-Version. Access-Datenbanken verwenden das zugrunde liegende Jet-Datenbankmodul.|  
|**Isupdatable**|**bit**|Gibt an, ob die Datenbank aktualisiert werden kann. Wenn der Wert 1 ist, ist die Datenbank aktualisierbar. Wenn der Wert 0 ist, ist die Datenbank schreibgeschützt.|  
|**QueryTimeout**|**int**|Der konfigurierte ODBC-Abfrage Timeout Wert für die Datenbank (in Sekunden). Der Standardwert ist 60 Sekunden.|  
  
## <a name="tables"></a>Tabellen  
Tabellen Metadaten werden in die **SSMA_Access_InventoryTables** Tabelle exportiert. Diese Tabelle enthält die folgenden Spalten:  
  
|Spaltenname|Datentyp|Beschreibung|  
|---------------|-------------|---------------|  
|**DatabaseID**|**uniqueidentifier**|Identifiziert die Datenbank, die diese Tabelle enthält.|  
|**TableID**|**uniqueidentifier**|Eine GUID, die die Tabelle eindeutig identifiziert. Diese Spalte ist auch der Primärschlüssel für die Tabelle.|  
|**TableName**|**nvarchar(4000)**|Der Name der Tabelle.|  
|**RowsCount**|**int**|Die Anzahl der Zeilen in der Tabelle.|  
|**ValidationRule**|**nvarchar(4000)**|Die Regel, die gültige Eingaben für die Tabelle definiert. Wenn keine Validierungs Regel vorhanden ist, enthält das Feld eine leere Zeichenfolge.|  
|**Linkedtable**|**nvarchar(4000)**|Eine andere Tabelle (falls vorhanden), die mit der Tabelle verknüpft ist. Durch das Verknüpfen von Tabellen werden Ergänzungen, Löschungen und Aktualisierungen der anderen Tabelle mithilfe dieser Tabelle ermöglicht.|  
|**ExternalSource**|**nvarchar(4000)**|Die Datenquelle, sofern vorhanden, die der Tabelle zugeordnet ist. Wenn eine Tabelle verknüpft ist, wird in diesem Feld eine externe Datenquelle angegeben.|  
  
## <a name="columns"></a>Spalten  
Spalten Metadaten werden in die **SSMA_Access_InventoryColumns** Tabelle exportiert. Diese Tabelle enthält die folgenden Spalten:  
  
|Spaltenname|Datentyp|Beschreibung|  
|---------------|-------------|---------------|  
|**DatabaseID**|**uniqueidentifier**|Identifiziert die Datenbank, die diese Spalte enthält.|  
|**TableID**|**uniqueidentifier**|Identifiziert die Tabelle, die diese Spalte enthält.|  
|**ColumnId**|**int**|Eine inkrementellen Ganzzahl, die die Spalte identifiziert. **ColumnID** ist der Primärschlüssel für die Tabelle.|  
|**ColumnName**|**nvarchar(4000)**|Der Name der Spalte.|  
|**IsNullable**|**bit**|Gibt an, ob die Spalte NULL-Werte enthalten kann. Wenn der Wert 1 ist, kann die Spalte NULL-Werte enthalten. Wenn der Wert 0 ist, darf die Spalte keine NULL-Werte enthalten. Beachten Sie, dass die Validierungs Regel auch zum Verhindern von NULL-Werten verwendet werden kann.|  
|**DataType**|**nvarchar(4000)**|Der Zugriffs Datentyp der Spalte, z. b. **Text** oder **Long**.|  
|**IsAutoIncrement**|**bit**|Gibt an, ob die Spalte automatisch ganzzahlige Werte erhöht. Wenn der Wert 1 ist, werden die ganzen Zahlen automatisch inkrementiert.|  
|**Ordinal**|**smallint**|Die Reihenfolge der Spalte in der Tabelle, beginnend bei Null.|  
|**DefaultValue**|**nvarchar(4000)**|Der Standardwert für die Spalte.|  
|**ValidationRule**|**nvarchar(4000)**|Die Regel, die zum Überprüfen von Daten verwendet wird, die in der Spalte hinzugefügt oder aktualisiert wurden.|  
  
## <a name="indexes"></a>Indizes  
Index Metadaten werden in die **SSMA_Access_InventoryIndexes** Tabelle exportiert. Diese Tabelle enthält die folgenden Spalten:  
  
|Spaltenname|Datentyp|Beschreibung|  
|---------------|-------------|---------------|  
|**DatabaseID**|**uniqueidentifier**|Identifiziert die Datenbank, die diesen Index enthält.|  
|**TableID**|**uniqueidentifier**|Identifiziert die Tabelle, die diesen Index enthält.|  
|**IndexId**|**int**|Eine inkrementellen Ganzzahl, die den Index identifiziert. Diese Spalte ist der Primärschlüssel für die Tabelle.|  
|**IndexName**|**nvarchar(4000)**|Der Name des Index.|  
|**Columnsincluded**|**nvarchar(4000)**|Listet die Spalten auf, die im Index enthalten sind. Die Spaltennamen werden durch ein Semikolon getrennt.|  
|**IsUnique**|**bit**|Gibt an, ob jedes Element im Index eindeutig sein muss. Bei einem mehrspaltigen Index muss die Kombination der Werte eindeutig sein. Wenn der Wert 1 ist, erzwingt der Index eindeutige Werte.|  
|**Ispk**|**bit**|Gibt an, ob der Index automatisch als Teil der Definition des Primärschlüssels erstellt wurde.|  
|**IsClustered**|**bit**|Gibt an, ob der Index gruppiert ist. Ein gruppierter Index ordnet den physischen Speicher der Daten neu an. Eine Tabelle kann nur über einen gruppierten Index verfügen.|  
  
## <a name="foreign-keys"></a>Fremdschlüssel  
Fremdschlüssel Metadaten werden in die **SSMA_Access_InventoryForeignKeys** Tabelle exportiert. Diese Tabelle enthält die folgenden Spalten:  
  
|Spaltenname|Datentyp|Beschreibung|  
|---------------|-------------|---------------|  
|**DatabaseID**|**uniqueidentifier**|Identifiziert die Datenbank, die diesen Fremdschlüssel enthält.|  
|**TableID**|**uniqueidentifier**|Gibt die Tabelle an, die diesen Fremdschlüssel enthält.|  
|**Fremdschlüssel-ID**|**int**|Eine inkrementellen Ganzzahl, die den Fremdschlüssel identifiziert. Diese Spalte ist der Primärschlüssel für die Tabelle.|  
|**Fremdschlüssel Name**|**nvarchar(4000)**|Der Name des Index.|  
|**Referencedtableid**|**uniqueidentifier**|Identifiziert die Tabelle, die die Quell Spalten enthält.|  
|**Sourcecolumschlag**|**nvarchar(4000)**|Listet die Fremdschlüssel Spalte oder-Spalten auf.|  
|**ReferencedColumns**|**nvarchar(4000)**|Listet die Primärschlüssel Spalten auf, auf die vom Fremdschlüssel verwiesen wird.|  
|**Iscascadeforupdate**|**bit**|Gibt an, dass alle Zeilen, die auf diesen Schlüsselwert verweisen, ebenfalls aktualisiert werden, wenn der Primärschlüssel Wert aktualisiert wird.|  
|**Iscascadefordelete**|**bit**|Gibt an, dass alle Zeilen, die auf diesen Schlüsselwert verweisen, ebenfalls gelöscht werden, wenn der Primärschlüssel Wert gelöscht wird.|  
|**Iserzwungen**|**bit**|Gibt an, dass die FOREIGN KEY-Einschränkung erzwungen wird.|  
  
## <a name="queries"></a>Abfragen  
Abfrage Metadaten werden in die **SSMA_Access_InventoryQueries** Tabelle exportiert. Diese Tabelle enthält die folgenden Spalten:  
  
|Spaltenname|Datentyp|Beschreibung|  
|---------------|-------------|---------------|  
|**DatabaseID**|**uniqueidentifier**|Identifiziert die Datenbank, in der diese Abfrage enthalten ist.|  
|**QueryId**|**int**|Eine inkrementellen Ganzzahl, die die Abfrage identifiziert. Diese Spalte ist der Primärschlüssel für die Tabelle.|  
|**QueryName**|**nvarchar(4000)**|Der Name der Abfrage.|  
|**QueryText**|**nvarchar(4000)**|Der SQL-Abfrage Code, z. b. eine SELECT-Anweisung.|  
|**Isupdatable**|**bit**|Gibt an, ob die Abfrage aktualisierbar oder schreibgeschützt ist.|  
|**QueryType**|**nvarchar(4000)**|Gibt den Typ der Abfrage an, z. b. **Select** oder **setoperation**.|  
|**ExternalSource**|**nvarchar(4000)**|Wenn die Abfrage auf eine externe Datenquelle verweist, ist dies die Verbindungs Zeichenfolge, die von der Abfrage verwendet wird.|  
  
## <a name="forms"></a>Formulare  
Formular Metadaten werden in die **SSMA_Access_InventoryForms** Tabelle exportiert. Diese Tabelle enthält die folgenden Spalten:  
  
|Spaltenname|Datentyp|Beschreibung|  
|---------------|-------------|---------------|  
|**DatabaseID**|**uniqueidentifier**|Identifiziert die Datenbank, die dieses Formular enthält.|  
|**Formid**|**int**|Eine inkrementellen Ganzzahl, die das Formular bezeichnet. Diese Spalte ist der Primärschlüssel für die Tabelle.|  
|**Formular Name**|**nvarchar(4000)**|Der Name des Formulars.|  
  
## <a name="macros"></a>Makros  
Makro Metadaten werden in die **SSMA_Access_InventoryMacros** Tabelle exportiert. Diese Tabelle enthält die folgenden Spalten:  
  
|Spaltenname|Datentyp|Beschreibung|  
|---------------|-------------|---------------|  
|**DatabaseID**|**uniqueidentifier**|Identifiziert die Datenbank, die das Makro enthält.|  
|**Makroid**|**int**|Eine inkrementellen Ganzzahl, die das Makro identifiziert. Diese Spalte ist der Primärschlüssel für die Tabelle.|  
|**MacroName**|**nvarchar(4000)**|Der Name des Makros.|  
  
## <a name="reports"></a>Berichte  
Die Berichts Metadaten werden in die **SSMA_Access_InventoryReports** Tabelle exportiert. Diese Tabelle enthält die folgenden Spalten:  
  
|Spaltenname|Datentyp|Beschreibung|  
|---------------|-------------|---------------|  
|**DatabaseID**|**uniqueidentifier**|Identifiziert die Datenbank, die den Bericht enthält.|  
|**ReportId**|**int**|Eine inkrementellen Ganzzahl, die den Bericht identifiziert. Diese Spalte ist der Primärschlüssel für die Tabelle.|  
|**ReportName**|**nvarchar(4000)**|Der Berichtsname.|  
  
## <a name="modules"></a>Module  
Modul Metadaten werden in die **SSMA_Access_InventoryModules** Tabelle exportiert. Diese Tabelle enthält die folgenden Spalten:  
  
|Spaltenname|Datentyp|Beschreibung|  
|---------------|-------------|---------------|  
|**DatabaseID**|**uniqueidentifier**|Identifiziert die Datenbank, die das Modul enthält.|  
|**ModuleID**|**int**|Eine inkrementellen Ganzzahl, die das Modul identifiziert. Diese Spalte ist der Primärschlüssel für die Tabelle.|  
|**ModuleName**|**nvarchar(4000)**|Der Name des Moduls.|  
  
## <a name="see-also"></a>Weitere Informationen  
[Exportieren eines Access-Inventars](exporting-an-access-inventory-accesstosql.md)  
  
