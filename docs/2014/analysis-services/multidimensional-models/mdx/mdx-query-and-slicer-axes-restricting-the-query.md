---
title: Einschränken der Abfrage mit Abfrage- und Slicerachsen (MDX) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
ms.topic: conceptual
helpviewer_keywords:
- Multidimensional Expressions [Analysis Services], axes
- queries [MDX], axes
- axes [MDX]
- MDX [Analysis Services], axes
ms.assetid: a64b8172-cd73-42f9-8847-52e967b9697a
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 3413f4da8443df07732e1c6acca5ed6112cb59dd
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62725344"
---
# <a name="restricting-the-query-with-query-and-slicer-axes-mdx"></a>Einschränken der Abfrage mit Abfrage- und Slicerachsen (MDX)
  Wenn Sie eine MDX-SELECT-Anweisung (Multidimensional Expressions) formulieren, durchsucht eine Anwendung i. d. R. einen Cube und unterteilt die Menge der Hierarchien in zwei Teilmengen:  
  
-   **Abfrageachsen**-die Menge der Hierarchien, aus denen Daten für mehrere Elemente abgerufen. Weitere Informationen zu den Abfrageachsen finden Sie unter [Angeben des Inhalts einer Abfrageachse &#40;MDX&#41;](mdx-query-and-slicer-axes-specify-the-contents-of-a-query-axis.md).  
  
-   **Slicer-Achse**-die Menge der Hierarchien, aus denen Daten für ein einzelnes Element abgerufen. Weitere Informationen zu den Slicerachsen finden Sie unter [Angeben des Inhalts einer Slicerachse &#40;MDX&#41;](mdx-query-and-slicer-axes-specify-the-contents-of-a-slicer-axis.md).  
  
 Da Abfrage- und Slicerachsen aus mehreren Hierarchien des abzufragenden Cubes erstellt werden können, wird mit diesen Begriffen unterschieden zwischen den Hierarchien, die im abzufragenden Cube verwendet werden, und den Hierarchien, die im von einer MDX-Abfrage zurückgegebenen Cube erstellt werden.  
  
 Ein einfaches Beispiel mit Verwendung von Abfrage- und Slicerachsen finden Sie unter [Verwenden von Abfrage- und Slicerachsen in einem einfachen Beispiel &#40;MDX&#41;](mdx-query-and-slicer-axes-using-axes-in-a-simple-example.md).  
  
## <a name="see-also"></a>Siehe auch  
 [Verwenden von Elementen, Tupeln und Mengen &#40;MDX&#41;](working-with-members-tuples-and-sets-mdx.md)   
 [Grundlegendes zu MDX-Abfragen &#40;Analysis Services&#41;](mdx-query-fundamentals-analysis-services.md)  
  
  
