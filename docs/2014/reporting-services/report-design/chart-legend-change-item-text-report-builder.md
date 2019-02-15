---
title: Ändern des Texts eines Legendenelements (Berichts-Generator und SSRS) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- reporting-services-native
ms.topic: conceptual
ms.assetid: 9e82fa34-17ed-494f-b25d-03dcc353a21f
author: markingmyname
ms.author: maghan
manager: kfile
ms.openlocfilehash: 72ff6c430ff3275fb2df7f79ad53333415f85683
ms.sourcegitcommit: 31800ba0bb0af09476e38f6b4d155b136764c06c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/15/2019
ms.locfileid: "56285798"
---
# <a name="change-the-text-of-a-legend-item-report-builder-and-ssrs"></a>Ändern des Texts eines Legendenelements (Berichts-Generator und SSRS)
  Wenn Sie ein Feld im Wertebereich des Diagramms ablegen, wird automatisch ein Legendenelement mit dem Namen dieses Felds erstellt. Alle Legendenelemente im Diagramm sind mit jeweils einer Reihe verknüpft, mit Ausnahme von Formdiagrammen, bei denen die Legende stattdessen mit einzelnen Datenpunkten verknüpft ist.  
  
 In Formdiagrammen können Sie den Text eines Legendenelements so ändern, dass weitere Informationen zu den einzelnen Datenpunkten angezeigt werden. Wenn beispielsweise die Werte der Datenpunkte in der Legende als Prozentsätze angezeigt werden sollen, können Sie ein Schlüsselwort wie `#PERCENT` angeben. Sie können .NET Framework-Formatcodes in Verbindung mit Schlüsselwörtern anfügen, um numerische Formate und Datumsformate anzuwenden. Weitere Informationen zu Schlüsselwörtern finden Sie unter [Formatieren von Datenpunkten in einem Diagramm &#40;Berichts-Generator und SSRS&#41;](formatting-data-points-on-a-chart-report-builder-and-ssrs.md).  
  
 ![Sharp-Diagramm](../media/sharpchart.png "Sharp-Diagramm")  
  
 In Nicht-Formdiagrammen können Sie den Text eines Legendenelements ändern. Wenn eine Reihe beispielsweise den Namen "Reihe1" aufweist, können Sie diesen in einen aussagekräftigeren Namen wie "Umsatz für 2008" ändern.  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
### <a name="to-modify-the-text-that-appears-in-the-legend-on-a-shape-chart"></a>So ändern Sie den Text, der in der Legende eines Formdiagramms angezeigt wird  
  
1.  Klicken Sie mit der rechten Maustaste auf eine Reihe, oder klicken Sie mit der rechten Maustaste auf ein Feld im Bereich **Werte** , und wählen Sie die Option **Reiheneigenschaften**aus.  
  
2.  Klicken Sie auf **Legende** , und geben Sie im Feld **Benutzerdefinierter Legendentext** ein Schlüsselwort ein.  
  
 In der folgenden Tabelle sind Beispiele für diagrammspezifische Schlüsselwörter aufgelistet, die für die Eigenschaft **Benutzerdefinierter Legendentext** verwendet werden sollen. Weitere Informationen zu Schlüsselwörtern finden Sie unter [Formatieren von Datenpunkten in einem Diagramm &#40;Berichts-Generator und SSRS&#41;](formatting-data-points-on-a-chart-report-builder-and-ssrs.md).  
  
|Schlüsselwort|Description|Beispiel für den in der Legende angezeigten Text|  
|-------------|-----------------|---------------------------------------------------|  
|`#PERCENT{P1}`|Zeigt den Prozentsatz des Gesamtwerts mit einer Dezimalstelle an.|85.0%|  
|`#VALY`|Zeigt den tatsächlichen numerischen Wert des Datenfelds an.|17000|  
|`#VALY{C2}`|Zeigt den tatsächlichen numerischen Wert des Datenfelds als Währung mit zwei Dezimalstellen an.|$17000.00|  
|`#AXISLABEL (#PERCENT{P0})`|Zeigt die Textdarstellung des Kategoriefelds an, gefolgt von dem Prozentsatz, der in den einzelnen Kategorien im Diagramm angezeigt wird.|Michael Blythe (85 %)|  
  
> [!NOTE]  
>  Das Schlüsselwort #AXISLABEL kann nur dann zur Laufzeit ausgewertet werden, wenn im Bereich **Reihengruppen** kein Feld angegeben ist.  
  
### <a name="to-modify-the-text-that-appears-in-the-legend-on-a-non-shape-chart"></a>So ändern Sie den Text, der in der Legende eines Nicht-Formdiagramms angezeigt wird  
  
1.  Klicken Sie mit der rechten Maustaste auf eine Reihe, oder klicken Sie mit der rechten Maustaste auf ein Feld im Bereich **Werte** , und wählen Sie die Option **Reiheneigenschaften**aus.  
  
2.  Klicken Sie auf **Legende** , und geben Sie im Feld **Benutzerdefinierter Legendentext** eine Legendenbezeichnung ein. Die Reihe wird mit dem Text aktualisiert.  
  
## <a name="see-also"></a>Siehe auch  
 [Formatieren der Legende in einem Diagramm &#40;Berichts-Generator und SSRS&#41;](chart-legend-formatting-report-builder.md)   
 [Formatieren von Reihenfarben in einem Diagramm &#40;Berichts-Generator und SSRS&#41;](formatting-series-colors-on-a-chart-report-builder-and-ssrs.md)   
 [Ausblenden von Legendenelementen im Diagramm &#40;Berichts-Generator und SSRS&#41;](chart-legend-hide-items-report-builder.md)  
  
  
