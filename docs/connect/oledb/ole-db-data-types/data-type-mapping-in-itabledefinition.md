---
title: Datentypzuordnung itabledefinition | Microsoft-Dokumentation
description: Datentypzuordnung zu ITableDefinition
ms.custom: ''
ms.date: 06/14/2018
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: connectivity
ms.topic: reference
helpviewer_keywords:
- mapping data types [OLE DB]
- OLE DB Driver for SQL Server, data types
- ITableDefinition interface
- DBCOLUMNDESC structure
- data types [OLE DB]
- CreateTable function
- OLE DB, data types
author: pmasl
ms.author: pelopes
manager: jroth
ms.openlocfilehash: 5dcd4b33121d5459120572b2b31de413106aeeda
ms.sourcegitcommit: ad2e98972a0e739c0fd2038ef4a030265f0ee788
ms.translationtype: MTE75
ms.contentlocale: de-DE
ms.lasthandoff: 06/07/2019
ms.locfileid: "66775597"
---
# <a name="data-type-mapping-in-itabledefinition"></a>Datentypzuordnung zu ITableDefinition
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

[!INCLUDE[Driver_OLEDB_Download](../../../includes/driver_oledb_download.md)]

  Beim Erstellen von Tabellen mit der Funktion **ITableDefinition::CreateTable** kann der Consumer des OLE DB-Treibers für SQL Server [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]-Datentypen im Element *pwszTypeName* des DBCOLUMNDESC-Arrays angeben, das der Funktion übergeben wird. Gibt der Consumer den Datentyp einer Spalte namentlich an, wird die OLE DB-Datentypzuordnung ignoriert, die durch das *wType*-Element der DBCOLUMNDESC-Struktur dargestellt wird.  
  
 Wenn die Datentypen neuer Spalten mit OLE DB-Datentypen mithilfe des Elements *wType* der DBCOLUMNDESC-Struktur angegeben werden, dann ordnet der OLE DB-Treiber für SQL Server die OLE DB-Datentypen wie folgt zu.  
  
