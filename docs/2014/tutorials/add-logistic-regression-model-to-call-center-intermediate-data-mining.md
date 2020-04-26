---
title: Hinzufügen eines logistischen Regressionsmodells zur Callcenterstruktur (Data Mining-Lernprogramm für Fortgeschrittene) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: 97abb77a-346c-44fa-8959-688dee1af6a8
author: minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: 32e66a84dea20964c11c7de0aa568530aa8c28c5
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/26/2020
ms.locfileid: "62823277"
---
# <a name="adding-a-logistic-regression-model-to-the-call-center-structure-intermediate-data-mining-tutorial"></a>Hinzufügen eines logistischen Regressionsmodells zur Callcenterstruktur (Data Mining-Lernprogramm für Fortgeschrittene)
  Zusätzlich zur Analyse der Faktoren, die sich auf den Callcenterbetrieb auswirken können, wurden Sie außerdem aufgefordert, bestimmte Empfehlungen zur Verbesserung der Dienst Qualität anzugeben. Für diese Aufgabe verwenden Sie dieselbe Miningstruktur wie beim Erstellen des explorativen Modells. Sie fügen jedoch ein Miningmodell hinzu, das zum Erstellen von Vorhersagen verwendet wird.  
  
 In [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] basiert ein logistisches Regressionsmodell auf dem neuronalen Netzwerke-Algorithmus und hat daher dieselbe Flexibilität und Leistungsstärke wie ein neuronales Netzwerkmodell. Die logistische Regression ist jedoch besonders gut dafür geeignet, binäre Ergebnisse vorherzusagen.  
  
 Für dieses Szenario verwenden Sie die gleiche Miningstruktur, die Sie für das neuronale Netzwerkmodell verwendet haben. Sie passen jedoch das neue Modell an, um Ihre Geschäftsfragen gezielt zu beantworten. Sie möchten die Dienstqualität verbessern und bestimmen, wie viele erfahrene Operatoren Sie benötigen. Deshalb richten Sie das Modell für die Vorhersage dieser Werte ein.  
  
 Um sicherzustellen, dass alle Modelle auf Grundlage der Callcenterdaten die größtmögliche Ähnlichkeit aufweisen, verwenden Sie denselben Ausgangswert wie zuvor. Durch Festlegen des Ausgangswertparameters gewährleisten Sie, dass das Modell die Daten vom gleichen Ausgangspunkt verarbeitet. Sie minimieren so die von Artefakten in den Daten verursachten Variationen.  
  
### <a name="to-add-a-new-mining-model-to-the-call-center-mining-structure"></a>So fügen Sie der Callcenter-Miningstruktur ein neues Miningmodell hinzu  
  
1.  Klicken [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]Sie in Projektmappen-Explorer mit der rechten Maustaste auf die Mining Struktur **, und**wählen Sie dann die Option zum **Öffnen des Designers**aus.  
  
2.  Klicken Sie im Data Mining-Designer auf die Registerkarte **Mining Modelle** .  
  
3.  Klicken Sie auf Verknüpftes **Mining Modell erstellen**.  
  
4.  Geben `Call Center - LR`Sie im Dialogfeld **Neues Mining Modell** für **Modellname den Namen**ein.  Wählen Sie unter **Algorithmusname**die Option **Microsoft Logistic Regression**aus.  
  
5.  Klicken Sie auf **OK**.  
  
     Das neue Mining Modell wird auf der Registerkarte **Mining Modelle** angezeigt.  
  
### <a name="to-customize-the-logistic-regression-model"></a>So passen Sie das logistische Regressionsmodell an  
  
1.  Belassen Sie in der Spalte für das neue Mining `Call Center - LR`Modell die Fakten-Callcenter-ID als Schlüssel.  
  
2.  Ändern Sie den Wert für die **vorher zusagenden**Operatoren Service Grade und Level Two.  
  
     Diese Spalten werden sowohl für die Eingabe als auch für Vorhersagen verwendet. In Wesentlichen erstellen Sie zwei separate Modelle auf derselben Datenbasis: eines für die Vorhersage der Operatorenzahl, und eines für die Vorhersage der Dienstqualität.  
  
3.  Ändern Sie alle anderen Spalten in **Input**.  
  
### <a name="to-specify-the-seed-and-process-the-models"></a>So geben Sie den Ausgangswert an und verarbeiten die Modelle  
  
1.  Klicken Sie auf der Registerkarte **Mining Modell** mit der rechten Maustaste auf die Spalte für das Modell "Callcenter-LR", und wählen Sie **Algorithmusparameter festlegen**aus.  
  
2.  Klicken Sie in der Zeile für den HOLDOUT_SEED-Parameter auf die leere Zelle unter **Wert**, `1`und geben Sie ein. Klicken Sie auf **OK**.  
  
    > [!NOTE]  
    >  Welchen Wert Sie als Ausgangswert auswählen, ist gleichgültig, solange für alle verwandten Modelle der gleiche Ausgangswert verwendet wird.  
  
3.  Wählen Sie im Menü **Mining Modelle** die Option **Mining Struktur und alle Modelle verarbeiten**aus. Klicken Sie auf **Ja** , um das aktualisierte Data Mining-Projekt auf dem Server bereitzustellen.  
  
4.  Klicken Sie im Dialogfeld **Miningmodell verarbeiten** auf **Ausführen**.  
  
5.  Klicken Sie auf **Schließen** , um das Dialogfeld **Verarbeitungsstatus** zu schließen, und klicken Sie im Dialogfeld **Miningmodell verarbeiten** erneut auf **Schließen** .  
  
## <a name="next-task-in-lesson"></a>Nächste Aufgabe in der Lektion  
 [Erstellen von Vorhersagen für die Callcentermodelle &#40;Data Mining-Lernprogramm für fortgeschrittene&#41;](../../2014/tutorials/create-predictions-call-center-models-intermediate-data-mining-tutorial.md)  
  
## <a name="see-also"></a>Weitere Informationen  
 [Anforderungen und Überlegungen zur Verarbeitung &#40;Data Mining&#41;](../../2014/analysis-services/data-mining/processing-requirements-and-considerations-data-mining.md)  
  
  
