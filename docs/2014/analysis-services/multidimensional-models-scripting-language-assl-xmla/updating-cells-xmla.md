---
title: Aktualisieren von Zellen (XMLA) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 04/27/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- modifying cells
- XMLA, cells
- updating cells
- cells [Analysis Services]
- XML for Analysis, cells
ms.assetid: a1c61496-36ee-4bce-98d9-d13440d349aa
caps.latest.revision: 12
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: d1b25b30623ddcdfe4c21442d15fd0cfa0966cc6
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/02/2018
ms.locfileid: "37275976"
---
# <a name="updating-cells-xmla"></a>Aktualisieren von Zellen (XMLA)
  Sie können die [UpdateCells](../xmla/xml-elements-commands/updatecells-element-xmla.md) Befehl zum Ändern des Werts von einer oder mehrerer Zellen in einem Cube, der rückschreibemodus aktiviert. [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] Speichert die aktualisierten Informationen in einer separaten Rückschreibetabelle für jede Partition, die zu aktualisierende Zellen enthält.  
  
> [!NOTE]  
>  Der Befehl `UpdateCells` unterstützt während des Rückschreibens keine Zuordnungen. Um zugeordnetes Rückschreiben zu verwenden, sollten Sie verwenden die [Anweisung](../xmla/xml-elements-commands/statement-element-xmla.md) Befehl aus, um eine MDX (Multidimensional Expressions) UPDATE-Anweisung zu senden. Weitere Informationen finden Sie unter [UPDATE CUBE-Anweisung &#40;MDX&#41;](/sql/mdx/mdx-data-manipulation-update-cube).  
  
## <a name="specifying-cells"></a>Angeben von Zellen  
 Die [Zelle](../xmla/xml-elements-properties/cell-element-xmla.md) Eigenschaft der `UpdateCells` -Befehl enthält, die zu aktualisierende Zellen. Sie identifizieren jede Zelle in der Eigenschaft `Cell` mithilfe der Ordinalzahl dieser Zelle. Im Prinzip [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] Zellen in einem Cube Zahlen, als sei der Cube eine *p*-, eindimensionales Array, in denen *p* ist die Anzahl der Achsen. Die Zellen werden in zeilengerichteter Reihenfolge adressiert. Die folgende Abbildung zeigt die Formel für die Berechnung der Ordinalzahl einer Zelle.  
  
 ![Formel zum Berechnen der Ordnungsposition der Zelle](../../../2014/analysis-services/dev-guide/media/cellordinalformula.gif "Formel zum Berechnen der Ordnungsposition der Zelle")  
  
 Wenn Sie die Ordinalzahl einer Zelle kennen, können Sie angeben, den vorgesehenen Wert der Zelle in der [Wert](../xmla/xml-elements-properties/value-element-xmla.md) Eigenschaft der [Zelle](../xmla/xml-elements-properties/cell-element-xmla.md) Eigenschaft.  
  
## <a name="see-also"></a>Siehe auch  
 [Update-Element &#40;XMLA&#41;](../xmla/xml-elements-commands/update-element-xmla.md)   
 [Entwickeln mit XMLA in Analysis Services](../multidimensional-models-scripting-language-assl-xmla/developing-with-xmla-in-analysis-services.md)  
  
  
