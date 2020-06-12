---
title: Assistent zum Schätzen von Daten (Data Mining-Add-Ins für Excel) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 12/29/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- data modeling [data mining]
- estimation
ms.assetid: 7f2b1d5f-c9b3-4939-b35a-34ae099af15f
author: minewiskan
ms.author: owend
ms.openlocfilehash: 2706dae37c1dc303aa6708fe1f7387a39835e4d5
ms.sourcegitcommit: 2f166e139f637d6edfb5731510d632a13205eb25
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/08/2020
ms.locfileid: "84528368"
---
# <a name="estimate-wizard-data-mining-add-ins-for-excel"></a>Assistent zum Schätzen von Daten (Data Mining-Add-Ins für Excel)
  ![Assistent zum Schätzen von Daten (Data Mining-Menüband)](media/dmc-estimate.gif "Assistent zum Schätzen von Daten (Data Mining-Menüband)")  
  
 Der Assistent für die **Schätzung** unterstützt Sie beim Erstellen eines Schätz Modells. Ein Schätzmodell extrahiert Datenmuster und verwendet diese Muster, um die Faktoren vorherzusagen, die sich auf Ergebnisse auswirken.  
  
 Die Schätzung wird für die Vorhersage von numerischen Ergebnissen verwendet. Wenn die Ziel Spalte z. b. die Abschluss Raten für Schulen enthält und die Abschluss Sätze als Prozentsätze ausgedrückt werden, können Sie Faktoren analysieren, die die Abschluss Raten potenziell erhöhen oder verringern, wie z. b. die Anzahl der Schüler/Studenten pro Schule, das Verhältnis des Studenten Lehrers und die Anzahl der Lehrkräfte.  
  
## <a name="using-the-estimate-data-wizard"></a>Verwenden des Assistenten zum Schätzen von Daten  
  
1.  Klicken Sie im Menüband **Data Mining** auf **Schätzung**.  
  
2.  Wählen Sie im Dialogfeld **Quelldaten auswählen** die Quelldaten aus, die verwendet werden sollen. Sie können Daten in einer Excel- **Tabelle**, einem Excel- **Datenbereich**oder einer **externen Datenquelle**verwenden.  
  
     Wenn Sie eine externe Datenquelle verwenden, können Sie benutzerdefinierte Sichten oder Abfragen erstellen und als [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]-Datenquelle speichern.  
  
3.  Wählen Sie im Dialogfeld **Schätzung** die **zu analysierende Spalte**aus.  
  
     Die Zielspalte muss kontinuierliche numerische Daten enthalten.  
  
4.  Wählen Sie die zu verwendenden Spalten aus, indem Sie das Kontrollkästchen **Eingabe Spalten** aktivieren.  
  
     Diese Spalten werden zum Erstellen der Muster verwendet. Es empfiehlt sich, alle Spalten aus der Analyse auszuschließen, die voraussichtlich nicht hilfreich bei einer Analyse sind (z. B. ID-Nummern) oder irrelevante Daten enthalten.  
  
5.  Der Assistent zum **schätzen** wählt den optimalen Algorithmus für das DataSet aus. Sie können jedoch auf **Parameter** klicken, um das Dialogfeld **Algorithmusparameter** zu öffnen und erweiterte Optionen festzulegen.  
  
6.  Wenn die Daten numerisch sind und Sie die lineare Regressions Methode von Microsoft verwenden können, können Sie das Feld **Regressor** für alle numerischen Spalten aktivieren, die Sie kennen (oder stark vermuten), die mit dem vorhersagbaren Wert korreliert werden sollen.  
  
     Der Algorithmus testet dann die Werte in der betreffenden Spalte, um zu ermitteln, ob sie sich auf die Ergebnisse auswirken. Wenn Sie sich nicht sicher sind, klicken Sie auf **vorschlagen** , und der Algorithmus testet alle Spalten und erkennt automatisch die besten Werte, die als Regressoren verwendet werden sollen.  
  
    > [!NOTE]  
    >  Ein Regressor ist erforderlich, um eine Schätzung zu erstellen. Der Assistent empfiehlt auf Grundlage eines ersten Datendurchlaufs immer den besten Regressor. Wenn Sie nicht sicher sind, ist es deshalb am besten, die empfohlene Auswahl zu akzeptieren.  
  
