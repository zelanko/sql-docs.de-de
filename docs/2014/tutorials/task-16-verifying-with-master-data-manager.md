---
title: 'Aufgabe 16: Überprüfung mit Master Data Manager | Microsoft Docs'
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- data-quality-services
- integration-services
- master-data-services
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 57ad9d3e-8f95-4df6-af01-c291ccf49164
caps.latest.revision: 6
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.openlocfilehash: 36220f21f3e2e28d75ff546857fd87b1e71436f1
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/19/2018
ms.locfileid: "36056131"
---
# <a name="task-16-verifying-with-master-data-manager"></a>Aufgabe 16: Überprüfung mit Master Data Manager
  In dieser Aufgabe prüfen Sie den Status des vom SSIS-Paket gesendeten Batchauftrags und verifizieren, ob die Daten mit Master Data Manager auf den MDS-Server hochgeladen wurden.  
  
1.  Starten Sie **Master Data Manager** ([http://localhost/MDS](http://localhost/MDS)). Wenn dieser bereits geöffnet ist, klicken Sie auf **Microsoft SQL Server Master Data Services** oben, um zum Wechseln der **Startseite**.  
  
2.  Klicken Sie auf **Integrationsmanagement**.  
  
3.  Beachten Sie, dass es ein Batch mit namens **EIMBatch** , den Sie in der Liste gesendet. Klicken Sie auf **Importdaten** in der Menüleiste, wenn Sie nicht den folgenden Bildschirm angezeigt werden.  
  
     ![EIM-Batch](../../2014/tutorials/media/et-verifyingwithmasterdatamanager.jpg "EIM-Batch")  
  
4.  Wechseln Sie zurück zur Startseite, indem Sie auf **SQL Server 2012 Master Data Services** oben.  
  
5.  Stellen Sie sicher, dass **Lieferanten** Modell ausgewählt ist **Modell** und **VERSION_1** ausgewählt ist, für die **Version**, und klicken Sie auf  **Explorer**.  
  
6.  Sie können das in MDS importierte Daten-SSIS-Paket anzeigen. Die Daten sollten bereinigt sein und müssen also keine Duplikate **Code** Werte (Hinweis: **SupplierID** Spalte in Excel entspricht **Code** -Attribut der lieferantenentität in MDS).  
  
## <a name="next-step"></a>Nächster Schritt  
 [Aufgabe 17: Überprüfung des DQS-Bereinigungsprojekts, das vom SSIS-Paket erstellt wurde](../../2014/tutorials/task-17-reviewing-dqs-cleansing-project-created-by-the-ssis-package.md)  
  
  