---
title: Grundlegendes zu den Anforderungen für ein Zeitreihen Modell (Data Mining-Lernprogramm für Fortgeschrittene) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: 1ce2b3e3-108a-4f7e-985f-a20b816d0da7
author: minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: 8e46d7fc8a0c214501841de448a94d1211b95fa1
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "68892961"
---
# <a name="understanding-the-requirements-for-a-time-series-model-intermediate-data-mining-tutorial"></a>Grundlegendes zu den Anforderungen für ein Zeitreihenmodell (Data Mining-Lernprogramm für Fortgeschrittene)
  Bei der Vorbereitung von Daten für ein Prognosemodell müssen Sie sicherstellen, dass die Daten eine Spalte enthalten, mit der Sie die Schritte in der Zeitreihe identifizieren können. Diese Spalte wird zur `Key Time`-Spalte bestimmt. Da es sich um einen Schlüssel handelt, muss die Spalte eindeutige numerische Werte enthalten.  
  
 Die Auswahl der richtigen Einheit für die `Key Time`-Spalte ist ein wichtiger Teil der Analyse. Nehmen Sie zum Beispiel an, dass die Umsatzdaten minütlich aktualisiert werden. Sie würden nicht notwendigerweise Minuten als Einheit für die Zeitreihe verwenden. Möglicherweise ist es sinnvoller, die Umsatzdaten nach Tag, Woche oder sogar Monat aufzufahren. Wenn Sie unsicher sind, welche Zeiteinheit verwendet werden soll, erstellen Sie eine neue Datenquellensicht für jede Aggregation. So stellen Sie fest, ob sich auf jeder Aggregationsebene unterschiedliche Trends ergeben.  
  
 Für dieses Lernprogramm werden täglich Umsatzdaten in der Transaktionsvertriebsdatenbank erfasst; für Data Mining werden die Daten jedoch mithilfe einer Sicht monatlich vorab aggregiert.  
  
 Zudem ist es für die Analyse vorteilhaft, wenn die Daten so wenige Lücken wie möglich aufweisen. Wenn Sie mehrere Datenreihen analysieren möchten, sollten alle Serien nach Möglichkeit einheitliche Start- und Enddaten haben. Wenn die Daten unvollständig sind, aber diese Lücken sich nicht am Anfang oder Ende der Serie befinden, kann die Serie mit dem Parameter MISSING_VALUE_SUBSTITUTION vervollständigt werden. 
  [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] stellt zudem mehrere Optionen zum Vervollständigen unvollständiger Daten durch Mittelwerte oder Konstanten bereit.  
  
> [!WARNING]  
>  Die Tools PivotChart und PivotTable, die in früheren Versionen des Datenquellensicht-Designers enthalten waren, sind nicht mehr enthalten. Es empfiehlt sich, Lücken in Zeitreihendaten im Voraus mit Tools wie dem in [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] enthaltenen Daten-Profiler zu identifizieren.  
  
### <a name="to-identify-the-time-key-for-the-forecasting-model"></a>So identifizieren Sie den Zeitschlüssel für das Prognosemodell  
  
1.  Klicken Sie im **Bereich SalesByRegion. DSV [Design]** mit der rechten Maustaste auf die Tabelle vTimeSeries, und wählen Sie dann **Daten durchsuchen**aus.  
  
     Eine neue Registerkarte mit der Bezeichnung **vTimeSeries-Tabelle durchsuchen**wird geöffnet.  
  
2.  Überprüfen Sie auf der Registerkarte **Tabelle** die Daten, die in den Spalten timeingedex und Reporting Date verwendet werden.  
  
     Beide sind Sequenzen mit eindeutigen Werten und können als Zeitreihenschlüssel verwendet werden; die Datentypen der Spalten unterscheiden sich jedoch. Der `datetime`-Datentyp ist für den Microsoft Time Series-Algorithmus nicht erforderlich; die Werte müssen lediglich unterschiedlich und sortiert sein. Sie können daher beide Spalten als Zeitschlüssel für das Prognosemodell verwenden.  
  
