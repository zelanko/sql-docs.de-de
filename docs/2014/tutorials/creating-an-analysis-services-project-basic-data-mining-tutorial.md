---
title: Erstellen eines Analysis Services Projekts (Lernprogramm zu Data Mining-Grundlagen) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: 784c0401-0358-4117-9c85-4e8220ce71d9
author: minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: a7fcece285a17e158fcdfe77ef00004afe637541
ms.sourcegitcommit: f5807ced6df55dfa78ccf402217551a7a3b44764
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/15/2019
ms.locfileid: "69494032"
---
# <a name="creating-an-analysis-services-project-basic-data-mining-tutorial"></a>Erstellen eines Analysis Services-Projekts (Lernprogramm zu Data Mining-Grundlagen)
  Für jedes Projekt von [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] werden die Objekte in einer einzelnen [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] -Datenbank definiert. Eine [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] -Datenbank kann viele verschiedene Objekttypen enthalten.  
  
-   Mehrdimensionale Modelle (Cubes)  
  
-   Miningstrukturen und Miningmodelle  
  
-   Unterstützende Objekte wie Datenquellen, Datenquellensichten und benutzerdefinierte Assemblys  
  
 Beachten Sie, dass für das Data Mining **kein** Cube erforderlich ist. Wenn Sie Data Mining-Funktionen für einen vorhandenen Cube ausführen müssen, sollten Sie die Data Mining-Modelle demselben Projekt hinzufügen, das Sie zum Erstellen des Cubes verwendet haben. In den meisten Fällen können Sie die Modelle jedoch für relationale Datenquellen erstellen, z. B. ein Data Warehouse, und eine bessere Leistung erzielen, wenn kein Cube verwendet wird.  
  
 In diesem Lernprogramm verwenden Sie das relationale Data Warehouse [!INCLUDE[ssSampleDBDWobject](../includes/sssampledbdwobject-md.md)]als Datenquelle. Sie stellen alle Ihre Data Mining-Objekte in einer [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]-Datenbank mit dem Namen `BasicDataMining` bereit, die ausschließlich für Data Mining verwendet wird.  
  
 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] verwendet standardmäßig die **localhost** -Instanz für neue Projekte. Wenn Sie eine benannte Instanz oder einen anderen Server verwenden, müssen Sie zunächst das Projekt erstellen und öffnen und anschließend den Instanznamen ändern.  
  
 Weitere Informationen zu [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] -Projekten finden Sie unter [Creating an Analysis Services Project](../analysis-services/lesson-1-1-creating-an-analysis-services-project.md).  
  
### <a name="to-create-an-analysis-services-project"></a>So erstellen Sie ein Analysis Services-Projekt  
  
1.  Öffnen Sie [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)].  
  
2.  Zeigen Sie im Menü **Datei** auf **Neu**, und klicken Sie dann auf **Projekt**.  
  
3.  Überprüfen Sie, ob **Business Intelligence-Projekte** im Bereich **Projekttypen** ausgewählt wurde.  
  
4.  Wählen Sie im Bereich **Vorlagen** die Vorlage für mehrdimensionale Projekte bzw. **Data Mining-Projekte von Analysis Services** aus.  
  
5.  Benennen Sie das neue Projekt `BasicDataMining`in das Feld Name.  
  
6.  [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
### <a name="to-change-the-instance-where-data-mining-objects-are-stored"></a>So ändern Sie die Instanz, in der die Data Mining-Objekte gespeichert werden  
  
1.  Wählen Sie in [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]im Menü **Projekt** den Befehl **Eigenschaften**aus.  
  
2.  Klicken Sie auf der linken Seite des Bereichs **Eigenschaftenseiten** unter **Konfigurationseigenschaften**auf **Bereitstellung**.  
  
3.  Überprüfen Sie, ob auf der rechten Seite des Bereichs **Eigenschaftenseiten** unter **Ziel**der **Servername** **localhost**angegeben ist. Wenn Sie eine andere Instanz verwenden, geben Sie den Namen der Instanz ein. [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
## <a name="next-task-in-lesson"></a>Nächste Aufgabe in dieser Lektion  
 [Erstellen eines Lernprogramms &#40;zu Data Mining-Grundlagen&#41;](../../2014/tutorials/creating-a-data-source-basic-data-mining-tutorial.md)  
  
## <a name="see-also"></a>Siehe auch  
 [Erstellen von Analysis Services-Projekten &#40;SSDT&#41;](https://docs.microsoft.com/analysis-services/multidimensional-models/build-analysis-services-projects-ssdt)   
 [Erstellen eines Analysis Services-Projekts &#40;SSDT&#41;](https://docs.microsoft.com/analysis-services/multidimensional-models/create-an-analysis-services-project-ssdt)  
  
  
