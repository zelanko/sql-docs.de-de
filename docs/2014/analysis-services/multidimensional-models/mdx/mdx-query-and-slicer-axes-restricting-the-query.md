---
title: Einschränken der Abfrage mit Abfrage- und Slicerachsen (MDX) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Multidimensional Expressions [Analysis Services], axes
- queries [MDX], axes
- axes [MDX]
- MDX [Analysis Services], axes
ms.assetid: a64b8172-cd73-42f9-8847-52e967b9697a
caps.latest.revision: 29
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: e727b432afec1f42a6a111442c2263d6c48784de
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/19/2018
ms.locfileid: "36159439"
---
# <a name="restricting-the-query-with-query-and-slicer-axes-mdx"></a>Einschränken der Abfrage mit Abfrage- und Slicerachsen (MDX)
  Wenn Sie eine MDX-SELECT-Anweisung (Multidimensional Expressions) formulieren, durchsucht eine Anwendung i. d. R. einen Cube und unterteilt die Menge der Hierarchien in zwei Teilmengen:  
  
-   **Abfrageachsen**– die Menge der Hierarchien, aus denen Daten für mehrere Elemente abgerufen werden. Weitere Informationen zu den Abfrageachsen finden Sie unter [Angeben des Inhalts einer Abfrageachse &#40;MDX&#41;](mdx-query-and-slicer-axes-specify-the-contents-of-a-query-axis.md).  
  
-   **Slicerachsen**- die Menge der Hierarchien, aus denen Daten für ein einzelnes Element abgerufen werden. Weitere Informationen zu den Slicerachsen finden Sie unter [Angeben des Inhalts einer Slicerachse &#40;MDX&#41;](mdx-query-and-slicer-axes-specify-the-contents-of-a-slicer-axis.md).  
  
 Da Abfrage- und Slicerachsen aus mehreren Hierarchien des abzufragenden Cubes erstellt werden können, wird mit diesen Begriffen unterschieden zwischen den Hierarchien, die im abzufragenden Cube verwendet werden, und den Hierarchien, die im von einer MDX-Abfrage zurückgegebenen Cube erstellt werden.  
  
 Ein einfaches Beispiel mit Verwendung von Abfrage- und Slicerachsen finden Sie unter [Verwenden von Abfrage- und Slicerachsen in einem einfachen Beispiel &#40;MDX&#41;](mdx-query-and-slicer-axes-using-axes-in-a-simple-example.md).  
  
## <a name="see-also"></a>Siehe auch  
 [Arbeiten mit Elementen, Tupeln und Mengen &#40;MDX&#41;](working-with-members-tuples-and-sets-mdx.md)   
 [Grundlegendes zu MDX-Abfragen &#40;Analysis Services&#41;](mdx-query-fundamentals-analysis-services.md)  
  
  