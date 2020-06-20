---
title: Datentypzuordnung in ITableDefinition | Microsoft-Dokumentation
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
author: rothja
ms.author: jroth
ms.openlocfilehash: 08574f42905831c4a194313b7d7d58ebeeffeee2
ms.sourcegitcommit: 57f1d15c67113bbadd40861b886d6929aacd3467
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/18/2020
ms.locfileid: "85056323"
---
# <a name="data-type-mapping-in-itabledefinition"></a>Datentypzuordnung zu ITableDefinition
  Beim Erstellen von Tabellen mit der **ITableDefinition:: aufgeschlable** -Funktion [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] kann der Consumer des Native Client OLE DB-Anbieters [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Datentypen im *pwsztykame* -Member des dbcolumndebug-Arrays angeben, das übergeben wird. Gibt der Consumer den Datentyp einer Spalte namentlich an, wird die OLE DB-Datentypzuordnung ignoriert, die durch das *wType*-Element der DBCOLUMNDESC-Struktur dargestellt wird.  
  
 Beim Angeben neuer Spaltendatentypen mit OLE DB-Datentypen unter Verwendung des *wType* -Elements der DBCOLUMNDESC-Struktur ordnet der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB-Anbieter OLE DB-Datentypen wie folgt zu.  
  
|OLE DB-Datentyp|SQL Server<br /><br /> Datentyp|Zusätzliche Informationen|  
|----------------------|------------------------------|----------------------------|  
|DBTYPE_BOOL|**bit**||  
|DBTYPE_BYTES|**binary**, **varbinary**, **image** oder **varbinary(max)**|Der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB-Anbieter überprüft das *ulColumnSize* -Element der dbcolumnde-Struktur. Basierend auf dem-Wert und der-Version der- [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Instanz ordnet der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB-Anbieter den Typ dem **Image**zu.<br /><br /> Wenn der Wert von *ulColumnSize* kleiner als die maximale Länge einer Spalte des **binären** Datentyps ist, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] überprüft der Native Client OLE DB-Anbieter den *rgPropertySets* -Member von DBCOLUMNDESC. Wenn DBPROP_COL_FIXEDLENGTH VARIANT_TRUE ist, ordnet der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB-Anbieter den Typ **Binär**zu. Wenn der Wert der Eigenschaft VARIANT_FALSE ist, ordnet der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB-Anbieter den Typ **varbinary**zu. In jedem Fall bestimmt das Element *ulColumnSize* der DBCOLUMNDESC-Struktur die Breite der SQL Server-Spalte, die erstellt wird.|  
|DBTYPE_CY|**money**||  
|DBTYPE_DBTIMESTAMP|**datetime**||  
|DBTYPE_GUID|**uniqueidentifier**||  
|DBTYPE_I2|**smallint**||  
|DBTYPE_I4|**int**||  
|DBTYPE_NUMERIC|**numeric**|Der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB-Anbieter überprüft die DBCOLUMDESC *bPrecision* -und *bScale* -Member, um die Genauigkeit und die Dezimalstellen für die **numerische** Spalte zu bestimmen.|  
|DBTYPE_R4|**real**||  
|DBTYPE_R8|**float**||  
|DBTYPE_STR|**char**, **varchar**, **text** oder **varchar(max)**|Der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB-Anbieter überprüft das *ulColumnSize* -Element der dbcolumnde-Struktur. Basierend auf dem Wert und der Version der- [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Instanz ordnet der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB-Anbieter den Typ **Text**zu.<br /><br /> Wenn der Wert von *ulColumnSize* kleiner ist als die maximale Länge einer Spalte mit einem Multibytezeichen-Zeichen Datentyp, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] überprüft der Native Client OLE DB-Anbieter den *rgPropertySets* -Member von DBCOLUMNDESC. Wenn DBPROP_COL_FIXEDLENGTH VARIANT_TRUE ist, ordnet der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB-Anbieter den Typ " **char**" zu. Wenn der Wert der Eigenschaft VARIANT_FALSE ist, ordnet der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB-Anbieter den Typ **varchar**zu. In jedem Fall bestimmt das Element *ulColumnSize* der DBCOLUMNDESC-Struktur die Breite der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Spalte, die erstellt wird.|  
|DBTYPE_UDT|**UDT**|Die folgenden Informationen werden in `DBCOLUMNDESC` Strukturen von **ITableDefinition:: aufforderbar** verwendet, wenn UDT-Spalten erforderlich sind:<br /><br /> -   *pwsztypame* wird ignoriert.<br />-   *rgPropertySets* muss einen `DBPROPSET_SQLSERVERCOLUMN` Eigenschaften Satz enthalten, wie im Abschnitt zum `DBPROPSET_SQLSERVERCOLUMN` Verwenden von [benutzerdefinierten Typen](../native-client/features/using-user-defined-types.md)beschrieben.|  
|DBTYPE_UI1|**tinyint**||  
|DBTYPE_WSTR|**nchar**, **nvarchar**, **ntext** oder **nvarchar(max)**|Der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB-Anbieter überprüft das *ulColumnSize* -Element der dbcolumnde-Struktur. Basierend auf dem-Wert ordnet der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB-Anbieter den Typ **ntext**zu.<br /><br /> Wenn der Wert von *ulColumnSize* kleiner als die maximale Länge einer Spalte des Datentyps für Unicode-Zeichen ist, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] überprüft der Native Client OLE DB-Anbieter den *rgPropertySets* -Member von DBCOLUMNDESC. Wenn DBPROP_COL_FIXEDLENGTH VARIANT_TRUE ist, ordnet der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB-Anbieter den Typ **NCHAR**zu. Wenn der Wert der Eigenschaft VARIANT_FALSE ist, ordnet der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB-Anbieter den Typ **nvarchar**zu. In jedem Fall bestimmt das Element *ulColumnSize* der DBCOLUMNDESC-Struktur die Breite der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Spalte, die erstellt wird.|  
|DBTYPE_XML|**XML**||  
  
> [!NOTE]  
>  Beim Erstellen einer neuen Tabelle ordnet der OLE DB-Anbieter von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] nur die in der vorstehenden Tabelle angegebenen Enumerationswerte für OLE DB-Datenwerte zu. Durch den Versuch, eine Tabelle mit einer Spalte eines anderen OLE DB-Datentyps zu erstellen, wird ein Fehler erzeugt.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Datentypen &#40;OLE DB&#41;](data-types-ole-db.md)  
  
  
