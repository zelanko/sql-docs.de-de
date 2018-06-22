---
title: Filtern des Quellcubes für eine Miningstruktur | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- slice cubes [Analysis Services]
- mining structures [Analysis Services], filtering source cube
- cubes [Analysis Services], slicing
- filtering data [Analysis Services]
ms.assetid: 05dce7e1-2fe5-4500-bacf-c1a8a76e1424
caps.latest.revision: 15
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: ed1ff70d4bb0f0ebd20da468c91f2603318ec217
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/19/2018
ms.locfileid: "36148945"
---
# <a name="filter-the-source-cube-for-a-mining-structure"></a>Filtern des Quellcubes für eine Miningstruktur
  Wenn Sie eine Miningstruktur, die auf Daten in einem mehrdimensionalen Modell (einem OLAP-Cube) basiert erstellen, können Sie *Slice* des Cubes, der die Miningstruktur basiert. Durch die Aufteilung in Slices können Sie Teilmengen der Daten erstellen. Diese dienen als Art von Filter für die Daten, die zum Trainieren des Miningmodells verwendet werden.  
  
### <a name="to-slice-a-cube"></a>So teilen Sie einen Cube in Slices auf  
  
1.  Data Mining-Designers in [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)], wählen die **Miningstruktur** Registerkarte oder die **Miningmodelle** Registerkarte.  
  
2.  Auf der **Miningmodell** klicken Sie im Menü **definieren Cubeslice für Miningstruktur**.  
  
     Die **Cube in Slices aufteilen** Dialogfeld wird geöffnet.  
  
3.  In der **Dimension** Spalte die **Cube in Slices aufteilen** Dialogfeld wählen die Dimension, die Sie filtern möchten.  
  
4.  Wählen Sie eine Ebene einer Hierarchie, die mit der Liste der **Hierarchie** Spalte.  
  
5.  Wählen Sie einen Operator aus der Liste der **Operator** -Spalte, um bei der Erstellung der filterbedingung verwenden.  
  
6.  Klicken Sie auf das Feld in der **Filter** Spalte.  
  
     Es wird ein Dialogfeld geöffnet, das alle Elemente in der angegebenen Hierarchieebene enthält.  
  
7.  Wählen Sie das Element bzw. die Elemente aus, die Sie filtern möchten.  
  
8.  Klicken Sie auf **OK** im Dialogfeld "Mitglied".  
  
9. Klicken Sie auf **OK** in der **Cube in Slices aufteilen** (Dialogfeld).  
  
     Der Quellcube wird jetzt entsprechend der Cubeslice-Definition gefiltert.  
  
## <a name="see-also"></a>Siehe auch  
 [Tasks und Anweisungen für Miningstrukturen](data-mining/mining-structure-tasks-and-how-tos.md)   
 [Erstellen einer neuen OLAP-Miningstruktur](data-mining/create-a-new-olap-mining-structure.md)  
  
  