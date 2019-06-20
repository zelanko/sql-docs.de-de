---
title: Erstellen von berechneten Elementen in MDX (Multidimensional Expressions) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- MDX [Analysis Services], calculated members
- calculated members [MDX]
- Multidimensional Expressions [Analysis Services], calculated members
- queries [MDX], calculated members
ms.assetid: 9322e8b8-43e1-4e02-a7d1-e41a586a5bb8
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 0275a071c5548de7086844e48cec7eff3bb72d31
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "66074541"
---
# <a name="building-calculated-members-in-mdx-mdx"></a>Erstellen von berechneten Elementen in MDX (MDX)
  Ein berechnetes Element in MDX (Multidimensional Expressions) ist ein Element, das durch Berechnen eines MDX-Ausdrucks aufgelöst wird, um einen Wert zurückzugeben. Diese einfach klingende Definition hat immense Auswirkungen. Die Erstellung und Verwendung von berechneten Elementen in einer MDX-Abfrage eröffnet umfassende Änderungsmöglichkeiten für mehrdimensionale Daten.  
  
 Sie können berechnete Elemente an jedem beliebigen Punkt in einer Hierarchie erstellen. Sie können außerdem berechnete Elemente erstellen, die nicht nur von vorhandenen Elementen in einem Cube abhängen, sondern auch von anderen berechneten Elementen, die in demselben MDX-Ausdruck definiert sind.  
  
 Sie können berechnete Elemente in einem der folgenden Kontexte definieren:  
  
-   **Im Bereich einer Abfrage** : Mit dem WITH-Schlüsselwort können Sie ein berechnetes Element erstellen, das als Teil einer MDX-Abfrage definiert ist und dessen Bereich somit auf die Abfrage beschränkt ist. Anschließend können Sie das berechnete Element in einer SELECT-Anweisung von MDX verwenden. Bei dieser Vorgehensweise kann das mit dem WITH-Schlüsselwort erstellte berechnete Element geändert werden, ohne dass die SELECT-Anweisung davon beeinflusst wird.  
  
     Weitere Informationen zum Erstellen berechneter Elemente mithilfe des WITH-Schlüsselworts finden Sie unter [Erstellen berechneter Elemente im Bereich einer Abfrage &#40;MDX&#41;](mdx-calculated-members-query-scoped-calculated-members.md).  
  
-   **Im Bereich einer Sitzung**: Mit der CREATE MEMBER-Anweisung können Sie ein berechnetes Element erstellen, dessen Bereich umfangreicher als der Kontext der Abfrage ist, d.h. der Dauer der MDX-Sitzung entspricht. Ein mit der CREATE MEMBER-Anweisung definiertes berechnetes Element ist für alle MDX-Abfragen in dieser Sitzung verfügbar. Die CREATE MEMBER-Anweisung ist z. B. in einer Clientanwendung sinnvoll, die die gleiche Menge in unterschiedlichen Abfragen wiederverwendet.  
  
     Weitere Informationen zum Erstellen berechneter Elemente in einer Sitzung mithilfe der CREATE MEMBER-Anweisung finden Sie unter [Erstellen berechneter Elemente im Bereich einer Abfrage &#40;MDX&#41;](mdx-calculated-members-session-scoped-calculated-members.md).  
  
## <a name="see-also"></a>Siehe auch  
 [CREATE MEMBER-Anweisung &#40;MDX&#41;](/sql/mdx/mdx-data-definition-create-member)   
 [MDX-Funktionsreferenz &#40;MDX&#41;](/sql/mdx/mdx-function-reference-mdx)   
 [SELECT-Anweisung &#40;MDX&#41;](/sql/mdx/mdx-data-manipulation-select)  
  
  
