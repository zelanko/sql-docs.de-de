---
title: Datentypzuordnung itabledefinition | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
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
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: e561742406c173b69bfb5040c2f2f51efdf5ed64
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "63201213"
---
# <a name="data-type-mapping-in-itabledefinition"></a>Datentypzuordnung zu ITableDefinition
  Beim Erstellen von Tabellen mit den **itabledefinition:: CreateTable** -Funktion, die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB-Anbieter-Consumer kann angeben, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Datentypen in der *PwszTypeName* Member des DBCOLUMNDESC-Arrays, die übergeben wird. Gibt der Consumer den Datentyp einer Spalte namentlich an, wird die OLE DB-Datentypzuordnung ignoriert, die durch das *wType*-Element der DBCOLUMNDESC-Struktur dargestellt wird.  
  
 Beim Angeben von Datentypen neuer Spalten mit OLE DB-Datentypen, die mithilfe der DBCOLUMNDESC-Struktur *wType* Member, die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB-Anbieter OLE DB-Datentypen folgendermaßen zugeordnet.  
  
|OLE DB-Datentyp|SQL Server<br /><br /> Datentyp|Zusätzliche Informationen|  
|----------------------|------------------------------|----------------------------|  
|DBTYPE_BOOL|**bit**||  
|DBTYPE_BYTES|**binary**, **varbinary**, **image** oder **varbinary(max)**|Die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB-Anbieter überprüft die *UlColumnSize* Mitglied der DBCOLUMNDESC-Struktur. Basierend auf den Wert ein, und Version der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Instanz die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB-Anbieter wird den Typ, zugeordnet **Image**.<br /><br /> Wenn der Wert des *UlColumnSize* ist kleiner als die maximale Länge des eine **binäre** -Datentypspalte, und klicken Sie dann die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB-Anbieter überprüft der dbcolumndesc-Struktur  *RgPropertySets* Member. Wenn DBPROP_COL_FIXEDLENGTH den Wert VARIANT_TRUE, die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB-Anbieter wird den Typ, zugeordnet **binäre**. Wenn der Wert der Eigenschaft VARIANT_TRUE, dann ist die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB-Anbieter wird den Typ, zugeordnet **Varbinary**. In jedem Fall bestimmt das Element *ulColumnSize* der DBCOLUMNDESC-Struktur die Breite der SQL Server-Spalte, die erstellt wird.|  
|DBTYPE_CY|**money**||  
|DBTYPE_DBTIMESTAMP|**datetime**||  
|DBTYPE_GUID|**uniqueidentifier**||  
|DBTYPE_I2|**smallint**||  
|DBTYPE_I4|**int**||  
|DBTYPE_NUMERIC|**numeric**|Die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB-Anbieter überprüft das DBCOLUMDESC *bPrecision* und *bScale* Elemente zum Bestimmen von Genauigkeit und Dezimalstellen der **numerischen** die Spalte.|  
|DBTYPE_R4|**real**||  
|DBTYPE_R8|**float**||  
|DBTYPE_STR|**char**, **varchar**, **text** oder **varchar(max)**|Die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB-Anbieter überprüft die *UlColumnSize* Mitglied der DBCOLUMNDESC-Struktur. Basierend auf den Wert und die Version der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Instanz die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB-Anbieter wird den Typ, zugeordnet **Text**.<br /><br /> Wenn der Wert des *UlColumnSize* ist kleiner als die maximale Länge von einem Multibytezeichen-Datentypspalte, und klicken Sie dann die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB-Anbieter überprüft der dbcolumndesc-Struktur *RgPropertySets*Member. Wenn DBPROP_COL_FIXEDLENGTH den Wert VARIANT_TRUE, die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB-Anbieter wird den Typ, zugeordnet **Char**. Wenn der Wert der Eigenschaft VARIANT_TRUE, dann ist die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB-Anbieter wird den Typ, zugeordnet **Varchar**. In jedem Fall bestimmt das Element *ulColumnSize* der DBCOLUMNDESC-Struktur die Breite der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Spalte, die erstellt wird.|  
|DBTYPE_UDT|**UDT**|Die folgende Informationen werden in `DBCOLUMNDESC` von Strukturen **itabledefinition:: CreateTable** Wenn UDT-Spalten erforderlich sind:<br /><br /> -   *PwSzTypeName* wird ignoriert.<br />-   *RgPropertySets* müssen eine `DBPROPSET_SQLSERVERCOLUMN` -Eigenschaft festgelegt wird, wie im Abschnitt zum beschrieben `DBPROPSET_SQLSERVERCOLUMN`im [Defined Types](../native-client/features/using-user-defined-types.md).|  
|DBTYPE_UI1|**tinyint**||  
|DBTYPE_WSTR|**nchar**, **nvarchar**, **ntext** oder **nvarchar(max)**|Die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB-Anbieter überprüft die *UlColumnSize* Mitglied der DBCOLUMNDESC-Struktur. Auf Grundlage des Werts, der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB-Anbieter wird den Typ, zugeordnet **Ntext**.<br /><br /> Wenn der Wert des *UlColumnSize* ist kleiner als der maximal ein Unicode-Zeichen-Datentypspalte, und klicken Sie dann die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB-Anbieter überprüft der dbcolumndesc-Struktur *RgPropertySets*Member. Wenn DBPROP_COL_FIXEDLENGTH den Wert VARIANT_TRUE, die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB-Anbieter wird den Typ, zugeordnet **Nchar**. Wenn der Wert der Eigenschaft VARIANT_TRUE, dann ist die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB-Anbieter wird den Typ, zugeordnet **Nvarchar**. In jedem Fall bestimmt das Element *ulColumnSize* der DBCOLUMNDESC-Struktur die Breite der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Spalte, die erstellt wird.|  
|DBTYPE_XML|**XML**||  
  
> [!NOTE]  
>  Beim Erstellen einer neuen Tabelle ordnet der OLE DB-Anbieter von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] nur die in der vorstehenden Tabelle angegebenen Enumerationswerte für OLE DB-Datenwerte zu. Durch den Versuch, eine Tabelle mit einer Spalte eines anderen OLE DB-Datentyps zu erstellen, wird ein Fehler erzeugt.  
  
## <a name="see-also"></a>Siehe auch  
 [Datentypen &#40;OLE-DB&#41;](data-types-ole-db.md)  
  
  
