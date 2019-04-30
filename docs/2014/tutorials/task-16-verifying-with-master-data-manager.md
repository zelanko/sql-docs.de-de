---
title: 'Aufgabe 16: Überprüfung mit Master Data Manager | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: data-quality-services
ms.topic: conceptual
ms.assetid: 57ad9d3e-8f95-4df6-af01-c291ccf49164
author: leolimsft
ms.author: lle
manager: craigg
ms.openlocfilehash: 3b9e24e062695c3b8b4c1aacd37b464fafd99558
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "63222547"
---
# <a name="task-16-verifying-with-master-data-manager"></a>Aufgabe 16: Überprüfung mit dem Master Data Manager
  In dieser Aufgabe prüfen Sie den Status des vom SSIS-Paket gesendeten Batchauftrags und verifizieren, ob die Daten mit Master Data Manager auf den MDS-Server hochgeladen wurden.  
  
1.  Starten Sie **Master Data Manager** ([http://localhost/MDS](http://localhost/MDS)). Wenn sie bereits geöffnet ist, klicken Sie auf **Microsoft SQL Server Master Data Services** oben, um zum Wechseln der **auf der Startseite**.  
  
2.  Klicken Sie auf **Integrationsmanagement**.  
  
3.  Beachten Sie, dass es ein Batch mit mit dem Namen **EIMBatch** , den Sie in der Liste gesendet. Klicken Sie auf **Importdaten** in der Menüleiste, wenn den folgenden Bildschirm nicht angezeigt wird.  
  
     ![EIM-Batch](../../2014/tutorials/media/et-verifyingwithmasterdatamanager.jpg "EIM-Batch")  
  
4.  Wechseln Sie zurück zur Startseite, indem auf **SQL Server 2012 Master Data Services** oben.  
  
5.  Stellen Sie sicher, dass **Lieferanten** Modell ausgewählt ist **Modell** und **VERSION_1** ausgewählt ist **Version**, und klicken Sie auf  **Explorer**.  
  
6.  Sie können das in MDS importierte Daten-SSIS-Paket anzeigen. Die Daten sollten bereinigt werden und haben keine Duplikate **Code** Werte (Beachten Sie: **SupplierID** Spalte in Excel entspricht **Code** -Attribut der lieferantenentität in MDS).  
  
## <a name="next-step"></a>Nächster Schritt  
 [Task 17: Überprüfung des DQS-Bereinigung erstellt wurde vom SSIS-Paket](../../2014/tutorials/task-17-reviewing-dqs-cleansing-project-created-by-the-ssis-package.md)  
  
  
