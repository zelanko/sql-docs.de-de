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
author: rothja
ms.author: jroth
manager: craigg
ms.openlocfilehash: 9dc9824efb3f962d97f786835fa2367be18b55f7
ms.sourcegitcommit: 4b5919e3ae5e252f8d6422e8e6fddac1319075a1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/09/2020
ms.locfileid: "83000413"
---
# <a name="lesson-2-creating-a-subscription-to-the-transactional-publication"></a>Lektion 2: Erstellen eines Abonnements für die Transaktionsveröffentlichung
  In dieser Lektion erstellen Sie mithilfe von [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]ein Abonnement. Für diese Lektion wird vorausgesetzt, dass Sie die vorherige Lektion abgeschlossen haben: [Lektion 1: Veröffentlichen von Daten mithilfe der Transaktionsreplikation](lesson-1-publishing-data-using-transactional-replication.md).  
  
### <a name="to-create-the-subscription"></a>So erstellen Sie das Abonnement  
  
1.  Stellen Sie in eine Verbindung mit dem Verleger her [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] , erweitern Sie den Server Knoten, und erweitern Sie dann den Ordner **Replikation** .  
  
2.  Klicken Sie im Ordner **Lokale Veröffentlichungen** mit der rechten Maustaste auf die **AdvWorksProductTrans** -Veröffentlichung und anschließend auf **Neue Abonnements**.  
  
     Der Assistent für neue Abonnements wird gestartet.  
  
3.  Wählen Sie auf der Seite Veröffentlichung die **AdvWorksProductTrans**-Veröffentlichung aus, und klicken Sie dann auf **Weiter**.  
  
4.  Wählen Sie auf der Seite Speicherort des Verteilungs-Agents die Option **Alle Agents auf dem Verteiler ausführen**aus, und klicken Sie dann auf **Weiter**.  
  
5.  Wenn der Name der Abonnenteninstanz auf der Seite Abonnenten nicht angezeigt wird, klicken Sie auf **Abonnent hinzufügen**, klicken Sie auf **SQL Server-Abonnenten hinzufügen**, geben Sie den Namen der Abonnenteninstanz im Dialogfeld **Verbindung mit Server herstellen** ein, und klicken Sie dann auf **Verbinden**.  
  
6.  Wählen Sie auf der Seite Abonnenten den Instanznamen des Abonnenten Servers aus, und wählen Sie unter **Abonnement Datenbank**die Option ** \< neue Daten Bank>** aus.  
  
7.  Geben Sie im Dialogfeld **Neue Datenbank** den Namen **ProductReplica** in das Feld **Datenbankname** ein, klicken Sie auf **OK**, und klicken Sie dann auf **Weiter**.  
  
8.  Klicken Sie im Dialogfeld **Verteilungs-Agent Sicherheit** auf die Schaltfläche mit den Auslassungs Punkten (**...**), geben Sie \< _Machine_Name>_ **\ repl_distribution** in das Feld **Prozess Konto** ein, geben Sie das Kennwort für dieses Konto ein, klicken Sie auf **OK**, und klicken Sie dann auf **weiter**.  
  
9. Klicken Sie auf **Fertig stellen** , um auf den verbleibenden Seiten die Standardwerte zu übernehmen und den Assistenten zu beenden.  
  
### <a name="setting-database-permissions-at-the-subscriber"></a>Festlegen der Datenbankberechtigungen auf dem Abonnenten  
  
1.  Stellen Sie in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]eine Verbindung mit dem Abonnenten her, erweitern Sie **Datenbanken**, **ProductReplica**und **Sicherheit**, klicken Sie mit der rechten Maustaste auf **Benutzer**, und wählen Sie anschließend **Neuer Benutzer**aus.  
  
2.  Klicken Sie auf der Seite **Allgemein** in der Liste **Benutzertyp** auf **Windows-Benutzer**.  
  
3.  Wählen Sie das Feld **Benutzername** aus, **und klicken Sie**auf die Schaltfläche mit den Auslassungs Punkten (...). Geben Sie im Feld **Geben Sie die zu ausgewäfenden Objektnamen** ein den <Machine_Name>**\ repl_distribution**ein, klicken Sie auf **Namen überprüfen**  
  
4.  Wählen Sie auf der Seite **Mitgliedschaft** im Bereich **Mitgliedschaft in Datenbankrollen** die **db_owner**-Rolle aus, und klicken Sie anschließend auf **OK** , um den Benutzer zu erstellen.  
  
### <a name="to-view-the-synchronization-status-of-the-subscription"></a>So zeigen Sie den Synchronisierungsstatus des Abonnements an  
  
1.  Stellen Sie in eine Verbindung mit dem Verleger her [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] , erweitern Sie den Server Knoten, und erweitern Sie dann den Ordner **Replikation** .  
  
2.  Erweitern Sie im Ordner **Lokale Veröffentlichungen** die **AdvWorksProductTrans** -Veröffentlichung, klicken Sie mit der rechten Maustaste auf das Abonnement in der **ProductReplica** -Datenbank und anschließend auf **Synchronisierungsstatus anzeigen**.  
  
     Der aktuelle Synchronisierungsstatus des Abonnements wird angezeigt.  
  
3.  Wenn das Abonnement unter **AdvWorksProductTrans**nicht angezeigt wird, drücken Sie F5, um die Liste zu aktualisieren.  
  
## <a name="next-steps"></a>Nächste Schritte  
 Sie haben erfolgreich ein Abonnement für die Transaktionsveröffentlichung erstellt. Da der Verteilungs-Agent für dieses Abonnement ständig ausgeführt wird, wird das Abonnement initialisiert, wenn es erstellt wird. Als Nächstes verwenden Sie Überwachungstoken, um zu überprüfen, ob die Änderungen auf dem Abonnenten repliziert werden, und um die Latenzzeit zu ermitteln. Siehe [Lesson 3: Validating the Subscription and Measuring Latency](lesson-3-validating-the-subscription-and-measuring-latency.md).  
  
## <a name="see-also"></a>Weitere Informationen  
 [Initialisieren eines Abonnements mit einer Momentaufnahme](initialize-a-subscription-with-a-snapshot.md)   
 [Erstellen eines Pushabonnements](create-a-push-subscription.md)   
 [Abonnieren von Veröffentlichungen](subscribe-to-publications.md)  
  
  