|OLE DB-Datentyp|SQL Server<br /><br /> Datentyp|Zusätzliche Informationen|  
|----------------------|------------------------------|----------------------------|  
|DBTYPE_BOOL|**bit**||  
|DBTYPE_BYTES|**binary**, **varbinary**, **image** oder **varbinary(max)**|Der OLE DB-Treiber für SQL Server überprüft die *UlColumnSize* Mitglied der DBCOLUMNDESC-Struktur. Basierend auf den Wert ein, und Version der [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Instanz, die OLE DB-Treiber für SQL Server-den Typ, Karten **Image**.<br /><br /> Wenn der Wert von *ulColumnSize* kleiner als die maximale Länge einer Spalte des **binary**-Datentyps ist, dann überprüft der OLE DB-Treiber für SQL Server das Element *rgPropertySets* der DBCOLUMNDESC-Struktur. Wenn DBPROP_COL_FIXEDLENGTH den Wert VARIANT_TRUE aufweist, ordnet der OLE DB-Treiber für SQL Server den Typ zu **binäre**. Wenn der Wert der Eigenschaft VARIANT_FALSE ist, ordnet der OLE DB-Treiber für SQL Server den Typ zu **Varbinary**. In jedem Fall bestimmt das Element *ulColumnSize* der DBCOLUMNDESC-Struktur die Breite der SQL Server-Spalte, die erstellt wird.|  
|DBTYPE_CY|**money**||  
|DBTYPE_DBTIMESTAMP|**datetime2**||  
|DBTYPE_GUID|**uniqueidentifier**||  
|DBTYPE_I2|**smallint**||  
|DBTYPE_I4|**ssNoversion**||  
|DBTYPE_I8|**bigint**||
|DBTYPE_NUMERIC|**numeric**|Der OLE DB-Treiber für SQL Server überprüft das Element *bPrecision* und das Element *bScale* der DBCOLUMDESC-Struktur, um Genauigkeit und Dezimalstellen der Spalte **numeric** zu bestimmen.|  
|DBTYPE_R4|**real**||  
|DBTYPE_R8|**float**||  
|DBTYPE_STR|**char**, **varchar**, **text** oder **varchar(max)**|Der OLE DB-Treiber für SQL Server überprüft die *UlColumnSize* Mitglied der DBCOLUMNDESC-Struktur. Basierend auf den Wert und die Version der [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Instanz, die OLE DB-Treiber für SQL Server-den Typ, Karten **Text**.<br /><br /> Wenn der Wert von *ulColumnSize* kleiner ist als die maximale Länge einer Spalte eines Datentyps für Multibyte-Zeichendaten ist, dann überprüft der OLE DB-Treiber für SQL Server das Element *rgPropertySets* von DBCOLUMNDESC. Wenn DBPROP_COL_FIXEDLENGTH den Wert VARIANT_TRUE aufweist, ordnet der OLE DB-Treiber für SQL Server den Typ zu **Char**. Wenn der Wert der Eigenschaft VARIANT_FALSE ist, ordnet der OLE DB-Treiber für SQL Server den Typ zu **Varchar**. In jedem Fall bestimmt das Element *ulColumnSize* der DBCOLUMNDESC-Struktur die Breite der [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]-Spalte, die erstellt wird.|  
|DBTYPE_UDT|**UDT**|Die folgenden Informationen werden von **DBCOLUMNDESC**-Strukturen verwendet, die von **ITableDefinition::CreateTable** verwendet werden, wenn UDT-Spalten erforderlich sind:<br /><br /> *PwSzTypeName* wird ignoriert.<br /><br /> *RgPropertySets* müssen eine **DBPROPSET_SQLSERVERCOLUMN** -Eigenschaft festgelegt wird, wie im Abschnitt zum beschrieben **DBPROPSET_SQLSERVERCOLUMN**im [Defined Types ](../../oledb/features/using-user-defined-types.md).|  
|DBTYPE_UI1|**tinyint**||  
|DBTYPE_VARIANT|**sql_variant**||
|DBTYPE_WSTR|**nchar**, **nvarchar**, **ntext** oder **nvarchar(max)**|Der OLE DB-Treiber für SQL Server überprüft die *UlColumnSize* Mitglied der DBCOLUMNDESC-Struktur. Basierend auf dem Wert, ordnet der OLE DB-Treiber für SQL Server den Typ, **Ntext**.<br /><br /> Wenn der Wert von *ulColumnSize* kleiner ist als die maximale Länge einer Spalte eines Datentyps für Unicode-Zeichendaten ist, dann überprüft der OLE DB-Treiber für SQL Server das Element *rgPropertySets* von DBCOLUMNDESC. Wenn DBPROP_COL_FIXEDLENGTH den Wert VARIANT_TRUE aufweist, ordnet der OLE DB-Treiber für SQL Server den Typ zu **Nchar**. Wenn der Wert der Eigenschaft VARIANT_FALSE ist, ordnet der OLE DB-Treiber für SQL Server den Typ zu **Nvarchar**. In jedem Fall bestimmt das Element *ulColumnSize* der DBCOLUMNDESC-Struktur die Breite der [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]-Spalte, die erstellt wird.|  
|DBTYPE_XML|**XML**||  

> [!NOTE]  
>  Beim Erstellen einer neuen Tabelle ordnet der OLE DB-Treiber für SQL Server nur die in der vorstehenden Tabelle angegebenen Enumerationswerte für OLE DB-Datentypen zu. Durch den Versuch, eine Tabelle mit einer Spalte eines anderen OLE DB-Datentyps zu erstellen, wird ein Fehler erzeugt.  

## <a name="see-also"></a>Weitere Informationen  
 [Datentypen &#40;OLE-DB&#41;](../../oledb/ole-db-data-types/data-types-ole-db.md)  
  
  
