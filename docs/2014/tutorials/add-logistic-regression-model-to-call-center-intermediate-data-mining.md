---
title: Hinzufügen eines logistischen Regressionsmodells zur Callcenter-Struktur (Datamining-Lernprogramm für fortgeschrittene) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
ms.topic: conceptual
ms.assetid: 97abb77a-346c-44fa-8959-688dee1af6a8
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: b4afe3881d8e5eafaeffbd45aa7f64a514d8c70a
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/02/2018
ms.locfileid: "48208203"
---
# <a name="adding-a-logistic-regression-model-to-the-call-center-structure-intermediate-data-mining-tutorial"></a>Hinzufügen eines logistischen Regressionsmodells zur Callcenterstruktur (Data Mining-Lernprogramm für Fortgeschrittene)
  Zusätzlich zur Analyse der Faktoren, die auswirken können, wurden Sie auch aufgefordert, einige spezifischen Empfehlungen bereitstellen, wie das Personal die Dienstqualität verbessern können. Für diese Aufgabe verwenden Sie dieselbe Miningstruktur wie beim Erstellen des explorativen Modells. Sie fügen jedoch ein Miningmodell hinzu, das zum Erstellen von Vorhersagen verwendet wird.  
  
 In [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] basiert ein logistisches Regressionsmodell auf dem neuronalen Netzwerke-Algorithmus und hat daher dieselbe Flexibilität und Leistungsstärke wie ein neuronales Netzwerkmodell. Die logistische Regression ist jedoch besonders gut dafür geeignet, binäre Ergebnisse vorherzusagen.  
  
 Für dieses Szenario verwenden Sie die gleiche Miningstruktur, die Sie für das neuronale Netzwerkmodell verwendet haben. Sie passen jedoch das neue Modell an, um Ihre Geschäftsfragen gezielt zu beantworten. Sie möchten die Dienstqualität verbessern und bestimmen, wie viele erfahrene Operatoren Sie benötigen. Deshalb richten Sie das Modell für die Vorhersage dieser Werte ein.  
  
 Um sicherzustellen, dass alle Modelle auf Grundlage der Callcenterdaten die größtmögliche Ähnlichkeit aufweisen, verwenden Sie denselben Ausgangswert wie zuvor. Durch Festlegen des Ausgangswertparameters gewährleisten Sie, dass das Modell die Daten vom gleichen Ausgangspunkt verarbeitet. Sie minimieren so die von Artefakten in den Daten verursachten Variationen.  
  
### <a name="to-add-a-new-mining-model-to-the-call-center-mining-structure"></a>So fügen Sie der Callcenter-Miningstruktur ein neues Miningmodell hinzu  
  
1.  In [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)], im Projektmappen-Explorer mit der Maustaste der Miningstruktur **Callcenter-Klassifizierung**, und wählen Sie **Designer öffnen**.  
  
2.  Klicken Sie im Data Mining-Designer auf die **Miningmodelle** Registerkarte.  
  
3.  Klicken Sie auf **ein verknüpftes Miningmodell erstellen**.  
  
4.  In der **Neues Miningmodell** im Dialogfeld für **Modellname**, Typ `Call Center - LR`.  Für **Algorithmusname**Option **Microsoft Logistic Regression**.  
  
5.  Klicken Sie auf **OK**.  
  
     Das neue Miningmodell wird angezeigt, der **Miningmodelle** Registerkarte.  
  
### <a name="to-customize-the-logistic-regression-model"></a>So passen Sie das logistische Regressionsmodell an  
  
1.  In der Spalte für das neue Miningmodell `Call Center - LR`, lassen Sie Fact CallCenter ID als Schlüssel.  
  
2.  Ändern Sie den Wert von ServiceGrade und Operatoren auf Ebene 2 zu **Predict**.  
  
     Diese Spalten werden sowohl für die Eingabe als auch für Vorhersagen verwendet. In Wesentlichen erstellen Sie zwei separate Modelle auf derselben Datenbasis: eines für die Vorhersage der Operatorenzahl, und eines für die Vorhersage der Dienstqualität.  
  
3.  Ändern Sie alle anderen Spalten in **Eingabe**.  
  
### <a name="to-specify-the-seed-and-process-the-models"></a>So geben Sie den Ausgangswert an und verarbeiten die Modelle  
  
1.  In der **Miningmodell** , mit der rechten Maustaste der Spalte, für das Modell mit dem Namen Callcenter - LR, und wählen Sie **Algorithmusparameter festlegen**.  
  
2.  Klicken Sie in der Zeile für den HOLDOUT_SEED-Parameter, auf die leere Zelle unter **Wert**, und geben `1`. Klicken Sie auf **OK**.  
  
    > [!NOTE]  
    >  Welchen Wert Sie als Ausgangswert auswählen, ist gleichgültig, solange für alle verwandten Modelle der gleiche Ausgangswert verwendet wird.  
  
3.  In der **Miningmodelle** , wählen Sie im Menü **Miningstruktur verarbeiten und alle Modelle**. Klicken Sie auf **Ja** , um das aktualisierte Data Mining-Projekt auf dem Server bereitzustellen.  
  
4.  Klicken Sie im Dialogfeld **Miningmodell verarbeiten** auf **Ausführen**.  
  
5.  Klicken Sie auf **Schließen** , um das Dialogfeld **Verarbeitungsstatus** zu schließen, und klicken Sie im Dialogfeld **Miningmodell verarbeiten** erneut auf **Schließen** .  
  
## <a name="next-task-in-lesson"></a>Nächste Aufgabe in dieser Lektion  
 [Erstellen von Vorhersagen für Callcentermodelle &#40;Datamining-Lernprogramm für fortgeschrittene&#41;](../../2014/tutorials/create-predictions-call-center-models-intermediate-data-mining-tutorial.md)  
  
## <a name="see-also"></a>Siehe auch  
 [Anforderungen und Überlegungen zur Verarbeitung &#40;Datamining&#41;](../../2014/analysis-services/data-mining/processing-requirements-and-considerations-data-mining.md)  
  
  