3.  Wählen Sie in der Entwurfs Oberfläche der Datenquellen Sicht die Spalte Berichtsdatum und anschließend **Eigenschaften**aus. Klicken Sie anschließend auf die Spalte TimeIndex, und wählen Sie **Eigenschaften**aus.  
  
     Das Feld "TimeIndex" weist den Datentyp System. Int32 auf, wohingegen das Feldbericht Erstellungsdatum den Datentyp System. DateTime aufweist. Viele Data Warehouses konvertieren Datums-/Uhrzeitwerte in ganze Zahlen und verwenden die Ganzzahl-Spalte als Schlüssel, die Indizierungsleistung zu verbessern. Wenn Sie diese Spalte verwenden, trifft der Microsoft Time Series-Algorithmus allerdings Vorhersagen und verwendet hierfür zukünftige Werte wie etwa 201014, 201014 usw. Da Sie die Vorhersage von Vertriebs Daten mithilfe von Kalenderdaten darstellen möchten, verwenden Sie die Spalte "Reporting Date" als eindeutigen Bezeichner für die Reihe.  
  
### <a name="to-set-the-key-in-the-data-source-view"></a>So legen Sie den Schlüssel in der Datenquellensicht fest  
  
1.  Wählen Sie im **Bereich SalesByRegion. DSV**die Tabelle vTimeSeries aus.  
  
2.  Klicken Sie mit der rechten Maustaste auf die Spalte Bericht Erstellungsdatum, und wählen Sie **logischen Primärschlüssel festlegen**aus.  
  
## <a name="handling-missing-data-optional"></a>Behandeln von unvollständigen Daten (optional)  
 Bei der Verarbeitung von Modellreihen mit unvollständigen Daten wird möglicherweise ein Fehler generiert. Sie haben mehrere Möglichkeiten, dieses Problem zu umgehen:  
  
-   Lassen Sie die unvollständigen Daten von Analysis Services durch Berechnung von Mittelwerten oder Verwendung von vorherigen Werten ergänzen. Zu diesem Zweck legen Sie den MISSING_VALUE_SUBSTITUTION-Parameter für das Miningmodell fest. Weitere Informationen zu diesem Parameter finden Sie unter [Technische Referenz für den Microsoft Time Series-Algorithmus](../../2014/analysis-services/data-mining/microsoft-time-series-algorithm-technical-reference.md). Weitere Informationen zum Ändern von Parametern für ein vorhandenes Mining Modell finden Sie unter [anzeigen oder Ändern von Algorithmusparametern](../../2014/analysis-services/data-mining/view-or-change-algorithm-parameters.md).  
  
-   Ändern Sie die Datenquelle, oder filtern Sie die zugrunde liegende Sicht, um unregelmäßige Reihe auszuschließen oder Werte zu ersetzen. Sie können dies in der relationalen Datenquelle vornehmen, oder Sie können die die Datenquellensicht ändern, indem Sie benutzerdefinierte benannte Abfragen oder benannte Berechnungen erstellen. Weitere Informationen finden Sie unter [Datenquellsichten in mehrdimensionalen Modellen](https://docs.microsoft.com/analysis-services/multidimensional-models/data-source-views-in-multidimensional-models). In einer weiteren Aufgabe in dieser Lektion wird ein Beispiel für das Erstellen einer benannten Abfrage sowie einer benutzerdefinierten Berechnung gegeben.  
  
 In diesem Szenario fehlen Daten am Anfang einer Reihe: das heißt, es gibt bis zu zum Juli 2007 keine Daten für die T1000-Produktlinie. Ansonsten enden alle Reihen zum selben Datum, und es gibt keine fehlenden Werte.  
  
 Der Microsoft Time Series-Algorithmus erfordert, dass jede Reihe, die Sie in einem einzelnen Modell einschließen, denselben **Endpunkt** hat. Das Fahrradmodell T1000 wurde erst im Jahr 2007 eingeführt. Die Daten für diese Reihe liegen daher im Vergleich zu den anderen Modellen erst ab einem späteren Zeitpunkt vor; der Endpunkt ist jedoch gleich, sodass die Daten verwendet werden können.  
  
#### <a name="to-close-the-data-source-view-designer"></a>So schließen Sie den Datenquellensicht-Designer  
  
-   Klicken Sie mit der rechten Maustaste auf die Registerkarte **vTimeSeries-Tabelle durchsuchen**, und wählen Sie **Schließen**.  
  
## <a name="next-task-in-lesson"></a>Nächste Aufgabe in der Lektion  
 [Erstellen einer Planungsstruktur und eines Modells &#40;Data Mining-Lernprogramm für fortgeschrittene&#41;](../../2014/tutorials/creating-a-forecasting-structure-and-model-intermediate-data-mining-tutorial.md)  
  
## <a name="see-also"></a>Weitere Informationen  
 [Microsoft Time Series-Algorithmus](../../2014/analysis-services/data-mining/microsoft-time-series-algorithm.md)  
  
  
