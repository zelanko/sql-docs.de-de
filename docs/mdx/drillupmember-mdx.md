---
title: DrillupMember (MDX) | Microsoft-Dokumentation
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 31981669d5d08e63a853b8daa530b886f9b7dfbe
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "62690768"
---
# <a name="drillupmember-mdx"></a>DrillupMember (MDX)


  Gibt die Elemente in einer angegebenen Menge zurück, die keine Nachfolger von Elementen in einer zweiten angegebenen Menge sind.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
DrillupMember(Set_Expression1, Set_Expression2)   
```  
  
## <a name="arguments"></a>Argumente  
 *Set_Expression1*  
 Ein gültiger MDX-Ausdruck (Multidimensional Expressions), der eine Menge zurückgibt.  
  
 *Set_Expression2*  
 Ein gültiger MDX-Ausdruck (Multidimensional Expressions), der eine Menge zurückgibt.  
  
## <a name="remarks"></a>Hinweise  
 Die **DrillupMember** Funktionsergebnis ist eine Menge von Elementen, die basierend auf den in der ersten Menge angegebenen Elementen, die Nachfolger von Elementen in der zweiten Menge sind. Die erste Menge kann jede beliebige Dimensionalität aufweisen, die zweite muss jedoch eine eindimensionale Menge enthalten. Die Reihenfolge der Originalelemente in der ersten Menge wird beibehalten. Die Funktion erstellt die Menge, indem nur die Elemente aus der ersten Menge eingeschlossen werden, die unmittelbare nachfolgende Werte von Elementen in der zweiten Menge sind. Ist der unmittelbare Vorgänger eines Elements in der ersten Menge nicht in der zweiten vorhanden, wird das Element in der ersten Menge in die von der Funktion zurückgegebene Menge eingeschlossen. Nachfolgende Werte in der ersten Menge, die einem Vorgängerelement in der zweiten Menge vorausgehen, werden ebenfalls eingeschlossen.  
  
 Die erste Menge kann auch Tupel anstelle von Elementen enthalten. Der Drilldown für Tupel ist eine Erweiterung von OLE DB und gibt eine Menge von Tupeln anstelle von Elementen zurück.  
  
> [!IMPORTANT]  
>  Ein Drillup wird nur für ein Element durchgeführt, auf das direkt ein untergeordnetes Element oder ein Nachfolger folgt. Die Reihenfolge der Elemente in der Menge ist wichtig, für sowohl den Drilldown\* und Drillups\* Funktionsreihe. Erwägen Sie die Verwendung der **Hierarchize** Funktion, um die Elemente der ersten Menge entsprechend zu sortieren.  
  
## <a name="example"></a>Beispiel  
 Die folgenden drei Beispiele sind mit Ausnahme der zweiten Menge identisch. Im ersten Beispiel lautet der zweite Satz "Vereinigte Staaten". Demzufolge wird Colorado aus dem Resultset ausgeschlossen. Es ist ein untergeordnetes Element der Vereinigten Staaten.  
  
```  
SELECT DrillUpMember (   
  { [Geography].[Geography].[Country].[Canada]   
   ,[Geography].[Geography].[Country].[United States]   
   ,[Geography].[Geography].[State-Province].[Colorado]   
   ,[Geography].[Geography].[State-Province].[Alberta]   
   ,[Geography].[Geography].[State-Province].[Brunswick]    
 }   
 , {[Geography].[Geography].[Country].[United States]}   
 ) ON 0   
FROM [Adventure Works]  
```  
  
 Beispiel zwei zeigt die Wichtigkeit der Elementreihenfolge. Da **DrillupMember** Drillup nur auf die Elemente, die sofort von untergeordneten Objekten in der ersten Menge eingehalten werden, es werden keinen Drillup auf dem Kanada-Element. Kanada wird vom Nachfolger durch die Vereinigten Staaten und Colorado getrennt. Wenn Sie die Elemente so neu anordnen, dass sich Kanada direkt über Alberta befindet, werden Alberta und Braunschweig aus dem Rowset ausgeschlossen.  
  
```  
SELECT DrillUpMember (   
 {  [Geography].[Geography].[Country].[Canada]   
   ,[Geography].[Geography].[Country].[United States]   
   ,[Geography].[Geography].[State-Province].[Colorado]   
   ,[Geography].[Geography].[State-Province].[Alberta]   
   ,[Geography].[Geography].[State-Province].[Brunswick]    
 }   
 , {[Geography].[Geography].[Country].[Canada]}   
 )   
ON 0   
FROM [Adventure Works]  
```  
  
 Beispiel drei zeigt wie die Verwendung von **Hierarchize** können verringern, die Auswirkungen der Elementreihenfolge, sodass ein Drillup auf dem Kanada-Element.  
  
```  
SELECT DrillUpMember (   
 Hierarchize   
  (   
   { [Geography].[Geography].[Country].[Canada]   
    ,[Geography].[Geography].[Country].[United States]   
    ,[Geography].[Geography].[State-Province].[Colorado]   
    ,[Geography].[Geography].[State-Province].[Alberta]   
    ,[Geography].[Geography].[State-Province].[Brunswick]    
   }   
  ), {[Geography].[Geography].[Country].[Canada]}   
 )   
ON 0   
FROM [Adventure Works]  
  
```  
  
## <a name="see-also"></a>Siehe auch  
 [MDX-Funktionsreferenz &#40;MDX&#41;](../mdx/mdx-function-reference-mdx.md)  
  
  
