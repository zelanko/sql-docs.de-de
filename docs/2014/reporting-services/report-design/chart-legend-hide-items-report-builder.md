---
title: Ausblenden von Legendenelementen im Diagramm (Berichts-Generator und SSRS) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- reporting-services-native
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 92256240-0cd5-4be4-8904-d1e3b93cb6b3
caps.latest.revision: 6
author: douglaslM
ms.author: douglasl
manager: mblythe
ms.openlocfilehash: 13064f5d0033a1a4677789c6031b1f9b0f322379
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/19/2018
ms.locfileid: "36047318"
---
# <a name="hide-legend-items-on-the-chart-report-builder-and-ssrs"></a>Ausblenden von Legendenelementen im Diagramm (Berichts-Generator und SSRS)
  Standardmäßig werden alle einem Nicht-Formdiagramm hinzugefügten Reihen in der Legende als Element hinzugefügt. Für Kreis-, Ring-, Trichter- und Pyramidendiagramme werden für alle dem Diagramm hinzugefügten Reihen der Legende einzelne Datenpunkte hinzugefügt.  
  
 Sie können in der Legende beliebige Elemente ausblenden. Wenn Sie ein Legendenelement ausblenden, wird dieses immer noch im Diagramm angezeigt. Dies ist hilfreich in Situationen, in denen für eine dem Diagramm hinzugefügte Reihe keine weiteren Informationen angezeigt werden sollen. Wenn Sie dem Diagramm beispielsweise eine berechnete Reihe (z. B. einen gleitenden Durchschnitt) hinzugefügt haben, empfiehlt es sich u. U., diesen Eintrag in der Legende auszublenden, sodass nur für die ursprüngliche Reihe weitere Informationen angezeigt werden.  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
### <a name="to-hide-an-item-from-display-in-the-legend"></a>So blenden Sie ein in der Legende angezeigtes Element aus  
  
1.  Klicken Sie mit der rechten Maustaste auf die auszublendende Reihe, und wählen Sie die Option **Reiheneigenschaften**aus.  
  
2.  Klicken Sie auf **Legende**. Aktivieren Sie die Option **Diese Reihe in Legende nicht anzeigen** .  
  
    > [!NOTE]  
    >  Eine Reihe kann nicht für eine Gruppe ausgeblendet und für andere angezeigt werden. Wenn Sie dem Bereich **Reihengruppen** ein Feld hinzugefügt haben, werden alle zu dieser Gruppe gehörenden Reihen ausgeblendet.  
  
## <a name="see-also"></a>Siehe auch  
 [Formatieren der Legende in einem Diagramm &#40;Berichts-Generator und SSRS&#41;](chart-legend-formatting-report-builder.md)   
 [Formatieren von Datenpunkten in einem Diagramm &#40;Berichts-Generator und SSRS&#41;](formatting-data-points-on-a-chart-report-builder-and-ssrs.md)   
 [Ändern des Texts eines Legendenelements (Berichts-Generator und SSRS)](chart-legend-change-item-text-report-builder.md)   
 [Hinzufügen eines gleitenden Durchschnitts zu einem Diagramm (Berichts-Generator und SSRS)](add-a-moving-average-to-a-chart-report-builder-and-ssrs.md)   
 [Legendeneigenschaften (Dialogfeld), Allgemein (Berichts-Generator und SSRS)](../legend-properties-dialog-box-general-report-builder-and-ssrs.md)  
  
  