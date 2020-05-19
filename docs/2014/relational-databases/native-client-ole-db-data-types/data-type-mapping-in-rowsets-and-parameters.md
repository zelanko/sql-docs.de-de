---
title: Datentypzuordnung in Rowsets und Parametern | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- mapping data types [OLE DB]
- DBTYPE_SQLVARIANT data type
- SQL Server Native Client OLE DB provider, data types
- rowsets [OLE DB], data type mapping
- data types [OLE DB]
- GetColumnInfo function
- parameters [OLE DB]
- SSPROP_ALLOWNATIVEVARIANT property
- GetParameterInfo function
- OLE DB, data types
ms.assetid: 3d831ff8-3b79-4698-b2c1-2b5dd2f8235c
author: rothja
ms.author: jroth
manager: craigg
ms.openlocfilehash: 65858c2d8f43a7fb675f17ff8c719b1041d6ea79
ms.sourcegitcommit: b72c9fc9436c44c6a21fd96223c73bf94706c06b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/01/2020
ms.locfileid: "82705117"
---
# <a name="data-type-mapping-in-rowsets-and-parameters"></a>Datentypzuordnung zu Rowsets und Parametern
  In Rowsets und als Parameterwerten stellt der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB-Anbieter [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Daten mithilfe der folgenden OLE DB definierten Datentypen dar, die in den Funktionen **IColumnsInfo:: GetColumnInfo** und **ICommandWithParameters:: GetParameterInfo**gemeldet werden.  
  
|SQL Server-Datentyp|OLE DB-Datentyp|  
|--------------------------|----------------------|  
|**bigint**|DBTYPE_I8|  
|**binary**|DBTYPE_BYTES|  
|**bit**|DBTYPE_BOOL|  
|**char**|DBTYPE_STR|  
|**datetime**|DBTYPE_DBTIMESTAMP|  
|**datetime2**|DBTYPE_DBTIME2|  
|**decimal**|DBTYPE_NUMERIC|  
|**float**|DBTYPE_R8|  
|**image**|DBTYPE_BYTES|  
|**int**|DBTYPE_I4|  
|**money**|DBTYPE_CY|  
|**nchar**|DBTYPE_WSTR|  
|**ntext**|DBTYPE_WSTR|  
|**numeric**|DBTYPE_NUMERIC|  
|**nvarchar**|DBTYPE_WSTR|  
|**real**|DBTYPE_R4|  
|**smalldatetime**|DBTYPE_DBTIMESTAMP|  
|**smallint**|DBTYPE_I2|  
|**smallmoney**|DBTYPE_CY|  
|**sql_variant**|DBTYPE_VARIANT, DBTYPE_SQLVARIANT|  
|**sysname**|DBTYPE_WSTR|  
|**text**|DBTYPE_STR|  
|**timestamp**|DBTYPE_BYTES|  
|**tinyint**|DBTYPE_UI1|  
|**UDT**|DBTYPE_UDT|  
|**uniqueidentifier**|DBTYPE_GUID|  
|**varbinary**|DBTYPE_BYTES|  
|**varchar**|DBTYPE_STR|  
|**XML**|DBTYPE_XML|  
  
 Der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB-Anbieter unterstützt vom Consumer angeforderte Datenkonvertierungen, wie in der Abbildung dargestellt.  
  
 Die **sql_variant**-Objekte können Daten jedes [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Datentyps enthalten, mit Ausnahme von „text“, „ntext“, „image“, „varchar(max)“, „nvarchar(max)“, „varbinary(max)“, „xml“, „timestamp“ sowie benutzerdefinierten CLR-Typen (Common Language Runtime) von Microsoft .NET Framework. Eine Instanz der sql_variant-Daten darf außerdem nicht sql_variant als zugrunde liegenden Basisdatentyp aufweisen. Die Spalte kann beispielsweise in einigen Zeilen **smallint**-Werte enthalten, in anderen Zeilen **float**-Werte und in den übrigen **char**/**nchar**-Werte.  
  
> [!NOTE]  
>  Der **sql_variant** -Datentyp ähnelt dem Variant-Datentyp in Microsoft Visual Basic?? und die DBTYPE_VARIANT DBTYPE_SQLVARIANT in OleDb.  
  
 Wenn **sql_variant**-Daten als DBTYPE_VARIANT abgerufen werden, werden sie in einer VARIANT-Struktur im Puffer abgelegt. Die Untertypen in der VARIANT-Struktur dürfen jedoch nicht den im **sql_variant**-Datentyp definierten Untertypen zugeordnet werden. Die **sql_variant**-Daten müssen dann als DBTYPE_SQLVARIANT abgerufen werden, damit alle Untertypen zugeordnet werden.  
  
## <a name="dbtype_sqlvariant-data-type"></a>DBTYPE_SQLVARIANT-Datentyp  
 Zur Unterstützung des **sql_variant** -Datentyps stellt der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB-Anbieter einen anbieterspezifischen Datentyp namens DBTYPE_SQLVARIANT bereit. Wenn **sql_variant**-Daten als DBTYPE_SQLVARIANT abgerufen werden, werden sie in einer anbieterspezifischen SSVARIANT-Struktur gespeichert. Die SSVARIANT-Struktur enthält alle Untertypen, die zu den Untertypen des **sql_variant**-Datentyps passen.  
  
 Die Sitzungseigenschaft SSPROP_ALLOWNATIVEVARIANT muss außerdem auf TRUE festgelegt werden.  
  
## <a name="provider-specific-property-ssprop_allownativevariant"></a>Anbieterspezifische Eigenschaft SSPROP_ALLOWNATIVEVARIANT  
 Beim Abrufen von Daten können Sie explizit angeben, welcher Datentyp für eine Spalte oder einen Parameter zurückgegeben werden soll. **IColumnsInfo** kann auch verwendet werden, um die Spalteninformationen abzurufen und diese Informationen für die Bindung zu verwenden. Wenn mit **IColumnsInfo** Spalteninformationen für Bindungszwecke abgerufen werden und die SSPROP_ALLOWNATIVEVARIANT-Sitzungseigenschaft FALSE (Standardwert) lautet, wird für die **sql_variant**-Spalten DBTYPE_VARIANT zurückgegeben. Wenn die SSPROP_ALLOWNATIVEVARIANT-Eigenschaft FALSE ist, wird DBTYPE_SQLVARIANT nicht unterstützt. Wenn die SSPROP_ALLOWNATIVEVARIANT-Eigenschaft auf TRUE festgelegt ist, wird der Spaltentyp als DBTYPE_SQLVARIANT zurückgegeben. In diesem Fall enthält der Puffer die SSVARIANT-Struktur. Beim Abrufen von **sql_variant**-Daten als DBTYPE_SQLVARIANT muss die SSPROP_ALLOWNATIVEVARIANT-Sitzungseigenschaft auf TRUE festgelegt sein.  
  
 Die SSPROP_ALLOWNATIVEVARIANT-Eigenschaft ist ein Teil des anbieterspezifischen DBPROPSET_SQLSERVERSESSION-Eigenschaftssatzes und eine Sitzungseigenschaft.  
  
 DBTYPE_VARIANT gilt für alle anderen OLE DB-Anbieter.  
  
## <a name="ssprop_allownativevariant"></a>SSPROP_ALLOWNATIVEVARIANT  
 SSPROP_ALLOWNATIVEVARIANT ist eine Sitzungseigenschaft und ein Teil des DBPROPSET_SQLSERVERSESSION-Eigenschaftssatzes.  
  
|||  
|-|-|  
|SSPROP_ALLOWNATIVEVARIANT|Typ: VT_BOOL<br /><br /> R/W: Lesen/Schreiben<br /><br /> Standard: VARIANT_FALSE<br /><br /> Beschreibung: Bestimmt, ob die Daten als DBTYPE_VARIANT oder DBTYPE_SQLVARIANT abgerufen werden.<br /><br /> VARIANT_TRUE: Der Spaltentyp wird als DBTYPE_SQLVARIANT zurückgegeben. In diesem Fall enthält der Puffer die SSVARIANT-Struktur.<br /><br /> VARIANT_FALSE: Der Spaltentyp wird als DBTYPE_VARIANT zurückgegeben und der Puffer enthält die VARIANT-Struktur.|  
  
## <a name="see-also"></a>Weitere Informationen  
 [Datentypen &#40;OLE DB&#41;](data-types-ole-db.md)  
  
  
