---
title: 'Lektion 3: Überprüfen des Abonnements und Messen der Latenzzeit | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- replication
ms.topic: conceptual
helpviewer_keywords:
- replication [SQL Server], tutorials
ms.assetid: 147f7b93-1804-4e0b-9e17-57a51d035b2a
author: craigg-msft
ms.author: craigg
manager: craigg
ms.openlocfilehash: 44d38b8d67163f053ffe98586f5338f4fd2ae949
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/02/2018
ms.locfileid: "48200194"
---
# <a name="lesson-3-validating-the-subscription-and-measuring-latency"></a>Lektion 3: Überprüfen des Abonnements und Messen der Latenzzeit
  In dieser Lektion verwenden Sie Überwachungstoken, um sicherzustellen, dass Änderungen auf dem Abonnenten repliziert werden, und um die Latenzzeit (die Zeit, nach der eine auf dem Verleger vorgenommene Änderung auf dem Abonnenten angezeigt wird) zu bestimmen. Diese Lektion setzt voraus, dass Sie die vorherige Lektion abgeschlossen haben: [Lektion 2: Erstellen eines Abonnements für die Transaktionsveröffentlichung](lesson-2-creating-a-subscription-to-the-transactional-publication.md).  
  
### <a name="to-insert-a-tracer-token-and-view-information-on-the-token"></a>So fügen Sie ein Überwachungstoken ein und zeigen Informationen zum Token an  
  
1.  Stellen Sie in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]eine Verbindung mit dem Verleger her, erweitern Sie den Serverknoten, klicken Sie mit der rechten Maustaste auf den Ordner **Replikation** , und klicken Sie anschließend auf **Replikationsmonitor starten**.  
  
     Der Replikationsmonitor wird gestartet.  
  
2.  Erweitern Sie im linken Bereich eine Verlegergruppe, erweitern Sie die Verlegerinstanz, und klicken Sie dann auf die **AdvWorksProductTrans** -Veröffentlichung.  
  
3.  Klicken Sie auf die Registerkarte **Überwachungstoken** .  
  
4.  Klicken Sie auf **Überwachung einfügen**.  
  
5.  In den folgenden Spalten sehen Sie die für das Überwachungstoken benötigte Zeit: **Verleger zu Verteiler**, **Verteiler zu Abonnent**, **Gesamtlatenzzeit**. Mit dem Wert **Ausstehend** wird angegeben, dass das Token noch nicht den Bestimmungspunkt erreicht hat.  
  
## <a name="next-steps"></a>Nächste Schritte  
 In dieser Lektion haben Sie mithilfe von Überwachungstoken erfolgreich überprüft, dass Datenänderungen vom Verleger zum Abonnenten repliziert werden. Zudem können Sie Daten in der **Product** -Tabelle auf dem Verleger einfügen, aktualisieren und löschen und die **Product** -Tabelle auf dem Abonnenten abfragen, um diese Änderungen anzuzeigen, nachdem sie repliziert wurden.  
  
 Damit ist das Lernprogramm Replizieren von Daten zwischen Servern mit kontinuierlicher Verbindung abgeschlossen. Ein ähnliches Lernprogramm zur Mergereplikation finden Sie unter [Tutorial: Replicating Data with Mobile Clients](tutorial-replicating-data-with-mobile-clients.md).  
  
## <a name="see-also"></a>Siehe auch  
 [Messen der Latenzzeit und Überprüfen der Verbindungen bei Transaktionsreplikationen](monitor/measure-latency-and-validate-connections-for-transactional-replication.md)  
  
  
