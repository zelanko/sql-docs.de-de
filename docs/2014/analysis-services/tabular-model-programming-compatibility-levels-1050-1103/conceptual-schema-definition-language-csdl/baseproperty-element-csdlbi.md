---
title: BaseProperty-Element (CSDLBI) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.topic: reference
ms.assetid: d0f63e52-7330-4b2c-a929-7a517acc6921
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 3dcea67deac28838f190947c0b890b86537536c4
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/02/2018
ms.locfileid: "48198810"
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
|None|Verwenden Sie den Attributnamen.|  
|Kontext|Verwenden Sie den Namen der eingehenden Beziehung.|  
|Merge|Verketten Sie den Namen der eingehenden Beziehung und den Eigenschaftsnamen gemäß den Regeln der aktuellen Grammatik.|  
  
## <a name="sortdirection-element"></a>SortDirections-Element  
 Mit diesem einfachen Typ wird das Namensformat definiert, das verwendet wird, um Elemente zu unterscheiden.  
  
|value|Description|  
|-----------|-----------------|  
|None|Verwenden Sie den Attributnamen.|  
|Kontext|Verwenden Sie den Namen der eingehenden Beziehung.|  
|Merge|Verketten Sie den Namen der eingehenden Beziehung und den Namen der Eigenschaft.|  
  
## <a name="see-also"></a>Siehe auch  
 [Grundlegendes zum tabellarischen Objektmodell](../representation/understanding-tabular-object-model-at-levels-1050-through-1103.md)  
  
  
