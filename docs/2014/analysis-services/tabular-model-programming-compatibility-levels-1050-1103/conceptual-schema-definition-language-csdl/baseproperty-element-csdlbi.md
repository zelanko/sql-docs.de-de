---
title: BaseProperty-Element (CSDLBI) | Microsoft-Dokumentation
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
ms.assetid: d0f63e52-7330-4b2c-a929-7a517acc6921
caps.latest.revision: 5
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 6de9e321e3cd5122a6252663c533be2d536800d2
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/02/2018
ms.locfileid: "37320840"
---
# <a name="baseproperty-element-csdlbi"></a>BaseProperty-Element (CSDLBI)
  Das BaseProperty-Element ist ein komplexer Typ, der als Basis für andere Elemente dient.  
  
 Seine Attribute können in den Spalten und Measures angezeigt werden.  
  
## <a name="elements-and-attributes"></a>Elemente und Attribute  
 In der folgenden Tabelle sind die Elemente und Attribute aufgeführt, die das BaseProperty-Element definieren.  
  
|Name|Ist erforderlich|Description|  
|----------|-----------------|-----------------|  
|Ausrichtung|nein|Der Name für das Element (Spalte, Measure, Navigationseigenschaft, Hierarchie oder Ebene), das von der Implementierung des Member-Typs definiert wird.|  
|FormatString|nein|Der Anzeigename für das Element.|  
|IsRightToLeft|nein|Ein boolescher Wert, der angibt, ob das Feld Text enthält, der von rechts nach links gelesen werden kann.<br /><br /> Wenn dieses Attribut weggelassen wird, wird die Standardeinstellung (des Modells) verwendet.|  
|SortDirection|nein|Ein Wert, der angibt, wie die Feldwerte normalerweise sortiert werden. Die Inhalte dieses Attributs werden vom einfachen Typ SortDirection definiert.<br /><br /> Wenn das Attribut nicht angegeben wird, wird eine Sortierrichtung auf Grundlage des Datentyps des Felds zugewiesen.|  
|Einheiten|nein|Das Symbol, das für Feldwerte zur Darstellung von Einheiten übernommen wird.<br /><br /> Wenn kein Wert angegeben ist, sind die Einheiten unbekannt.|  
  
## <a name="alignment-element"></a>Alignment-Element  
 Mit diesem einfachen Typ wird das Namensformat definiert, das verwendet wird, um Elemente zu unterscheiden.  
  
|value|Description|  
|-----------|-----------------|  
|InclusionThresholdSetting|Verwenden Sie den Attributnamen.|  
|Kontext|Verwenden Sie den Namen der eingehenden Beziehung.|  
|Merge|Verketten Sie den Namen der eingehenden Beziehung und den Eigenschaftsnamen gemäß den Regeln der aktuellen Grammatik.|  
  
## <a name="sortdirection-element"></a>SortDirections-Element  
 Mit diesem einfachen Typ wird das Namensformat definiert, das verwendet wird, um Elemente zu unterscheiden.  
  
|value|Description|  
|-----------|-----------------|  
|InclusionThresholdSetting|Verwenden Sie den Attributnamen.|  
|Kontext|Verwenden Sie den Namen der eingehenden Beziehung.|  
|Merge|Verketten Sie den Namen der eingehenden Beziehung und den Namen der Eigenschaft.|  
  
## <a name="see-also"></a>Siehe auch  
 [Grundlegendes zum tabellarischen Objektmodell](../representation/understanding-tabular-object-model-at-levels-1050-through-1103.md)  
  
  
