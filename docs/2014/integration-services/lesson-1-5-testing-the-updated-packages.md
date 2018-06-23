---
title: 'Schritt 5: Testen der aktualisierten Pakete | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- integration-services
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 683e52e5-1c7e-49ab-9ffe-6a450a1c5776
caps.latest.revision: 13
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.openlocfilehash: 7db13e319b07a605172746a650c0292dc7f2bfd8
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/19/2018
ms.locfileid: "36050636"
---
# <a name="step-5-testing-the-updated-packages"></a>Schritt 5: Testen der aktualisierten Pakete
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
 [Lektion 2: Erstellen des Bereitstellungspakets](../integration-services/lesson-2-create-the-deployment-bundle-in-ssis.md)  
  
![Integration Services (kleines Symbol)](media/dts-16.gif "Integration Services (kleines Symbol)")**bleiben Sie mit Integration Services** <br /> Die neuesten Downloads, Artikel, Beispiele und Videos von Microsoft sowie ausgewählte Lösungen aus der Community finden Sie auf MSDN auf der [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] -Seite:<br /><br /> [Besuchen Sie die Integration Services-Seite auf MSDN](http://go.microsoft.com/fwlink/?LinkId=136655)<br /><br /> Abonnieren Sie die auf der Seite verfügbaren RSS-Feeds, um automatische Benachrichtigungen zu diesen Updates zu erhalten.  
  
  