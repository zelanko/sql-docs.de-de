---
title: Schätzen der Assistent (Data Mining-Add-ins für Excel) | Microsoft Docs
ms.custom: ''
ms.date: 12/29/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- data modeling [data mining]
- estimation
ms.assetid: 7f2b1d5f-c9b3-4939-b35a-34ae099af15f
caps.latest.revision: 23
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: 231afdcfdc5c6e9e461e463fb5b6c3c682e70cde
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/19/2018
ms.locfileid: "36057370"
---
# <a name="estimate-wizard-data-mining-add-ins-for-excel"></a>Assistent zum Schätzen von Daten (Data Mining-Add-Ins für Excel)
  ![Assistent zum schätzen in Data Mining-Menüband](media/dmc-estimate.gif "Schätzung-Assistenten im Data Mining-Menüband")  
  
 Die **Schätzung** Assistenten können Sie ein schätzmodell erstellen. Ein Schätzmodell extrahiert Datenmuster und verwendet diese Muster, um die Faktoren vorherzusagen, die sich auf Ergebnisse auswirken.  
  
 Die Schätzung wird für die Vorhersage von numerischen Ergebnissen verwendet. Z. B. wenn die Zielspalte schulabschlussquoten, mit etwa schulabschlussquoten enthält Sie können analysieren Faktoren, die potenziell erhöht oder gesenkt schulabschlussquoten, z. B. die Anzahl der Schüler pro Schule, die Schüler-Lehrer-Verhältnis und die Anzahl der Lehrer.  
  
## <a name="using-the-estimate-data-wizard"></a>Verwenden des Assistenten zum Schätzen von Daten  
  
1.  Auf der **Data Mining** des Menübands, klicken Sie auf **Schätzung**.  
  
2.  In der **Quelldaten auswählen** Dialogfeld wählen die Quelldaten zu verwenden. Können Sie Daten in einem Excel **Tabelle**, eine Excel **Datenbereich**, oder aus einer **externen Datenquelle**.  
  
     Wenn Sie eine externe Datenquelle verwenden, können Sie benutzerdefinierte Sichten oder Abfragen erstellen und als [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]-Datenquelle speichern.  
  
3.  In der **Schätzung** wählen Sie im Dialogfeld die **zu analysierende Spalte**.  
  
     Die Zielspalte muss kontinuierliche numerische Daten enthalten.  
  
4.  Wählen Sie Spalten aus, die als Eingabe verwenden, indem Sie die Überprüfung der **Eingabespalten** Kontrollkästchen.  
  
     Diese Spalten werden zum Erstellen der Muster verwendet. Es empfiehlt sich, alle Spalten aus der Analyse auszuschließen, die voraussichtlich nicht hilfreich bei einer Analyse sind (z. B. ID-Nummern) oder irrelevante Daten enthalten.  
  
5.  Die **Schätzung** Assistent wählt den optimalen Algorithmus für das DataSet. Sie können jedoch klicken **Parameter** zu öffnen die **Algorithmusparameter** Dialogfeld und erweiterte Optionen festzulegen.  
  
6.  Wenn Ihre Daten numerische sind und Sie können den Microsoft Linear Regression-Methode verwenden, sehen Sie sich die **Regressor** Kontrollkästchen für alle numerischen Spalten, die Sie kennen (oder höchster) mit dem vorhersagbaren Wert korreliert werden.  
  
     Der Algorithmus testet dann die Werte in der betreffenden Spalte, um zu ermitteln, ob sie sich auf die Ergebnisse auswirken. Wenn Sie unsicher sind, klicken Sie auf **vorschlagen** und der Algorithmus testet dann alle Spalten und automatisch erkennen die besten Werte, die als Regressoren verwendet wird.  
  
    > [!NOTE]  
    >  Ein Regressor ist erforderlich, um eine Schätzung zu erstellen. Der Assistent empfiehlt auf Grundlage eines ersten Datendurchlaufs immer den besten Regressor. Wenn Sie nicht sicher sind, ist es deshalb am besten, die empfohlene Auswahl zu akzeptieren.  
  
