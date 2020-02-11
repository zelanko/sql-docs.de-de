---
title: Hinzufügen einer Datenquellen Sicht für Vorhersagen (Data Mining-Lernprogramm für Fortgeschrittene) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: 2665040a-1291-4064-ba01-f458637dda57
author: minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: f60ea2b2a642cf9435ed8366c42e43abb927e426
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "62823130"
---
# <a name="adding-a-data-source-view-for-forecasting-intermediate-data-mining-tutorial"></a>Hinzufügen einer Datenquellensicht für die Planungserstellung (Data Mining-Lernprogramm für Fortgeschrittene)
  In dieser Aufgabe fügen Sie eine neue Datenquellensicht für das Planungserstellungsszenario hinzu. Vorhersagemodelle erfordern eine Spalte in den Daten, die zur Identifizierung von Schritten in einer Zeitreihe verwendet werden kann. Wenn Sie mehrere Datenreihen analysieren möchten, müssen alle Reihen mit dem gleichen Datums- oder Zeitschritt enden.  
  
### <a name="to-add-a-data-source-view"></a>So fügen Sie eine Datenquellensicht hinzu  
  
1.  Klicken Sie in Projektmappen-Explorer mit der rechten Maustaste auf **Datenquellen Sichten**, und wählen Sie dann **neue Datenquellen Sicht**aus.  
  
2.  Klicken Sie auf der Seite **Willkommen beim Datenquellensicht-Assistenten** auf **Weiter**.  
  
3.  Wählen Sie auf der Seite **Datenquelle auswählen** unter **relationale Datenquellen**die [!INCLUDE[ssSampleDBDWobject](../includes/sssampledbdwobject-md.md)] Datenquelle aus. Klicken Sie auf **Weiter**.  
  
    > [!NOTE]  
    >  Wenn Sie nicht über diese Datenquelle verfügen, finden Sie die Schritte zum Erstellen der Datenquelle im Lernprogramm zu [Data Mining-Grundlagen](../../2014/tutorials/basic-data-mining-tutorial.md).  
  
4.  Wählen Sie auf der Seite **Tabellen und Sichten auswählen** die Tabelle vTimeSeries (dbo) aus, und klicken Sie dann auf den Pfeil nach rechts, um Sie der Datenquellen Sicht hinzuzufügen.  
  
5.  Klicken Sie auf **Weiter**.  
  
6.  Auf der Seite **Assistenten abschließen** wird die Datenquellen Sicht standardmäßig benannt [!INCLUDE[ssAWDWsp](../includes/ssawdwsp-md.md)]. Ändern Sie den Namen in **SalesByRegion**, und klicken Sie dann auf **Fertig**stellen.  
  
     Der Datenquellen Sicht-Designer wird geöffnet, und die Datenquellen Sicht **SalesByRegion** wird angezeigt.  
  
## <a name="working-with-the-data-source-view"></a>Arbeiten mit der Datenquellensicht  
 Nachdem Sie die Datenquellensicht erstellt haben, können Sie die Daten wie folgt untersuchen:  
  
-   Klicken Sie im Designer mit der rechten Maustaste auf die vTimeSeries-Tabelle, und wählen Sie **Daten durchsuchen** aus, um die ausgewählte Tabelle in einem Raster zu öffnen.  
  
-   Klicken Sie auf **samplingoptionen** , und ändern Sie dann mithilfe des Dialog Felds **Optionen** zum Durchsuchen der Stichprobenentnahme Klicken Sie auf **Aktualisieren** , um Daten in der Tabelle mithilfe der neuen Options Einstellungen zu laden. Beispielsweise können Sie die Anzahl der Zeilen angeben, die im Beispiel ausgegeben werden sollen, oder die ersten n Zeilen auswählen.  
  
-   Klicken Sie mit der rechten Maustaste auf die Tabelle vTimeSeries, und wählen Sie **Eigenschaften** aus, um der Tabelle einen neuen Namen zuzuweisen. Sie können auch einzelne Spalten aus der Datenquellensicht auswählen und die Spalteneigenschaften ändern.  
  
-   Klicken Sie im Entwurfsbereich der Datenquellensicht auf eine beliebige Stelle, um eine neue Abfrage zu erstellen und ihr einen Namen zuzuweisen, Beziehungen zwischen Tabellen zu erstellen oder das Layout des Entwurfsbereichs zu ändern.  
  
-   Klicken Sie mit der rechten Maustaste auf eine Tabelle, und wählen Sie **neue benannte Berechnung** , um abgeleitete Spalten einschließlich Aggregationen zu erstellen Sie können auch neue Tabellen und Sichten aus der Datenquelle dieser Sicht hinzufügen.  
  
 In der nächsten Aufgabe untersuchen Sie die Zeitreihendaten und stellen fest, welche Spalte sich am besten für die Verwendung als Zeitreihenbezeichner verwenden lässt. Außerdem erfahren Sie, wie unvollständige Zeitreihendaten behandelt werden.  
  
## <a name="next-task-in-lesson"></a>Nächste Aufgabe in der Lektion  
 [Grundlegendes zu den Anforderungen für ein Zeitreihen Modell &#40;Data Mining-Lernprogramm für fortgeschrittene&#41;](../../2014/tutorials/time-series-model-requirements-intermediate-data-mining-tutorial.md)  
  
## <a name="see-also"></a>Weitere Informationen  
 [Microsoft Time Series-Algorithmus](../../2014/analysis-services/data-mining/microsoft-time-series-algorithm.md)  
  
  
