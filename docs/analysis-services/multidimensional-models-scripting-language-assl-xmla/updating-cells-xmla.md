---
title: Aktualisieren von Zellen (XMLA) | Microsoft-Dokumentation
ms.date: 05/02/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: xmla
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 0cfee2adf9d730b458fd482317d16d963f15ebc1
ms.sourcegitcommit: 7fe14c61083684dc576d88377e32e2fc315b7107
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/26/2018
ms.locfileid: "50146774"
---
# <a name="updating-cells-xmla"></a>Aktualisieren von Zellen (XMLA)
  Sie können die [UpdateCells](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/updatecells-element-xmla) Befehl zum Ändern des Werts von einer oder mehrerer Zellen in einem Cube, der rückschreibemodus aktiviert. [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] Speichert die aktualisierten Informationen in einer separaten Rückschreibetabelle für jede Partition, die zu aktualisierende Zellen enthält.  
  
> [!NOTE]  
>  Die **UpdateCells** Befehl unterstützt während des Rückschreibens keine Zuordnungen. Um zugeordnetes Rückschreiben zu verwenden, sollten Sie verwenden die [Anweisung](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/statement-element-xmla) Befehl aus, um eine MDX (Multidimensional Expressions) UPDATE-Anweisung zu senden. Weitere Informationen finden Sie unter [UPDATE CUBE-Anweisung &#40;MDX&#41;](../../mdx/mdx-data-manipulation-update-cube.md).  
  
## <a name="specifying-cells"></a>Angeben von Zellen  
 Die [Zelle](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/cell-element-xmla) Eigenschaft der **UpdateCells** -Befehl enthält, die zu aktualisierende Zellen. Sie identifizieren jede Zelle in der **Zelle** Eigenschaft mithilfe der Ordinalzahl dieser Zelle. Im Prinzip [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] Zellen in einem Cube Zahlen, als sei der Cube eine *p*-, eindimensionales Array, in denen *p* ist die Anzahl der Achsen. Die Zellen werden in zeilengerichteter Reihenfolge adressiert. Die folgende Abbildung zeigt die Formel für die Berechnung der Ordinalzahl einer Zelle.  
  
 ![Formel zum Berechnen der Ordnungsposition der Zelle](../../analysis-services/multidimensional-models-scripting-language-assl-xmla/media/cellordinalformula.gif "Formel zum Berechnen der Ordnungsposition der Zelle")  
  
 Wenn Sie die Ordinalzahl einer Zelle kennen, können Sie angeben, den vorgesehenen Wert der Zelle in der [Wert](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/value-element-xmla) Eigenschaft der [Zelle](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/cell-element-xmla) Eigenschaft.  
  
## <a name="see-also"></a>Siehe auch  
 [Update-Element &#40;XMLA&#41;](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/update-element-xmla)   
 [Entwickeln mit XMLA in Analysis Services](../../analysis-services/multidimensional-models-scripting-language-assl-xmla/developing-with-xmla-in-analysis-services.md)  
  
  
