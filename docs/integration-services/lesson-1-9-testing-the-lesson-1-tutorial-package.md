---
description: 'Schritt 9: Testen des Tutorialpakets aus Lektion 1'
title: 'Schritt 9: Testen des Tutorialpakets aus Lektion 1 | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 01/03/2019
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.technology: integration-services
ms.topic: tutorial
ms.assetid: 9aee7acf-797b-46f2-830d-80ab64a9f0b6
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 758f5e0c312afc2a8310743f917cc00a1c43462c
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 08/17/2020
ms.locfileid: "88462012"
---
# <a name="lesson-1-9-test-the-lesson-1-package"></a>Lektion 1.9: Testen des Tutorialpakets aus Lektion 1

[!INCLUDE[sqlserver-ssis](../includes/applies-to-version/sqlserver-ssis.md)]



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
  
1.  Wählen Sie im Menü **Debuggen** die Option **Debuggen starten** aus.  
  
    Dann wird das Paket ausgeführt, wobei 1.097 Zeilen erfolgreich zur **NewFactCurrencyRate**-Faktentabelle in **AdventureWorksDW2012** hinzugefügt werden. Klicken Sie auf die Registerkarte **Datenfluss**, um dieses Ergebnis zu überprüfen.
  
2.  Klicken Sie nach dem Ausführen des Pakets im Menü **Debuggen** auf **Stop Debugging** (Debuggen beenden).  
  
## <a name="go-to-next-lesson"></a>Weiter zur nächsten Lektion
[Lektion 2: Hinzufügen von Schleifen mit SSIS](../integration-services/lesson-2-adding-looping-with-ssis.md)  
  
## <a name="see-also"></a>Weitere Informationen  
[Ausführen von Projekten und Paketen](packages/run-integration-services-ssis-packages.md) 
  
  
  
