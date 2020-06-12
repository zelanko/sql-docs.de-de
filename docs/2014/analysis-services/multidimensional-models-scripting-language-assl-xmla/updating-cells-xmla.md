---
title: Aktualisieren von Zellen (XMLA) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 04/27/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: reference
helpviewer_keywords:
- modifying cells
- XMLA, cells
- updating cells
- cells [Analysis Services]
- XML for Analysis, cells
ms.assetid: a1c61496-36ee-4bce-98d9-d13440d349aa
author: minewiskan
ms.author: owend
ms.openlocfilehash: 2c3d9a7c27533666c75102d9eac3b8311bfe4af6
ms.sourcegitcommit: f0772f614482e0b3cde3609e178689ce62ca3a19
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/09/2020
ms.locfileid: "84544911"
---
# <a name="updating-cells-xmla"></a>Aktualisieren von Zellen (XMLA)
  Sie können den [UpdateCells](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/updatecells-element-xmla) -Befehl verwenden, um den Wert einer oder mehrerer Zellen in einem Cube zu ändern, der für das Cuberückschreiben aktiviert ist. [!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] speichert die aktualisierten Informationen in einer separaten Rück schreibe Tabelle für jede Partition, die zu Aktualisier Ende Zellen enthält.  
  
> [!NOTE]  
>  Der Befehl `UpdateCells` unterstützt während des Rückschreibens keine Zuordnungen. Um das zugeordnete Rück schreiben zu verwenden, verwenden Sie den [Anweisungs](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/statement-element-xmla) Befehl, um eine MDX-UPDATE Anweisung (Multidimensional Expressions) zu senden. Weitere Informationen finden Sie unter [Update CUBE-Anweisung &#40;MDX-&#41;](/sql/mdx/mdx-data-manipulation-update-cube).  
  
## <a name="specifying-cells"></a>Angeben von Zellen  
 Die [Cell](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/cell-element-xmla) -Eigenschaft des `UpdateCells` Befehls enthält die zu aktualisierenden Zellen. Sie identifizieren jede Zelle in der Eigenschaft `Cell` mithilfe der Ordinalzahl dieser Zelle. Konzeptionell [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] zählt Zellen in einem Cube so, als ob der Cube ein *p*-dimensionales Array wäre, wobei *p* für die Anzahl der Achsen steht. Die Zellen werden in zeilengerichteter Reihenfolge adressiert. Die folgende Abbildung zeigt die Formel für die Berechnung der Ordinalzahl einer Zelle.  
  
 ![Formel zum Berechnen der Zellenordnungsposition](../../analysis-services/dev-guide/media/cellordinalformula.gif "Formel zum Berechnen der Zellenordnungsposition")  
  
 Nachdem Sie die Ordinalzahl einer Zelle kennen, können Sie den beabsichtigten Wert der Zelle in der [value](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/value-element-xmla) -Eigenschaft der [Cell](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/cell-element-xmla) -Eigenschaft angeben.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Element &#40;XMLA aktualisieren&#41;](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/update-element-xmla)   
 [Entwickeln mit XMLA in Analysis Services](../multidimensional-models-scripting-language-assl-xmla/developing-with-xmla-in-analysis-services.md)  
  
  
