---
description: 'Lektion 2.4: Testen des Tutorialpakets aus Lektion 2'
title: 'Schritt 4: Testen des Tutorialpakets aus Lektion 2 | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 01/03/2019
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.technology: integration-services
ms.topic: tutorial
ms.assetid: 0e8c0a25-8f79-41df-8ed2-f82a74b129cd
author: chugugrace
ms.author: chugu
ms.openlocfilehash: d431f2c14b42d5dbaa1dfdc7d987560eab58d4c5
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 08/17/2020
ms.locfileid: "88413566"
---
# <a name="lesson-2-4-test-the-lesson-2-tutorial-package"></a>Lektion 2.4: Testen des Tutorialpakets aus Lektion 2

[!INCLUDE[sqlserver-ssis](../includes/applies-to-version/sqlserver-ssis.md)]



Mit dem jetzt konfigurierten Foreach-Schleifencontainer und Verbindungs-Manager für Flatfiles kann das Paket aus Lektion 2 nun die Sammlung von 14 Flatfiles im Ordner „Sample Data“ (Beispieldaten) durchlaufen. Jedes Mal, wenn ein Dateiname gefunden wird, der mit den angegebenen Dateinamenskriterien übereinstimmt, wird die benutzerdefinierte Variable vom Foreach-Schleifencontainer mit dem Dateinamen aufgefüllt. Diese Variable aktualisiert im Gegenzug die Eigenschaft „ConnectionString“ des Verbindungs-Managers für Flatfiles und stellt eine Verbindung mit der neuen Flatfile her. Vom Foreach-Schleifencontainer wird dann der unveränderte Datenflusstask gegen die Daten in der neuen Flatfile ausgeführt, bevor eine Verbindung zur nächsten Datei im Ordner hergestellt wird.  
  
> [!NOTE]  
> Wenn Sie das Paket aus Lektion 1 ausgeführt haben, müssen Sie die Datensätze aus der „dbo.NewFactCurrencyRate“-Tabelle in der „AdventureWorksDW2012“-Datenbank löschen, bevor Sie das Paket für diese Lektion ausführen. Das Paket aus Lektion 2 versucht, Datensätze einzufügen, die bereits in das Paket aus Lektion 1 eingefügt wurden. Dadurch wird ein Fehler ausgelöst.  
  
## <a name="check-the-package-layout"></a>Überprüfen des Paketlayouts  
Bevor Sie das Paket testen, überprüfen Sie, ob Ablaufsteuerung und Datenfluss im Paket aus Lektion 2 die in den folgenden Diagrammen gezeigten Objekte enthalten. Der Datenfluss des Pakets aus Lektion 2 entspricht dem Datenfluss des Pakets aus Lektion 1.  
  
**Ablaufsteuerung**  
  
![Ablaufsteuerung im Paket](../integration-services/media/task4lesson2control.gif "Ablaufsteuerung im Paket")  
  
**Datenfluss**  
  
![Datenfluss im Paket](../integration-services/media/task9lesson1data.gif "Datenfluss im Paket")  
  
## <a name="test-the-lesson-2-tutorial-package"></a>Testen des Tutorialpakets aus Lektion 2  
  
1.  Klicken Sie im **Projektmappen-Explorer** erst mit der rechten Maustaste auf **Lesson 2.dtsx**, und klicken Sie anschließend auf **Paket ausführen**.  
  
    Dann wird das Paket ausgeführt. Sie können den Status jeder Schleife im Fenster **Ausgabe** überprüfen oder dafür auf die Registerkarte **Status** klicken. So können Sie beispielsweise sehen, dass 1.097 Zeilen zur Zieltabelle aus der Datei „Currency_VEB.txt“ hinzugefügt wurden.  
  
2.  Klicken Sie nach dem Ausführen des Pakets im Menü **Debuggen** auf **Stop Debugging** (Debuggen beenden).  
  
## <a name="go-to-next-lesson"></a>Weiter zur nächsten Lektion  
[Lektion 3: Hinzufügen der Protokollierung mit SSIS](../integration-services/lesson-3-add-logging-with-ssis.md)  
  
## <a name="see-also"></a>Siehe auch  
[Ausführen von Projekten und Paketen](../integration-services/packages/deploy-integration-services-ssis-projects-and-packages.md)  
  
  
  

