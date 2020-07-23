---
title: 'Schritt 5: Testen der aktualisierten Pakete | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.technology: integration-services
ms.topic: tutorial
ms.assetid: 683e52e5-1c7e-49ab-9ffe-6a450a1c5776
author: chugugrace
ms.author: chugu
ms.openlocfilehash: b00453b2bd6bf49db66f93e6c536d4f75033d35e
ms.sourcegitcommit: c8e1553ff3fdf295e8dc6ce30d1c454d6fde8088
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/22/2020
ms.locfileid: "86917351"
---
# <a name="lesson-1-5---testing-the-updated-packages"></a>Lektion 1-5: Testen der aktualisierten Pakete

[!INCLUDE[sqlserver-ssis](../includes/applies-to-version/sqlserver-ssis.md)]


Bevor Sie mit der nächsten Lektion fortfahren, in der Sie das Bereitstellungspaket erstellen, das bei der Installation der Lernprogrammpakete auf dem Zielcomputer verwendet werden soll, sollten Sie die Pakete testen. In dieser Aufgabe führen Sie die Pakete DataTransfer.dtsx und LoadXMLData aus, die Sie dem Deployment Tutorial-Projekt hinzugefügt und dann mit Konfigurationen erweitert haben.  
  
Bei der Ausführung der Pakete wird jede ausführbare Datei im Paket, die erfolgreich abgeschlossen wurde, in Grün angezeigt. Werden alle ausführbaren Dateien in Grün angezeigt, wurde das Paket erfolgreich abgeschlossen. Sie können den Status der Paketausführung auch auf der Registerkarte **Status** verfolgen.  
  
Werden die Pakete nicht erfolgreich ausgeführt, müssen Sie das Problem beheben, bevor Sie mit der nächsten Lektion fortfahren.  
  
### <a name="to-run-the-datatransfer-package"></a>So führen Sie das DataTransfer-Paket aus  
  
1.  Klicken Sie im Projektmappen-Explorer auf DataTransfer.dtsx.  
  
2.  Klicken Sie im Menü **Debuggen** auf **Debuggen starten**.  
  
3.  Klicken Sie nach Ausführen des Pakets im Menü **Debuggen** auf **Debuggen beenden**.  
  
### <a name="to-run-the-loadxmldata-package"></a>So führen Sie das LoadXMLData-Paket aus  
  
1.  Klicken Sie im Projektmappen-Explorer auf LoadXMLData.dtsx.  
  
2.  Klicken Sie im Menü **Debuggen** auf **Debuggen starten**.  
  
3.  Klicken Sie nach Ausführen des Pakets im Menü **Debuggen** auf **Debuggen beenden**.  
  
## <a name="next-lesson"></a>Nächste Lektion  
[Lesson 2: Create the Deployment Bundle in SSIS](../integration-services/lesson-2-create-the-deployment-bundle-in-ssis.md)  
  
  
  
