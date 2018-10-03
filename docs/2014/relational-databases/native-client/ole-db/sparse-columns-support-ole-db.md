---
title: Unterstützung für Spalten mit geringer Dichte (OLE DB) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
ms.assetid: 918574b3-c62e-4937-9e5f-37310dedc8f9
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: b286ba7bde145a9a3676f38f329a8efbd932a4cf
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/02/2018
ms.locfileid: "48106383"
---
# <a name="sparse-columns-support-ole-db"></a>Unterstützung für Spalten mit geringer Dichte (OLE DB)
  Dieses Thema enthält Informationen über [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client OLE DB-Unterstützung für Spalten mit geringer Dichte. Weitere Informationen zu Sparsespalten finden Sie unter [Sparse Columns Support in SQL Server Native Client](../features/sparse-columns-support-in-sql-server-native-client.md). Ein Beispiel finden Sie unter [Anzeigen von Spalten- und Katalogmetadaten für Spalten mit geringer Dichte &#40;OLE DB&#41;](../../native-client-ole-db-how-to/display-column-and-catalog-metadata-for-sparse-columns-ole-db.md).  
  
## <a name="ole-db-statement-metadata"></a>OLE DB-Anweisungsmetadaten  
 Ab [!INCLUDE[ssKatmai](../../../includes/sskatmai-md.md)]ist ein neuer DBCOLUMNFLAGS-Flagwert, DBCOLUMNFLAGS_SS_ISCOLUMNSET, verfügbar. Dieser Wert sollte für Spalten festgelegt werden, die `column_set`-Werte sind. Das DBCOLUMNFLAGS-Flag abgerufen werden können, über die *DwFlags* -Parameters von IColumnsInfo:: GetColumnsInfo und die DBCOLUMN_FLAGS-Spalte des Rowsets von IColumnsRowset:: GetColumnsRowset zurückgegeben.  
  
## <a name="ole-db-catalog-metadata"></a>OLE DB-Katalogmetadaten  
 Zwei zusätzliche [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]-spezifische Spalten wurden zu DBSCHEMA_COLUMNS hinzugefügt.  
  
|Spaltenname|Datentyp|Wert/Kommentare|  
|-----------------|---------------|---------------------|  
|SS_IS_SPARSE|DBTYPE_BOOL|Wenn die Spalte eine Sparsespalte ist, weist sie den Wert VARIANT_TRUE auf, andernfalls den Wert VARIANT_FALSE.|  
|SS_IS_COLUMN_SET|DBTYPE_BOOL|Wenn die Spalte mit geringer Dichte ist `column_set` Spalte besitzt den Wert VARIANT_TRUE ist, andernfalls VARIANT_FALSE.|  
  
 Zwei zusätzliche Schemarowsets wurden ebenfalls hinzugefügt. Diese Rowsets verfügen über die gleiche Struktur wie DBSCHEMA_COLUMNS, geben aber andere Inhalte zurück. DBSCHEMA_COLUMNS_EXTENDED gibt alle Spalten zurück, unabhängig davon, ob sie Elemente von `column_set` sind. DBSCHEMA_SPARSE_COLUMN_SET gibt nur Spalten, die Elemente des Sparse- `column_set`.  
  
## <a name="ole-db-datatypecompatibility-behavior"></a>OLE DB DataTypeCompatibility-Verhalten  
 Verhalten mit `DataTypeCompatibility=80` (in der Verbindungszeichenfolge) ist mit einem [!INCLUDE[ssVersion2000](../../../includes/ssversion2000-md.md)]-Client konsistent:  
  
-   Die neuen Schemarowsets sind nicht sichtbar, und es gibt keine Zeilen für sie im Rowset der Schemarowsets.  
  
-   Neue Spalten im COLUMNS-Rowset sind nicht sichtbar.  
  
-   DBCOLUMNFLAGS_SS_ISCOLUMNSET wird nicht für `column_set`-Spalten festgelegt.  
  
-   DBCOMPUTEMODE_NOTCOMPUTED wird für `column_set`-Spalten festgelegt.  
  
## <a name="ole-db-support-for-sparse-columns"></a>OLE DB-Unterstützung für Spalten mit geringer Dichte  
 Die folgenden OLE DB-Schnittstellen wurden in [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client geändert, um Sparsespalten zu unterstützen:  
  
|Typ oder Elementfunktion|Description|  
|-----------------------------|-----------------|  
|IColumnsInfo::GetColumnsInfo|Ein neuer DBCOLUMNFLAGS-Flagwert DBCOLUMNFLAGS_SS_ISCOLUMNSET festgelegt ist, für die `column_set` Spalten in *DwFlags*.<br /><br /> DBCOLUMNFLAGS_WRITE wird für festgelegt `column_set` Spalten.|  
|IColumsRowset::GetColumnsRowset|Ein neuer DBCOLUMNFLAGS-Flagwert, DBCOLUMNFLAGS_SS_ISCOLUMNSET, wird festgelegt, für die `column_set` -Spalten in DBCOLUMN_FLAGS.<br /><br /> DBCOLUMN_COMPUTEMODE wird für `column_set`-Spalten auf DBCOMPUTEMODE_DYNAMIC festgelegt.|  
|IDBSchemaRowset::GetSchemaRowset|DBSCHEMA_COLUMNS gibt zwei neue Spalten zurück: SS_IS_COLUMN_SET und SS_IS_SPARSE.<br /><br /> DBSCHEMA_COLUMNS gibt nur Spalten, die keine Mitglieder sind eine `column_set`.<br /><br /> Zwei neue Schemarowsets wurden hinzugefügt: DBSCHEMA_COLUMNS_EXTENDED gibt alle Spalten zurück, unabhängig davon, ob sie eine geringe Dichte aufweisen oder Elemente von `column_set` sind. DBSCHEMA_SPARSE_COLUMN_SET gibt nur Spalten zurück, die Elemente eines `column_set` sind. Diese neuen Rowsets verfügen über die gleichen Spalten und die Einschränkungen wie DBSCHEMA_COLUMNS.|  
|IDBSchemaRowset::GetSchemas|IDBSchemaRowset::GetSchemas schließt die GUIDs für die neuen Rowsets DBSCHEMA_COLUMNS_EXTENDED und DBSCHEMA_SPARSE_COLUMN_SET in die Liste verfügbarer Schemarowsets ein.|  
|ICommand::Execute|Wenn **wählen \* aus** *Tabelle* wird verwendet, werden alle Spalten, die nicht Elemente des Sparse-sind zurückgegeben `column_set`, sowie eine XML-Spalte, die Werte aller nicht-Null-Spalten enthält, sind Elemente des Sparse- `column_set`, falls vorhanden.|  
|IOpenRowset::OpenRowset|IOpenRowset:: OPENROWSET gibt ein Rowset mit den gleichen Spalten wie ICommand:: Execute, mit einem **wählen \***  Abfrage in der gleichen Tabelle.|  
|ITableDefinition|Es gibt keine Änderungen an dieser Schnittstelle für Sparsespalten oder für `column_set`-Spalten. Anwendungen, die Schemaänderungen vornehmen müssen, müssen das entsprechende [!INCLUDE[tsql](../../../includes/tsql-md.md)] direkt ausführen.|  
  
## <a name="see-also"></a>Siehe auch  
 [SQL Server Native Client &#40;OLE DB&#41;](sql-server-native-client-ole-db.md)  
  
  
