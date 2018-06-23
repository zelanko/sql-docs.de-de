---
title: TableBinding-Datentyp (ASSL) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
api_name:
- TableBinding Data Type
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- TableBinding
helpviewer_keywords:
- TableBinding data type
ms.assetid: 3195dca4-82bf-46b7-a31f-5383586e3573
caps.latest.revision: 39
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: d0790fe5d8567c8ab23e3aaf39430d46675dcbdc
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/19/2018
ms.locfileid: "36162791"
---
# <a name="tablebinding-data-type-assl"></a>TableBinding-Datentyp (ASSL)
  Definiert einen abgeleiteten Datentyp, der eine Bindung mit einer Tabelle darstellt.  
  
## <a name="syntax"></a>Syntax  
  
```xml  
  
<TableBinding>  
   <!-- The following elements extend TabularBinding -->  
   <DataSourceID>...</DataSourceID>  
   <DbTableName>...</DbTableName>  
   <DbSchemaName>...</DbSchemaName>  
</TableBinding>  
```  
  
## <a name="data-type-characteristics"></a>Datentypmerkmale  
  
|Merkmal|Description|  
|--------------------|-----------------|  
|Basisdatentypen|[TabularBinding](binding-data-type-assl.md)|  
|Abgeleitete Datentypen|InclusionThresholdSetting|  
  
## <a name="data-type-relationships"></a>Datentypbeziehungen  
  
|Beziehung|Element|  
|------------------|-------------|  
|Übergeordnete Elemente|InclusionThresholdSetting|  
|Untergeordnete Elemente|[DataSourceID](../properties/id-element-assl.md), [DbSchemaName](../properties/name-element-assl.md), [DbTableName](../properties/dbtablename-element-assl.md)|  
|Abgeleitete Elemente|Finden Sie unter [binden](binding-data-type-assl.md)|  
  
## <a name="remarks"></a>Hinweise  
 Beachten Sie, dass Verweise auf andere Tabellen im Filterausdruck durch eine untergeordnete SELECT-Anweisung Auswirkungen auf die Leistung in einigen Datenquellen haben können. Der Designer hat jedoch die vollständige Kontrolle über die SQL-Ausdrücke, indem er eine benannte Abfrage in der Datenquellensicht definiert und anschließend darauf verweist.  
  
 Die Methoden zum Definieren der Bindungen für eine Partition sind unabhängig von der Verwendung partitionierter Tabellen in der Datenquellensicht.  
  
 Ein Beispiel: Eine Measuregruppe verfügt über die Standardtabelle "Sales" und weist die Spalten "Date", "ProductID", "Qty", "Price" und "Amount" auf (in der Datenquellensicht berechnet). Dann könnte die Partition "Sales97" die Tabelle "Sales97" mit dem Filter "Year(Sales.Date) = 97" verwenden.  
  
 Die effektive Abfrage lautet:  
  
```  
SELECT Date, Product ID, Qty, Price, Qty * Price AS Amount   
   FROM Sales97 As Sales  
   WHERE Year(Sales.Date) = 97  
```  
  
 Der berechnete Ausdruck ist auch dann noch gültig, wenn der Ausdruck qualifizierte Tabellennamen (z. B. "Sales.Qty") verwendet hat. Dasselbe gilt, wenn stattdessen die Tabelle durch eine Abfrage "SELECT..." ersetzt wurden. Die oben genannten FROM-Klausel werden "FROM SELECT... As Sales" werden.  
  
 Weitere Informationen zu den `Binding` Typ, einschließlich Tabellen, die von Analysis Services Scripting Language (ASSL) von Objekten des Typs `Binding` und der Vererbungshierarchie der `Binding` , finden Sie unter [Binding-Datentyp &#40;ASSL&#41;](binding-data-type-assl.md).  
  
 Einen Überblick über datenbindungen in ASSL finden Sie unter [Datenquellen und-Bindungen &#40;mehrdimensionale SSAS-&#41;](../../multidimensional-models/data-sources-and-bindings-ssas-multidimensional.md).  
  
 Das entsprechende Element im Objektmodell von Analysis Management Objects (AMO) ist <xref:Microsoft.AnalysisServices.TableBinding>.  
  
## <a name="see-also"></a>Siehe auch  
 [Binding-Datentyp &#40;ASSL&#41;](binding-data-type-assl.md)   
 [Datenquellen und-Bindungen &#40;SSAS – mehrdimensional&#41;](../../multidimensional-models/data-sources-and-bindings-ssas-multidimensional.md)   
 [Analysis Services Scripting Language-XML-Datentypen &#40;ASSL&#41;](analysis-services-scripting-language-xml-data-types-assl.md)  
  
  