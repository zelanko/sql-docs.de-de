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
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: 40884a52395aee9bb45338f5c56d2709f3d4d956
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "65722962"
---
# <a name="lesson-1-5---testing-the-updated-packages"></a>Lektion 1-5: Testen der aktualisierten Pakete

[!INCLUDE[ssis-appliesto](../includes/ssis-appliesto-ssvrpluslinux-asdb-asdw-xxx.md)]


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
[Lektion 2: Erstellen des Bereitstellungspakets in SSIS](../integration-services/lesson-2-create-the-deployment-bundle-in-ssis.md)  
  
  
  
