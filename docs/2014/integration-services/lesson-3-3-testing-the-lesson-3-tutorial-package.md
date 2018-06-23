---
title: 'Schritt 3: Testen des Lektion 3-Tutorialpakets | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- integration-services
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 1096a476-93cf-4474-86f5-27d6357eb380
caps.latest.revision: 27
author: douglaslM
ms.author: douglasl
manager: jhubbard
ms.openlocfilehash: 03a681cf4ab018d82d991b91c463dfbef3fe8d73
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/19/2018
ms.locfileid: "36148654"
---
# <a name="step-3-testing-the-lesson-3-tutorial-package"></a>Schritt 3: Testen des Lektion 3-Tutorialpakets
  In dieser Aufgabe führen Sie das Paket Lesson 3.dtsx aus. Beim Ausführen des Pakets werden im Fenster Protokollereignisse die Protokolleinträge aufgelistet, die in die Protokolldatei geschrieben werden. Nachdem vom Paket die Ausführung abgeschlossen wurde, überprüfen Sie den Inhalt der Protokolldatei, die vom Protokollanbieter generiert worden ist.  
  
## <a name="checking-the-package-layout"></a>Überprüfen des Paketlayouts  
 Bevor Sie das Paket testen, sollten Sie überprüfen, ob Ablaufsteuerung und Datenfluss im Paket aus Lektion 3 die in den folgenden Diagrammen gezeigten Objekte enthalten. Die Ablaufsteuerung sollte mit der Ablaufsteuerung in Lektion 2 übereinstimmen. Der Datenfluss sollte mit dem Datenfluss in den Lektionen 1 und 2 übereinstimmen.  
  
 **Ablaufsteuerung**  
  
 ![Ablaufsteuerung im Paket](../../2014/tutorials/media/task4lesson2control.gif "Ablaufsteuerung im Paket")  
  
 **Datenfluss**  
  
 ![Datenfluss im Paket](../../2014/tutorials/media/task9lesson1data.gif "Datenfluss im Paket")  
  
### <a name="to-run-the-lesson-4-tutorial-package"></a>So führen Sie das Lernprogrammpaket aus Lektion 4 aus  
  
1.  Klicken Sie im Menü SSIS auf Protokollereignisse.  
  
2.  Klicken Sie im Menü **Debuggen** auf **Debuggen starten**.  
  
3.  Klicken Sie nach Ausführen des Pakets im Menü **Debuggen** auf **Debuggen beenden**.  
  
### <a name="to-examine-the-generated-log-file"></a>So überprüfen Sie die generierte Protokolldatei  
  
-   Öffnen Sie mithilfe von Editor oder einem anderen Text-Editor die Datei TutorialLog.log.  
  
-   Obwohl für die Semantik der Informationen generiert die `PipelineExecutionPlan` und `PipelineExecutionTrees` Ereignisse sind nicht Gegenstand dieses Lernprogramms, sehen Sie, dass die erste Zeile die Informationsfelder, die im angegebenen Listet die **Details** Registerkarte die **SSIS-Protokolle konfigurieren** (Dialogfeld). Darüber hinaus können Sie überprüfen, dass die zwei von Ihnen ausgewählten Ereignisse (PipelineExecutionPlan und PipelineExecutionTrees) für jede Iteration der Foreach-Schleife protokolliert worden sind.  
  
## <a name="next-lesson"></a>Nächste Lektion  
 [Lektion 4: Hinzufügen der Fehlerflussumleitung](../integration-services/lesson-4-add-error-flow-redirection-with-ssis.md)  
  
  