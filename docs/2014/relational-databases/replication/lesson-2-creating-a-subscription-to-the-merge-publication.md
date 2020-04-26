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
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/25/2020
ms.locfileid: "62721028"
---
# <a name="lesson-2-creating-a-subscription-to-the-merge-publication"></a>Lektion 2: Erstellen eines Abonnements für die Mergeveröffentlichung
  In dieser Lektion erstellen Sie das Abonnement mithilfe von [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]. Anschließend erstellen Sie Berechtigungen für die Abonnementdatenbank und generieren die gefilterte Datenmomentaufnahme für das neue Abonnement manuell. Für diese Lektion wird vorausgesetzt, dass Sie die vorherige Lektion abgeschlossen haben: [Lektion 1: Veröffentlichen von Daten mithilfe der Mergereplikation](lesson-1-publishing-data-using-merge-replication.md).  
  
### <a name="to-create-the-subscription"></a>So erstellen Sie das Abonnement  
  
1.  Stellen Sie in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]eine Verbindung mit dem Abonnenten her, erweitern Sie den Serverknoten und den Ordner **Replikation** . Klicken Sie mit der rechten Maustaste auf den Ordner **Lokale Abonnements** , und klicken Sie anschließend auf **Neue Abonnements**.  
  
     Der Assistent für neue Abonnements wird gestartet.  
  
2.  Klicken Sie auf der Seite **Veröffentlichung** in der Liste **Verleger** auf **SQL Server-Verleger suchen** .  
  
3.  Geben Sie im Dialogfeld **Verbindung mit Server herstellen** im Feld **Servername** den Namen der Verlegerinstanz ein, und klicken Sie auf **Verbinden**.  
  
4.  Klicken Sie auf **AdvWorksSalesOrdersMerge**, und klicken Sie auf **Weiter**.  
  
5.  Klicken Sie auf der Seite Speicherort des Merge-Agents auf **Jeden Agent auf seinem Abonnenten ausführen**, und klicken Sie anschließend auf **Weiter**.  
  
6.  Wählen Sie auf der Seite Abonnenten den Instanznamen des Abonnenten Servers aus, und **Subscription Database**wählen Sie ** \<** unter Abonnement Datenbank die Option neue Daten Bank>aus der Liste aus.  
  
7.  Geben Sie im Dialogfeld **Neue Datenbank** den Namen **SalesOrdersReplica** in das Feld **Datenbankname** ein, klicken Sie auf **OK**, und klicken Sie anschließend auf **Weiter**.  
  
8.  Klicken Sie auf der Seite Merge-Agent Sicherheit auf die Schaltfläche mit den Auslassungs Punkten (**...**), geben Sie \< _Machine_Name>_ **\ repl_merge** in das Feld **Prozess Konto** ein, geben Sie das Kennwort für dieses Konto ein, klicken Sie auf **OK**, klicken Sie auf **weiter**und dann erneut auf **weiter** .  
  
9. Wählen Sie auf der Seite Abonnements initialisieren aus der Liste **Initialisierungszeitpunkt** die Option **Bei der ersten Synchronisierung** aus, klicken Sie auf **Weiter**, und klicken Sie erneut auf **Weiter** .  
  
10. Geben Sie auf der Seite HOST_NAME Werte `adventure-works\pamela0` im Feld **HOST_NAME Wert** den Wert ein, und klicken Sie dann auf **Fertig**stellen.  
  
11. Klicken Sie erneut auf **Fertig stellen** , und klicken Sie nach dem Erstellen des Abonnements auf **Schließen**.  
  
### <a name="setting-database-permissions-at-the-subscriber"></a>Festlegen der Datenbankberechtigungen auf dem Abonnenten  
  
1.  Stellen Sie in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]eine Verbindung mit dem Abonnenten her, erweitern Sie **Datenbanken**, **SalesOrdersReplica**und **Sicherheit**, klicken Sie mit der rechten Maustaste auf **Benutzer**, und wählen Sie anschließend **Neuer Benutzer**aus.  
  
2.  Geben \<Sie auf der Seite **Allgemein** _Machine_Name>_ **\ repl_merge** im Feld **Benutzer Name** ein, klicken Sie auf die Schaltfläche mit den Auslassungs Punkten (**..**.), klicken Sie auf **Durchsuchen**, wählen Sie \< _Machine_Name>_ **\ repl_merge**, klicken Sie auf **OK**, klicken Sie auf **Namen überprüfen**und dann auf **OK**.  
  
3.  Wählen Sie unter **Mitgliedschaft in Datenbankrollen**die **db_owner**-Rolle aus, und klicken Sie anschließend auf **OK** , um den Benutzer zu erstellen.  
  
### <a name="to-create-the-filtered-data-snapshot-for-the-subscription"></a>So erstellen Sie die gefilterte Datenmomentaufnahme für das Abonnement  
  
1.  Stellen Sie in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]eine Verbindung mit dem Verleger her, erweitern Sie den Server Knoten, und erweitern Sie dann den Ordner **Replikation** .  
  
2.  Klicken Sie im Ordner **Lokale Veröffentlichungen** mit der rechten Maustaste auf die **AdvWorksSalesOrdersMerge** -Veröffentlichung, und klicken Sie anschließend auf **Eigenschaften**.  
  
     Das Dialogfeld **Veröffentlichungseigenschaften** wird angezeigt.  
  
3.  Wählen Sie die Seite **Datenpartitionen** aus, und klicken Sie auf **Hinzufügen**.  
  
4.  Geben `adventure-works\pamela0` Sie im Dialogfeld **Daten Partition hinzufügen** im Feld **HOST_NAME Wert** ein, und klicken Sie dann auf **OK**.  
  
5.  Wählen Sie die neu hinzugefügte Partition aus, klicken Sie auf **Die ausgewählten Momentaufnahmen jetzt generieren**, und klicken Sie anschließend auf **OK**.  
  
## <a name="next-steps"></a>Nächste Schritte  
 Sie haben erfolgreich ein Abonnement für die Mergeveröffentlichung erstellt und die gefilterte Momentaufnahme für die Datenpartition des neuen Abonnements generiert, damit diese verfügbar ist, wenn das Abonnement initialisiert wird. Als Nächstes gewähren Sie dem Merge-Agent Rechte für die Abonnementdatenbank und führen den Merge-Agent aus, um die Synchronisierung zu starten und das Abonnement zu initialisieren. Weitere Informationen finden Sie unter [Lektion 3: Synchronisieren des Abonnements für die Mergeveröffentlichung](lesson-3-synchronizing-the-subscription-to-the-merge-publication.md).  
  
## <a name="see-also"></a>Weitere Informationen  
 [Abonnieren von Veröffentlichungen](subscribe-to-publications.md)   
 [Create a Pull Subscription](create-a-pull-subscription.md)   
 [Momentaufnahmen für eine Mergeveröffentlichung mit parametrisierten Filtern](snapshots-for-merge-publications-with-parameterized-filters.md)  
  
  
