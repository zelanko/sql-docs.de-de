---
title: Datentypzuordnung zu Rowsets und Parametern | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology: native-client
ms.tgt_pltfrm: ''
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
caps.latest.revision: 40
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 77b7718febb0a6b8e8a8575ff776ffb44364b68a
ms.sourcegitcommit: f8ce92a2f935616339965d140e00298b1f8355d7
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/03/2018
ms.locfileid: "37422679"
---
# <a name="data-type-mapping-in-rowsets-and-parameters"></a>Datentypzuordnung zu Rowsets und Parametern
  In Rowsets und als Parameterwerte stellt der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB-Anbieter stellt [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Daten über die folgenden OLE DB definierten Datentypen, die in den Funktionen gemeldet **IColumnsInfo:: GetColumnInfo** und  **ICommandWithParameters:: GetParameterInfo**.  
  
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
  
 Die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB-Anbieter unterstützt Consumer angeforderte datenkonvertierungen, wie in der Abbildung dargestellt.  
  
 Die **Sql_variant** Ojekte können Daten jedes [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Datentyp mit Ausnahme von Text, Ntext, Image, varchar(max), nvarchar(max), varbinary(max), Xml, Timestamp und Microsoft .NET Framework common Language Runtime (CLR) Benutzerdefinierte Typen. Eine Instanz der sql_variant-Daten darf außerdem nicht sql_variant als zugrunde liegenden Basisdatentyp aufweisen. Die Spalte kann z. B. enthalten **Smallint** Werte für einige Zeilen **"float"** Werte für die anderen Zeilen hat und **Char**/**Nchar**Werte in den Rest.  
  
> [!NOTE]  
>  Die **Sql_variant** Datentyp den Variant-Datentyp in Microsoft Visual Basic® und den Typen DBTYPE_VARIANT, DBTYPE_SQLVARIANT in OLEDB ähnlich ist.  
  
 Wenn **Sql_variant** Daten als DBTYPE_VARIANT abgerufen werden, wird es in einem VARIANT-Struktur im Puffer eingefügt. Die Untertypen in der VARIANT-Struktur können nicht definierten Untertypen zugeordnet, aber die **Sql_variant** -Datentyp. Die **Sql_variant** Daten müssen dann als DBTYPE_SQLVARIANT abgerufen werden, in der Reihenfolge für alle Untertypen zugeordnet.  
  
## <a name="dbtypesqlvariant-data-type"></a>DBTYPE_SQLVARIANT-Datentyp  
 Zur Unterstützung der **Sql_variant** -Datentyp, der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB-Anbieter stellt einen anbieterspezifischen Datentyp mit dem Namen DBTYPE_SQLVARIANT. Wenn **Sql_variant** Daten werden als DBTYPE_SQLVARIANT abgerufen werden, wird in einer anbieterspezifischen SSVARIANT-Struktur gespeichert. Die SSVARIANT-Struktur enthält alle Untertypen, die den Untertypen des der **Sql_variant** -Datentyp.  
  
 Die Sitzungseigenschaft SSPROP_ALLOWNATIVEVARIANT muss außerdem auf TRUE festgelegt werden.  
  
## <a name="provider-specific-property-sspropallownativevariant"></a>Anbieterspezifische Eigenschaft SSPROP_ALLOWNATIVEVARIANT  
 Beim Abrufen von Daten können Sie explizit angeben, welcher Datentyp für eine Spalte oder einen Parameter zurückgegeben werden soll. **IColumnsInfo** kann auch verwendet werden, um die Spalteninformationen aus, und verwenden, um die Bindung verwenden. Wenn **IColumnsInfo** wird verwendet, um Spalteninformationen für Bindungszwecke abgerufen, wenn die SSPROP_ALLOWNATIVEVARIANT-Sitzung, die Eigenschaft ist FALSE (Standardwert), DBTYPE_VARIANT zurückgegeben wird **Sql_variant**Spalten. Wenn die SSPROP_ALLOWNATIVEVARIANT-Eigenschaft FALSE ist, wird DBTYPE_SQLVARIANT nicht unterstützt. Wenn die SSPROP_ALLOWNATIVEVARIANT-Eigenschaft auf TRUE festgelegt ist, wird der Spaltentyp als DBTYPE_SQLVARIANT zurückgegeben. In diesem Fall enthält der Puffer die SSVARIANT-Struktur. Beim Abrufen von **Sql_variant** -Daten als DBTYPE_SQLVARIANT, die Sitzungseigenschaft SSPROP_ALLOWNATIVEVARIANT muss festgelegt werden auf "true".  
  
 Die SSPROP_ALLOWNATIVEVARIANT-Eigenschaft ist ein Teil des anbieterspezifischen DBPROPSET_SQLSERVERSESSION-Eigenschaftssatzes und eine Sitzungseigenschaft.  
  
 DBTYPE_VARIANT gilt für alle anderen OLE DB-Anbieter.  
  
## <a name="sspropallownativevariant"></a>SSPROP_ALLOWNATIVEVARIANT  
 SSPROP_ALLOWNATIVEVARIANT ist eine Sitzungseigenschaft und ein Teil des DBPROPSET_SQLSERVERSESSION-Eigenschaftssatzes.  
  
|||  
|-|-|  
|SSPROP_ALLOWNATIVEVARIANT|Typ: VT_BOOL<br /><br /> R/W: Lesen/Schreiben<br /><br /> Standard: VARIANT_FALSE<br /><br /> Beschreibung: Bestimmt, ob die Daten als DBTYPE_VARIANT oder DBTYPE_SQLVARIANT abgerufen werden.<br /><br /> VARIANT_TRUE: Der Spaltentyp wird als DBTYPE_SQLVARIANT zurückgegeben. In diesem Fall enthält der Puffer die SSVARIANT-Struktur.<br /><br /> VARIANT_FALSE: Der Spaltentyp wird als DBTYPE_VARIANT zurückgegeben und der Puffer enthält die VARIANT-Struktur.|  
  
## <a name="see-also"></a>Siehe auch  
 [Datentypen &#40;OLE-DB&#41;](data-types-ole-db.md)  
  
  
