---
title: 'Schritt 4: Testen des Lektion 2-Tutorialpakets | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: 0e8c0a25-8f79-41df-8ed2-f82a74b129cd
author: janinezhang
ms.author: janinez
ms.openlocfilehash: b4483facba1a1233dda7f3330f432ef8d3f9c2b5
ms.sourcegitcommit: f71e523da72019de81a8bd5a0394a62f7f76ea20
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/17/2020
ms.locfileid: "84968227"
---
# <a name="step-4-testing-the-lesson-2-tutorial-package"></a>Schritt 4: Testen des Tutorialpakets aus Lektion 2
  Mit dem jetzt konfigurierten Foreach-Schleifencontainer und Verbindungs-Manager für Flatfiles kann das Paket aus Lektion 2 nun die Sammlung von 14 Flatfiles im Sample Data-Ordner durchlaufen. Jedes Mal, wenn ein Dateiname gefunden wird, der mit den angegebenen Dateinamenskriterien übereinstimmt, wird die benutzerdefinierte Variable vom Foreach-Schleifencontainer mit dem Dateinamen aufgefüllt. Von dieser Variablen wird im Gegenzug die Eigenschaft ConnectionString des Verbindungs-Managers für Flatfiles aktualisiert, und es wird eine Verbindung mit der neuen Flatfile hergestellt. Vom Foreach-Schleifencontainer wird dann der unveränderte Datenflusstask gegen die Daten in der neuen Flatfile ausgeführt, bevor eine Verbindung zur nächsten Datei im Ordner hergestellt wird.  
  
 Verwenden Sie die folgende Prozedur, um die neue Schleifenfunktionalität zu testen, die Sie zu Ihrem Paket hinzugefügt haben.  
  
> [!NOTE]  
>  Wenn Sie das Paket aus Lektion 1 ausgeführt haben, müssen Sie die Datensätze aus dbo.FactCurrency in AdventureWorksDW2012 löschen, bevor Sie das Paket von dieser Lektion aus ausführen. Andernfalls wird für das Paket eine Verletzung der PRIMARY KEY-Einschränkung angezeigt. Die gleichen Fehler werden angezeigt, wenn Sie das Paket durch Auswahl von Debuggen bzw. Debuggen starten (oder Drücken von F5) ausführen. Das liegt daran, dass sowohl Lektion 1 als auch Lektion 2 ausgeführt wird. In Lektion 2 wird versucht, die Datensätze einzufügen, die bereits in Lektion 1 eingefügt wurden.  
  
## <a name="checking-the-package-layout"></a>Überprüfen des Paketlayouts  
 Bevor Sie das Paket testen, sollten Sie überprüfen, ob Ablaufsteuerung und Datenfluss im Paket aus Lektion 2 die in den folgenden Diagrammen gezeigten Objekte enthalten. Der Datenfluss sollte mit dem Datenfluss in Lektion 1 übereinstimmen.  
  
 **Ablauf Steuerung**  
  
 ![Ablaufsteuerung im Paket](../../2014/tutorials/media/task4lesson2control.gif "Ablaufsteuerung im Paket")  
  
 **Datenfluss**  
  
 ![Datenfluss im Paket](../../2014/tutorials/media/task9lesson1data.gif "Datenfluss im Paket")  
  
### <a name="to-test-the-lesson-2-tutorial-package"></a>So testen Sie das Lektion 2-Lernprogrammpaket  
  
1.  Klicken Sie im **Projektmappen-Explorer**mit der rechten Maustaste auf **Lesson 2.dtsx** , und klicken Sie auf **Paket ausführen**.  
  
     Das Paket wird ausgeführt. Sie können den Status jeder Schleife im Ausgabefenster überprüfen, oder indem Sie **auf die Register** Karte Status klicken. Beispielsweise können Sie sehen, dass der Ziel Tabelle 1097 Zeilen aus dem Datei Currency_VEB.txt hinzugefügt wurden.  
  
2.  Klicken Sie nach Ausführen des Pakets im Menü **Debuggen** auf **Debuggen beenden**.  
  
## <a name="next-lesson"></a>Nächste Lektion  
 [Lektion 5: Hinzufügen von Paketkonfigurationen für das Paketbereitstellungsmodell](../integration-services/lesson-5-add-ssis-package-configurations-for-the-package-deployment-model.md)  
  
## <a name="see-also"></a>Weitere Informationen  
 [Ausführung von Projekten und Paketen](packages/run-integration-services-ssis-packages.md)  
  
  
