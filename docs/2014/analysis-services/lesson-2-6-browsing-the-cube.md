---
title: Durchsuchen des Cubes | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: 3819946e-d3fa-4c1d-afe3-599c938b1b2e
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 910bb7a425e62221dce932392e1aedfaa401a992
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "66078979"
---
# <a name="browsing-the-cube"></a>Durchsuchen des Cubes
  Nach dem Bereitstellen des Cubes können dessen Daten auf der Registerkarte **Browser** im Cube-Designer und die Dimensionsdaten auf der Registerkarte **Browser** im Dimensions-Designer angezeigt werden. Indem Sie Cube- und Dimensionsdaten durchsuchen, können Sie Ihre Arbeit schrittweise überprüfen. Sie können überprüfen, ob geringe Änderungen an Eigenschaften, Beziehungen und anderen Objekten nach der Verarbeitung des Objekts den gewünschten Effekt hatten. Obwohl auf der Registerkarte Browser sowohl Cube- als auch Dimensionsdaten angezeigt werden, enthält die Registerkarte je nach Objekt, das durchsucht wird, unterschiedliche Funktionen.  
  
 Bei Dimensionen bietet die Registerkarte Browser die Möglichkeit, Elemente anzuzeigen oder durch eine ganze Hierarchie bis zum Blattknoten zu navigieren. Dimensionsdaten können in verschiedenen Sprachen durchsucht werden, wenn Sie dem Modell entsprechende Übersetzungen hinzugefügt haben.  
  
 Bei Cubes bietet die Registerkarte Browser zwei Möglichkeiten zum Durchsuchen von Daten. Mit dem integrierten MDX-Abfrage-Designer können Sie Abfragen erstellen, die ein vereinfachtes Rowset aus einer mehrdimensionalen Datenbank zurückgeben. Alternativ können Sie eine Excel-Verknüpfung verwenden. Wenn Sie Excel in [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)]starten, wird beim Öffnen von Excel ein Arbeitsblatt mit einer PivotTable und eine vordefinierte Verbindung mit der Arbeitsbereichsdatenbank des Modells angezeigt.  
  
 Excel bietet im Allgemeinen eine bessere Browsererfahrung, weil Sie die Cubedaten mithilfe von horizontalen und vertikalen Achsen interaktiv durchsuchen können, um die Beziehungen innerhalb von Daten zu analysieren. Im Unterschied dazu ist der MDX-Abfrage-Designer auf eine einzelne Achse beschränkt. Da das Rowset vereinfacht ist, verfügen Sie darüber hinaus nicht über die Drilldownfunktionen, die eine Excel-PivotTable bereitstellt. Während dem Cube in den nachfolgenden Lektionen weitere Dimensionen und Hierarchien hinzugefügt werden, wird Excel zur bevorzugten Lösung für das Durchsuchen von Daten.  
  
### <a name="to-browse-the-deployed-cube"></a>So durchsuchen Sie den bereitgestellten Cube  
  
1.  Wechseln Sie zum **Dimensions-Designer** für die Produkt-Dimension in [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]. Doppelklicken Sie dazu auf die **Product** -Dimension im **Dimensionen** -Knoten des Projektmappen-Explorers.  
  
2.  Klicken Sie auf die Registerkarte **Browser** , um das **alle** -Element der `Product Key` Attribut Hierarchie anzuzeigen. In Lektion 3 definieren Sie eine Benutzerhierarchie für die Product-Dimension, mit der Sie die Dimension durchsuchen können.  
  
3.  Wechseln Sie in **zum** Cube-Designer [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]. Doppelklicken Sie hierzu auf den **Analysis Services Tutorial** -Cube im **Cubes** -Knoten Projektmappen-Explorer.  
  
4.  Klicken Sie auf die Registerkarte **Browser** und anschließend auf der Symbolleiste des Designers auf das Symbol zum **Wiederherstellen der Verbindung** .  
  
     Im linken Bereich des Designers werden die Objekte für den [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] Tutorial-Cube angezeigt. Auf der rechten Seite der Registerkarte **Browser** sind zwei Bereiche enthalten: Beim oberen Bereich handelt es sich um den Bereich **Filter** , beim unteren um den Bereich **Daten** . In einer der nächsten Lektionen verwenden Sie den Cube-Browser zur Durchführung von Analysen.  
  
## <a name="next-lesson"></a>Nächste Lektion  
 [Lektion 3: Ändern von Maßen, Attributen und Hierarchien](lesson-3-modifying-measures-attributes-and-hierarchies.md)  
  
## <a name="see-also"></a>Weitere Informationen  
 [MDX-Abfrage-Editor &#40;Analysis Services Mehrdimensionale Daten&#41;](mdx-query-editor-analysis-services-multidimensional-data.md)  
  
  
