---
title: Hinzufügen einer Datenquellensicht für die Planungserstellung (Datamining-Lernprogramm für fortgeschrittene) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 2665040a-1291-4064-ba01-f458637dda57
caps.latest.revision: 25
author: minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: 3c355f9755e4dfd2ddd1fcc3f65e1b34857709ca
ms.sourcegitcommit: 8c040e5b4e8c7d37ca295679410770a1af4d2e1f
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/21/2018
ms.locfileid: "36312218"
---
# <a name="adding-a-data-source-view-for-forecasting-intermediate-data-mining-tutorial"></a>Hinzufügen einer Datenquellensicht für die Planungserstellung (Data Mining-Lernprogramm für Fortgeschrittene)
  In dieser Aufgabe fügen Sie eine neue Datenquellensicht für das Planungserstellungsszenario hinzu. Vorhersagemodelle erfordern eine Spalte in den Daten, die zur Identifizierung von Schritten in einer Zeitreihe verwendet werden kann. Wenn Sie mehrere Datenreihen analysieren möchten, müssen alle Reihen mit dem gleichen Datums- oder Zeitschritt enden.  
  
### <a name="to-add-a-data-source-view"></a>So fügen Sie eine Datenquellensicht hinzu  
  
1.  Klicken Sie im Projektmappen-Explorer mit der Maustaste **Datenquellensichten**, und wählen Sie dann **neue Datenquellensicht**.  
  
2.  Klicken Sie auf der Seite **Willkommen beim Datenquellensicht-Assistenten** auf **Weiter**.  
  
3.  Auf der **wählen Sie eine Datenquelle** Seite **relationale Datenquellen**, wählen die [!INCLUDE[ssSampleDBDWobject](../includes/sssampledbdwobject-md.md)] -Datenquelle. Klicken Sie auf **Weiter**.  
  
    > [!NOTE]  
    >  Wenn Sie nicht über diese Datenquelle verfügen, finden Sie die Schritte zum Erstellen der Datenquelle in die [Basic Data Mining Tutorial](../../2014/tutorials/basic-data-mining-tutorial.md).  
  
4.  Auf der **Tabellen und Sichten auswählen** Seite, wählen Sie die Tabelle vTimeSeries (Dbo), und klicken Sie dann auf den Pfeil nach rechts, um sie der Datenquellensicht hinzuzufügen.  
  
5.  Klicken Sie auf **Weiter**.  
  
6.  Auf der **Abschließen des Assistenten** Seite standardmäßig den Namen die Datenquellensicht [!INCLUDE[ssAWDWsp](../includes/ssawdwsp-md.md)]. Ändern Sie den Namen in **SalesByRegion**, und klicken Sie dann auf **Fertig stellen**.  
  
     Datenquellensicht-Designers wird geöffnet und die **SalesByRegion** Datenquellensicht angezeigt wird.  
  
## <a name="working-with-the-data-source-view"></a>Arbeiten mit der Datenquellensicht  
 Nachdem Sie die Datenquellensicht erstellt haben, können Sie die Daten wie folgt untersuchen:  
  
-   Maustaste auf die vtimeseries-Tabelle, in den Designer, und wählen Sie **Stichprobenoptionen** auf die ausgewählte Tabelle in einem Raster zu öffnen.  
  
-   Klicken Sie auf **Samplingoptionen** und verwenden Sie dann die **zum Durchsuchen von Datenoptionen** Dialogfeld zum Ändern der Samplingmethode. Klicken Sie auf **aktualisieren** zum Laden von Daten in der Tabelle mit den neuen optionseinstellungen. Sie können z. B. die Anzahl der Zeilen in der Probe ausgegeben werden soll, oder wählen die obersten n Zeilen angeben.  
  
-   Maustaste auf die vtimeseries-Tabelle, und wählen Sie **Eigenschaften** der Tabelle einen neuen Namen zuweisen. Sie können auch einzelne Spalten aus der Datenquellensicht auswählen und die Spalteneigenschaften ändern.  
  
-   Klicken Sie im Entwurfsbereich der Datenquellensicht auf eine beliebige Stelle, um eine neue Abfrage zu erstellen und ihr einen Namen zuzuweisen, Beziehungen zwischen Tabellen zu erstellen oder das Layout des Entwurfsbereichs zu ändern.  
  
-   Mit der rechten Maustaste in einer Tabellenstatus, und wählen Sie **neue benannte Berechnung** abgeleitete Spalten, einschließlich Aggregationen zu erstellen. Sie können auch neue Tabellen und Sichten aus der Datenquelle dieser Sicht hinzufügen.  
  
 In der nächsten Aufgabe untersuchen Sie die Zeitreihendaten und stellen fest, welche Spalte sich am besten für die Verwendung als Zeitreihenbezeichner verwenden lässt. Außerdem erfahren Sie, wie unvollständige Zeitreihendaten behandelt werden.  
  
## <a name="next-task-in-lesson"></a>Nächste Aufgabe in dieser Lektion  
 [Grundlegendes zu den Anforderungen für eine Zeitreihe &#40;Datamining-Lernprogramm für fortgeschrittene&#41;](../../2014/tutorials/time-series-model-requirements-intermediate-data-mining-tutorial.md)  
  
## <a name="see-also"></a>Siehe auch  
 [Microsoft Time Series-Algorithmus](../../2014/analysis-services/data-mining/microsoft-time-series-algorithm.md)  
  
  