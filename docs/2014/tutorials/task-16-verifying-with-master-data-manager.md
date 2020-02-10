---
title: 'Aufgabe 16: Überprüfen mit Master Data Manager | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: data-quality-services
ms.topic: conceptual
ms.assetid: 57ad9d3e-8f95-4df6-af01-c291ccf49164
author: lrtoyou1223
ms.author: lle
manager: craigg
ms.openlocfilehash: 35dd2da7f6cf6598918cd9d109b97f3d314556d1
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "65484692"
---
# <a name="task-16-verifying-with-master-data-manager"></a>Aufgabe 16: Überprüfung mit Master Data Manager
  In dieser Aufgabe prüfen Sie den Status des vom SSIS-Paket gesendeten Batchauftrags und verifizieren, ob die Daten mit Master Data Manager auf den MDS-Server hochgeladen wurden.  
  
1.  Starten **** Sie Master Data Manager[http://localhost/MDS](http://localhost/MDS)(). Wenn Sie bereits geöffnet ist, klicken Sie oben auf **Microsoft SQL Server Master Data Services** , um zur **Startseite**zu wechseln.  
  
2.  Klicken Sie auf **Integrations Management**.  
  
3.  Beachten Sie, dass es einen Batch mit dem Namen **eimbatch** gibt, den Sie in der Liste übermittelt haben. Klicken Sie in der Menüleiste auf **Daten importieren** , wenn der folgende Bildschirm nicht angezeigt wird.  
  
     ![EIM-Batch](../../2014/tutorials/media/et-verifyingwithmasterdatamanager.jpg "EIM-Batch")  
  
4.  Wechseln Sie zurück zur Startseite, indem Sie oben auf **SQL Server 2012 Master Data Services** klicken.  
  
5.  Stellen Sie sicher, dass das Modell **Suppliers** als **Modell** ausgewählt ist und **VERSION_1** für die **Version**ausgewählt ist, und klicken Sie auf **Explorer**.  
  
6.  Sie können das in MDS importierte Daten-SSIS-Paket anzeigen. Die Daten sollten bereinigt werden und keine doppelten **Code** Werte aufweisen (Hinweis: die **SupplierID-** Spalte in Excel entspricht dem **Code** -Attribut der Lieferanten Entität in MDS).  
  
## <a name="next-step"></a>Nächster Schritt  
 [Aufgabe 17: Überprüfung des DQS-Bereinigungsprojekts, das vom SSIS-Paket erstellt wurde](../../2014/tutorials/task-17-reviewing-dqs-cleansing-project-created-by-the-ssis-package.md)  
  
  
