---
title: Erstellen von Zellenberechnungen in MDX (Multidimensional Expressions) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- calculated cells [MDX]
- queries [MDX], cell calculations
- cells [MDX]
- MDX [Analysis Services], calculations
- calculation subcubes [MDX]
- calculated values [MDX]
- Multidimensional Expressions [Analysis Services], cell calculations
ms.assetid: 068aea63-d419-4791-a960-3d74e76f808e
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 2b1d0c01be4901e771278c82c4277c280aeb43ad
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "66074519"
---
# <a name="building-cell-calculations-in-mdx-mdx"></a>Erstellen von Zellenberechnungen in MDX (MDX)
  MDX (Multidimensional Expressions) stellt eine Reihe von Tools zum Generieren berechneter Werte bereit, wie z. B. berechnete Elemente, benutzerdefinierte Rollups und benutzerdefinierte Elemente. Allerdings ist es schwierig, mithilfe dieser Funktionen eine bestimmte Menge von Zellen oder eine einzelne Zelle zu beeinflussen.  
  
 Wenn Sie berechnete Werte für bestimmte Zellen generieren möchten, sollten Sie die Funktion für berechnete Zellen in MDX verwenden. Mit berechneten Zellen können Sie einen bestimmten Slice von Zellen definieren, der als *Berechnungsteilcube*bezeichnet wird, und eine Formel auf jede einzelne Zelle im Berechnungsteilcube anwenden, wobei eine optionale Bedingung zugrunde liegt, die auf jede Zelle angewendet werden kann.  
  
 Berechnete Zellen stellen außerdem eine komplexe Funktionalität bereit, z. B. zielsuchende Formeln (wie sie in KPIs verwendet werden) oder Formeln für spekulative Analysen. Dieses Maß an Funktionalität ergibt sich aus der Funktion der Durchlaufreihenfolge in [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] , die es ermöglicht, dass rekursive Durchläufe mit berechneten Zellen ausgeführt werden, wobei Berechnungsformeln auf bestimmte Durchläufe in der Durchlaufreihenfolge angewendet werden. Weitere Informationen zur Durchlaufreihenfolge finden Sie unter [Grundlegendes zu Durchlauf- und Lösungsreihenfolge &#40;MDX&#41;](mdx-data-manipulation-understanding-pass-order-and-solve-order.md).  
  
 In Bezug auf den Gültigkeitsbereich sind berechnete Zellen sowohl mit benannten Mengen als auch mit berechneten Elementen vergleichbar, da berechnete Zellen temporär für die Dauer einer Sitzung oder einer einzelnen Abfrage erstellt oder global als Teil eines Cubes zur Verfügung gestellt werden können.  
  
-   **Im Bereich einer Abfrage** Mit dem WITH-Schlüsselwort können Sie eine berechnete Zelle erstellen, die als Teil einer MDX-Abfrage definiert ist und deren Bereich somit auf die Abfrage beschränkt ist. Anschließend können Sie die berechnete Zelle in einer MDX-SELECT-Anweisung verwenden. Bei dieser Vorgehensweise kann die mit dem `WITH`-Schlüsselwort erstellte berechnete Zelle geändert werden, ohne dass die SELECT-Anweisung davon beeinflusst wird.  
  
     Weitere Informationen zum Erstellen berechneter Elemente mithilfe des WITH-Schlüsselworts finden Sie unter [Erstellen von Zellenberechnungen im Bereich einer Abfrage &#40;MDX&#41;](../../multidimensional-models-olap-logical-cube-objects/calculations.md).  
  
-   **Im Bereich einer Sitzung** Mit der CREATE CELL CALCULATION- oder der ALTER CUBE-Anweisung können Sie ein berechnetes Element erstellen, dessen Bereich mehr als den Kontext der Abfrage umfasst, dessen Bereich nämlich die Dauer der MDX-Sitzung ist.  
  
     Weitere Informationen zum Erstellen berechneter Elemente in einer Sitzung mithilfe der CREATE CELL CALCULATION- oder der ALTER CUBE-Anweisung finden Sie unter [Erstellen berechneter Zellen im Bereich einer Sitzung](mdx-cell-calculations-session-scoped-calculated-cells.md).  
  
## <a name="see-also"></a>Siehe auch  
 [ALTER CUBE-Anweisung &#40;MDX&#41;](/sql/mdx/mdx-data-definition-alter-cube)   
 [CREATE CELL CALCULATION-Anweisung &#40;MDX&#41;](/sql/mdx/mdx-data-definition-create-cell-calculation)   
 [Erstellen von Zellenberechnungen im Bereich einer Abfrage &#40;MDX&#41;](../../multidimensional-models-olap-logical-cube-objects/calculations.md)   
 [Grundlegendes zu MDX-Abfragen &#40;Analysis Services&#41;](mdx-query-fundamentals-analysis-services.md)  
  
  
