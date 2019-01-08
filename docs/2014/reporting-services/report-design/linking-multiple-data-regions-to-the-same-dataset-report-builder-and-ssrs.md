---
title: Verknüpfen mehrerer Datenbereiche mit demselben Dataset (Berichts-Generator und SSRS) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- reporting-services-native
ms.topic: conceptual
ms.assetid: 90c94a91-8fb2-42cb-b998-563691f30d2d
author: maggiesMSFT
ms.author: maggies
manager: craigg
ms.openlocfilehash: 146edd7519674ba83ac996a9b4aa1f7ec9a43ec2
ms.sourcegitcommit: 334cae1925fa5ac6c140e0b2c38c844c477e3ffb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/13/2018
ms.locfileid: "53365982"
---
# <a name="linking-multiple-data-regions-to-the-same-dataset-report-builder-and-ssrs"></a>Verknüpfen mehrerer Datenbereiche mit einem Dataset (Berichts-Generator und SSRS)
  Sie können einem Bericht mehrere Datenbereiche hinzufügen, um verschiedene Datensichten für ein Berichtsdataset bereitzustellen. Beispielsweise können Sie Daten in einer Tabelle anzeigen und visuell in einem Diagramm veranschaulichen. Voraussetzung hierfür ist die Verwendung identischer Ausdrücke und Bereiche für die entsprechenden Filterausdrücke, Sortierungsausdrücke und Gruppenausdrücke.  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
 Die Verwendung eines Diagramms und einer Tabelle oder Matrix zum Anzeigen gleicher Daten hilft, die Ähnlichkeiten zwischen einer Tabelle und Formdiagrammen sowie einer Matrix und Bereichs-, Balken- und Säulendiagrammen zu verstehen. Tabellen mit einer einzelnen Zeilengruppe können einfach als Kreisdiagramm angezeigt werden. Beim Hinzufügen mehrerer Zeilengruppen können Sie verschiedene Diagramme zur optimalen Darstellung der geschachtelten Gruppen auswählen. Durch das Hinzufügen geschachtelter Zeilengruppen zu einem Kreisdiagramm wird die Anzahl der Slices im Kreis erhöht. Dabei ist zu beachten, dass die Gesamtanzahl der Gruppeninstanzen für die übergeordnete und die untergeordnete Gruppe zu groß sein kann, um in einem Kreisdiagramm angezeigt zu werden. Bei mehreren Gruppenwerten, die als kleine Slices in einem Kreisdiagramm angezeigt werden, können Sie mithilfe einer Eigenschaft festlegen, dass alle Werte unter einem bestimmten Schwellenwert als eine Kreisslice angezeigt werden. Weitere Informationen finden Sie unter [Zusammenfassen von kleinen Slices in einem Kreisdiagramm &#40;Berichts-Generator und SSRS&#41;](collect-small-slices-on-a-pie-chart-report-builder-and-ssrs.md).  
  
 Eine Tabelle mit mehreren Zeilengruppen kann als Säulendiagramm mit mehreren Kategoriegruppen angezeigt werden. Weitere Informationen finden Sie unter [Anzeigen derselben Daten in einer Matrix und einem Diagramm &#40;Berichts-Generator&#41;](display-the-same-data-on-a-matrix-and-a-chart-report-builder.md). Ein Beispiel für eine Tabelle und ein Diagramm, die unterschiedliche Sichten des gleichen Berichtsdatasets darstellen, finden Sie im Product Line Sales-Bericht in den AdventureWorks-Beispielberichten. Die Tabelle und das Diagramm sind mit dem gleichen Dataset im Bericht verknüpft. Wenn Sie auf die Schaltfläche für die interaktive Sortierung für den Mitarbeiternamen in der Tabelle mit den führenden Mitarbeitern klicken, wird die neue Sortierungsreihenfolge automatisch auch für das entsprechende Diagramm übernommen. Weitere Informationen zum Herunterladen des Beispielberichts und anderer Berichte finden Sie unter [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)][Beispielberichte zu Berichts-Generator und Berichts-Designer](https://go.microsoft.com/fwlink/?LinkId=198283).  
  
 Eine Matrix mit mehreren Zeilen- und Spaltengruppen kann am besten mit einem Bereichs-, Balken- oder Säulendiagramm dargestellt werden, das über Kategorie- und Seriengruppen verfügt. Verwenden Sie einheitliche Gruppenausdrücke für Spaltengruppen in der Matrix und Kategoriegruppen im Diagramm, und verwenden Sie einheitliche Gruppenausdrücke für Zeilengruppen in der Matrix und Seriengruppen im Diagramm. Bedenken Sie, dass die Anzahl der Gruppeninstanzen Auswirkungen auf die Lesbarkeit des Diagramms hat. Sie können Gruppen auf der Basis von Bereichswerten definieren, um die Anzahl der Gruppeninstanzen in einem Bericht zu verringern. Weitere Informationen finden Sie unter [Beispiele für Gruppierungsausdrücke &#40;Berichts-Generator und SSRS&#41;](expression-examples-report-builder-and-ssrs.md).  
  
## <a name="see-also"></a>Siehe auch  
 [Diagramme &#40;Berichts-Generator und SSRS&#41;](charts-report-builder-and-ssrs.md)   
 [Listen (Berichts-Generator und SSRS)](tables-matrices-and-lists-report-builder-and-ssrs.md)   
 [Geschachtelte Datenbereiche &#40;Berichts-Generator und SSRS&#41;](nested-data-regions-report-builder-and-ssrs.md)  
  
  
