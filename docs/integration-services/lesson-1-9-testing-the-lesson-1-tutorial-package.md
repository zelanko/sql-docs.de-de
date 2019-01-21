---
title: 'Schritt 9: Testen des Tutorialpakets aus Lektion 1 | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 01/03/2019
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.technology: integration-services
ms.topic: tutorial
ms.assetid: 9aee7acf-797b-46f2-830d-80ab64a9f0b6
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: dde0ffe53ab5763230cafa752d687ab42d3a60c5
ms.sourcegitcommit: dd794633466b1da8ead9889f5e633bdf4b3389cd
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/09/2019
ms.locfileid: "54143220"
---
# <a name="lesson-1-9-test-the-lesson-1-package"></a>Lektion 1.9: Testen des Tutorialpakets aus Lektion 1

In diesem Tutorial haben Sie die folgenden Aufgaben ausgeführt:  
  
-   Ein neues [!INCLUDE[ssIS](../includes/ssis-md.md)] -Projekt erstellt.  
  
-   Sie haben die Verbindungs-Manager-Instanzen konfiguriert, die vom Paket zum Herstellen einer Verbindung mit den Quell- und Zieldaten benötigt werden.  
  
-   Einen Datenfluss hinzugefügt, der Daten aus einer Flatfilequelle abruft, die notwendigen Transformationen zum Suchen in den Daten ausführt und die Daten für das Ziel konfiguriert.  
  
Ihr Paket ist jetzt vollständig und kann getestet werden.
  
## <a name="check-the-package-components"></a>Überprüfen der Paketkomponenten
  
Bevor Sie das Paket testen, überprüfen Sie, ob Ablaufsteuerung und Datenfluss im Paket aus Lektion 1 die in den folgenden Diagrammen gezeigten Objekte enthalten.  
  
**Ablaufsteuerung** 
  
![Ablaufsteuerung im Paket](../integration-services/media/task9lesson1control.gif "Ablaufsteuerung im Paket")  
  
**Datenfluss**  
  
![Datenfluss im Paket](../integration-services/media/task9lesson1data.gif "Datenfluss im Paket")  
  
## <a name="run-the-lesson-1-package"></a>Ausführen des Pakets aus Lektion 1  
  
1.  Klicken Sie im Menü **Debuggen** auf **Start Debugging** (Debuggen starten).  
  
    Dann wird das Paket ausgeführt, wobei 1.097 Zeilen erfolgreich zur **NewFactCurrencyRate**-Faktentabelle in **AdventureWorksDW2012** hinzugefügt werden. Klicken Sie auf die Registerkarte **Datenfluss**, um dieses Ergebnis zu überprüfen.
  
2.  Klicken Sie nach dem Ausführen des Pakets im Menü **Debuggen** auf **Stop Debugging** (Debuggen beenden).  
  
## <a name="go-to-next-lesson"></a>Weiter zur nächsten Lektion
[Lektion 2: Hinzufügen von Schleifen mit SSIS](../integration-services/lesson-2-adding-looping-with-ssis.md)  
  
## <a name="see-also"></a>Siehe auch  
[Ausführen von Projekten und Paketen](packages/run-integration-services-ssis-packages.md) 
  
  
  
