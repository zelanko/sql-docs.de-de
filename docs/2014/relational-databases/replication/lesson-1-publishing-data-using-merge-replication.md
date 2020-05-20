---
title: 'Lektion 1: Veröffentlichen von Daten mithilfe der Mergereplikation | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 06/14/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- replication [SQL Server], tutorials
ms.assetid: c3c6e0b6-54cd-4b7d-8efb-2cefe14fcd7f
author: rothja
ms.author: jroth
manager: craigg
ms.openlocfilehash: 63df76a4e136a7d0a581d613829482b7eb430ea6
ms.sourcegitcommit: 4b5919e3ae5e252f8d6422e8e6fddac1319075a1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/09/2020
ms.locfileid: "83000480"
---
# <a name="lesson-1-publishing-data-using-merge-replication"></a>Lektion 1: Veröffentlichen von Daten mithilfe der Mergereplikation
  In dieser Lektion erstellen Sie mithilfe von [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] eine Mergeveröffentlichung, um eine Teilmenge der Tabellen **Employee**, **SalesOrderHeader**und **SalesOrderDetail** in der [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] -Beispieldatenbank zu veröffentlichen. Diese Tabellen werden mit parametrisierten Zeilenfiltern gefiltert, sodass in den einzelnen Abonnements jeweils eine eindeutige Teilmenge der Daten enthalten ist. Außerdem fügen Sie der Veröffentlichungszugriffsliste (Publication Access List, PAL) die vom Merge-Agent verwendete [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Anmeldung hinzu. Für dieses Lernprogramm ist es erforderlich, dass Sie das vorherige Lernprogramm ( [Vorbereiten des Servers für die Replikation](tutorial-preparing-the-server-for-replication.md)) abgeschlossen haben.  
  
### <a name="to-create-a-publication-and-define-articles"></a>So erstellen Sie eine Veröffentlichung und definieren Artikel  
  
1.  Stellen Sie in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]eine Verbindung mit dem Verleger her, und erweitern Sie dann den Serverknoten.  
  
2.  Erweitern Sie den Ordner **Replikation** und klicken Sie mit der rechten Maustaste auf **Lokale Veröffentlichungen**. Klicken Sie anschließend auf **Neue Veröffentlichung**.  
  
     Der Assistent für neue Veröffentlichung wird gestartet.  
  
3.  Wählen Sie auf der Seite Veröffentlichungsdatenbank [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)]aus, und klicken Sie anschließend auf **Weiter**.  
  
4.  Wählen Sie auf der Seite **Veröffentlichungstyp**die Option **Mergeveröffentlichung**aus und klicken Sie anschließend auf Weiter.  
  
5.  Stellen Sie auf der Seite „Abonnententypen“ sicher, dass [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] oder höher ausgewählt ist, und klicken Sie anschließend auf **Weiter**.  
  
6.  Erweitern Sie auf der Seite Artikel den Knoten **Tabellen** und wählen Sie **SalesOrderHeader** und **SalesOrderDetail**aus. Erweitern Sie anschließend **Employee**, wählen Sie **EmployeeID** oder **LoginID**aus und klicken Sie auf **Weiter**.  
  
    > [!TIP]  
    >  Zusätzliche erforderliche Spalten werden automatisch ausgewählt. Wählen Sie beliebige automatisch ausgewählte Spalten aus, und lesen Sie unter der Liste **Zu veröffentlichende Objekte** die Erklärung, warum die Spalte erforderlich ist.  
  
7.  Klicken Sie auf der Seite Tabellenzeilen filtern auf **Hinzufügen** und klicken Sie anschließend auf **Filter hinzufügen**.  
  
8.  Wählen Sie im Dialogfeld **Filter hinzufügen** unter **Wählen Sie die zu filternde Tabelle aus** die Option **Employee (HumanResources)** aus. Klicken Sie auf die Spalte **LoginID** und anschließend auf den nach rechts weisenden Pfeil, um der WHERE-Klausel der Filterabfrage die Spalte hinzuzufügen, und ändern Sie die WHERE-Klausel wie folgt:  
  
    ```  
    WHERE [LoginID] = HOST_NAME()  
    ```  
  
9. Klicken Sie auf **Eine Zeile aus dieser Tabelle wird nur an ein Abonnement gesendet**und anschließend auf **OK**.  
  
10. Klicken Sie auf der Seite **Tabellenzeilen filtern** auf **Employee (Human Resources)**, klicken Sie auf **Hinzufügen** und anschließend auf **Join hinzufügen, um den ausgewählten Filter zu erweitern**.  
  
11. Wählen Sie im Dialogfeld **Join hinzufügen** unter **Verknüpfte Tabelle** die Tabelle **Sales.SalesOrderHeader**aus, klicken Sie auf **Joinanweisung manuell schreiben**und vervollständigen Sie die Joinanweisung wie folgt:  
  
    ```  
    ON Employee.EmployeeID = SalesOrderHeader.SalesPersonID  
    ```  
  
12. Wählen Sie unter **Geben Sie Joinoptionen an**die Option **Eindeutiger Schlüssel**aus und klicken Sie anschließend auf **OK**.  
  
