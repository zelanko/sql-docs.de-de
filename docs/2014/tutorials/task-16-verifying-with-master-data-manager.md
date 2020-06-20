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
ms.openlocfilehash: d1649582f97e9e08691726745e4ba14b2f8226bd
ms.sourcegitcommit: 57f1d15c67113bbadd40861b886d6929aacd3467
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/18/2020
ms.locfileid: "85061081"
---
# <a name="task-16-verifying-with-master-data-manager"></a>Aufgabe 16: Überprüfung mit dem Master Data Manager
  In dieser Aufgabe prüfen Sie den Status des vom SSIS-Paket gesendeten Batchauftrags und verifizieren, ob die Daten mit Master Data Manager auf den MDS-Server hochgeladen wurden.  
  
1.  Starten Sie **Master Data Manager** ( `http://localhost/MDS` ). Wenn Sie bereits geöffnet ist, klicken Sie oben auf **Microsoft SQL Server Master Data Services** , um zur **Startseite**zu wechseln.  
  
2.  Klicken Sie auf **Integrations Management**.  
  
3.  Beachten Sie, dass es einen Batch mit dem Namen **eimbatch** gibt, den Sie in der Liste übermittelt haben. Klicken Sie in der Menüleiste auf **Daten importieren** , wenn der folgende Bildschirm nicht angezeigt wird.  
  
     ![EIM-Batch](../../2014/tutorials/media/et-verifyingwithmasterdatamanager.jpg "EIM-Batch")  
  
4.  Wechseln Sie zurück zur Startseite, indem Sie oben auf **SQL Server 2012 Master Data Services** klicken.  
  
5.  Stellen Sie sicher, dass das Modell **Suppliers** als **Modell** ausgewählt ist und **VERSION_1** für die **Version**ausgewählt ist, und klicken Sie auf **Explorer**.  
  
6.  Sie können das in MDS importierte Daten-SSIS-Paket anzeigen. Die Daten sollten bereinigt werden und keine doppelten **Code** Werte aufweisen (Hinweis: die **SupplierID-** Spalte in Excel entspricht dem **Code** -Attribut der Lieferanten Entität in MDS).  
  
## <a name="next-step"></a>Nächster Schritt  
 [Aufgabe 17: Überprüfung des vom SSIS-Paket erstellten DQS-Bereinigungsprojekts](../../2014/tutorials/task-17-reviewing-dqs-cleansing-project-created-by-the-ssis-package.md)  
  
  
