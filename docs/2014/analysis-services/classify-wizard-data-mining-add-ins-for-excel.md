---
title: Klassifizieren-Assistent (Data Mining-Add-ins für Excel) | Microsoft Docs
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
- classification [data mining]
ms.assetid: 409c5076-c4c3-4f09-8f30-d3297df45f13
caps.latest.revision: 20
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: 5f71610a317be36a84fa90aff08bed8d6a50d8aa
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/19/2018
ms.locfileid: "36057721"
---
# <a name="classify-wizard-data-mining-add-ins-for-excel"></a>Assistent zum Klassifizieren (Data Mining-Add-Ins für Excel)
  ![Assistenten zum Klassifizieren in Data Mining-Menüband](media/dmc-classify.gif "klassifizieren-Assistenten im Data Mining-Menüband")  
  
 Die **klassifizieren** Assistent unterstützt Sie bei der Erstellung eines klassifizierungsmodells des Typs basierend auf vorhandenen Daten in einer Excel-Tabelle, einem Excel-Bereich oder einer externen Datenquelle.  
  
 Mit einem Klassifizierungsmodell werden Muster in den Daten extrahiert, die auf Übereinstimmungen hinweisen. So können Sie Vorhersagen basierend auf Wertgruppen treffen. Ein Klassifizierungsmodell kann beispielsweise verwendet werden, um das Risiko auf der Grundlage von Einkommens- und Konsummustern vorherzusagen.  
  
## <a name="using-the-classify-wizard"></a>Verwenden des Assistenten zum Klassifizieren  
  
1.  In der **Data Mining** des Menübands, klicken Sie auf **klassifizieren**, und klicken Sie dann auf **Weiter**.  
  
2.  In der **Quelldaten auswählen** Seite, und wählen Sie die zu analysierenden Daten.  
  
     Dieser Assistent unterstützt verschiedene Daten: Excel-Tabellen, Excel-Bereiche und externe Datenquellen. Externe Daten können Sie entweder zu Excel hinzufügen, oder Sie wählen in einer Analysis Services-Datenquelle eine Gruppe von Tabellen oder Sichten aus. Sie können auch Tabellen hinzufügen und Spalten ändern, um Ad-hoc-Datenquellen zu erstellen.  
  
3.  Auf der **Klassifizierung** Seite, und wählen Sie die Spalte, die Sie klassifizieren möchten.  
  
     Überprüfen Sie die Spalten in der Liste **Eingabespalten**, und deaktivieren Sie alle Spalten, die eindeutige Werte aufweisen und somit nicht nützlich zum Erstellen von Mustern, z. B. IDs, Kundennamen, und so weiter. Außerdem sollten Sie auch die Spalten entfernen, die die klassifizierbare Spalte im Grunde duplizieren.  
  
     Wenn Sie zum Beispiel die Kategorieprognose eines Produkts klassifizieren, sollten Sie das Feld mit der Unterkategorie ausschließen, wenn eine bekannte Geschäftsregel vorhanden ist. Andernfalls könnte die Stärke dieser Regel verhindern, dass Sie andere Korrelationen erkennen.  
  
4.  Klicken Sie optional auf **Parameter** die Algorithmusparameter ändern und das Verhalten des Clusteringmodells anzupassen.  
  
5.  In der **Daten in Trainings- und Testsätze aufteilen** Seite, die angeben, wie viele Daten zum Testen zurückgehalten. Der Rest wird immer zum Trainieren des Modells verwendet.  
  
     In der Standardeinstellung sind 30 % als Testdaten und 70 % als Trainingsdaten festgelegt.  
  
6.  Auf der **Fertig stellen** Seite Geben Sie einen beschreibenden Namen für das DataSet und das Modell, und legen Sie die folgenden Optionen, die steuern, wie Sie mit dem fertigen Modell arbeiten:  
  
    -   **Modell durchsuchen,**. Wenn diese Option aktiviert ist, so bald wie den Assistenten nach Abschluss der Verarbeitung des Modells Eröffnung einen **Durchsuchen** Fenster können Sie die Ergebnisse untersuchen. Der Inhalt des Viewers hängt vom Typ des erstellten Modells ab. Weitere Informationen finden Sie unter [Durchsuchen eines Entscheidungsstrukturmodells](browsing-a-decision-trees-model.md) und [Durchsuchen eines neuronalen Netzwerkmodells](browsing-a-neural-network-model.md).  
  
    -   **Aktivieren von Drillthrough**. Wählen Sie diese Option aus, um die zugrunde liegenden Daten des fertigen Modells anzuzeigen. Diese Option ist nur verfügbar, wenn Sie ein Decision Tree-Modell erstellen.  
  
    -   **Temporäres Modell**. Wenn Sie diese Option auswählen, wird das Modell nicht auf dem Server gespeichert. Temporäre Modelle werden beim Schließen von Excel gelöscht.  
  
## <a name="more-about-classification-models"></a>Weitere Informationen zu Klassifikationsmodellen  
 In der **Algorithmusparameter** (Dialogfeld), Sie können auch die Klassifizierungsmethode aus dieser in Analysis Services bereitgestellten Algorithmen auswählen:  
  
-   Microsoft Decision Tree  
  
-   Microsoft Logistic Regression  
  
-   Microsoft Naive Bayes  
  
-   Microsoft Neural Network  
  
 Die Algorithmen führen zwar zu ähnlichen Ergebnissen, doch die Daten werden unterschiedlich analysiert. Daher wird empfohlen, mehrere Algorithmen zu testen und die Ergebnisse zu vergleichen. Die Standardmethode ist Microsoft Decision Trees.  
  
 In der **Parameter** Liste können Sie erweiterte Optionen, die auf den Typ des Algorithmus abhängig sind, wählen Sie Sie, ändern. Die Parameter für die einzelnen Algorithmen werden in der SQL Server-Onlinedokumentation ausführlicher beschrieben.  
  
 [Technische Referenz für den Microsoft Decision Trees-Algorithmus](data-mining/microsoft-decision-trees-algorithm-technical-reference.md)  
  
 [Technische Referenz für den Microsoft Logistic Regression-Algorithmus](data-mining/microsoft-logistic-regression-algorithm-technical-reference.md)  
  
 [Technische Referenz für den Microsoft Naive Bayes-Algorithmus](data-mining/microsoft-naive-bayes-algorithm-technical-reference.md)  
  
 [Technische Referenz für den Microsoft Neural Network-Algorithmus](data-mining/microsoft-neural-network-algorithm-technical-reference.md)  
  
### <a name="requirements"></a>Anforderungen  
 Verwenden der **klassifizieren** Assistenten, Sie müssen verbunden sein ein [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] Datenbank. Informationen dazu, wie Sie eine Verbindung zu erstellen, finden Sie unter [Herstellen einer Verbindung mit Quelldaten &#40;Data Mining-Client für Excel&#41;](connect-to-source-data-data-mining-client-for-excel.md).  
  
## <a name="see-also"></a>Siehe auch  
 [Erstellen eines Data Mining-Modells](creating-a-data-mining-model.md)  
  
  