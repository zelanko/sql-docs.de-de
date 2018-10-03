---
title: 'Aufgabe 16: Überprüfung mit Master Data Manager | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- data-quality-services
- integration-services
- master-data-services
ms.topic: conceptual
ms.assetid: 57ad9d3e-8f95-4df6-af01-c291ccf49164
author: douglaslms
ms.author: douglasl
manager: craigg
ms.openlocfilehash: b0f8c608384e3840f0c154233e90a79d4319bbad
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/02/2018
ms.locfileid: "48203190"
---
# <a name="task-16-verifying-with-master-data-manager"></a>Aufgabe 16: Überprüfung mit Master Data Manager
  In dieser Aufgabe prüfen Sie den Status des vom SSIS-Paket gesendeten Batchauftrags und verifizieren, ob die Daten mit Master Data Manager auf den MDS-Server hochgeladen wurden.  
  
1.  Starten Sie **Master Data Manager** ([http://localhost/MDS](http://localhost/MDS)). Wenn sie bereits geöffnet ist, klicken Sie auf **Microsoft SQL Server Master Data Services** oben, um zum Wechseln der **auf der Startseite**.  
  
2.  Klicken Sie auf **Integrationsmanagement**.  
  
3.  Beachten Sie, dass es ein Batch mit mit dem Namen **EIMBatch** , den Sie in der Liste gesendet. Klicken Sie auf **Importdaten** in der Menüleiste, wenn den folgenden Bildschirm nicht angezeigt wird.  
  
     ![EIM-Batch](../../2014/tutorials/media/et-verifyingwithmasterdatamanager.jpg "EIM-Batch")  
  
4.  Wechseln Sie zurück zur Startseite, indem auf **SQL Server 2012 Master Data Services** oben.  
  
5.  Stellen Sie sicher, dass **Lieferanten** Modell ausgewählt ist **Modell** und **VERSION_1** ausgewählt ist **Version**, und klicken Sie auf  **Explorer**.  
  
6.  Sie können das in MDS importierte Daten-SSIS-Paket anzeigen. Die Daten sollten bereinigt werden und haben keine Duplikate **Code** Werte (Hinweis: **SupplierID** Spalte in Excel entspricht **Code** -Attribut der lieferantenentität in MDS).  
  
## <a name="next-step"></a>Nächster Schritt  
 [Aufgabe 17: Überprüfung des DQS-Bereinigungsprojekts, das vom SSIS-Paket erstellt wurde](../../2014/tutorials/task-17-reviewing-dqs-cleansing-project-created-by-the-ssis-package.md)  
  
  