7.  Auf der **Daten in Trainings- und Testsätze aufteilen** Seite, die angeben, ob Sie eine kleine Teilmenge der Daten für Tests erstellen möchten.  
  
8.  Auf der **Fertig stellen** Seite, geben Sie Namen für die neue Miningstruktur und Mining-Modus, oder übernehmen Sie den Standardnamen, die bereitgestellt werden.  
  
9. Legen Sie die Optionen zum Verwenden des Modells fest.  
  
    -   Wählen Sie **Durchsuchen** um das Modell sofort in einem Viewer zu öffnen.  
  
         Dieser grafische Viewer zeigt ein Abhängigkeitsnetzwerkdiagramm und die vom Algorithmus generierte Entscheidungsstruktur an. Untersuchen Sie diese Informationen, um sich ein Bild von den Faktoren zu machen, die die geschätzten Werte beeinflussen.  
  
    -   Wählen Sie **Drillthrough aktivieren** können Benutzer, der die Analyse der zugrunde liegenden Daten anzeigen.  
  
         Diese Option ist nur verfügbar, wenn Sie den Decision Trees-Algorithmus oder den Linear Regression-Algorithmus verwenden.  
  
    -   **Temporäres Modell**. Wenn Sie diese Option auswählen, wird das Modell nicht auf dem Server gespeichert. Temporäre Modelle werden beim Schließen von Excel gelöscht.  
  
## <a name="more-about-estimation-models"></a>Weitere Informationen zu Schätzmodellen  
 Die **Schätzung** -Assistent unterstützt die Verwendung von einem der folgenden Algorithmen:  
  
-   Microsoft Decision Tree-Algorithmus  
  
-   Microsoft Linear Regression-Algorithmus  
  
-   Microsoft Logistic Regression-Algorithmus  
  
-   Microsoft Neural Network-Algorithmus  
  
 In der **Algorithmusparameter** (Dialogfeld), Sie können zusätzliche erweiterte Optionen, je nachdem welcher Algorithmus gewählten festlegen. Weitere Informationen zu den Optionen für die einzelnen Algorithmen finden Sie in der SQL Server-Onlinedokumentation in folgenden Themen:  
  
 [Technische Referenz für den Microsoft Decision Trees-Algorithmus](data-mining/microsoft-decision-trees-algorithm-technical-reference.md)  
  
 [Technische Referenz für den Microsoft Linear Regression-Algorithmus](data-mining/microsoft-linear-regression-algorithm-technical-reference.md)  
  
 [Technische Referenz für den Microsoft Logistic Regression-Algorithmus](data-mining/microsoft-logistic-regression-algorithm-technical-reference.md)  
  
 [Technische Referenz für den Microsoft Neural Network-Algorithmus](data-mining/microsoft-neural-network-algorithm-technical-reference.md)  
  
### <a name="requirements"></a>Anforderungen  
 Zum Verwenden des Assistenten zum Schätzen von Daten muss eine Verbindung mit einer [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]-Datenbank bestehen.  
  
 Informationen dazu, wie Sie eine Verbindung zu erstellen, finden Sie unter [Herstellen einer Verbindung mit Quelldaten &#40;Data Mining-Client für Excel&#41;](connect-to-source-data-data-mining-client-for-excel.md).  
  
 Um den Schätzalgorithmus zu verwenden, muss das Ergebnis, das vorhergesagt werden soll, als numerischer Wert ausgedrückt werden, z. B. als Währung, Umsatz, Datum oder Uhrzeit.  
  
## <a name="see-also"></a>Siehe auch  
 [Erstellen von Datamining-Modells](creating-a-data-mining-model.md)   
 [Exemplarische Vorgehensweise für die Entscheidung &#40;Data Mining-Add-ins&#41;](decision-tree-diagram-walkthrough-data-mining-add-ins.md)  
  
  