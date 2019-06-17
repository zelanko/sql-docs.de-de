---
title: UPDATE CUBE-Anweisung (MDX) | Microsoft-Dokumentation
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 878f103e236a198ff71181a64b39400c8f6ea0ca
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "63187621"
---
# <a name="mdx-data-manipulation---update-cube"></a>MDX-Datenbearbeitung – UPDATE CUBE


  Mithilfe der UPDATE CUBE-Anweisung werden Daten in eine beliebige Zelle in einem Cube zurückgeschrieben, der mit der SUM-Aggregation in den übergeordneten Cube aggregiert wird. Weitere erläuterungen und ein Beispiel finden Sie unter "Grundlagen zu Zuordnungen" in diesem Blogbeitrag: [Erstellen einer Rückschreibeanwendung mit Analysis Services (Blog)](https://go.microsoft.com/fwlink/?LinkId=394977).  
  
## <a name="syntax"></a>Syntax  
  
```  
  
UPDATE [ CUBE ] Cube_Name   
   SET   
            <update clause>   
           [, <update clause> ...n ]  
  
<update clause> ::=   
      Tuple_Expression[.VALUE]= New_Value  
      [   
        USE_EQUAL_ALLOCATION   
        | USE_EQUAL_INCREMENT   
        | USE_WEIGHTED_ALLOCATION [ BY Weight_Expression]   
        | USE_WEIGHTED_INCREMENT [ BY Weight_Expression]  
      ]  
```  
  
## <a name="arguments"></a>Argumente  
 *Cube_Name*  
 Eine gültige Zeichenfolge, die den Namen eines Cubes bereitstellt.  
  
 *Tuple_Expression*  
 Ein gültiger MDX-Ausdruck (Multidimensional Expressions), der ein Tupel zurückgibt.  
  
 *New_Value*  
 Ein gültiger numerischer Ausdruck.  
  
 *Weight_Expression*  
 Ein gültiger numerischer MDX-Ausdruck (Multidimensional Expressions), der einen Dezimalwert zwischen 0 und 1 zurückgibt.  
  
## <a name="remarks"></a>Hinweise  
 Sie können den Wert einer angegebenen Blatt- oder Nichtblattzelle in einem Cube aktualisieren. Dabei wird den abhängigen Blattzellen optional der Wert für eine angegebene Nichtblattzelle zugeordnet. Bei der durch den Tupelausdruck angegebenen Zelle kann es sich um eine beliebige gültige Zelle im mehrdimensionalen Raum handeln (d. h., die Zelle muss keine Blattzelle sein). Allerdings muss die Zelle aggregiert werden, mit der [Summe](../mdx/sum-mdx.md) Aggregatfunktion und dürfen kein berechnetes Element im Tupel, das verwendet wird, um die Zelle zu identifizieren.  
  
 Es kann hilfreich sein, vorstellen der **UPDATE CUBE** -Anweisung als Unterroutine, die automatisch eine Reihe von einzelnen Vorgänge zum Zellenrückschreiben Blatt- und innerer Zellen generieren, die eine angegebene Summe Rollup wird.  
  
 Im folgenden finden eine Beschreibung der Methoden der Zuordnung.  
  
 **USE_EQUAL_ALLOCATION:** Jeder Blattzelle, die zur aktualisierten Zelle beiträgt, wird derselbe Wert basierend auf den folgenden Ausdruck zugewiesen werden.  
  
```  
<leaf cell value> =   
<New Value> / Count(leaf cells that are contained in <tuple>)  
```  
  
 **USE_EQUAL_INCREMENT:** jeder Blattzelle, die zur aktualisierten Zelle beiträgt, wird entsprechend dem folgenden Ausdruck geändert werden.  
  
```  
<leaf cell value> = <leaf cell value> +   
(<New Value > - <existing value>) /  
Count(leaf cells contained in <tuple>)  
```  
  
 **USE_WEIGHTED_ALLOCATION:** Jeder Blattzelle, die zur aktualisierten Zelle beiträgt wird derselbe Wert zugewiesen, der auf den folgenden Ausdruck basiert.  
  
```  
<leaf cell value> = < New Value> * Weight_Expression  
```  
  
 **USE_WEIGHTED_INCREMENT:** Jeder Blattzelle, die zur aktualisierten Zelle beiträgt, wird entsprechend dem folgenden Ausdruck geändert werden.  
  
```  
<leaf cell value> = <leaf cell value> +   
(<New Value> - <existing value>)  * Weight_Expression  
```  
  
 Wenn ein Gewichtungsausdruck nicht angegeben wird, die **UPDATE CUBE** -Anweisung verwendet implizit den folgenden Ausdruck.  
  
```  
Weight_Expression = <leaf cell value> / <existing value>  
```  
  
 Ein Gewichtungsausdruck sollte als Dezimalwert zwischen 0 (null) und 1 ausgedrückt werden. Dieser Wert gibt das Verhältnis zum zugeordneten Wert an, den Sie den Blattzellen zuweisen möchten, die von der Zuordnung betroffen sind. Der Programmierer der Clientanwendung ist dafür verantwortlich, Ausdrücke zu erstellen, deren Rollupaggregatwerte gleich dem zugeordneten Wert des Ausdrucks sind.  
  
> [!CAUTION]  
>  Die Clientanwendung muss die gleichzeitige Zuordnung aller Dimensionen berücksichtigen, um unerwartete Ergebnisse, einschließlich falscher Rollupwerte oder inkonsistenter Daten, zu vermeiden.  
  
 Jede **UPDATE CUBE** Zuordnung sollte um zu transaktionszwecken atomar betrachtet werden. Das bedeutet, dass beim Fehlschlagen eines einzelnen Zuordnungsvorgangs, z. B. wegen eines Fehlers in einer Formel oder einer Sicherheitsverletzung, der gesamte UPDATE CUBE-Vorgang fehlschlägt. Bevor die Berechnungen der einzelnen Zuordnungsvorgänge verarbeitet werden, wird eine Momentaufnahme der Daten erstellt, um sicherzustellen, dass die sich ergebenden Berechnungen richtig sind.  
  
> [!CAUTION]  
>  Wenn die USE_WEIGHTED_ALLOCATION-Methode für ein Measure verwendet wird, das ganze Zahlen enthält, gibt die Methode möglicherweise aufgrund von inkrementellen Rundungsänderungen ungenaue Ergebnisse zurück.  
  
> [!IMPORTANT]  
>  Wenn sich die aktualisierten Zellen nicht überlagern, kann mithilfe der **Update Isolation Level** -Eigenschaft der Verbindungszeichenfolge das Leistungsverhalten in Bezug auf UPDATE CUBE verbessert werden.  
  
## <a name="see-also"></a>Siehe auch  
 <xref:Microsoft.AnalysisServices.AdomdClient.AdomdConnection.ConnectionString%2A>   
 [MDX-Datenbearbeitungsanweisungen &#40;MDX&#41;](../mdx/mdx-data-manipulation-statements-mdx.md)  
  
  
