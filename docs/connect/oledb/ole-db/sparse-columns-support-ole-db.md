---
title: Unterstützung für Spalten mit geringer Dichte (OLE DB) | Microsoft-Dokumentation
description: Unterstützung für Sparsespalten (OLE DB)
ms.custom: ''
ms.date: 06/12/2018
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.component: oledb|ole-db
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: reference
author: pmasl
ms.author: Pedro.Lopes
manager: craigg
ms.openlocfilehash: d2f4cd73d4d20d4b54573b300c5006bebd5fb6eb
ms.sourcegitcommit: 50838d7e767c61dd0b5e677b6833dd5c139552f2
ms.translationtype: MTE75
ms.contentlocale: de-DE
ms.lasthandoff: 07/18/2018
ms.locfileid: "39109002"
---
# <a name="sparse-columns-support-ole-db"></a>Unterstützung für Spalten mit geringer Dichte (OLE DB)
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

[!INCLUDE[Driver_OLEDB_Download](../../../includes/driver_oledb_download.md)]

  Dieses Thema enthält Informationen zu OLE DB-Treiber für SQL Server-Unterstützung für Spalten mit geringer Dichte. Weitere Informationen zu Sparsespalten finden Sie unter [Sparse Columns Support in OLE DB Driver for SQL Server (Unterstützung von Sparsespalten im OLE DB-Treiber für SQL Server)](../../oledb/features/sparse-columns-support-in-oledb-driver-for-sql-server.md). Ein Beispiel finden Sie unter [Anzeigen von Spalten- und Katalogmetadaten für Spalten mit geringer Dichte &#40;OLE DB&#41;](../../oledb/ole-db-how-to/display-column-and-catalog-metadata-for-sparse-columns-ole-db.md).  
  
## <a name="ole-db-statement-metadata"></a>OLE DB-Anweisungsmetadaten  
 Ab [!INCLUDE[ssKatmai](../../../includes/sskatmai-md.md)]ist ein neuer DBCOLUMNFLAGS-Flagwert, DBCOLUMNFLAGS_SS_ISCOLUMNSET, verfügbar. Dieser Wert sollte für Spalten festgelegt werden, die **column_set** -Werte sind. Das DBCOLUMNFLAGS-Flag abgerufen werden können, über die *DwFlags* -Parameters von IColumnsInfo:: GetColumnsInfo und die DBCOLUMN_FLAGS-Spalte des Rowsets von IColumnsRowset:: GetColumnsRowset zurückgegeben.  
  
## <a name="ole-db-catalog-metadata"></a>OLE DB-Katalogmetadaten  
 Zwei zusätzliche [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]-spezifische Spalten wurden zu DBSCHEMA_COLUMNS hinzugefügt.  
  
|Spaltenname|Datentyp|Wert/Kommentare|  
|-----------------|---------------|---------------------|  
|SS_IS_SPARSE|DBTYPE_BOOL|Wenn die Spalte eine Sparsespalte ist, weist sie den Wert VARIANT_TRUE auf, andernfalls den Wert VARIANT_FALSE.|  
|SS_IS_COLUMN_SET|DBTYPE_BOOL|Wenn die Spalte die **column_set** -Sparsespalte ist, weist sie den Wert VARIANT_TRUE auf, andernfalls den Wert VARIANT_FALSE.|  
  
 Zwei zusätzliche Schemarowsets wurden ebenfalls hinzugefügt. Diese Rowsets verfügen über die gleiche Struktur wie DBSCHEMA_COLUMNS, geben aber andere Inhalte zurück. DBSCHEMA_COLUMNS_EXTENDED gibt alle Spalten zurück, unabhängig davon, ob sie Elemente von **column_set** sind. DBSCHEMA_SPARSE_COLUMN_SET gibt nur Spalten zurück, die Elemente des Sparse-**column_set** sind.  
  
## <a name="ole-db-datatypecompatibility-behavior"></a>OLE DB DataTypeCompatibility-Verhalten  
 Das Verhalten mit **DataTypeCompatibility=80** (in der Verbindungszeichenfolge) entspricht dem eines [!INCLUDE[ssVersion2000](../../../includes/ssversion2000-md.md)]-Clients folgendermaßen:  
  
-   Die neuen Schemarowsets sind nicht sichtbar, und es gibt keine Zeilen für sie im Rowset der Schemarowsets.  
  
-   Neue Spalten im COLUMNS-Rowset sind nicht sichtbar.  
  
-   DBCOLUMNFLAGS_SS_ISCOLUMNSET wird nicht für **column_set** -Spalten festgelegt.  
  
-   DBCOMPUTEMODE_NOTCOMPUTED wird für **column_set** -Spalten festgelegt.  
  
## <a name="ole-db-support-for-sparse-columns"></a>OLE DB-Unterstützung für Spalten mit geringer Dichte  
 Die folgenden OLE DB-Schnittstellen, die in der OLE DB-Treiber für SQL Server zur Unterstützung von Spalten mit geringer Dichte geändert wurden:  
  
|Typ oder Elementfunktion|und Beschreibung|  
|-----------------------------|-----------------|  
|IColumnsInfo::GetColumnsInfo|Ein neuer DBCOLUMNFLAGS-Flagwert, DBCOLUMNFLAGS_SS_ISCOLUMNSET, wird für **column_set** -Spalten in *dwFlags*festgelegt.<br /><br /> DBCOLUMNFLAGS_WRITE wird für **column_set** -Spalten festgelegt.|  
|IColumsRowset::GetColumnsRowset|Ein neuer DBCOLUMNFLAGS-Flagwert, DBCOLUMNFLAGS_SS_ISCOLUMNSET, wird für **column_set** -Spalten in DBCOLUMN_FLAGS festgelegt.<br /><br /> DBCOLUMN_COMPUTEMODE wird für **column_set** -Spalten auf DBCOMPUTEMODE_DYNAMIC festgelegt.|  
|IDBSchemaRowset::GetSchemaRowset|DBSCHEMA_COLUMNS gibt zwei neue Spalten zurück: SS_IS_COLUMN_SET und SS_IS_SPARSE.<br /><br /> DBSCHEMA_COLUMNS gibt nur Spalten zurück, die keine Elemente eines **column_set**sind.<br /><br /> Zwei neue Schemarowsets wurden hinzugefügt: DBSCHEMA_COLUMNS_EXTENDED gibt alle Spalten zurück, unabhängig davon, ob sie eine geringe Dichte aufweisen oder Elemente von **column_set** sind. DBSCHEMA_SPARSE_COLUMN_SET gibt nur Spalten zurück, die Elemente eines **column_set**sind. Diese neuen Rowsets verfügen über die gleichen Spalten und die Einschränkungen wie DBSCHEMA_COLUMNS.|  
|IDBSchemaRowset::GetSchemas|IDBSchemaRowset::GetSchemas schließt die GUIDs für die neuen Rowsets DBSCHEMA_COLUMNS_EXTENDED und DBSCHEMA_SPARSE_COLUMN_SET in die Liste verfügbarer Schemarowsets ein.|  
|ICommand::Execute|Wenn **SELECT \* FROM** *Tabelle* verwendet wird, werden alle Spalten zurückgegeben, die keine Elemente der **column_set**-Sparsespalte sind, zuzüglich einer XML-Spalte, die Werte von allen Nicht-NULL-Spalten enthält, die Elemente der **column_set**-Sparsespalte sind (falls vorhanden).|  
|IOpenRowset::OpenRowset|IOpenRowset:: OPENROWSET gibt ein Rowset mit den gleichen Spalten wie ICommand:: Execute, mit einem **wählen \***  Abfrage in der gleichen Tabelle.|  
|ITableDefinition|Es gibt keine Änderungen an dieser Schnittstelle für Sparsespalten oder für **column_set** -Spalten. Anwendungen, die Schemaänderungen vornehmen müssen, müssen das entsprechende [!INCLUDE[tsql](../../../includes/tsql-md.md)] direkt ausführen.|  
  
## <a name="see-also"></a>Weitere Informationen finden Sie unter  
 [OLE DB-Treiber für SQL Server-Programmierung](../../oledb/ole-db/oledb-driver-for-sql-server-programming.md)  
  
  
