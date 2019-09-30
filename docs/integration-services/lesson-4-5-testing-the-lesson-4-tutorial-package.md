---
title: 'Schritt 5: Testen des Tutorialpakets aus Lektion 4 | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 01/07/2019
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.technology: integration-services
ms.topic: tutorial
ms.assetid: 5f18df92-0248-4858-836b-c8b02f0e0439
author: chugugrace
ms.author: chugu
ms.openlocfilehash: ba5766483def3dc357bc8f1bf65dd1048fa94b48
ms.sourcegitcommit: e8af8cfc0bb51f62a4f0fa794c784f1aed006c71
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 09/26/2019
ms.locfileid: "71295919"
---
# <a name="lesson-4-5-test-the-lesson-4-package"></a>Lektion 4.5: Testen des Tutorialpakets aus Lektion 4

[!INCLUDE[ssis-appliesto](../includes/ssis-appliesto-ssvrpluslinux-asdb-asdw-xxx.md)]



Die beschädigte Datei **Currency_BAD.txt** kann in der Transformation „Currency Key Lookup“ keine Übereinstimmung generieren. Da die Fehlerausgabe der Transformation „Currency Key Lookup“ so konfiguriert wurde, dass fehlerhafte Zeilen zum neuen Ziel für fehlerhafte Dateien umgeleitet werden, erzeugt die Komponente keinen Fehler, und das Paket wird erfolgreich ausgeführt. [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] schreibt alle fehlgeschlagenen Zeilen in die Datei **ErrorOutput.txt**.  
  
In dieser Aufgabe testen Sie die überarbeitete Fehlerausgabekonfiguration, indem Sie das Paket ausführen. Bei einer erfolgreichen Paketausführung zeigen Sie dann den Inhalt der Datei **ErrorOutput.txt** an.  
  
> [!NOTE]  
> Wenn Sie keine Fehlerzeilen in der Datei **ErrorOutput.txt** anhäufen möchten, sollten Sie den Dateiinhalt zwischen Paketausführungen manuell löschen.  
  
## <a name="check-the-package-layout"></a>Überprüfen des Paketlayouts  
Bevor Sie das Paket testen, sollten Sie überprüfen, ob Ablaufsteuerung und Datenfluss im Paket aus Lektion 4 denen in den folgenden Diagrammen gezeigten Objekten ähneln: 
  
**Ablaufsteuerung**  
  
![Ablaufsteuerung im Paket](../integration-services/media/task4lesson2control.gif "Ablaufsteuerung im Paket")  
  
**Datenfluss**  
  
![Datenfluss im Paket](../integration-services/media/task5lesson5data.gif "Datenfluss im Paket")  
  
## <a name="run-the-lesson-4-tutorial-package"></a>Ausführen des Tutorialpakets aus Lektion 4  
  
1.  Klicken Sie im Menü **Debuggen** auf **Start Debugging** (Debuggen starten).  
  
2.  Klicken Sie nach dem Ausführen des Pakets im Menü **Debuggen** auf **Stop Debugging** (Debuggen beenden).  
  
## <a name="view-the-contents-of-the-erroroutputtxt-file"></a>Anzeigen des Inhalts der Datei „ErrorOutput.txt“  
  
Öffnen Sie in Editor oder einem anderen Text-Editor die Datei **ErrorOutput.txt**. Die standardmäßige Spaltenreihenfolge ist: AverageRate, CurrencyID, CurrencyDate, EndOfDateRate, ErrorCode, ErrorColumn, ErrorDescription.  
 
Beachten Sie, dass alle in der Datei enthaltenen Zeilen den nicht übereinstimmenden CurrencyID-Wert BAD, den ErrorCode-Wert –1071607778, den ErrorColumn-Wert 0 und den ErrorDescription-Wert "Row yielded no match during lookup" (Es wurde für die Zeile bei der Suche keine Übereinstimmung gefunden.) enthalten. Der ErrorColumn-Wert ist 0, weil der Fehler nicht spaltenspezifisch ist, sondern vielmehr der Suchvorgang fehlgeschlagen ist.
  
  
## <a name="next-lesson"></a>Nächste Lektion
[Lesson 5: Add SSIS Package Configurations for the Package Deployment Model (Lektion 5: Hinzufügen von SSIS-Paketkonfigurationen für das Paketbereitstellungsmodell)](../integration-services/lesson-5-add-ssis-package-configurations-for-the-package-deployment-model.md)  
