---
title: 'Lektion 2: Erstellen eines Abonnements für die Transaktionsveröffentlichung | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- replication [SQL Server], tutorials
ms.assetid: 5995b7d2-7c06-46f5-b96c-2bee879bcda2
author: craigg-msft
ms.author: craigg
manager: craigg
ms.openlocfilehash: d3e8b5f0be58d9153fbe4d0ffd0287ea753fcc5e
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "62721083"
---
# <a name="lesson-2-creating-a-subscription-to-the-transactional-publication"></a>Lektion 2: Erstellen eines Abonnements für die Transaktionsveröffentlichung
  In dieser Lektion erstellen Sie mithilfe von [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]ein Abonnement. Diese Lektion setzt voraus, dass Sie die vorherige Lektion abgeschlossen haben [Lektion 1: Veröffentlichen von Daten mithilfe der Transaktionsreplikation](lesson-1-publishing-data-using-transactional-replication.md).  
  
### <a name="to-create-the-subscription"></a>So erstellen Sie das Abonnement  
  
1.  Stellen Sie in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]eine Verbindung mit dem Verleger her, und erweitern Sie dann den Serverknoten und den Ordner **Replikation** .  
  
2.  Klicken Sie im Ordner **Lokale Veröffentlichungen** mit der rechten Maustaste auf die **AdvWorksProductTrans** -Veröffentlichung und anschließend auf **Neue Abonnements**.  
  
     Der Assistent für neue Abonnements wird gestartet.  
  
3.  Wählen Sie auf der Seite Veröffentlichung die **AdvWorksProductTrans**-Veröffentlichung aus, und klicken Sie dann auf **Weiter**.  
  
4.  Wählen Sie auf der Seite Speicherort des Verteilungs-Agents die Option **Alle Agents auf dem Verteiler ausführen**aus, und klicken Sie dann auf **Weiter**.  
  
5.  Wenn der Name der Abonnenteninstanz auf der Seite Abonnenten nicht angezeigt wird, klicken Sie auf **Abonnent hinzufügen**, klicken Sie auf **SQL Server-Abonnenten hinzufügen**, geben Sie den Namen der Abonnenteninstanz im Dialogfeld **Verbindung mit Server herstellen** ein, und klicken Sie dann auf **Verbinden**.  
  
6.  Klicken Sie auf der Seite "Abonnenten", wählen Sie den Instanznamen des Abonnentenservers aus, und wählen  **\<neue Datenbank >** unter **Abonnementdatenbank**.  
  
7.  Geben Sie im Dialogfeld **Neue Datenbank** den Namen **ProductReplica** in das Feld **Datenbankname** ein, klicken Sie auf **OK**, und klicken Sie dann auf **Weiter**.  
  
8.  In der **Sicherheit für den Verteilungs-Agent** Dialogfeld klicken Sie auf die Auslassungspunkte ( **...** ) Geben Sie eine Schaltfläche \< _Machine_Name >_ **\repl_distribution** in die **Prozesskonto** Geben Sie das Kennwort für dieses auf **OK**, und klicken Sie dann auf **Weiter**.  
  
9. Klicken Sie auf **Fertig stellen** , um auf den verbleibenden Seiten die Standardwerte zu übernehmen und den Assistenten zu beenden.  
  
### <a name="setting-database-permissions-at-the-subscriber"></a>Festlegen der Datenbankberechtigungen auf dem Abonnenten  
  
1.  Stellen Sie in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]eine Verbindung mit dem Abonnenten her, erweitern Sie **Datenbanken**, **ProductReplica**und **Sicherheit**, klicken Sie mit der rechten Maustaste auf **Benutzer**, und wählen Sie anschließend **Neuer Benutzer**aus.  
  
2.  Klicken Sie auf der Seite **Allgemein** in der Liste **Benutzertyp** auf **Windows-Benutzer**.  
  
3.  Wählen Sie die **Benutzernamen** ein, und klicken Sie auf die Schaltfläche mit den Auslassungspunkten (...) in der **Geben Sie den zu verwendenden Objektnamen** Feldtyp < Machine_Name > **\repl_distribution**, klicken Sie auf  **Überprüfen Sie die Namen**, und klicken Sie dann auf **OK**.  
  
4.  Wählen Sie auf der Seite **Mitgliedschaft** im Bereich **Mitgliedschaft in Datenbankrollen** die **db_owner**-Rolle aus, und klicken Sie anschließend auf **OK** , um den Benutzer zu erstellen.  
  
### <a name="to-view-the-synchronization-status-of-the-subscription"></a>So zeigen Sie den Synchronisierungsstatus des Abonnements an  
  
1.  Stellen Sie in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]eine Verbindung mit dem Verleger her, und erweitern Sie dann den Serverknoten und den Ordner **Replikation** .  
  
2.  Erweitern Sie im Ordner **Lokale Veröffentlichungen** die **AdvWorksProductTrans** -Veröffentlichung, klicken Sie mit der rechten Maustaste auf das Abonnement in der **ProductReplica** -Datenbank und anschließend auf **Synchronisierungsstatus anzeigen**.  
  
     Der aktuelle Synchronisierungsstatus des Abonnements wird angezeigt.  
  
3.  Wenn das Abonnement unter **AdvWorksProductTrans**nicht angezeigt wird, drücken Sie F5, um die Liste zu aktualisieren.  
  
## <a name="next-steps"></a>Nächste Schritte  
 Sie haben erfolgreich ein Abonnement für die Transaktionsveröffentlichung erstellt. Da der Verteilungs-Agent für dieses Abonnement ständig ausgeführt wird, wird das Abonnement initialisiert, wenn es erstellt wird. Als Nächstes verwenden Sie Überwachungstoken, um zu überprüfen, ob die Änderungen auf dem Abonnenten repliziert werden, und um die Latenzzeit zu ermitteln. Siehe [Lektion 3: Überprüfen des Abonnements und Messen der Latenzzeit](lesson-3-validating-the-subscription-and-measuring-latency.md).  
  
## <a name="see-also"></a>Siehe auch  
 [Initialisieren eines Abonnements mit einer Momentaufnahme](initialize-a-subscription-with-a-snapshot.md)   
 [Create a Push Subscription](create-a-push-subscription.md)   
 [Abonnieren von Veröffentlichungen](subscribe-to-publications.md)  
  
  
