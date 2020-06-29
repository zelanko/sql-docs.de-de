---
title: 'Schritt 5: Testen des Tutorialpakets aus Lektion 4 | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: 5f18df92-0248-4858-836b-c8b02f0e0439
author: chugugrace
ms.author: chugu
ms.openlocfilehash: a033fd1bc3384fa5a246c61d3176e3fadccf5500
ms.sourcegitcommit: 34278310b3e005d008cd2106a7b86fc6e736f661
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/26/2020
ms.locfileid: "85440407"
---
# <a name="step-5-testing-the-lesson-4-tutorial-package"></a>Schritt 5: Testen des Tutorialpakets aus Lektion 4
  Die beschädigte Datei Currency_BAD.txt kann in der Currency Key-Transformation keine Übereinstimmung generieren. Weil die Fehlerausgabe von Currency Key Lookup jetzt so konfiguriert wurde, dass fehlerhafte Zeilen zum neuen Ziel für fehlerhafte Dateien umgeleitet werden, erzeugt die Komponente keinen Fehler, und das Paket wird erfolgreich ausgeführt. Alle fehlgeschlagenen Zeilen werden in die Datei ErrorOutput.txt geschrieben.  
  
 In dieser Aufgabe testen Sie die überarbeitete Fehlerausgabekonfiguration, indem Sie das Paket ausführen. Bei einer erfolgreichen Paketausführung zeigen Sie dann den Inhalt der Datei ErrorOutput.txt an.  
  
> [!NOTE]  
>  Wenn Sie keine Fehlerzeilen in der Datei ErrorOutput.txt anhäufen möchten, sollten Sie den Dateiinhalt zwischen Paketausführungen manuell löschen.  
  
## <a name="checking-the-package-layout"></a>Überprüfen des Paketlayouts  
 Bevor Sie das Paket testen, sollten Sie überprüfen, ob Ablaufsteuerung und Datenfluss im Paket aus Lektion 4 die in den folgenden Diagrammen gezeigten Objekte enthalten. Die Ablaufsteuerung sollte mit der Ablaufsteuerung in den Lektionen 2 bis 4 übereinstimmen.  
  
 **Ablauf Steuerung**  
  
 ![Ablaufsteuerung im Paket](../../2014/tutorials/media/task4lesson2control.gif "Ablaufsteuerung im Paket")  
  
 **Datenfluss**  
  
 ![Datenfluss im Paket](../../2014/tutorials/media/task5lesson5data.gif "Datenfluss im Paket")  
  
### <a name="to-run-the-lesson-4-tutorial-package"></a>So führen Sie das Lernprogrammpaket aus Lektion 4 aus  
  
1.  Klicken Sie im Menü **Debuggen** auf **Debuggen starten**.  
  
2.  Klicken Sie nach Ausführen des Pakets im Menü **Debuggen** auf **Debuggen beenden**.  
  
### <a name="to-verify-the-contents-of-the-erroroutputtxt-file"></a>So überprüfen Sie den Inhalt der Datei ErrorOutput.txt  
  
-   Öffnen Sie in Editor oder einem anderen Texteditor die Datei ErrorOutput.txt. Die standardmäßige Spaltenreihenfolge ist: AverageRate, CurrencyID, CurrencyDate, EndOfDateRate, ErrorCode, ErrorColumn und ErrorDescription.  
  
     Beachten Sie, dass alle in der Datei enthaltenen Zeilen den nicht übereinstimmenden CurrencyID-Wert BAD, den ErrorCode-Wert -1071607778, den ErrorColumn-Wert 0 und den ErrorDescription-Wert "Die Zeile ergab bei der Suche keine Übereinstimmung" enthalten. Der Wert für ErrorColumn ist auf 0 festgelegt, da der Fehler nicht spaltenspezifisch ist. Es ist der Suchvorgang, der fehlerhaft ist. .  
  
  
