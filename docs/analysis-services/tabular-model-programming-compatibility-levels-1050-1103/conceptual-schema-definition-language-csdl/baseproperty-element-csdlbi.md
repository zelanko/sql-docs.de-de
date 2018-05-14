---
title: BaseProperty-Element (CSDLBI) | Microsoft Docs
ms.date: 05/07/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: tabular-models
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: f1e14b3bcfe862083aa78d634ca20ecaa0f4dd5c
ms.sourcegitcommit: c12a7416d1996a3bcce3ebf4a3c9abe61b02fb9e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/10/2018
---
# <a name="baseproperty-element-csdlbi"></a>BaseProperty-Element (CSDLBI)
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]
  Das BaseProperty-Element ist ein komplexer Typ, der als Basis für andere Elemente dient.  
  
 Seine Attribute können in den Spalten und Measures angezeigt werden.  
  
## <a name="elements-and-attributes"></a>Elemente und Attribute  
 In der folgenden Tabelle sind die Elemente und Attribute aufgeführt, die das BaseProperty-Element definieren.  
  
|Name|Ist erforderlich|Beschreibung|  
|----------|-----------------|-----------------|  
|Ausrichtung|Nein|Der Name für das Element (Spalte, Measure, Navigationseigenschaft, Hierarchie oder Ebene), das von der Implementierung des Member-Typs definiert wird.|  
|FormatString|Nein|Der Anzeigename für das Element.|  
|IsRightToLeft|Nein|Ein boolescher Wert, der angibt, ob das Feld Text enthält, der von rechts nach links gelesen werden kann.<br /><br /> Wenn dieses Attribut weggelassen wird, wird die Standardeinstellung (des Modells) verwendet.|  
|SortDirection|Nein|Ein Wert, der angibt, wie die Feldwerte normalerweise sortiert werden. Die Inhalte dieses Attributs werden vom einfachen Typ SortDirection definiert.<br /><br /> Wenn das Attribut nicht angegeben wird, wird eine Sortierrichtung auf Grundlage des Datentyps des Felds zugewiesen.|  
|Einheiten|Nein|Das Symbol, das für Feldwerte zur Darstellung von Einheiten übernommen wird.<br /><br /> Wenn kein Wert angegeben ist, sind die Einheiten unbekannt.|  
  
## <a name="alignment-element"></a>Alignment-Element  
 Mit diesem einfachen Typ wird das Namensformat definiert, das verwendet wird, um Elemente zu unterscheiden.  
  
|Wert|Beschreibung|  
|-----------|-----------------|  
|Keine|Verwenden Sie den Attributnamen.|  
|Kontext|Verwenden Sie den Namen der eingehenden Beziehung.|  
|Merge|Verketten Sie den Namen der eingehenden Beziehung und den Eigenschaftsnamen gemäß den Regeln der aktuellen Grammatik.|  
  
## <a name="sortdirection-element"></a>SortDirections-Element  
 Mit diesem einfachen Typ wird das Namensformat definiert, das verwendet wird, um Elemente zu unterscheiden.  
  
|Wert|Beschreibung|  
|-----------|-----------------|  
|Keine|Verwenden Sie den Attributnamen.|  
|Kontext|Verwenden Sie den Namen der eingehenden Beziehung.|  
|Merge|Verketten Sie den Namen der eingehenden Beziehung und den Namen der Eigenschaft.|  
  
## <a name="see-also"></a>Siehe auch  
 [Informationen zum tabellarischen Objektmodell auf Kompatibilität Ebenen 1050 bis 1103](../../../analysis-services/tabular-model-programming-compatibility-levels-1050-1103/representation/understanding-tabular-object-model-at-levels-1050-through-1103.md)  
  
  
