---
title: Ändern von Daten (MDX) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- modifying data [MDX]
- Multidimensional Expressions [Analysis Services], data modifications
- MDX [Analysis Services], data modifications
- data modifications [MDX]
ms.assetid: 363b662c-b839-4971-bbd7-1842f73ce141
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 81d1df159944b96d0945bb45d2c331922d0f46e4
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "66074233"
---
# <a name="modifying-data-mdx"></a>Ändern von Daten (MDX)
  MDX (Multidimensional Expressions) kann nicht nur zum Abrufen und Verwalten von Daten aus Dimensionen und Cubes, sondern auch zum Aktualisieren oder *Rückschreiben* von Dimensions- und Cubedaten verwendet werden. Diese Updates können temporär (wie bei einer spekulativen oder "Was-wäre-wenn-Analyse") oder permanent sein (dies ist der Fall, wenn Änderungen aufgrund einer Datenanalyse vorgenommen werden müssen).  
  
 Updates von Daten sind auf Dimensions- oder Cubeebene möglich.  
  
 **Rück Schreiben von Dimensionen**  
 Die [ALTER CUBE-Anweisung (MDX)](/sql/mdx/mdx-data-definition-alter-cube) wird verwendet, um die Daten einer Dimension mit aktiviertem Schreibzugriff zu ändern, und die [REFRESH CUBE-Anweisung (MDX)](/sql/mdx/mdx-data-definition-refresh-cube) wird verwendet, um das Löschen, Erstellen oder Aktualisieren von Attributwerten zu berücksichtigen. Mit der ALTER CUBE-Anweisung können Sie auch komplexe Operationen ausführen, so z. B. das Löschen einer gesamten Unterstruktur in einer Hierarchie oder das Heraufstufen der untergeordneten Elemente eines gelöschten Elements.  
  
 **Cube-Rück schreiben**  
 Sie verwenden die [UPDATE CUBE](/sql/mdx/mdx-data-manipulation-update-cube) -Anweisung dazu, Änderungen an einem Cube mit aktiviertem Schreibzugriff vorzunehmen. Mit der UPDATE CUBE-Anweisung können Sie ein Tupel mit einem bestimmten Wert aktualisieren. Die [REFRESH CUBE-Anweisung (MDX)](/sql/mdx/mdx-data-definition-refresh-cube) wird zum Aktualisieren von Daten in einer Clientsitzung mit aktualisierten Daten vom Server verwendet.  
  
 Weitere Informationen finden Sie unter [Verwenden von Cuberückschreiben &#40;MDX&#41;](mdx-data-modification-using-cube-writebacks.md).  
  
## <a name="see-also"></a>Weitere Informationen  
 [Grundlagen der MDX-Abfrage &#40;Analysis Services&#41;](mdx-query-fundamentals-analysis-services.md)  
  
  
