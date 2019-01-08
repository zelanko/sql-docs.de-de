---
title: 'Schritt 9: Testen des Lektion 1-Tutorialpakets | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: 9aee7acf-797b-46f2-830d-80ab64a9f0b6
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 069f9ca26aa59c8edb8b97f1acbdf336a61b7d9b
ms.sourcegitcommit: ceb7e1b9e29e02bb0c6ca400a36e0fa9cf010fca
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/03/2018
ms.locfileid: "52793982"
---
# <a name="step-9-testing-the-lesson-1-tutorial-package"></a>Schritt 9: Testen des Lektion 1-Lernprogrammpakets
  In dieser Lektion haben Sie die folgenden Aufgaben ausgeführt:  
  
-   Ein neues [!INCLUDE[ssIS](../includes/ssis-md.md)] -Projekt erstellt.  
  
-   Die Verbindungs-Manager konfiguriert, die vom Paket zum Herstellen einer Verbindung mit den Quell- und Zieldaten benötigt werden.  
  
-   Einen Datenfluss hinzugefügt, der Daten aus einer Flatfilequelle abruft, die notwendigen Transformationen zum Suchen in den Daten ausführt und die Daten für das Ziel konfiguriert.  
  
 Ihr Paket ist jetzt vollständig. Testen Sie jetzt Ihr Paket.  
  
## <a name="checking-the-package-layout"></a>Überprüfen des Paketlayouts  
 Bevor Sie das Paket testen, sollten Sie überprüfen, ob Ablaufsteuerung und Datenfluss im Paket aus Lektion 1 die in den folgenden Diagrammen gezeigten Objekte enthalten.  
  
 **Ablaufsteuerung**  
  
 ![Ablaufsteuerung im Paket](../../2014/tutorials/media/task9lesson1control.gif "Ablaufsteuerung im Paket")  
  
 **Datenfluss**  
  
 ![Datenfluss im Paket](../../2014/tutorials/media/task9lesson1data.gif "Datenfluss im Paket")  
  
### <a name="to-run-the-lesson-1-tutorial-package"></a>So führen Sie das Lernprogrammpaket aus Lektion 1 aus  
  
1.  Klicken Sie im Menü **Debuggen** auf **Debuggen starten**.  
  
     Das Paket wird ausgeführt, wobei der **FactCurrency** -Faktentabelle in **AdventureWorksDW2012**1.097 Zeilen erfolgreich hinzugefügt werden.  
  
2.  Klicken Sie nach Ausführen des Pakets im Menü **Debuggen** auf **Debuggen beenden**.  
  
## <a name="next-lesson"></a>Nächste Lektion  
 [Lektion 2: Hinzufügen von Schleifen](../integration-services/lesson-2-adding-looping-with-ssis.md)  
  
## <a name="see-also"></a>Siehe auch  
 [Ausführung von Projekten und Paketen](packages/run-integration-services-ssis-packages.md)  
  
  
