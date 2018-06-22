---
title: Erstellungsmethode auswählen (Cube-Assistent) | Microsoft Docs
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
- sql12.asvs.cubewizard.cubedefinition.f1
ms.assetid: 985d3b5b-7891-465b-862d-f7e75431b342
caps.latest.revision: 28
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: b99ea0d73d9d24992af5fcac09d8df3f4d71fafd
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/19/2018
ms.locfileid: "36050393"
---
# <a name="select-creation-method-cube-wizard"></a>Erstellungsmethode auswählen (Cube-Assistent)
  Auf der Seite **Erstellungsmethode auswählen** können Sie angeben, wie der Cube erstellt werden soll.  
  
## <a name="options"></a>Tastatur  
 **Vorhandene Tabellen verwenden**  
 Wählen Sie diese Option aus, um einen Cube mithilfe vorhandener Tabellen in einer Datenquelle zu erstellen. Der Assistent führt Sie durch den Vorgang der Auswahl und Definition von Measuregruppen und Dimensionen anhand vorhandener Tabellen zur Erstellung des neuen Cubes.  
  
 **Leeren Cube erstellen**  
 Wählen Sie diese Option aus, um einen leeren Cube zu erstellen. Diese Option ist dann hilfreich, wenn Sie alles manuell erstellen möchten, oder wenn es sich bei allen Measuregruppen im Cube um verknüpfte Measuregruppen handelt.  
  
> [!NOTE]  
>  Diese Option ist nur dann verfügbar, wenn Sie mit einem [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] -Projekt arbeiten, aber nicht dann, wenn Sie direkt mit einer [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] -Datenbank verbunden sind.  
  
 **Tabellen in der Datenquelle generieren**  
 Wählen Sie diese Option aus, um zuerst einen Cube zu erstellen und anschließend anhand der Cubedefinition neue Tabellen in der Datenquelle zu generieren.  
  
> [!NOTE]  
>  Um diese Option nutzen zu können, müssen Sie über die Berechtigung zum Erstellen von Objekten in der zugrunde liegenden Datenquelle verfügen.  
  
 Bei Auswahl dieser Option ist auch die Option **Vorlage** verfügbar.  
  
 **Vorlage**  
 Wählen Sie die Vorlage aus, die Sie zum Erstellen des Cubes verwenden möchten. Vorlagen enthalten einen Satz von Definitionen, die auf einen bestimmten geschäftlichen Zweck ausgerichtet sind.  
  
> [!NOTE]  
>  Diese Option ist nur verfügbar, wenn die Option **Tabelle in der Datenquelle generieren** ausgewählt wurde.  
  
## <a name="see-also"></a>Siehe auch  
 [Cubeobjekte &#40;Analysis Services – mehrdimensionale Daten&#41;](multidimensional-models-olap-logical-cube-objects/cube-objects-analysis-services-multidimensional-data.md)   
 [Cubes in mehrdimensionalen Modellen](multidimensional-models/cubes-in-multidimensional-models.md)   
 [Dimensionen in mehrdimensionalen Modellen](multidimensional-models/dimensions-in-multidimensional-models.md)  
  
  