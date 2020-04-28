---
title: 'Aufgabe 1 (Voraussetzung): Entfernen von Lieferantendaten in MDS | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: data-quality-services
ms.topic: conceptual
ms.assetid: 6f0a4287-7fd4-4f18-b7e4-a5191a9d4a3c
author: lrtoyou1223
ms.author: lle
manager: craigg
ms.openlocfilehash: 0290f033be47bec61e9ccce8465892d8cc98608c
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/27/2020
ms.locfileid: "81484630"
---
# <a name="task-1-prerequisite-removing-supplier-data-in-mds"></a>Aufgabe 1 (Voraussetzung): Entfernen von Lieferantendaten aus MDS
  In dieser Aufgabe entfernen Sie die Lieferantendaten, die in MDS gespeichert werden. Sie haben die Daten in der vorherigen Lektion manuell mithilfe des **MDS-Excel-Add-ins** hochgeladen. Das SSIS-Paket, das Sie in dieser Lektion erstellen, lädt die Daten für Sie automatisch in MDS hoch. Bevor Sie das SSIS-Paket testen, müssen Sie daher die Lieferantendaten aus MDS entfernen, die abgeleitete Hierarchie entfernen, die Entitäten "Supplier" und "State" entfernen und die Entität "Supplier" ohne Daten erstellen.  
  
1.  Starten Sie **Master Data Manager** , indem `http://localhost/MDS` Sie zu oder der Website und Anwendung navigieren, die Sie beim Konfigurieren von MDS angegeben haben. Wenn Sie die **Master Data Manager** geöffnet gehalten haben, klicken Sie oben auf **SQL Server 2012 Master Data Services** , um zur **Startseite**zu wechseln.  
  
2.  Klicken Sie im Abschnitt **administrative Aufgaben** auf **System Verwaltung** .  
  
3.  Zeigen Sie mit der Maus auf **Verwalten** im Menü, und klicken Sie auf **abgeleitete Hierarchien**. Sie müssen die abgeleitete Hierarchie **suppliersinstate** löschen, bevor Sie die Entitäten im Modell **Suppliers** löschen.  
  
4.  Wählen Sie in der Liste **abgeleitete Hierarchie** den Eintrag **suppliersinstate** aus, und klicken Sie auf der Symbolleiste auf die Schaltfläche **X**  
  
5.  Klicken Sie zum Bestätigen des Löschvorgangs auf **OK** .  
  
6.  Zeigen Sie mit der Maus auf **Verwalten** im Menü, und klicken Sie auf **Entitäten**.  
  
7.  Klicken **Sie in** der Symbolleiste auf die Schaltfläche **Löschen (X)** , um die Entität zu löschen. Klicken Sie in den Meldungs Feldern auf **OK** .  
  
8.  Wiederholen Sie den vorherigen Schritt zum Löschen der **Zustands** Entität.  
  
9. Schließen Sie **Master Data Manager**nicht.  
  
10. Wechseln Sie zum Excel-Fenster, das bereinigt wurde und die Datei **Suppliers. xls** geöffnet ist. Wechseln Sie im unteren Bereich zur Registerkarte **Sheet1** .  
  
11. Wählen Sie nur die **erste Zeile mit Headern**aus. Wählen Sie keine andere Zeile aus. Sie möchten die Entitäten auf der Grundlage der Excel-Spalten erstellen, aber keine Daten hochladen. Daher wählen Sie nur die erste Zeile mit den Headern aus.  
  
12. Klicken Sie in der Menüleiste auf **Master Daten** .  
  
13. Klicken Sie im Menüband auf **Entität erstellen** .  
  
14. Wenn im Dialogfeld **Verbindungen verwalten** die Verbindung mit dem **lokalen MDS-Server** unter **vorhandene Verbindungen**nicht angezeigt wird, gehen Sie wie folgt vor:  
  
    1.  Wählen Sie **neue Verbindung erstellen**aus, und klicken Sie auf die Schaltfläche **neu** .  
  
    2.  Geben Sie im Dialogfeld neue Verbindung hinzufügen den **Namen local MDS Server** for **Description** und **http:\//localhost/MDS** für die **MDS-Server Adresse**ein, und klicken Sie auf **OK** , um das Dialogfeld zu schließen.  
  
15. Wählen Sie im Dialogfeld **Verbindungen verwalten** die Option **lokaler MDS-Server** (`http://localhost/MDS`) aus, klicken Sie auf **Testen** , um die Verbindung zu testen. Klicken Sie im Meldungs Feld auf **OK** .  
  
16. Klicken Sie auf **verbinden** , um eine Verbindung mit dem MDS-Server herzustellen.  
  
17. Führen Sie im Dialogfeld **Entität erstellen** die folgenden Schritte aus:  
  
    1.  Vergewissern Sie sich, dass der **Bereich** auf **$1: $1**festgelegt ist.  
  
    2.  Wählen Sie **Suppliers** für **Model**aus.  
  
    3.  Wählen Sie **VERSION_1** für die **Version**aus.  
  
    4.  Geben Sie **Supplier** als **neuen Entitäts Namen**ein.  
  
    5.  Wählen Sie **SupplierID** für **Code**aus.  
  
    6.  Wählen Sie **Lieferanten Name** für **Name**aus.  
  
    7.  Klicken Sie auf **OK** , um die Entität zu erstellen und das Dialogfeld zu schließen.  
  
18. Schließen Sie **Excel** , und **Speichern Sie** die Datei nicht.  
  
19. Aktualisieren Sie in **Master Data Manager**den Internetbrowser, und vergewissern Sie sich, dass die Entität **Supplier** in der Liste angezeigt wird.  
  
20. Wechseln Sie zur **Startseite** , indem Sie oben auf **SQL Server 2012 Master Data Services** klicken.  
  
21. Vergewissern Sie sich, dass das Modell **Suppliers** als **Modell** ausgewählt ist und **VERSION_1** für die **Version**ausgewählt ist.  
  
22. Klicken Sie auf **Explorer**. Beachten Sie, dass die Entität " **Supplier** " mit allen Attributen **ohne Werte**erstellt wird.  
  
## <a name="next-step"></a>Nächster Schritt  
 [Aufgabe 2 &#40;optionale&#41;: Erstellen einer MDS-Abonnement Sicht mithilfe Master Data Manager](../../2014/tutorials/task-2-optional-creating-a-mds-subscription-view-using-master-data-manager.md)  
  
  
