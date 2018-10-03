---
title: Member-Element (CSDLBI) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.topic: reference
ms.assetid: 1ba225f5-3867-4aae-a519-e3c277688d1e
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: f193cb746b8df43c33aa65ea3d69d87ab7c36655
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/02/2018
ms.locfileid: "48218830"
---
# <a name="member-element-csdlbi"></a>Member-Element (CSDLBI)
  Das Member-Element ist ein komplexer Typ, der als Basis für andere Elemente dient.  
  
 Die zugehörigen Attribute können in Spalten, Measures, Navigationseigenschaften, Hierarchien und Ebenen angezeigt werden.  
  
## <a name="elements-and-attributes"></a>Elemente und Attribute  
 In der folgenden Tabelle sind die Elemente und Attribute aufgeführt, die das Member-Element definieren.  
  
|Name|Ist erforderlich|Description|  
|----------|-----------------|-----------------|  
|Name||Der Name für das Element (Spalte, Measure, Navigationseigenschaft, Hierarchie oder Ebene), das von der Implementierung des TMember-Typs definiert wird.|  
|Beschriftung|Benutzerkontensteuerung|Der Anzeigename für das Element.|  
|ContextualNameRule|Benutzerkontensteuerung|Das Namensformat, das verwendet wird, um Elemente zu unterscheiden. Die Inhalte dieses Attributs werden vom einfachen Typ ContextualNameRule definiert.|  
|Ausgeblendet||Ein boolescher Wert, der angibt, ob das Element für den Client ausgeblendet wird.<br /><br /> Der Standardwert lautet false und gibt an, dass Spalten im Client sichtbar sind.|  
|ReferenceName||Der Bezeichner, mit dem in einer DAX-Abfrage auf das Element verwiesen wird. Wenn dieses Attribut weggelassen wird, wird der Feldname verwendet.|  
  
## <a name="contextualnamerule-element"></a>ContextualNameRule-Element  
 Mit diesem einfachen Typ wird das Namensformat definiert, das verwendet wird, um Elemente zu unterscheiden.  
  
|value|Description|  
|-----------|-----------------|  
|None|Verwenden Sie den Attributnamen.|  
|Kontext|Verwenden Sie den Namen der eingehenden Beziehung.|  
|Merge|Verketten Sie den Namen der eingehenden Beziehung und den Namen der Eigenschaft.|  
  
## <a name="see-also"></a>Siehe auch  
 [Grundlegendes zum tabellarischen Objektmodell](../representation/understanding-tabular-object-model-at-levels-1050-through-1103.md)  
  
  
