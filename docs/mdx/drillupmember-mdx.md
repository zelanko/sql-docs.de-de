---
description: DrillupMember (MDX)
title: DrillupMember (MDX) | Microsoft-Dokumentation
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: 9db34a9117bf7405511b86e8e989d2e002cb12d2
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/17/2020
ms.locfileid: "88494943"
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
  
## <a name="remarks"></a>Bemerkungen  
 Die **DrillupMember** -Funktion gibt eine Menge von Membern basierend auf den Membern zurück, die in der ersten Menge, die Nachfolger der Elemente in der zweiten Menge sind, angegeben sind. Die erste Menge kann jede beliebige Dimensionalität aufweisen, die zweite muss jedoch eine eindimensionale Menge enthalten. Die Reihenfolge der Originalelemente in der ersten Menge wird beibehalten. Die Funktion erstellt die Menge, indem nur die Elemente aus der ersten Menge eingeschlossen werden, die unmittelbare nachfolgende Werte von Elementen in der zweiten Menge sind. Ist der unmittelbare Vorgänger eines Elements in der ersten Menge nicht in der zweiten vorhanden, wird das Element in der ersten Menge in die von der Funktion zurückgegebene Menge eingeschlossen. Nachfolgende Werte in der ersten Menge, die einem Vorgängerelement in der zweiten Menge vorausgehen, werden ebenfalls eingeschlossen.  
  
 Die erste Menge kann auch Tupel anstelle von Elementen enthalten. Der Drilldown für Tupel ist eine Erweiterung von OLE DB und gibt eine Menge von Tupeln anstelle von Elementen zurück.  
  
> [!IMPORTANT]  
>  Ein Drillup wird nur für ein Element durchgeführt, auf das direkt ein untergeordnetes Element oder ein Nachfolger folgt. Die Reihenfolge der Elemente in der Gruppe ist für die Drilldown \* -und Drillup- \* Funktions Familien von Bedeutung. Verwenden Sie ggf. die **Hierarchize** -Funktion, um die Elemente der ersten Menge entsprechend zu ordnen.  
  
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
  
 Beispiel zwei zeigt die Wichtigkeit der Elementreihenfolge. Da **DrillupMember** nur auf den Membern führt, die unmittelbar von Nachfolgern in der ersten Menge gefolgt werden, führt er keinen Drillup auf dem Canada-Member durch. Kanada wird vom Nachfolger durch die Vereinigten Staaten und Colorado getrennt. Wenn Sie die Elemente so neu anordnen, dass sich Kanada direkt über Alberta befindet, werden Alberta und Braunschweig aus dem Rowset ausgeschlossen.  
  
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
  
 In Beispiel 3 wird gezeigt, wie die Verwendung von **Hierarchize** die Auswirkungen der Element Reihenfolge mindern und einen Drilldown für das Mitglied Kanadas durchführen kann.  
  
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
  
## <a name="see-also"></a>Weitere Informationen  
 [MDX-Funktionsreferenz &#40;MDX&#41;](../mdx/mdx-function-reference-mdx.md)  
  
  
