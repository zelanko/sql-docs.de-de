---
title: Drillthrough Aktionsformular-Editor (Registerkarte ' Aktionen ', Cube-Designer) (Analysis Services – mehrdimensionale Daten) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- sql12.asvs.cubeeditor.actionexpression.drillthroughaction.f1
ms.assetid: 225fd818-b5ea-494f-b67b-66e09798274a
caps.latest.revision: 22
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: 81b7cde92983bf16f37b586389c059dfbff639d9
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/19/2018
ms.locfileid: "36161921"
---
# <a name="drillthrough-action-form-editor-actions-tab-cube-designer-analysis-services---multidimensional-data"></a>Drillthroughaktionsformular-Editor (Registerkarte 'Aktionen', Cube-Designer) (Analysis Services – Mehrdimensionale Daten)
  Im Bereich des **Drillthroughaktionsformular-Editors** auf der Registerkarte **Aktionen** des Cube-Designers können Sie die im Bereich **Aktionsplaner** ausgewählte Drillthroughaktion ändern. Weitere Informationen zu Drillthroughaktionen finden Sie unter [Aktionen &#40;Analysis Services – mehrdimensionale Daten&#41;](multidimensional-models/actions-analysis-services-multidimensional-data.md).  
  
> [!NOTE]  
>  Durch die Drillthroughaktionen wird kein Drilldown zum zugrunde liegenden Datenspeicher mehr ausgeführt. Die Informationen, auf die die Drillthroughaktionen zugreifen, müssen im Cube mithilfe von Dimensions- oder Hierarchieelementen definiert werden.  
  
## <a name="options"></a>Tastatur  
 **name**  
 Geben Sie den Namen der Aktion ein.  
  
 **Aktionsziel**  
 Erweitern Sie dieses Element, um die Option **Measuregruppenelemente** anzuzeigen.  
  
 **Measuregruppenelemente**  
 Wählen Sie die Measuregruppe aus, der die Drillthroughaktion zugeordnet werden soll.  
  
 **Bedingung (Optional)**  
 Geben Sie einen MDX-Ausdruck (Multidimensional Expressions) ein, der eine optionale Bedingung beschreibt, die in Verbindung mit **Measuregruppenelemente**verwendet werden soll, um die Verfügbarkeit der Aktion weiter einzuschränken. Der Ausdruck muss einen booleschen Wert zurückgeben, der mit "True" anzeigt, dass die Aktion verfügbar ist.  
  
 Ziehen Sie ausgewählte Elemente aus dem Bereich **Berechnungstools** auf diese Option, um die MDX-Syntax für das ausgewählte Element einzuschließen.  
  
 **Drillthroughspalten**  
 Erweitern Sie dieses Element, um ein Raster zur Kennzeichnung der Attribute anzuzeigen, die zurückgegeben werden, wenn der Benutzer diese Aktion ausführt.  
  
> [!NOTE]  
>  Sie können zwar mehrere Dimensionen auswählen, jede Dimension kann jedoch nur einmal in einer Drillthroughaktion verwendet werden.  
  
 Das Raster enthält die folgenden Spalten:  
  
|Spalte|Description|  
|------------|-----------------|  
|**Dimensions**|Wählen Sie die Dimension aus, aus der das zurückgegebene Attribut stammt. Um das Drillthrough für Measures auszuführen, wählen Sie MEASURES aus.|  
|**Rückgabespalten**|Wählen Sie das Attribut oder Measure aus der ausgewählten Dimension aus, das bei Ausführung der Aktion zurückgegeben werden soll.|  
  
 **Weitere Eigenschaften**  
 Erweitern Sie dieses Element, um die Optionen **Standard**, **Maximale Zeilenanzahl**, **Aufruf**, **Anwendung**, **Beschreibung**, **Beschriftung**und **Beschriftung ist MDX** anzuzeigen.  
  
 **Default**  
 Wählen Sie **True** aus, um diese Drillthroughaktion als Standarddrillthroughaktion einzuschließen. Andernfalls wählen Sie **False**aus.  
  
 Wenn die `RETURN` aus einer MDX-Klausel weggelassen `DRILLTHROUGH` -Anweisung ausgeführt, die von einer Clientanwendung, die [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] Instanz wertet alle standarddrillthroughaktionen aus und führt die erste Standard Drillthrough Aktion, die einen nicht leerer Satz zurückgegeben. Weitere Informationen zu MDX `DRILLTHROUGH` -Anweisung finden Sie unter [Drillthroughanweisung &#40;MDX&#41;](/sql/mdx/mdx-data-manipulation-drillthrough).  
  
> [!NOTE]  
>  Diese Option wird im Interesse der Abwärtskompatibilität verwendet.  
  
 **Maximale Zeilenanzahl**  
 Geben Sie die maximale Anzahl der Zeilen ein, die durch die Drillthroughaktion zurückgegeben werden sollen. Wenn für diese Option null oder ein leerer Wert festgelegt wird, werden durch die Drillthroughaktion alle Zeilen zurückgegeben, die durch die Aktion für die Clientanwendung abgerufen wurden.  
  
 **Aufruf**  
 Wählen Sie die Einstellung aus, durch die angegeben wird, wann die Aktion ausgeführt werden soll.  
  
> [!NOTE]  
>  Diese Option stellt einer Clientanwendung nur eine Empfehlung für den Ausführungszeitpunkt einer Aktion zur Verfügung. Sie steuert nicht direkt den Aufruf der Aktion.  
  
 Die folgende Tabelle beschreibt die verfügbaren Einstellungen.  
  
|value|Description|  
|-----------|-----------------|  
|Batch|Die Aktion sollte als Teil eines Batchvorgangs oder eines [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] -Tasks ausgeführt werden.|  
|Interaktiv|Die Aktion wird ausgeführt, wenn der Benutzer die Aktion aufruft.|  
|Beim Öffnen|Die Aktion wird ausgeführt, wenn der Cube erstmalig geöffnet wird.|  
  
 **Application**  
 Geben Sie den Namen der Anwendung ein, durch die die Drillthroughaktion ausgeführt werden kann.  
  
 Sie können diese Option auch verwenden, um zu ermitteln, welche Clientanwendung diese Aktion am häufigsten verwendet, oder um entsprechende Symbole neben der Aktion in einem Popupmenü anzuzeigen.  
  
> [!NOTE]  
>  Diese Option stellt nur eine Empfehlung für eine Clientanwendung bereit, die angibt, welche Clientanwendung eine Aktion ausführen soll. Sie steuert nicht direkt den Zugriff auf die Aktion. Clientanwendungen sollten alle Aktionen ausblenden, die anderen Clientanwendungen zugeordnet sind.  
  
 **Beschreibung**  
 Geben Sie die optionale Beschreibung der Aktion ein.  
  
 **Beschriftung**  
 Geben Sie die Beschriftung ein, die für die Aktion in der Clientanwendung angezeigt wird, wenn **Beschriftung ist MDX** auf **FALSE**festgelegt ist.  
  
 Geben Sie den MDX-Ausdruck (Multidimensional Expressions) ein, der eine Zeichenfolge für die Beschriftung zurückgibt, wenn **Beschriftung ist MDX** auf **TRUE**festgelegt ist.  
  
 **Beschriftung ist MDX**  
 Wählen Sie **FALSE** aus, um anzuzeigen, dass **Beschriftung** eine Literalzeichenfolge enthält, die eine Beschriftung darstellt, welche für die Aktion in der Clientanwendung angezeigt werden soll.  
  
 Wählen Sie **True** aus, um anzuzeigen, dass **Beschriftung** einen MDX-Ausdruck enthält, der eine Zeichenfolge mit einer Beschriftung zurückgibt, die für die Aktion in der Clientanwendung angezeigt werden soll. Der MDX-Ausdruck muss aufgelöst werden, bevor die Aktion an die Clientanwendung zurückgegeben wird.  
  
## <a name="see-also"></a>Siehe auch  
 [Mehrdimensionale Ausdrücke &#40;MDX&#41; Verweis](/sql/mdx/multidimensional-expressions-mdx-reference)   
 [Aktionen &#40;Cube-Designer&#41; &#40;Analysis Services – mehrdimensionale Daten&#41;](actions-cube-designer-analysis-services-multidimensional-data.md)   
 [Symbolleiste &#40;Registerkarte ' Aktionen ', Cube-Designer&#41; &#40;Analysis Services – mehrdimensionale Daten&#41;](toolbar-actions-tab-cube-designer-analysis-services-multidimensional-data.md)   
 [Aktionsplaner &#40;Registerkarte ' Aktionen ', Cube-Designer&#41; &#40;Analysis Services – mehrdimensionale Daten&#41;](action-organizer-cube-designer-analysis-services-multidimensional-data.md)   
 [Berechnungstools &#40;Registerkarte ' Aktionen ', Cube-Designer&#41; &#40;Analysis Services – mehrdimensionale Daten&#41;](calculation-tools-actions-cube-designer-analysis-services-multidimensional-data.md)   
 [Aktionsformular-Editor &#40;Registerkarte ' Aktionen ', Cube-Designer&#41; &#40;Analysis Services – mehrdimensionale Daten&#41;](action-form-editor-cube-designer-analysis-services-multidimensional-data.md)   
 [Bericht Aktionsformular-Editor &#40;Registerkarte ' Aktionen ', Cube-Designer&#41; &#40;Analysis Services – mehrdimensionale Daten&#41;](report-action-form-editor-cube-designer-analysis-services-multidimensional-data.md)  
  
  
