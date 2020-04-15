---
title: Datentypzuordnung in ITableDefinition | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- mapping data types [OLE DB]
- SQL Server Native Client OLE DB provider, data types
- ITableDefinition interface
- DBCOLUMNDESC structure
- data types [OLE DB]
- CreateTable function
- OLE DB, data types
ms.assetid: 13292d1f-c17e-4d11-bf98-3460a10cbb18
author: markingmyname
ms.author: maghan
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: d3e828efa513db1ace272e59379f77d063220290
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81297030"
---
# <a name="data-type-mapping-in-itabledefinition"></a>Datentypzuordnung zu ITableDefinition
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

  Beim Erstellen von Tabellen mithilfe der Funktion **ITableDefinition::CreateTable** kann der Consumer des [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] nativen Client-OLE-DB-Anbieters Datentypen im [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] *pwszTypeName-Member* des übergebenen DBCOLUMNDESC-Arrays angeben. Gibt der Consumer den Datentyp einer Spalte namentlich an, wird die OLE DB-Datentypzuordnung ignoriert, die durch das *wType*-Element der DBCOLUMNDESC-Struktur dargestellt wird.  
  
 Wenn Sie neue Spaltendatentypen mit OLE DB-Datentypen mithilfe des DBCOLUMNDESC-Struktur-wType-Members angeben, ordnet der *wType* [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] native Client-OLE-DB-Anbieter OLE DB-Datentypen wie folgt zu.  
  
|OLE DB-Datentyp|SQL Server<br /><br /> Datentyp|Zusätzliche Informationen|  
|----------------------|------------------------------|----------------------------|  
|DBTYPE_BOOL|**bit**||  
|DBTYPE_BYTES|**binary**, **varbinary**, **image** oder **varbinary(max)**|Der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] native Client-OLE-DB-Anbieter überprüft das *ulColumnSize-Member* der DBCOLUMNDESC-Struktur. Basierend auf dem Wert und [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Version der Instance ordnet der Native Client-OLE-DB-Anbieter den Typ dem **Image**zu.<br /><br /> Wenn der Wert von *ulColumnSize* kleiner als die maximale Länge [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] einer **binären** Datentypspalte ist, überprüft der native Client-OLE-DB-Anbieter den DBCOLUMNDESC *rgPropertySets-Member.* Wenn DBPROP_COL_FIXEDLENGTH VARIANT_TRUE [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ist, ordnet der Native Client OLE DB-Anbieter den Typ **binären**zu. Wenn der Wert der Eigenschaft [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] VARIANT_FALSE ist, ordnet der Native Client OLE DB-Anbieter den Typ **varbinary**zu. In jedem Fall bestimmt das Element *ulColumnSize* der DBCOLUMNDESC-Struktur die Breite der SQL Server-Spalte, die erstellt wird.|  
|DBTYPE_CY|**money**||  
|DBTYPE_DBTIMESTAMP|**datetime**||  
|DBTYPE_GUID|**UNIQUEIDENTIFIER**||  
|DBTYPE_I2|**SMALLINT**||  
|DBTYPE_I4|**int**||  
|DBTYPE_NUMERIC|**Numerischen**|Der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] native Client-OLE-DB-Anbieter überprüft die DBCOLUMDESC *bPrecision-* und *bScale-Member,* um die Genauigkeit und Skalierung für die **numerische** Spalte zu bestimmen.|  
|DBTYPE_R4|**real**||  
|DBTYPE_R8|**float**||  
|DBTYPE_STR|**char**, **varchar**, **text** oder **varchar(max)**|Der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] native Client-OLE-DB-Anbieter überprüft das *ulColumnSize-Member* der DBCOLUMNDESC-Struktur. Basierend auf dem Wert [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] und der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Version der Instance ordnet der Native Client OLE DB-Anbieter den Typ **text**zu.<br /><br /> Wenn der Wert von *ulColumnSize* kleiner als die maximale Länge einer Multibyte-Zeichendatentypspalte ist, überprüft der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] native Client-OLE-DB-Anbieter den DBCOLUMNDESC *rgPropertySets-Member.* Wenn DBPROP_COL_FIXEDLENGTH VARIANT_TRUE [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] wird, ordnet der Native Client OLE DB-Anbieter den Typ **char**zu. Wenn der Wert der Eigenschaft [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] VARIANT_FALSE ist, ordnet der Native Client OLE DB-Anbieter den Typ **varchar**zu. In jedem Fall bestimmt das Element *ulColumnSize* der DBCOLUMNDESC-Struktur die Breite der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Spalte, die erstellt wird.|  
|DBTYPE_UDT|**UDT**|Die folgenden Informationen werden von **DBCOLUMNDESC**-Strukturen verwendet, die von **ITableDefinition::CreateTable** verwendet werden, wenn UDT-Spalten erforderlich sind:<br /><br /> *pwSzTypeName* wird ignoriert.<br /><br /> *rgPropertySets* muss wie im Abschnitt zu **DBPROPSET_SQLSERVERCOLUMN** unter [Verwenden von benutzerdefinierten Typen](../../relational-databases/native-client/features/using-user-defined-types.md) beschrieben einen **DBPROPSET_SQLSERVERCOLUMN**-Eigenschaftensatz umfassen.|  
|DBTYPE_UI1|**TINYINT**||  
|DBTYPE_WSTR|**nchar**, **nvarchar**, **ntext** oder **nvarchar(max)**|Der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] native Client-OLE-DB-Anbieter überprüft das *ulColumnSize-Member* der DBCOLUMNDESC-Struktur. Basierend auf dem [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Wert ordnet der Native Client OLE DB-Anbieter den Typ **ntext**zu.<br /><br /> Wenn der Wert von *ulColumnSize* kleiner als die maximale Länge einer [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Unicode-Zeichendatentypspalte ist, überprüft der native Client-OLE-DB-Anbieter den DBCOLUMNDESC *rgPropertySets-Member.* Wenn DBPROP_COL_FIXEDLENGTH VARIANT_TRUE [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ist, ordnet der Native Client OLE DB-Anbieter den Typ **nchar**zu. Wenn der Wert der Eigenschaft [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] VARIANT_FALSE ist, ordnet der Native Client OLE DB-Anbieter den Typ **nvarchar**zu. In jedem Fall bestimmt das Element *ulColumnSize* der DBCOLUMNDESC-Struktur die Breite der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Spalte, die erstellt wird.|  
|DBTYPE_XML|**XML**||  
  
> [!NOTE]  
>  Beim Erstellen einer neuen Tabelle ordnet der OLE DB-Anbieter von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] nur die in der vorstehenden Tabelle angegebenen Enumerationswerte für OLE DB-Datenwerte zu. Durch den Versuch, eine Tabelle mit einer Spalte eines anderen OLE DB-Datentyps zu erstellen, wird ein Fehler erzeugt.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Datentypen &#40;OLE DB&#41;](../../relational-databases/native-client-ole-db-data-types/data-types-ole-db.md)  
  
  
