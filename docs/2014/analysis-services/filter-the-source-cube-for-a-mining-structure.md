---
title: Filtern des Quellcubes für eine Mining Struktur | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- slice cubes [Analysis Services]
- mining structures [Analysis Services], filtering source cube
- cubes [Analysis Services], slicing
- filtering data [Analysis Services]
ms.assetid: 05dce7e1-2fe5-4500-bacf-c1a8a76e1424
author: minewiskan
ms.author: owend
ms.openlocfilehash: 058ba6e78fd6c6e5aa7b06fbd5d34c256dac07b3
ms.sourcegitcommit: f0772f614482e0b3cde3609e178689ce62ca3a19
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/09/2020
ms.locfileid: "84544452"
---
# <a name="filter-the-source-cube-for-a-mining-structure"></a>Filtern des Quellcubes für eine Miningstruktur
  Wenn Sie eine Mining Struktur erstellen, die auf Daten in einem mehrdimensionalen Modell (einem OLAP-Cube) basiert, *können Sie* den Cube, auf dem die Mining Struktur basiert, segmentieren. Durch die Aufteilung in Slices können Sie Teilmengen der Daten erstellen. Diese dienen als Art von Filter für die Daten, die zum Trainieren des Miningmodells verwendet werden.  
  
### <a name="to-slice-a-cube"></a>So teilen Sie einen Cube in Slices auf  
  
1.  Wählen Sie im Data Mining-Designer in [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)] die Registerkarte **Mining Struktur** oder **Mining Modelle** aus.  
  
2.  Wählen Sie im Menü **Mining Modell** die Option **Mining Struktur Cube Slice definieren**aus.  
  
     Das Dialogfeld **Cube Slice** wird geöffnet.  
  
3.  Wählen Sie in der Spalte **Dimension** des Dialog Felds **Cube Slice** die Dimension aus, die Sie filtern möchten.  
  
4.  Wählen Sie eine Ebene einer Hierarchie aus, und verwenden Sie dabei die Liste in der Spalte **Hierarchie** .  
  
5.  Wählen Sie einen Operator aus der Liste in der Spalte **Operator** aus, der beim Aufbau der Filterbedingung verwendet werden soll.  
  
6.  Klicken Sie in der Spalte **Filter** auf das Feld.  
  
     Es wird ein Dialogfeld geöffnet, das alle Elemente in der angegebenen Hierarchieebene enthält.  
  
7.  Wählen Sie das Element bzw. die Elemente aus, die Sie filtern möchten.  
  
8.  Klicken Sie im Dialogfeld Mitglied auf **OK** .  
  
9. Klicken Sie im Dialogfeld **Cube Slice** auf **OK** .  
  
     Der Quellcube wird jetzt entsprechend der Cubeslice-Definition gefiltert.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Mining Struktur Tasks und-Anleitungen](data-mining/mining-structure-tasks-and-how-tos.md)   
 [Erstellen einer neuen OLAP-Miningstruktur](data-mining/create-a-new-olap-mining-structure.md)  
  
  
