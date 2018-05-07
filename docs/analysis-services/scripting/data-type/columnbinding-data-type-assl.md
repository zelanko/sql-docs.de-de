---
title: ColumnBinding-Datentyp (ASSL) | Microsoft Docs
ms.date: 05/03/2018
ms.prod: sql
ms.technology: analysis-services
ms.component: assl
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 608597fd347f1e70804bc873d4333d9ec92c0401
ms.sourcegitcommit: f1caaa156db2b16e817e0a3884394e7b30fb642f
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/04/2018
---
# <a name="columnbinding-data-type-assl"></a>ColumnBinding-Datentyp (ASSL)
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]
  Definiert einen abgeleiteten Datentyp, der die Bindung einer Spalte in einer Datenquellensicht steht eine [DataItem](../../../analysis-services/scripting/data-type/dataitem-data-type-assl.md) Element.  
  
## <a name="syntax"></a>Syntax  
  
```xml  
  
<ColumnBinding>  
   <!-- The following elements extend Binding -->  
   <TableID>...</TableID>  
      <ColumnID>...</ColumnID>  
</ColumnBinding>  
```  
  
## <a name="data-type-characteristics"></a>Datentypmerkmale  
  
|Merkmal|Beschreibung|  
|--------------------|-----------------|  
|Basisdatentypen|[Bindung](../../../analysis-services/scripting/data-type/binding-data-type-assl.md)|  
|Abgeleitete Datentypen|Keine|  
  
## <a name="data-type-relationships"></a>Datentypbeziehungen  
  
|Beziehung|Element|  
|------------------|-------------|  
|Übergeordnete Elemente|Keine|  
|Untergeordnete Elemente|[ColumnID](../../../analysis-services/scripting/properties/columnid-element-eventcolumn-assl.md), [TableID](../../../analysis-services/scripting/properties/tableid-element-assl.md)|  
|Abgeleitete Elemente|Siehe [Binding](../../../analysis-services/scripting/data-type/binding-data-type-assl.md)|  
  
## <a name="remarks"></a>Hinweise  
 So erstellen gültige Namen für die XML-Elemente, [!INCLUDE[vstecado](../../../includes/vstecado-md.md)] **DataSet** Objekte codieren Tabellennamen, während sie in XML-Schemadefinition (XSD) serialisieren; dem Namen "Order Details" wird z. B. "Order_x0020_Details". Entsprechend der **ColumnID** und **TableID** Elemente, die von der **ColumnBinding** Element- und auch die Verweisobjekte, die in der Datenquellensicht (DSV) codiert werden sollen Namen während der Serialisierung, um sicherzustellen, dass den Text in der DSV direkt mit den Namen übereinstimmen. Analysis Services-Instanz decodiert diese Namen, ebenso wie die **DataSet** Objektmodell.  
  
 Ein **TableDefinitions** Element enthalten sind, ein Element mit dem **TableBinding** -Datentyp und die Tabellen in der DSV verweist müssen auch Namen codieren Serialisierung in XSD. Allerdings die Tabellennamen in der **Partition** Bindungen nicht codiert werden sollte, da diese Namen nur um Namen von Tabellen sind, die in der Datenbank vorhanden und müssen nicht in der DSV vorkommen. Keine Codierung in der Tabelle den Namen der **Partition** Bindungen erreicht auch die folgenden:  
  
-   Die Datendefinitionsbibliothek (Data Definition Library, DDL) für Partitionen bleibt einfacher.  
  
-   Es kann mehr Konsistenz erzielt werden, da Partitionen entweder einen Tabellennamen oder eine SELECT-Anweisung aufweisen und die SELECT-Anweisung nicht codiert werden sollte.  
  
 Tabellen- und Spaltennamen schließen keine Trennzeichen (z. B. "[" für [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]) ein.  
  
 Weitere Informationen zu den **binden** Typs, einschließlich der Tabellen von Analysis Services Scripting Language (ASSL) von Objekten des der **binden** Typ und der Vererbungshierarchie des  **Binden von** , finden Sie unter [Binding-Datentyp &#40;ASSL&#41;](../../../analysis-services/scripting/data-type/binding-data-type-assl.md).  
  
 Einen Überblick über datenbindungen in ASSL finden Sie unter [& #40; Datenquellen und Bindungen SSAS – mehrdimensional & #41; ](../../../analysis-services/multidimensional-models/data-sources-and-bindings-ssas-multidimensional.md).  
  
 Das entsprechende Element im AMO-Objektmodell ist <xref:Microsoft.AnalysisServices.ColumnBinding>.  
  
## <a name="see-also"></a>Siehe auch  
 [Analysis Services Scripting Language-XML-Datentypen & #40; ASSL & #41;](../../../analysis-services/scripting/data-type/analysis-services-scripting-language-xml-data-types-assl.md)  
  
  
