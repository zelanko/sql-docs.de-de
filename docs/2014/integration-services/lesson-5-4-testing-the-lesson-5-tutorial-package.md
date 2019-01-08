---
title: 'Schritt 4: Testen des Lektion 5-Tutorialpakets | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: 5215b77d-c2ec-4b25-a3de-ca49ea197d74
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 29154120646f74da7471f44a1630b3d99afefa4f
ms.sourcegitcommit: ceb7e1b9e29e02bb0c6ca400a36e0fa9cf010fca
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/03/2018
ms.locfileid: "52747482"
---
# <a name="step-4-testing-the-lesson-5-tutorial-package"></a>Schritt 4: Testen des Lektion 5-Lernprogrammpakets
  Zur Laufzeit erhält Ihr Paket den Wert für die `Directory`-Eigenschaft von einer zur Laufzeit aktualisierten Variable. Es wird also nicht der ursprüngliche Verzeichnisname verwendet, den Sie beim Erstellen des Pakets angegeben haben. Der Wert der Variablen wird durch die Datei SSISTutorial.dtsConfig aufgefüllt.  
  
 Um zu überprüfen, ob vom Paket die Directory-Eigenschaft während der Laufzeit auf den neuen Wert aktualisiert wird, führen Sie das Paket einfach aus. Weil nur drei Beispieldatendateien in das neue Verzeichnis kopiert werden, wird der Datenfluss nur drei Mal ausgeführt, statt durch 14 Dateien im ursprünglichen Ordner zu iterieren.  
  
## <a name="checking-the-package-layout"></a>Überprüfen des Paketlayouts  
 Bevor Sie das Paket testen, sollten Sie überprüfen, ob Ablaufsteuerung und Datenfluss im Paket aus Lektion 5 die in den folgenden Diagrammen gezeigten Objekte enthalten. Die Ablaufsteuerung sollte mit der Ablaufsteuerung in Lektion 4 übereinstimmen. Der Datenfluss sollte mit dem Datenfluss in Lektion 4 übereinstimmen.  
  
 **Ablaufsteuerung**  
  
 ![Ablaufsteuerung im Paket](../../2014/tutorials/media/task4lesson2control.gif "Ablaufsteuerung im Paket")  
  
 **Datenfluss**  
  
 ![Datenfluss im Paket](../../2014/tutorials/media/task9lesson1data.gif "Datenfluss im Paket")  
  
### <a name="to-test-the-lesson-5-tutorial-package"></a>So testen Sie das Lernprogrammpaket aus Lektion 5  
  
1.  Klicken Sie im Menü **Debuggen** auf **Debuggen starten**.  
  
2.  Klicken Sie nach dem Ausführen des Pakets im Menü **Debuggen** auf **Debuggen beenden**.  
  
## <a name="next-lesson"></a>Nächste Lektion  
 [Lektion 6: Verwenden von Parametern mit dem Projektbereitstellungsmodell](../integration-services/lesson-6-using-parameters-with-the-project-deployment-model-in-ssis.md)  
  
  
