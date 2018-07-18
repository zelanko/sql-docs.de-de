---
title: Erstellen von benannten Mengen in MDX (Multidimensional Expressions) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- Multidimensional Expressions [Analysis Services], named sets
- named sets [MDX]
- sets [MDX]
- MDX [Analysis Services], named sets
- queries [MDX], named sets
- set expressions [MDX]
ms.assetid: 213b0035-e96d-4ba0-83f2-ded206905603
caps.latest.revision: 27
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: f990def60c377ca84b5dde593470634f3927b496
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/02/2018
ms.locfileid: "37297460"
---
# <a name="building-named-sets-in-mdx-mdx"></a>Erstellen von benannten Mengen in MDX (MDX)
  Ein Mengenausdruck kann aus einer langen und komplexen und deshalb schwer verständlichen Deklaration bestehen. Wenn ein Mengenausdruck häufig verwendet wird, kann das wiederholte Definieren der Menge lästig werden. Um das Verwenden längerer, komplexer oder häufig verwendeter Ausdrücke zu vereinfachen, ermöglicht MDX (Multidimensional Expressions) die Definition eines solchen Ausdrucks als *benannte Menge*.  
  
 Grundsätzlich handelt es sich bei einer benannten Menge um einen Mengenausdruck, dem ein Alias zugewiesen wurde. Eine benannte Menge kann alle Elemente oder Funktionen enthalten, die normalerweise in eine Menge aufgenommen werden können. Da der Alias der benannten Menge von MDX als Mengenausdruck behandelt wird, können Sie den Alias überall verwenden, wo ein Mengenausdruck zulässig ist.  
  
 Sie können eine benannte Menge in einem der folgenden Kontexte definieren:  
  
-   **Im Bereich einer Abfrage** Mit dem WITH-Schlüsselwort können Sie eine benannte Menge erstellen, die als Teil einer MDX-Abfrage definiert ist und deren Bereich daher auf die Abfrage beschränkt ist. Anschließend können Sie die benannte Menge in einer SELECT-Anweisung von MDX verwenden. Bei dieser Vorgehensweise kann die mit dem WITH-Schlüsselwort erstellte benannte Menge geändert werden, ohne dass die SELECT-Anweisung davon beeinflusst wird.  
  
     Weitere Informationen zum Erstellen benannter Mengen mithilfe des WITH-Schlüsselworts finden Sie unter [Erstellen benannter Mengen im Bereich einer Abfrage &#40;MDX&#41;](mdx-named-sets-creating-query-scoped-named-sets.md).  
  
-   **Im Bereich einer Sitzung** Mit der CREATE SET-Anweisung können Sie eine benannte Menge erstellen, deren Bereich über den Kontext der Abfrage hinausgeht, d.h., deren Bereich die Dauer der MDX-Sitzung ist. Eine mit der CREATE SET-Anweisung definierte benannte Menge ist für alle MDX-Abfragen in dieser Sitzung verfügbar. Die CREATE SET-Anweisung ist z. B. in einer Clientanwendung sinnvoll, die die gleiche Menge in unterschiedlichen Abfragen wiederverwendet.  
  
     Weitere Informationen zum Erstellen benannter Mengen in einer Sitzung mithilfe der CREATE SET-Anweisung finden Sie unter [Erstellen benannter Mengen im Bereich einer Sitzung &#40;MDX&#41;](mdx-named-sets-creating-session-scoped-named-sets.md).  
  
## <a name="see-also"></a>Siehe auch  
 [SELECT-Anweisung &#40;MDX&#41;](/sql/mdx/mdx-data-manipulation-select)   
 [CREATE SET-Anweisung &#40;MDX&#41;](/sql/mdx/mdx-data-definition-create-set)   
 [Grundlegendes zu MDX-Abfrage &#40;Analysis Services&#41;](mdx-query-fundamentals-analysis-services.md)  
  
  
