---
title: Update CUBE-Anweisung (MDX) | Microsoft-Dokumentation
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: f52dd59b67b42ad430df9bb1e9d00dce7ad6d697
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/27/2020
ms.locfileid: "68003528"
---
# <a name="mdx-data-manipulation---update-cube"></a>MDX-Datenbearbeitung – UPDATE CUBE


  Mithilfe der UPDATE CUBE-Anweisung werden Daten in eine beliebige Zelle in einem Cube zurückgeschrieben, der mit der SUM-Aggregation in den übergeordneten Cube aggregiert wird. Eine ausführlichere Erläuterung und ein Beispiel finden Sie unter "Grundlegendes zu Zuordnungen" in diesem Blogbeitrag: [Building a Write Back Application with Analysis Services (Blog)](https://go.microsoft.com/fwlink/?LinkId=394977).  
  
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
  
## <a name="remarks"></a>Bemerkungen  
 Sie können den Wert einer angegebenen Blatt- oder Nichtblattzelle in einem Cube aktualisieren. Dabei wird den abhängigen Blattzellen optional der Wert für eine angegebene Nichtblattzelle zugeordnet. Bei der durch den Tupelausdruck angegebenen Zelle kann es sich um eine beliebige gültige Zelle im mehrdimensionalen Raum handeln (d. h., die Zelle muss keine Blattzelle sein). Die Zelle muss jedoch mit der [Sum](../mdx/sum-mdx.md) -Aggregatfunktion aggregiert werden und darf kein berechnetes Element im Tupel enthalten, das zum Identifizieren der Zelle verwendet wird.  
  
 Es kann hilfreich sein, sich die **Update Cube** -Anweisung als Unterroutine vorzustellen, die automatisch eine Reihe einzelner Zellen Rückschreibe Vorgänge für Blatt-und nicht Blatt Zellen generiert, für die ein Rollup in eine angegebene Summe ausgeführt wird.  
  
 Im folgenden finden Sie eine Beschreibung der Zuordnungs Methoden.  
  
 **USE_EQUAL_ALLOCATION:** Jeder Blatt Zelle, die zur aktualisierten Zelle beiträgt, wird basierend auf dem folgenden Ausdruck ein gleicher Wert zugewiesen.  
  
```  
<leaf cell value> =   
<New Value> / Count(leaf cells that are contained in <tuple>)  
```  
  
 **USE_EQUAL_INCREMENT:** Jede Blatt Zelle, die zur aktualisierten Zelle beiträgt, wird gemäß dem folgenden Ausdruck geändert.  
  
```  
<leaf cell value> = <leaf cell value> +   
(<New Value > - <existing value>) /  
Count(leaf cells contained in <tuple>)  
```  
  
 **USE_WEIGHTED_ALLOCATION:** Jeder Blatt Zelle, die zur aktualisierten Zelle beiträgt, wird ein gleicher Wert zugewiesen, der auf dem folgenden Ausdruck basiert.  
  
```  
<leaf cell value> = < New Value> * Weight_Expression  
```  
  
 **USE_WEIGHTED_INCREMENT:** Jede Blatt Zelle, die zur aktualisierten Zelle beiträgt, wird gemäß dem folgenden Ausdruck geändert.  
  
```  
<leaf cell value> = <leaf cell value> +   
(<New Value> - <existing value>)  * Weight_Expression  
```  
  
 Wenn kein Gewichtungs Ausdruck angegeben ist, verwendet die **Update Cube** -Anweisung implizit den folgenden Ausdruck.  
  
```  
Weight_Expression = <leaf cell value> / <existing value>  
```  
  
 Ein Gewichtungsausdruck sollte als Dezimalwert zwischen 0 (null) und 1 ausgedrückt werden. Dieser Wert gibt das Verhältnis zum zugeordneten Wert an, den Sie den Blattzellen zuweisen möchten, die von der Zuordnung betroffen sind. Der Programmierer der Clientanwendung ist dafür verantwortlich, Ausdrücke zu erstellen, deren Rollupaggregatwerte gleich dem zugeordneten Wert des Ausdrucks sind.  
  
> [!CAUTION]  
>  Die Clientanwendung muss die gleichzeitige Zuordnung aller Dimensionen berücksichtigen, um unerwartete Ergebnisse, einschließlich falscher Rollupwerte oder inkonsistenter Daten, zu vermeiden.  
  
 Jede **Update Cube** -Zuordnung sollte für Transaktions Zwecke als atomarisch angesehen werden. Das bedeutet, dass beim Fehlschlagen eines einzelnen Zuordnungsvorgangs, z. B. wegen eines Fehlers in einer Formel oder einer Sicherheitsverletzung, der gesamte UPDATE CUBE-Vorgang fehlschlägt. Bevor die Berechnungen der einzelnen Zuordnungsvorgänge verarbeitet werden, wird eine Momentaufnahme der Daten erstellt, um sicherzustellen, dass die sich ergebenden Berechnungen richtig sind.  
  
> [!CAUTION]  
>  Wenn die USE_WEIGHTED_ALLOCATION-Methode für ein Measure verwendet wird, das ganze Zahlen enthält, gibt die Methode möglicherweise aufgrund von inkrementellen Rundungsänderungen ungenaue Ergebnisse zurück.  
  
> [!IMPORTANT]  
>  Wenn sich die aktualisierten Zellen nicht überlagern, kann mithilfe der **Update Isolation Level** -Eigenschaft der Verbindungszeichenfolge das Leistungsverhalten in Bezug auf UPDATE CUBE verbessert werden.  
  
## <a name="see-also"></a>Weitere Informationen  
 <xref:Microsoft.AnalysisServices.AdomdClient.AdomdConnection.ConnectionString%2A>   
 [MDX-Daten Bearbeitungsanweisungen &#40;MDX-&#41;](../mdx/mdx-data-manipulation-statements-mdx.md)  
  
  
