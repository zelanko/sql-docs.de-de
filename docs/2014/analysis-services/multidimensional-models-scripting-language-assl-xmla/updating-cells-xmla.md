---
title: Aktualisieren von Zellen (XMLA) | Microsoft Docs
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
manager: craigg
ms.openlocfilehash: f0eab50aa7e70aedee93eef2cefee648e6ceb5c9
ms.sourcegitcommit: a3f5c3742d85d21f6bde7c6ae133060dcf1ddd44
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/15/2020
ms.locfileid: "81387890"
---
# <a name="updating-cells-xmla"></a>Aktualisieren von Zellen (XMLA)
  Sie können den Befehl [UpdateCells](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/updatecells-element-xmla) verwenden, um den Wert einer oder mehrerer Zellen in einem Cube zu ändern, der für das Schreiben von Cubeen aktiviert ist. [!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] speichert die aktualisierten Informationen in einer separaten Rückschreibetabelle für jede Partition, die zu aktualisierende Zellen [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] enthält.  
  
> [!NOTE]  
>  Der Befehl `UpdateCells` unterstützt während des Rückschreibens keine Zuordnungen. Um das zugewiesene Rückschreiben zu verwenden, sollten Sie den [Befehl Anweisung](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/statement-element-xmla) verwenden, um eine MDX-Anweisung (Multidimensional Expressions) zu senden. Weitere Informationen finden Sie unter [UPDATE CUBE-Anweisung &#40;MDX&#41;](/sql/mdx/mdx-data-manipulation-update-cube).  
  
## <a name="specifying-cells"></a>Angeben von Zellen  
 Die [Cell-Eigenschaft](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/cell-element-xmla) des `UpdateCells` Befehls enthält die zu aktualisierenden Zellen. Sie identifizieren jede Zelle in der Eigenschaft `Cell` mithilfe der Ordinalzahl dieser Zelle. Konzeptionell [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] werden Zellen in einem Cube so nummeriert, als wäre der Cube ein *p-dimensionales*Array, wobei *p* die Anzahl der Achsen ist. Die Zellen werden in zeilengerichteter Reihenfolge adressiert. Die folgende Abbildung zeigt die Formel für die Berechnung der Ordinalzahl einer Zelle.  
  
 ![Formel zum Berechnen der Zellenordnungsposition](../../analysis-services/dev-guide/media/cellordinalformula.gif "Formel zum Berechnen der Zellenordnungsposition")  
  
 Sobald Sie die Ordinalnummer einer Zelle kennen, können Sie den beabsichtigten Wert der Zelle in der [Value-Eigenschaft](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/value-element-xmla) der [Cell-Eigenschaft](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/cell-element-xmla) angeben.  
  
## <a name="see-also"></a>Weitere Informationen  
 [UpdateElement &#40;XMLA-&#41;](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/update-element-xmla)   
 [Entwickeln mit XMLA in Analysis Services](../multidimensional-models-scripting-language-assl-xmla/developing-with-xmla-in-analysis-services.md)  
  
  
