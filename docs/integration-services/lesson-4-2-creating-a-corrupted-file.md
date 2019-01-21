---
title: 'Schritt 2: Erstellen einer beschädigten Datei | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 01/07/2019
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.technology: integration-services
ms.topic: tutorial
ms.assetid: cd0b18dc-66c3-4d88-86ef-8e40cb660fae
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: d81ac7d0a5c7a42a2292bab7ca5beffa464d02d7
ms.sourcegitcommit: e2fa721b6f46c18f1825dd1b0d56c0a6da1b2be1
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/11/2019
ms.locfileid: "54211011"
---
# <a name="lesson-4-2-create-a-corrupted-file"></a>Lektion 4.2: Erstellen einer beschädigten Datei

Sie müssen eine Beispielflatfile erstellen, die beim Verarbeiten für eine Komponente einen Fehler erzeugt, um die Konfiguration und die Behandlung von Transformationsfehlern zu demonstrieren.  
  
In dieser Aufgabe erstellen Sie eine Kopie einer vorhandenen Beispielflatfile. Anschließend öffnen Sie die Datei in Editor und bearbeiten die Spalte **CurrencyID** so, dass sie einen fehlerhaften Wert enthält, durch den der Suchvorgang fehlschlägt. Wenn die beschädigte Datei verarbeitet wird, erzeugt die fehlgeschlagene Suche einen Fehler der „Currency Key Lookup“-Transformation, sodass auch für den Rest des Pakets ein Fehler ausgelöst wird. Nach dem Erstellen der beschädigten Beispieldatei führen Sie das Paket aus, um den vom Paket verursachten Fehler anzuzeigen.  
  
## <a name="create-a-corrupted-sample-flat-file"></a>Erstellen einer beschädigten Beispielflatfile  
  
1.  Öffnen Sie in Editor oder einem anderen Text-Editor die Datei **Currency_VEB.txt**.  
  
2.  Suchen Sie mithilfe der Funktion des Texteditors zum Suchen und Ersetzen alle Instanzen von **VEB** und ersetzen Sie sie durch **BAD**.  
  
3.  Speichern Sie im gleichen Ordner wie die anderen Beispieldatendateien die geänderte Datei als **Currency_BAD.txt**.  
  
    > [!NOTE]  
    > Vergewissern Sie sich, dass Sie **Currency_BAD.txt** im selben Ordner wie die anderen Beispieldatendateien speichern.  
  
4.  Schließen Sie den Texteditor.  
  
## <a name="verify-that-an-error-occurs-during-run-time"></a>Überprüfen, ob während der Laufzeit ein Fehler auftritt  
  
1.  Klicken Sie im Menü **Debuggen** auf **Start Debugging** (Debuggen starten).  
  
    In der dritten Iteration des Datenflusses versucht die „Lookup Currency Key“-Transformation, die Datei **Currency_BAD.txt** zu verarbeiten, und die Transformation löst einen Fehler aus. Der Fehler der Transformation löst wiederum einen Fehler des gesamten Pakets aus.  
  
2.  Klicken Sie im Menü **Debuggen** auf **Stop Debugging** (Debuggen beenden).  
  
3.  Klicken Sie auf der Entwurfsoberfläche auf die Registerkarte **Ausführungsergebnisse**.  
  
4.  Durchsuchen Sie das Protokoll und überprüfen Sie, ob der folgende nicht behandelte Fehler aufgetreten ist:  
  
    ```
    [Lookup Currency Key[27]] Error: Row yielded no match during lookup.
    ```
  
    > [!NOTE]  
    > Die Zahl 27 ist die ID der Komponente. Dieser Wert wird zugewiesen, wenn Sie den Datenfluss erstellen. Der Wert in Ihrem Paket kann sich von diesem Wert unterscheiden.  
  
## <a name="go-to-next-task"></a>Weiter zur nächsten Aufgabe  
[Schritt 3: Hinzufügen der Fehlerflussumleitung](../integration-services/lesson-4-3-adding-error-flow-redirection.md)  
  
  
  
