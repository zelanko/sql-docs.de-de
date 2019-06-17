---
title: 'Lektion 2: Erstellen eines Abonnements für die Mergeveröffentlichung | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- replication [SQL Server], tutorials
ms.assetid: 06722baa-9065-443e-b1d5-99036cf89074
author: craigg-msft
ms.author: craigg
manager: craigg
ms.openlocfilehash: 495fb831490a35043b500caea2c835bfd80b6a8c
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "62721028"
---
# <a name="lesson-2-creating-a-subscription-to-the-merge-publication"></a>Lektion 2: Erstellen eines Abonnements für die Mergeveröffentlichung
  In dieser Lektion erstellen Sie das Abonnement mithilfe von [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]. Anschließend erstellen Sie Berechtigungen für die Abonnementdatenbank und generieren die gefilterte Datenmomentaufnahme für das neue Abonnement manuell. Diese Lektion setzt voraus, dass Sie die vorherige Lektion abgeschlossen haben [Lektion 1: Veröffentlichen von Daten mithilfe der Mergereplikation](lesson-1-publishing-data-using-merge-replication.md).  
  
### <a name="to-create-the-subscription"></a>So erstellen Sie das Abonnement  
  
1.  Stellen Sie in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]eine Verbindung mit dem Abonnenten her, erweitern Sie den Serverknoten und den Ordner **Replikation** . Klicken Sie mit der rechten Maustaste auf den Ordner **Lokale Abonnements** , und klicken Sie anschließend auf **Neue Abonnements**.  
  
     Der Assistent für neue Abonnements wird gestartet.  
  
2.  Klicken Sie auf der Seite **Veröffentlichung** in der Liste **Verleger** auf **SQL Server-Verleger suchen** .  
  
3.  Geben Sie im Dialogfeld **Verbindung mit Server herstellen** im Feld **Servername** den Namen der Verlegerinstanz ein, und klicken Sie auf **Verbinden**.  
  
4.  Klicken Sie auf **AdvWorksSalesOrdersMerge**, und klicken Sie auf **Weiter**.  
  
5.  Klicken Sie auf der Seite Speicherort des Merge-Agents auf **Jeden Agent auf seinem Abonnenten ausführen**, und klicken Sie anschließend auf **Weiter**.  
  
6.  Wählen Sie auf der Seite Abonnenten den Instanznamen des Abonnentenservers, und klicken Sie unter **Abonnementdatenbank**Option  **\<neue Datenbank >** aus der Liste.  
  
7.  Geben Sie im Dialogfeld **Neue Datenbank** den Namen **SalesOrdersReplica** in das Feld **Datenbankname** ein, klicken Sie auf **OK**, und klicken Sie anschließend auf **Weiter**.  
  
8.  Klicken Sie auf der Seite Sicherheit für den Merge-Agent auf die Auslassungspunkte ( **...** ) Geben Sie eine Schaltfläche \< _Machine_Name >_ **\repl_merge** in die **Prozesskonto** ein, geben Sie das Kennwort für dieses Konto ein, klicken Sie auf **OK**, klicken Sie auf **Weiter**, und klicken Sie dann auf **Weiter** erneut aus.  
  
9. Wählen Sie auf der Seite Abonnements initialisieren aus der Liste **Initialisierungszeitpunkt** die Option **Bei der ersten Synchronisierung** aus, klicken Sie auf **Weiter**, und klicken Sie erneut auf **Weiter** .  
  
10. Geben Sie den Wert, auf der Seite HOST_NAME-Werte `adventure-works\pamela0` in die **HOST_NAME-Wert** ein, und klicken Sie dann auf **Fertig stellen**.  
  
11. Klicken Sie erneut auf **Fertig stellen** , und klicken Sie nach dem Erstellen des Abonnements auf **Schließen**.  
  
### <a name="setting-database-permissions-at-the-subscriber"></a>Festlegen der Datenbankberechtigungen auf dem Abonnenten  
  
1.  Stellen Sie in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]eine Verbindung mit dem Abonnenten her, erweitern Sie **Datenbanken**, **SalesOrdersReplica**und **Sicherheit**, klicken Sie mit der rechten Maustaste auf **Benutzer**, und wählen Sie anschließend **Neuer Benutzer**aus.  
  
2.  Auf der **allgemeine** geben \< _Machine_Name >_ **\repl_merge** in die **Benutzernamen** klicken Sie auf die Auslassungszeichen () **...** ), zeigen Sie auf **Durchsuchen**Option \< _Machine_Name >_ **\repl_merge**, klicken Sie auf **OK**, klicken Sie auf **Namen überprüfen**, und klicken Sie dann auf **OK**.  
  
3.  Wählen Sie unter **Mitgliedschaft in Datenbankrollen**die **db_owner**-Rolle aus, und klicken Sie anschließend auf **OK** , um den Benutzer zu erstellen.  
  
### <a name="to-create-the-filtered-data-snapshot-for-the-subscription"></a>So erstellen Sie die gefilterte Datenmomentaufnahme für das Abonnement  
  
1.  Stellen Sie in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]eine Verbindung mit dem Verleger her, und erweitern Sie dann den Serverknoten und den Ordner **Replikation** .  
  
2.  Klicken Sie im Ordner **Lokale Veröffentlichungen** mit der rechten Maustaste auf die **AdvWorksSalesOrdersMerge** -Veröffentlichung, und klicken Sie anschließend auf **Eigenschaften**.  
  
     Das Dialogfeld **Veröffentlichungseigenschaften** wird angezeigt.  
  
3.  Wählen Sie die Seite **Datenpartitionen** aus, und klicken Sie auf **Hinzufügen**.  
  
4.  In der **Datenpartition hinzufügen** (Dialogfeld), Typ `adventure-works\pamela0` in die **HOST_NAME-Wert** ein, und klicken Sie dann auf **OK**.  
  
5.  Wählen Sie die neu hinzugefügte Partition aus, klicken Sie auf **Die ausgewählten Momentaufnahmen jetzt generieren**, und klicken Sie anschließend auf **OK**.  
  
## <a name="next-steps"></a>Nächste Schritte  
 Sie haben erfolgreich ein Abonnement für die Mergeveröffentlichung erstellt und die gefilterte Momentaufnahme für die Datenpartition des neuen Abonnements generiert, damit diese verfügbar ist, wenn das Abonnement initialisiert wird. Als Nächstes gewähren Sie dem Merge-Agent Rechte für die Abonnementdatenbank und führen den Merge-Agent aus, um die Synchronisierung zu starten und das Abonnement zu initialisieren. Siehe [Lektion 3: Synchronisieren des Abonnements für die Mergeveröffentlichung](lesson-3-synchronizing-the-subscription-to-the-merge-publication.md).  
  
## <a name="see-also"></a>Siehe auch  
 [Abonnieren von Veröffentlichungen](subscribe-to-publications.md)   
 [Erstellen eines Pullabonnements](create-a-pull-subscription.md)   
 [Momentaufnahmen für Mergeveröffentlichungen mit parametrisierten Filtern](snapshots-for-merge-publications-with-parameterized-filters.md)  
  
  
