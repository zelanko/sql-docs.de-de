---
title: Zeichnen von Daten auf einer sekundären Achse (Berichts-Generator und SSRS) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- reporting-services-native
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: 094f39bf-3634-4852-9fc3-3adec4b266e5
caps.latest.revision: 8
author: maggiesMSFT
ms.author: maggies
manager: craigg
ms.openlocfilehash: 34d4ab217564f931dc441d5c90b077960bd11486
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/02/2018
ms.locfileid: "37149171"
---
# <a name="plot-data-on-a-secondary-axis-report-builder-and-ssrs"></a>Zeichnen von Daten auf einer sekundären Achse (Berichts-Generator und SSRS)
  Das Diagramm verfügt über zwei Achsentypen: primär und sekundär. Die sekundäre Achse ist nützlich beim Vergleichen von zwei Wertsätzen mit zwei unterschiedlichen Datenbereichen, die eine gemeinsame Kategorie verwenden.  
  
 Angenommen, Sie haben ein Diagramm, das Einnahmen und Steuern für das Jahr 2008 berechnet. In diesem Fall verwenden beide Wertsätze den Zeitraum 2008 gemeinsam. Wenn beide Reihen jedoch auf derselben Y-Achse gezeichnet werden, kann kein sinnvoller Vergleich durchgeführt werden, da die Skala der Y-Achse für die größten Werte im Dataset optimiert ist. Wenn die Einnahmen auf der primären Achse und die Steuern auf der sekundären Achse angezeigt werden, kann jede Reihe auf einer eigenen Y-Achse mit einer eigenen Werteskala dargestellt werden. Die Reihen verwenden nach wie vor eine gemeinsame X-Achse.  
  
 In Fällen, in denen mehr als zwei Reihen verglichen werden, sollten Sie einen anderen Ansatz für den Vergleich und die Anzeige mehrerer Reihen in einem Diagramm in Erwägung ziehen. Weitere Informationen hierzu finden Sie unter [Mehrere Reihen in einem Diagramm &#40;Berichts-Generator und SSRS&#41;](multiple-series-on-a-chart-report-builder-and-ssrs.md).  
  
 Ein Beispiel für dieses Diagramm ist als Beispielbericht verfügbar. Weitere Informationen zum Herunterladen des Beispielberichts und anderer Berichte finden Sie unter [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)][Beispielberichte zu Berichts-Generator und Berichts-Designer](http://go.microsoft.com/fwlink/?LinkId=198283).  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
### <a name="to-plot-a-series-on-the-secondary-axis"></a>So zeichnen Sie eine Reihe auf der sekundären Achse  
  
1.  Klicken Sie mit der rechten Maustaste auf die Reihe im Diagramm oder auf ein Feld im Bereich **Werte** , das Sie auf der sekundären Achse anzeigen möchten. Klicken Sie anschließend auf **Reiheneigenschaften**. Das Dialogfeld **Reiheneigenschaften** wird angezeigt.  
  
2.  Klicken Sie auf **Achsen und Diagrammfläche**, und wählen Sie die sekundäre Achse aus, die Sie aktivieren möchten, d. h. die Wertachse oder die Kategorieachse.  
  
## <a name="see-also"></a>Siehe auch  
 [Formatieren von Achsenbezeichnungen in einem Diagramm &#40;Berichts-Generator und SSRS&#41;](formatting-axis-labels-on-a-chart-report-builder-and-ssrs.md)   
 [Angeben eines Achsenintervalls &#40;Berichts-Generator und SSRS&#41;](specify-an-axis-interval-report-builder-and-ssrs.md)  
  
  
