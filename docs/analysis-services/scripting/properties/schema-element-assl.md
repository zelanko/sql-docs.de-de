---
title: Schema-Element (ASSL) | Microsoft Docs
ms.date: 5/8/2018
ms.prod: sql
ms.custom: assl
ms.reviewer: owend
ms.technology: analysis-services
ms.topic: reference
author: minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: e491c5070f8e21c68d52289a80409606eddd850a
ms.sourcegitcommit: c12a7416d1996a3bcce3ebf4a3c9abe61b02fb9e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/10/2018
---
# <a name="schema-element-assl"></a>Schema-Element (ASSL)
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]
  Enthält das Schema der Datenquellensicht.  
  
## <a name="syntax"></a>Syntax  
  
```xml  
  
<DataSourceView>  
   ...  
   <Schema>...</Schema>  
   ...  
</DataSourceView>  
```  
  
## <a name="element-characteristics"></a>Elementmerkmale  
  
|Merkmal|Beschreibung|  
|--------------------|-----------------|  
|Datentyp und -länge|Schema|  
|Standardwert|Keine|  
|Kardinalität|1-1: Erforderliches Element, das nur einmal auftritt.|  
  
## <a name="element-relationships"></a>Elementbeziehungen  
  
|Beziehung|Element|  
|------------------|-------------|  
|Übergeordnetes Element|[DataSourceView-Objekt](../../../analysis-services/scripting/objects/datasourceview-element-assl.md)|  
|Untergeordnete Elemente|Keine|  
  
## <a name="remarks"></a>Hinweise  
 Die **Schema** wird dargestellt, mit dem XML-Schemadefinition (XSD) Sprachformat des DataSets in der [!INCLUDE[msCoName](../../../includes/msconame-md.md)] .NET Framework, wobei einige Erweiterungen für DataSets und andere spezifisch für die Verwendung in der Definition Datendefinitionssprache (DDL). DataSets definieren eine flexible Zuordnung von XSD zu einem relationalen Schema, aber geben XSD in einer kanonischeren Form zurück. Nur diese kanonische Form ist innerhalb der Datenquellen gültig.  
  
 Das Element, das das übergeordnete Element des entspricht **Schema** im Objekt Analysis Management Objects (AMO) Modell ist <xref:Microsoft.AnalysisServices.DataSourceView>.  
  
## <a name="see-also"></a>Siehe auch  
 [Datenbankeigenschaften & #40; ASSL & #41;](../../../analysis-services/scripting/properties/properties-assl.md)  
  
  
