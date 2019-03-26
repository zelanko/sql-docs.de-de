---
title: 'Schritt 3: Testen des Tutorialpakets aus Lektion 3 | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 01/04/2019
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.technology: integration-services
ms.topic: tutorial
ms.assetid: 1096a476-93cf-4474-86f5-27d6357eb380
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: c7e644744a53318ed1359bc0cdb47c3c896ed5ff
ms.sourcegitcommit: 7ccb8f28eafd79a1bddd523f71fe8b61c7634349
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/20/2019
ms.locfileid: "58274854"
---
# <a name="lesson-3-3-test-the-lesson-3-tutorial-package"></a>Lektion 3.3: Testen des Tutorialpakets aus Lektion 3

In dieser Aufgabe sollen Sie das Paket **Lesson 3.dtsx** ausführen. Während das Paket ausgeführt wird, werden im Fenster **Protokollereignisse** die Protokollereignisse nach Protokollanbieter aufgelistet, die SSIS in die Protokolldatei schreibt. Wenn die Ausführung des Pakets beendet wird, können Sie die Inhalte der Protokolldatei abrufen.  
  
## <a name="check-the-package-layout"></a>Überprüfen des Paketlayouts  
Bevor Sie das Paket testen, sollten Sie überprüfen, ob Ablaufsteuerung und Datenfluss im Paket aus Lektion 3 den in den folgenden Diagrammen gezeigten Objekte ähneln. Die Ablaufsteuerung sollte dieselbe wie im Paket aus Lektion 2 sein, und der Datenfluss sollte derselbe wie in den Paketen aus Lektion 1 und 2 sein.  
  
**Ablaufsteuerung**  
  
![Ablaufsteuerung im Paket](../integration-services/media/task4lesson2control.gif "Ablaufsteuerung im Paket")  
  
**Datenfluss**  
  
![Datenfluss im Paket](../integration-services/media/task9lesson1data.gif "Datenfluss im Paket")  
  
## <a name="run-the-lesson-3-tutorial-package"></a>Ausführen des Tutorialpakets aus Lektion 3  
  
1.  Klicken Sie im Menü „SSIS“ auf **Protokollereignisse**.  
  
2.  Klicken Sie im Menü **Debuggen** auf **Start Debugging** (Debuggen starten).  
  
3.  Klicken Sie nach dem Ausführen des Pakets im Menü **Debuggen** auf **Stop Debugging** (Debuggen beenden).  
  
## <a name="examine-the-generated-log-file"></a>Überprüfen der generierten Protokolldatei  
  
-   Öffnen Sie mithilfe von Editor oder einem anderen Text-Editor die Datei TutorialLog.log.  
  
-   Eine vollständige Beschreibung der für die Ereignisse **PipelineExecutionPlan** und **PipelineExecutionTrees** erstellten Informationen kann in diesem Tutorial nicht abgedeckt werden.  In der Protokolldatei werden in der ersten Zeile die auf der Registerkarte **Details** des Dialogfelds **SSIS-Protokolle konfigurieren** angegebenen Informationsfelder angezeigt. Darüber hinaus sollten Sie sehen, dass [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] die zwei von Ihnen ausgewählten Ereignisse (**PipelineExecutionPlan** und **PipelineExecutionTrees**) für jede Iteration der Foreach-Schleife protokolliert hat.  
  
## <a name="next-lesson"></a>Nächste Lektion  
[Lektion 4: Hinzufügen der Fehlerflussumleitung mit SSIS](../integration-services/lesson-4-add-error-flow-redirection-with-ssis.md)  
  
  
  
