---
title: Measures (Registerkarte Cubestruktur, Cube-Designer) (Analysis Services – mehrdimensionale Daten) | Microsoft Docs
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
- sql12.asvs.cubeeditor.cubebuilder.measurespane.f1
ms.assetid: be70f63b-58f2-4eff-81bc-c86d8229e617
caps.latest.revision: 21
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: 4b81387a3eb85ca695ffd9860e09a9bf2c696ba6
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/19/2018
ms.locfileid: "36150906"
---
# <a name="measures-cube-structure-tab-cube-designer-analysis-services---multidimensional-data"></a>Measures (Registerkarte 'Cubestruktur', Cube-Designer) (Analysis Services – Mehrdimensionale Daten)
  Im Bereich **Measures** können Sie die im Cube-Designer auf der Registerkarte **Cubestruktur** enthaltenen Measuregruppen und Elemente bearbeiten.  
  
## <a name="options"></a>Tastatur  
 Measures  
 Zeigt in Abhängigkeit von der ausgewählten Sicht die im Cube enthaltenen Measures und Measuregruppen an:  
  
 trEE  
 Zeigt eine Strukturansicht der Measuregruppen an, deren untergeordnete Knoten Measures sind.  
  
 Erweitern Sie die Measuregruppen, um die Measures anzuzeigen. Klicken Sie auf ein markiertes Measure oder eine markierte Measuregruppe, um diese umzubenennen.  
  
 Raster  
 Zeigt ein Raster mit Measures und den Measureeigenschaften an, auf die besonders oft zugegriffen wird. Klicken Sie auf **Neues Measure hinzufügen** , um das Dialogfeld **Neues Measure** anzuzeigen und dem Raster ein neues Measure hinzuzufügen.  
  
 Das Raster enthält die folgenden Spalten:  
  
 Measure  
 Geben Sie den Namen des Measures ein.  
  
 Measuregruppe  
 Zeigt die Measuregruppe an, die das Measure enthält.  
  
 Datentyp  
 Wählen Sie den Datentyp des Measures aus.  
  
 Aggregation  
 Wählen Sie die Aggregatfunktion des Measures aus.  
  
## <a name="context-menu"></a>Kontextmenü  
 Wenn Sie mit der rechten Maustaste in den Bereich **Measures** klicken, wird ein Kontextmenü mit den folgenden Optionen angezeigt:  
  
 **Neues Measure**  
 Wählen Sie diese Option aus, um das Dialogfeld **Neues Measure** anzuzeigen und der im Bereich **Measures** aktuell ausgewählten Measuregruppe ein neues Measure hinzuzufügen.  
  
 **Neue Measuregruppe**  
 Wählen Sie diese Option aus, um das Dialogfeld **Neue Measuregruppe** anzuzeigen und dem Bereich **Measures** eine neue Measuregruppe hinzuzufügen.  
  
 **Zeigen Sie Measures In an**  
 Wählen Sie diese Option aus, um die folgenden Optionen der Reihe nach anzuzeigen oder eine der folgenden Optionen auszuwählen, um die Sicht des Bereichs **Measures** zu ändern:  
  
|Option|Definition|  
|------------|----------------|  
|**Struktur**|Zeigt die Measuregruppen und Measures in einer Strukturansicht an.|  
|**Raster**|Zeigt die Measuregruppen und Measures in einem Raster an.|  
  
 **Umbenennen**  
 Wählen Sie diese Option aus, um die ausgewählte Measuregruppe oder das ausgewählte Measure umzubenennen.  
  
 **Delete**  
 Wählen Sie diese Option aus, um das Dialogfeld **Objekte löschen** anzuzeigen und die im Bereich **Measures** ausgewählten Objekte zu löschen.  
  
 **Nach oben**  
 Wählen Sie diese Option aus, um die ausgewählten Measuregruppen oder Measures um eine Position nach oben zu verschieben.  
  
> [!NOTE]  
>  Wenn das ausgewählte Element nicht nach oben verschoben werden kann, ist diese Option deaktiviert.  
  
 **Nach unten**  
 Wählen Sie diese Option aus, um die ausgewählten Measuregruppen oder Measures um eine Position nach unten zu verschieben.  
  
> [!NOTE]  
>  Wenn das ausgewählte Element nicht nach unten verschoben werden kann, ist diese Option deaktiviert.  
  
 **Neues verknüpftes Objekt**  
 Klicken Sie auf diese Option, um **Assistent für verknüpfte Objekte** anzuzeigen und Measuregruppen mit Dimensionen aus anderen Cubes zu verknüpfen oder Aktionen, KPIs und Berechnungen in den ausgewählten Cube zu importieren.  
  
 **Eigenschaften**  
 Wählen Sie diese Option aus, um das Fenster **Eigenschaften** von [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] für die ausgewählte Measuregruppe oder das ausgewählte Measure anzuzeigen.  
  
## <a name="see-also"></a>Siehe auch  
 [Konfigurieren von Measureeigenschaften](multidimensional-models/configure-measure-properties.md)   
 [Measures und Measuregruppen](multidimensional-models/measures-and-measure-groups.md)  
  
  