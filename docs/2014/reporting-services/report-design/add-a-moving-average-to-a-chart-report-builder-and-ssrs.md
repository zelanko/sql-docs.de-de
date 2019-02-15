---
title: Hinzufügen eines gleitenden Durchschnitts zu einem Diagramm (Berichts-Generator und SSRS) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- reporting-services-native
ms.topic: conceptual
ms.assetid: 166cf9c1-0750-4866-8381-542e4fbfe65a
author: markingmyname
ms.author: maghan
manager: kfile
ms.openlocfilehash: 7114291f64190207a48526a42976580b09933282
ms.sourcegitcommit: 31800ba0bb0af09476e38f6b4d155b136764c06c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/15/2019
ms.locfileid: "56297198"
---
# <a name="add-a-moving-average-to-a-chart-report-builder-and-ssrs"></a>Hinzufügen eines gleitenden Durchschnitts zu einem Diagramm (Berichts-Generator und SSRS)
  Ein gleitender Durchschnitt ist ein Mittelwert der Daten in der Reihe, die im Verlauf eines definierten Zeitraums berechnet wird. Der gleitende Durchschnitt kann im Diagramm angezeigt werden, um bedeutende Trends zu identifizieren.  
  
 Die Formel für den gleitenden Durchschnitt ist der gängigste in technischen Analysen verwendete Preisindikator. Viele andere Formeln, einschließlich Mittel, Median und Standardabweichung, können auch von einer Reihe des Diagramms abgeleitet werden. Wenn ein gleitender Durchschnitt angegeben wird, verfügt jede Formel möglicherweise über einen oder mehrere Parameter, die ebenfalls angegeben werden müssen.  
  
 Wenn eine Formel für den gleitenden Durchschnitt im Entwurfsmodus hinzugefügt wird, ist die hinzugefügte Linienreihe nur ein visueller Platzhalter. Das Diagramm berechnet die Datenpunkte jeder Formel bei der Berichtsverarbeitung.  
  
 Integrierte Unterstützung für Trendlinien ist in [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]nicht verfügbar.  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
### <a name="to-add-a-calculated-moving-average-to-a-series-on-the-chart"></a>So fügen Sie einen berechneten gleitenden Durchschnitt einer Reihe des Diagramms hinzu  
  
1.  Klicken Sie mit der rechten Maustaste auf ein Feld im Bereich **Werte** , und klicken Sie auf **Berechnete Reihe hinzufügen**. Das Dialogfeld **Eigenschaften von berechneten Reihen** wird geöffnet.  
  
2.  Wählen Sie in der Dropdownliste **Formel** die Option **Gleitender Durchschnitt** aus.  
  
3.  Geben Sie einen ganzzahligen Wert für den **Zeitraum** an, über den der gleitende Durchschnitt ermittelt werden soll.  
  
    > [!NOTE]  
    >  Der Zeitraum entspricht der Anzahl von Tagen, die verwendet wird, um einen gleitenden Durchschnitt zu berechnen. Wenn auf der X-Achse keine Datum/Uhrzeit-Werte angegeben sind, wird der Zeitraum durch die Anzahl der Datenpunkte dargestellt, die zur Berechnung eines gleitenden Durchschnitts verwendet werden. Wenn es nur einen Datenpunkt gibt, wird die Formel für den gleitenden Durchschnitt nicht berechnet. Der gleitende Durchschnitt wird am zweiten Punkt beginnend berechnet. Wenn Sie die Option **Bei erstem Punkt beginnen** angeben, startet das Diagramm den gleitenden Durchschnitt am ersten Punkt. Wenn nur ein Datenpunkt vorhanden ist, entspricht der Punkt im berechneten gleitenden Durchschnitt dem ersten Punkt Ihrer ursprünglichen Reihe.  
  
## <a name="see-also"></a>Siehe auch  
 [Formatieren eines Diagramms &#40;Berichts-Generator und SSRS&#41;](formatting-a-chart-report-builder-and-ssrs.md)   
 [Diagramme &#40;Berichts-Generator und SSRS&#41;](charts-report-builder-and-ssrs.md)   
 [Hinzufügen von leeren Punkten zum Diagramm &#40;Berichts-Generator und SSRS&#41;](add-empty-points-to-a-chart-report-builder-and-ssrs.md)  
  
  
