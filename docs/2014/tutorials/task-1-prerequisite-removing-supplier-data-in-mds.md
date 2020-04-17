---
title: 'Aufgabe 1 (Voraussetzung): Entfernen von Lieferantendaten in MDB | Microsoft Docs'
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
ms.sourcegitcommit: b2cc3f213042813af803ced37901c5c9d8016c24
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2020
ms.locfileid: "81484630"
---
# <a name="task-1-prerequisite-removing-supplier-data-in-mds"></a>Aufgabe 1 (Voraussetzung): Entfernen von Lieferantendaten aus MDS
  In dieser Aufgabe entfernen Sie die Lieferantendaten, die in MDS gespeichert werden. Sie haben die Daten manuell mit **dem MDS Excel Add-In** in der vorherigen Lektion hochgeladen. Das SSIS-Paket, das Sie in dieser Lektion erstellen, lädt die Daten für Sie automatisch in MDS hoch. Bevor Sie das SSIS-Paket testen, müssen Sie daher die Lieferantendaten aus MDS entfernen, die abgeleitete Hierarchie entfernen, die Entitäten "Supplier" und "State" entfernen und die Entität "Supplier" ohne Daten erstellen.  
  
1.  Starten Sie **den Stammdaten-Manager,** indem Sie zu oder zu `http://localhost/MDS` der Website und Anwendung navigieren, die Sie beim Konfigurieren von MDS angegeben haben. Wenn Sie den **Master Data Manager** geöffnet gehalten haben, klicken Sie oben auf SQL Server **2012 Master Data Services,** um zur **Startseite**zu wechseln.  
  
2.  Klicken Sie im Abschnitt **Verwaltungsaufgaben** auf **Systemadministration.**  
  
3.  Bewegen Sie den Mauszeiger über **Verwalten** im Menü und klicken Sie auf **Abgeleitete Hierarchien**. Sie müssen die abgeleitete Hierarchie **SuppliersInState** löschen, bevor Sie die Entitäten im **Lieferantenmodell** löschen.  
  
4.  Wählen Sie **SuppliersInState** aus der Liste **Abgeleitete Hierarchie** aus, und klicken Sie auf der Symbolleiste auf die Schaltfläche **X (Löschen).**  
  
5.  Klicken Sie auf **OK,** um den Löschvorgang zu bestätigen.  
  
6.  Bewegen Sie den Mauszeiger über **Verwalten** im Menü, und klicken Sie auf **Entitäten**.  
  
7.  Klicken Sie auf **Lieferant,** und klicken Sie auf der Symbolleiste auf Löschen **(X),** um die Entität zu löschen. Klicken Sie auf **OK** in den Meldungsfeldern.  
  
8.  Wiederholen Sie den vorherigen Schritt, um **die Statusentität** zu löschen.  
  
9. Master Data **Manager**nicht schließen .  
  
10. Wechseln Sie zum Excel-Fenster, in dem die Datei **Cleansed and Matched Suppliers.xls** geöffnet ist. Wechseln Sie zur Registerkarte **Sheet1** unten.  
  
11. Wählen Sie nur die **erste Zeile mit Kopfzeilen**aus. Wählen Sie keine andere Zeile aus. Sie möchten die Entitäten basierend auf den Excel-Spalten erstellen, aber keine Daten hochladen. Daher wählen Sie nur die erste Zeile mit den Headern aus.  
  
12. Klicken Sie in der Menüleiste auf **Stammdaten.**  
  
13. Klicken Sie im Menüband auf **Entität erstellen.**  
  
14. Wenn im Dialogfeld **Verbindungen verwalten** die Verbindung zum **lokalen MDS-Server** unter **Vorhandene Verbindungen**nicht angezeigt wird, gehen Sie wie folgt vor:  
  
    1.  Wählen Sie **Neue Verbindung erstellen**aus, und klicken Sie auf **Neu.**  
  
    2.  Geben Sie im Dialogfeld Neue Verbindung hinzufügen ein, geben Sie **Local MDS Server** for **Description** und **http:\//localhost/MDS** für **MDS-Serveradresse**ein, und klicken Sie auf **OK,** um das Dialogfeld zu schließen.  
  
15. Wählen Sie im Dialogfeld **Verbindungen verwalten** die Option **Lokaler MDS-Server** (`http://localhost/MDS`), auf **Testen** klicken, um die Verbindung zu testen. Klicken Sie im Meldungsfeld auf **OK.**  
  
16. Klicken Sie auf **Verbinden,** um eine Verbindung zum MDS-Server herzustellen.  
  
17. Führen Sie im Dialogfeld **Entität erstellen** die folgenden Schritte aus:  
  
    1.  Vergewissern Sie sich, dass **der Bereich** auf **1:1**festgelegt ist.  
  
    2.  Wählen Sie **Lieferanten** für **Modell**aus.  
  
    3.  Wählen Sie **VERSION_1** für **Version**.  
  
    4.  Geben Sie **Supplier** für **neuen Entitätsnamen ein.**  
  
    5.  Wählen Sie **SupplierID** für **Code**.  
  
    6.  Wählen Sie **Lieferantenname** für **Name**aus.  
  
    7.  Klicken Sie auf **OK,** um die Entität zu erstellen und das Dialogfeld zu schließen.  
  
18. Schließen Sie **Excel,** und speichern Sie die Datei **nicht.**  
  
19. Aktualisieren Sie in **Master Data Manager**den Internetbrowser, und bestätigen Sie, dass die **Supplier-Entität** in der Liste angezeigt wird.  
  
20. Wechseln Sie zur **Startseite,** indem Sie oben auf **SQL Server 2012 Master Data Services** klicken.  
  
21. Vergewissern Sie sich, dass **das Lieferantenmodell** für **Modell** ausgewählt ist und **VERSION_1** für **Version**ausgewählt ist.  
  
22. Klicken Sie auf **Explorer**. Beachten Sie, dass die **Supplier-Entität** mit allen Attributen **ohne Werte**erstellt wird.  
  
## <a name="next-step"></a>Nächster Schritt  
 [Aufgabe 2 &#40;Optionaler&#41;: Erstellen einer MDS-Abonnementansicht mit dem Stammdaten-Manager](../../2014/tutorials/task-2-optional-creating-a-mds-subscription-view-using-master-data-manager.md)  
  
  
