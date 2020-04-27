---
title: Assistent zum Klassifizieren (Data Mining-Add-Ins für Excel) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 12/29/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- data modeling [data mining]
- classification [data mining]
ms.assetid: 409c5076-c4c3-4f09-8f30-d3297df45f13
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: a62d937a733ea41b85a83224a043ff4ad7ecdd29
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/26/2020
ms.locfileid: "66087929"
---
# <a name="classify-wizard-data-mining-add-ins-for-excel"></a>Assistent zum Klassifizieren (Data Mining-Add-Ins für Excel)
  ![Assistent zum Klassifizieren (Data Mining-Menüband)](media/dmc-classify.gif "Assistent zum Klassifizieren (Data Mining-Menüband)")  
  
 Der Assistent zum **klassifizieren** unterstützt Sie beim Erstellen eines Klassifizierungs Modells auf der Grundlage vorhandener Daten in einer Excel-Tabelle, eines Excel-Bereichs oder einer externen Datenquelle.  
  
 Mit einem Klassifizierungsmodell werden Muster in den Daten extrahiert, die auf Übereinstimmungen hinweisen. So können Sie Vorhersagen basierend auf Wertgruppen treffen. Ein Klassifizierungsmodell kann beispielsweise verwendet werden, um das Risiko auf der Grundlage von Einkommens- und Konsummustern vorherzusagen.  
  
## <a name="using-the-classify-wizard"></a>Verwenden des Assistenten zum Klassifizieren  
  
1.  Klicken Sie im Menüband **Data Mining** auf **klassifizieren**und dann auf **weiter**.  
  
2.  Wählen Sie auf der Seite **Quelldaten auswählen** die zu analysierenden Daten aus.  
  
     Dieser Assistent unterstützt verschiedene Daten: Excel-Tabellen, Excel-Bereiche und externe Datenquellen. Externe Daten können Sie entweder zu Excel hinzufügen, oder Sie wählen in einer Analysis Services-Datenquelle eine Gruppe von Tabellen oder Sichten aus. Sie können auch Tabellen hinzufügen und Spalten ändern, um Ad-hoc-Datenquellen zu erstellen.  
  
3.  Wählen Sie auf der Seite **Klassifizierung** die Spalte aus, die Sie klassifizieren möchten.  
  
     Überprüfen Sie die Spalten in der Liste, **Eingabe Spalten**, und deaktivieren Sie alle Spalten, die eindeutige Werte aufweisen und daher nicht zum Erstellen von Mustern wie ID-Nummern, Kundennamen usw. nützlich sind. Außerdem sollten Sie auch die Spalten entfernen, die die klassifizierbare Spalte im Grunde duplizieren.  
  
     Wenn Sie zum Beispiel die Kategorieprognose eines Produkts klassifizieren, sollten Sie das Feld mit der Unterkategorie ausschließen, wenn eine bekannte Geschäftsregel vorhanden ist. Andernfalls könnte die Stärke dieser Regel verhindern, dass Sie andere Korrelationen erkennen.  
  
4.  Klicken Sie optional auf **Parameter** , um die Algorithmusparameter zu ändern und das Verhalten des Clustering-Modells anzupassen.  
  
5.  Geben Sie auf der Seite **Daten in Trainings-und Testsätze aufteilen** an, wie viele Daten zum Testen aufbewahrt werden sollen. Der Rest wird immer zum Trainieren des Modells verwendet.  
  
     In der Standardeinstellung sind 30 % als Testdaten und 70 % als Trainingsdaten festgelegt.  
  
6.  Geben Sie auf der Seite **Fertig** stellen einen beschreibenden Namen für das DataSet und das Modell an, und legen Sie die folgenden Optionen fest, mit denen die Arbeit mit dem fertigen Modell gesteuert wird:  
  
    -   **Modell durchsuchen**. Wenn diese Option ausgewählt ist, wird das Fenster **Durchsuchen** geöffnet, sobald der Assistent die Verarbeitung des Modells abgeschlossen hat, damit Sie die Ergebnisse untersuchen können. Der Inhalt des Viewers hängt vom Typ des erstellten Modells ab. Weitere Informationen finden Sie unter durch [Suchen eines Entscheidungsstruktur Modells](browsing-a-decision-trees-model.md) und durch [Suchen eines neuronalen Netzwerk Modells](browsing-a-neural-network-model.md).  
  
    -   **Drillthrough aktivieren**. Wählen Sie diese Option aus, um die zugrunde liegenden Daten des fertigen Modells anzuzeigen. Diese Option ist nur verfügbar, wenn Sie ein Decision Tree-Modell erstellen.  
  
    -   **Temporäres Modell verwenden**. Wenn Sie diese Option auswählen, wird das Modell nicht auf dem Server gespeichert. Temporäre Modelle werden beim Schließen von Excel gelöscht.  
  
## <a name="more-about-classification-models"></a>Weitere Informationen zu Klassifikationsmodellen  
 Im Dialogfeld **Algorithmusparameter** können Sie auch die Klassifizierungsmethode aus diesen Algorithmen auswählen, die in Analysis Services bereitgestellt werden:  
  
-   Microsoft Decision Tree  
  
-   Microsoft Logistic Regression  
  
-   Microsoft Naive Bayes  
  
-   Microsoft Neural Network  
  
 Die Algorithmen führen zwar zu ähnlichen Ergebnissen, doch die Daten werden unterschiedlich analysiert. Daher wird empfohlen, mehrere Algorithmen zu testen und die Ergebnisse zu vergleichen. Die Standardmethode ist Microsoft Decision Trees.  
  
 In der Liste **Parameter** können Sie erweiterte Optionen ändern, die vom gewählten Algorithmustyp abhängen. Die Parameter für die einzelnen Algorithmen werden in der SQL Server-Onlinedokumentation ausführlicher beschrieben.  
  
 [Technische Referenz für den Microsoft Decision Trees-Algorithmus](data-mining/microsoft-decision-trees-algorithm-technical-reference.md)  
  
 [Technische Referenz für den Microsoft Logistic Regression-Algorithmus](data-mining/microsoft-logistic-regression-algorithm-technical-reference.md)  
  
 [Technische Referenz für den Microsoft Naive Bayes-Algorithmus](data-mining/microsoft-naive-bayes-algorithm-technical-reference.md)  
  
 [Technische Referenz für den Microsoft Neural Network-Algorithmus](data-mining/microsoft-neural-network-algorithm-technical-reference.md)  
  
### <a name="requirements"></a>Anforderungen  
 Wenn Sie den **klassifizier** enden Assistenten verwenden möchten, müssen Sie [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] mit einer-Datenbank verbunden sein. Weitere Informationen zum Erstellen einer Verbindung finden Sie unter Herstellen einer Verbindung [mit Quelldaten &#40;Data Mining-Client für Excel&#41;](connect-to-source-data-data-mining-client-for-excel.md).  
  
## <a name="see-also"></a>Weitere Informationen  
 [Erstellen eines Data Mining-Modells](creating-a-data-mining-model.md)  
  
  
