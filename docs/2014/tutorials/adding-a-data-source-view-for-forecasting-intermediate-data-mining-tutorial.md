---
title: Hinzufügen einer Datenquellensicht für Vorhersagen (mittleres Datamining Tutorial) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
ms.topic: conceptual
ms.assetid: 2665040a-1291-4064-ba01-f458637dda57
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: b91be4b60c65a246b56a2d08142ce6937d80cea0
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/02/2018
ms.locfileid: "48162580"
---
# <a name="adding-a-data-source-view-for-forecasting-intermediate-data-mining-tutorial"></a>Hinzufügen einer Datenquellensicht für die Planungserstellung (Data Mining-Lernprogramm für Fortgeschrittene)
  In dieser Aufgabe fügen Sie eine neue Datenquellensicht für das Planungserstellungsszenario hinzu. Vorhersagemodelle erfordern eine Spalte in den Daten, die zur Identifizierung von Schritten in einer Zeitreihe verwendet werden kann. Wenn Sie mehrere Datenreihen analysieren möchten, müssen alle Reihen mit dem gleichen Datums- oder Zeitschritt enden.  
  
### <a name="to-add-a-data-source-view"></a>So fügen Sie eine Datenquellensicht hinzu  
  
1.  Klicken Sie im Projektmappen-Explorer mit der Maustaste **Datenquellensichten**, und wählen Sie dann **neue Datenquellensicht**.  
  
2.  Klicken Sie auf der Seite **Willkommen beim Datenquellensicht-Assistenten** auf **Weiter**.  
  
3.  Auf der **Vybrat Zdroj DAT** Seite **relationale Datenquellen**, wählen die [!INCLUDE[ssSampleDBDWobject](../includes/sssampledbdwobject-md.md)] -Datenquelle. Klicken Sie auf **Weiter**.  
  
    > [!NOTE]  
    >  Wenn Sie nicht über diese Datenquelle verfügen, finden Sie die Schritte zum Erstellen der Datenquelle in die [Basic Data Mining Tutorial](../../2014/tutorials/basic-data-mining-tutorial.md).  
  
4.  Auf der **Tabellen und Sichten auswählen** Seite, wählen Sie die Tabelle vTimeSeries (Dbo), und klicken Sie dann auf den Pfeil nach rechts, um sie der Datenquellensicht hinzuzufügen.  
  
5.  Klicken Sie auf **Weiter**.  
  
6.  Auf der **Abschließen des Assistenten** Seite standardmäßig den Namen die Datenquellensicht [!INCLUDE[ssAWDWsp](../includes/ssawdwsp-md.md)]. Ändern Sie den Namen in **SalesByRegion**, und klicken Sie dann auf **Fertig stellen**.  
  
     Datenquellensicht-Designer wird geöffnet und die **SalesByRegion** Datenquellensicht angezeigt wird.  
  
## <a name="working-with-the-data-source-view"></a>Arbeiten mit der Datenquellensicht  
 Nachdem Sie die Datenquellensicht erstellt haben, können Sie die Daten wie folgt untersuchen:  
  
-   Mit der rechten Maustaste im Designer die vTimeSeries-Tabelle, und wählen **Stichprobenoptionen** um die ausgewählte Tabelle in einem Raster zu öffnen.  
  
-   Klicken Sie auf **Samplingoptionen** und verwenden Sie dann die **Optionen zum Durchsuchen von Daten** Dialogfeld zum Ändern der Samplingmethode. Klicken Sie auf **aktualisieren** zum Laden von Daten in der Tabelle mit den neuen optionseinstellungen. Sie können z. B. die Anzahl der Zeilen in der Probe ausgegeben werden soll, oder wählen die obersten n Zeilen angeben.  
  
-   Mit der rechten Maustaste die vTimeSeries-Tabelle, und wählen Sie **Eigenschaften** in der Tabelle einen neuen Namen zuweisen. Sie können auch einzelne Spalten aus der Datenquellensicht auswählen und die Spalteneigenschaften ändern.  
  
-   Klicken Sie im Entwurfsbereich der Datenquellensicht auf eine beliebige Stelle, um eine neue Abfrage zu erstellen und ihr einen Namen zuzuweisen, Beziehungen zwischen Tabellen zu erstellen oder das Layout des Entwurfsbereichs zu ändern.  
  
-   Mit der rechten Maustaste in einer Tabelle, und wählen Sie **neue benannte Berechnung** abgeleitete Spalten, einschließlich Aggregationen zu erstellen. Sie können auch neue Tabellen und Sichten aus der Datenquelle dieser Sicht hinzufügen.  
  
 In der nächsten Aufgabe untersuchen Sie die Zeitreihendaten und stellen fest, welche Spalte sich am besten für die Verwendung als Zeitreihenbezeichner verwenden lässt. Außerdem erfahren Sie, wie unvollständige Zeitreihendaten behandelt werden.  
  
## <a name="next-task-in-lesson"></a>Nächste Aufgabe in dieser Lektion  
 [Grundlegendes zu den Anforderungen für ein Zeitreihenmodell &#40;Datamining-Lernprogramm für fortgeschrittene&#41;](../../2014/tutorials/time-series-model-requirements-intermediate-data-mining-tutorial.md)  
  
## <a name="see-also"></a>Siehe auch  
 [Microsoft Time Series-Algorithmus](../../2014/analysis-services/data-mining/microsoft-time-series-algorithm.md)  
  
  