13. Klicken Sie auf der Seite Tabellenzeilen filtern auf **SalesOrderHeader**, klicken Sie auf **Hinzufügen**und anschließend auf **Join hinzufügen, um den ausgewählten Filter zu erweitern**.  
  
14. Wählen Sie im Dialogfeld **Join hinzufügen** unter **Verknüpfte Tabelle** den Eintrag **Sales.SalesOrderDetail**aus.  
  
15. Klicken Sie auf **Joinanweisung manuell schreiben**.  
  
16. Wählen Sie in **Gefilterte Tabellenspalten**den Eintrag **BusinessEntityID**aus und klicken Sie anschließend auf die Pfeilschaltfläche, um den Spaltennamen in die Joinanweisung zu kopieren.  
  
17. Schließen Sie im Feld **Joinanweisung** die Joinanweisung wie folgt ab:  
  
    ```  
    ON Employee.BusinessEntityID = SalesOrderHeader.SalesPersonID  
    ```  
  
18. Wählen Sie unter **Geben Sie Joinoptionen an**die Option **Eindeutiger Schlüssel**aus und klicken Sie anschließend auf **OK**.  
  
19. Klicken Sie auf der Seite **Tabellenzeilen filtern** auf **SalesOrderHeader (Sales)**, klicken Sie auf **Hinzufügen**und anschließend auf **Join hinzufügen, um den ausgewählten Filter zu erweitern**.  
  
20. Wählen Sie im Dialogfeld **Join hinzufügen** unter **Verknüpfte Tabelle** die Tabelle **Sales.SalesOrderDetail**aus, klicken Sie auf **OK**und klicken Sie anschließend auf **Weiter**.  
  
21. Wählen Sie **Momentaufnahme sofort erstellen**aus, deaktivieren Sie **Ausführung des Momentaufnahme-Agents zu folgenden Zeitpunkten planen**und klicken Sie auf **Weiter**.  
  
22. Klicken Sie auf der Seite Agentsicherheit auf **Sicherheitseinstellungen**, geben Sie \< im Feld **Prozess Konto** _Machine_Name>_ **\ repl_snapshot** ein, geben Sie das Kennwort für dieses Konto an, und klicken Sie dann auf **OK**. Klicken Sie auf **Fertig stellen**.  
  
23. Geben Sie auf der Seite „Assistenten abschließen“ im Feld **Veröffentlichungsname** den Namen **AdvWorksSalesOrdersMerge** ein und klicken Sie auf **Fertig stellen**.  
  
24. Klicken Sie auf **Schließen**, nachdem die Veröffentlichung erstellt wurde.  
  
### <a name="to-view-the-status-of-snapshot-generation"></a>So zeigen Sie den Status der Momentaufnahmegenerierung an  
  
1.  Stellen Sie in eine Verbindung mit dem Verleger her [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] , erweitern Sie den Server Knoten, und erweitern Sie dann den Ordner **Replikation** .  
  
2.  Klicken Sie im Ordner Lokale Veröffentlichungen mit der rechten Maustaste auf **AdvWorksSalesOrdersMerge**und anschließend auf **Status des Momentaufnahme-Agents anzeigen**.  
  
3.  Der aktuelle Status des Auftrags des Momentaufnahme-Agents für die Veröffentlichung wird angezeigt. Stellen Sie sicher, dass der Momentaufnahmeauftrag erfolgreich war, bevor Sie zur nächsten Lektion wechseln.  
  
### <a name="to-add-the-merge-agent-login-to-the-pal"></a>So fügen Sie der PAL die Anmeldung des Merge-Agents hinzu  
  
1.  Stellen Sie in eine Verbindung mit dem Verleger her [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] , erweitern Sie den Server Knoten, und erweitern Sie dann den Ordner **Replikation** .  
  
2.  Klicken Sie im Ordner Lokale Veröffentlichungen mit der rechten Maustaste auf **AdvWorksSalesOrdersMerge**und anschließend auf **Eigenschaften**.  
  
     Das Dialogfeld **Veröffentlichungseigenschaften** wird angezeigt.  
  
3.  Wählen Sie die Seite **Veröffentlichungszugriffsliste** aus und klicken Sie auf **Hinzufügen**.  
  
4.  Wählen Sie im Dialogfeld „Veröffentlichungszugriff hinzufügen“ Folgendes aus: _<Computername>_**\repl_merge**. Klicken Sie anschließend auf **OK**. Klicken Sie auf **OK**.  
  
## <a name="next-steps"></a>Nächste Schritte  
 Sie haben die Mergeveröffentlichung erfolgreich erstellt. Als Nächstes abonnieren Sie diese Veröffentlichung. Siehe [Lektion 2: Erstellen eines Abonnements für die Mergeveröffentlichung](lesson-2-creating-a-subscription-to-the-merge-publication.md).  
  
## <a name="see-also"></a>Weitere Informationen  
 [Filtern von veröffentlichten Daten](publish/filter-published-data.md)   
 [Parametrisierte Zeilen Filter](merge/parameterized-filters-parameterized-row-filters.md)   
 [Definieren eines Artikels](publish/define-an-article.md)  
  
  
