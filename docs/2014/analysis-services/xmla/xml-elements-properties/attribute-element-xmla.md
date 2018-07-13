---
title: Attribut-Element (XMLA) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
api_name:
- Attribute Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- http://schemas.microsoft.com/analysisservices/2003/engine#Attribute
- microsoft.xml.analysis.attribute
- urn:schemas-microsoft-com:xml-analysis#Attribute
helpviewer_keywords:
- Attribute element
ms.assetid: 0df9cf44-dc5f-4234-8a5a-daac8aabc0d6
caps.latest.revision: 17
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 262114f7bbd9200bfab3a74bb14e8cea08400f5d
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/02/2018
ms.locfileid: "37185117"
---
# <a name="attribute-element-xmla"></a>Attribute-Element (XMLA)
  Definiert oder filtert ein Element in einem Attribut auf dem ein übergeordnetes Element [einfügen](../xml-elements-commands/insert-element-xmla.md), [Update](../xml-elements-commands/update-element-xmla.md), oder [löschen](../xml-elements-commands/drop-element-xmla.md) Befehl ausführt.  
  
## <a name="syntax"></a>Syntax  
  
```xml  
  
<Attributes>  
   ...  
   <Attribute>  
      <AttributeName>...</AttributeName>  
      <Keys>...</Keys>  
      <!-- The following elements are included only for attributes contained in the Attributes element of a parent Insert or Update command -->  
      <Name>...</Name>  
      <Translations>...</Translations>  
      <CustomRollup>...</CustomRollup>  
      <CustomRollupProperties>...</CustomRollupProperties>  
      <UnaryOperator>...</UnaryOperator>  
      <SkippedLevels>...</SkippedLevels>  
   </Attribute>  
   ...  
</Attributes>  
```  
  
## <a name="element-characteristics"></a>Elementmerkmale  
  
|Merkmal|Description|  
|--------------------|-----------------|  
|Datentyp und -länge|InclusionThresholdSetting|  
|Standardwert|InclusionThresholdSetting|  
|Cardinality|1-1: Erforderliches Element, das nur einmal auftritt.|  
  
## <a name="element-relationships"></a>Elementbeziehungen  
  
|Beziehung|Element|  
|------------------|-------------|  
|Übergeordnete Elemente|[Attribute](attributes-element-xmla.md)|  
  
 **Untergeordnete Elemente**  
  
|||  
|-|-|  
|**Vorgänger oder übergeordnetes Element**|**Untergeordnetes Element**|  
|[Drop](../xml-elements-commands/drop-element-xmla.md), [, in denen](name-element-xmla.md), [Schlüssel](keys-element-xmla.md)|  
|[Fügen Sie](../xml-elements-commands/insert-element-xmla.md), [aktualisieren](../xml-elements-commands/update-element-xmla.md)|[AttributeName](name-element-xmla.md), [CustomRollup](customrollup-element-xmla.md), [CustomRollupProperties](properties-element-xmla.md), [Schlüssel](keys-element-xmla.md), [Namen](name-element-xmla.md), [ SkippedLevels](skippedlevels-element-xmla.md), [Übersetzungen](translations-element-xmla.md), [UnaryOperator](unaryoperator-element-xmla.md)|  
  
## <a name="remarks"></a>Hinweise  
 Die `Attribute` Element definiert das Attributelement, das eingefügt, aktualisiert oder gelöscht bzw. durch die `Insert`, `Update`, oder `Drop` Befehl. Da diese Befehle nur für jeweils ein Attributelement zu einem Zeitpunkt ausgeführt werden können die [Attribute](attributes-element-xmla.md) Auflistung von der `Insert`, `Update`, und `Drop` Befehle können nur einen enthalten `Attribute` Element. Jedoch kann die `Attributes`-Auflistung des `Where`-Elements für den `Drop`- und den `Update`-Befehl mehrere `Attribute`-Elemente enthalten, sodass Sie die Attribute filtern können, die in einer Dimension mit Schreibzugriff gelöscht oder aktualisiert werden sollen.  
  
## <a name="see-also"></a>Siehe auch  
 [Eigenschaften &#40;XMLA&#41;](xml-elements-properties.md)   
 [Dimensionen mit aktiviertem Schreibzugriff](../../multidimensional-models-olap-logical-dimension-objects/write-enabled-dimensions.md)  
  
  