7.  Geben Sie auf der Seite **Daten in Trainings-und Testsätze aufteilen** an, ob Sie eine kleine Teilmenge der Daten für Tests erstellen möchten.  
  
8.  Geben Sie auf der Seite **Fertig** stellen Namen für die neue Mining Struktur und den Mining Modus an, oder übernehmen Sie die bereitgestellten Standardnamen.  
  
9. Legen Sie die Optionen zum Verwenden des Modells fest.  
  
    -   Wählen Sie **Durchsuchen** aus, um das Modell direkt in einem Viewer zu öffnen.  
  
         Dieser grafische Viewer zeigt ein Abhängigkeitsnetzwerkdiagramm und die vom Algorithmus generierte Entscheidungsstruktur an. Untersuchen Sie diese Informationen, um sich ein Bild von den Faktoren zu machen, die die geschätzten Werte beeinflussen.  
  
    -   Wählen Sie **Drillthrough aktivieren** aus, damit Benutzer Ihrer Analyse die zugrunde liegenden Daten anzeigen können.  
  
         Diese Option ist nur verfügbar, wenn Sie den Decision Trees-Algorithmus oder den Linear Regression-Algorithmus verwenden.  
  
    -   **Temporäres Modell verwenden**. Wenn Sie diese Option auswählen, wird das Modell nicht auf dem Server gespeichert. Temporäre Modelle werden beim Schließen von Excel gelöscht.  
  
## <a name="more-about-estimation-models"></a>Weitere Informationen zu Schätzmodellen  
 Der Assistent für die **Schätzung** unterstützt die Verwendung der folgenden Algorithmen:  
  
-   Microsoft Decision Tree-Algorithmus  
  
-   Microsoft Linear Regression-Algorithmus  
  
-   Microsoft Logistic Regression-Algorithmus  
  
-   Microsoft Neural Network-Algorithmus  
  
 Im Dialogfeld **Algorithmusparameter** können Sie je nach ausgewähltem Algorithmus zusätzliche erweiterte Optionen festlegen. Weitere Informationen zu den Optionen für die einzelnen Algorithmen finden Sie in der SQL Server-Onlinedokumentation in folgenden Themen:  
  
 [Technische Referenz für den Microsoft Decision Trees-Algorithmus](data-mining/microsoft-decision-trees-algorithm-technical-reference.md)  
  
 [Technische Referenz für den Microsoft Linear Regression-Algorithmus](data-mining/microsoft-linear-regression-algorithm-technical-reference.md)  
  
 [Technische Referenz für den Microsoft Logistic Regression-Algorithmus](data-mining/microsoft-logistic-regression-algorithm-technical-reference.md)  
  
 [Technische Referenz für den Microsoft Neural Network-Algorithmus](data-mining/microsoft-neural-network-algorithm-technical-reference.md)  
  
### <a name="requirements"></a>Requirements (Anforderungen)  
 Zum Verwenden des Assistenten zum Schätzen von Daten muss eine Verbindung mit einer [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]-Datenbank bestehen.  
  
 Weitere Informationen zum Erstellen einer Verbindung finden Sie unter Herstellen einer Verbindung [mit Quelldaten &#40;Data Mining-Client für Excel&#41;](connect-to-source-data-data-mining-client-for-excel.md).  
  
 Um den Schätzalgorithmus zu verwenden, muss das Ergebnis, das vorhergesagt werden soll, als numerischer Wert ausgedrückt werden, z. B. als Währung, Umsatz, Datum oder Uhrzeit.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Erstellen eines Data Mining-Modells](creating-a-data-mining-model.md)   
 [Entscheidungsstruktur Diagramm Exemplarische Vorgehensweise &#40;Data Mining-Add-ins&#41;](decision-tree-diagram-walkthrough-data-mining-add-ins.md)  
  
  
