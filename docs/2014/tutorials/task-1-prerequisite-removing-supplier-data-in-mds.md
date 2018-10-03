---
title: 'Aufgabe 1 (Voraussetzung): Entfernen von Lieferantendaten in MDS | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- data-quality-services
- integration-services
- master-data-services
ms.topic: conceptual
ms.assetid: 6f0a4287-7fd4-4f18-b7e4-a5191a9d4a3c
author: douglaslms
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 74862c1db4ad3c34afc759ba94f36ba5fb896e7e
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/02/2018
ms.locfileid: "48227700"
---
# <a name="task-1-prerequisite-removing-supplier-data-in-mds"></a>Aufgabe 1 (Voraussetzung): Entfernen von Lieferantendaten in MDS
  In dieser Aufgabe entfernen Sie die Lieferantendaten, die in MDS gespeichert werden. Sie hochgeladen haben, die Daten manuell mit **MDS-Excel-Add-in** in der vorherigen Lektion. Das SSIS-Paket, das Sie in dieser Lektion erstellen, lädt die Daten für Sie automatisch in MDS hoch. Bevor Sie das SSIS-Paket testen, müssen Sie daher die Lieferantendaten aus MDS entfernen, die abgeleitete Hierarchie entfernen, die Entitäten "Supplier" und "State" entfernen und die Entität "Supplier" ohne Daten erstellen.  
  
1.  Starten Sie **Master Data Manager** durch Navigieren zu **http://localhost/MDS** oder die Website und die angegebene eingabeanwendung beim Konfigurieren von MDS. Weiterhin die **Master Data Manager** öffnen, klicken Sie auf **SQL Server 2012 Master Data Services** oben, um zum Wechseln der **auf der Startseite**.  
  
2.  Klicken Sie auf **Systemverwaltung** in die **Verwaltungsaufgaben** Abschnitt.  
  
3.  Zeigen Sie auf den **verwalten** im Menü, und klicken Sie auf **abgeleitete Hierarchien**. Sie müssen die abgeleitete Hierarchie löschen **SuppliersInState** vor dem Löschen von Entitäten in der **Lieferanten** Modell.  
  
4.  Wählen Sie **SuppliersInState** aus der **abgeleitete Hierarchie** aus, und klicken Sie auf **X (löschen)** auf der Symbolleiste.  
  
5.  Klicken Sie auf **OK** , Löschvorgang zu bestätigen.  
  
6.  Zeigen Sie auf den **verwalten** im Menü, und klicken Sie auf **Entitäten**.  
  
7.  Klicken Sie auf **Lieferanten** , und klicken Sie auf **löschen (X)** Schaltfläche auf der Symbolleiste, um die Entität zu löschen. Klicken Sie auf **OK** in den Meldungsfeldern.  
  
8.  Wiederholen Sie den vorherigen Schritt löschen **Zustand** Entität.  
  
9. Schließen Sie nicht **Master Data Manager**.  
  
10. Wechseln Sie zu der Excel-Fenster, **Cleansed and Matched Suppliers.xls** Datei geöffnet. Wechseln Sie zu der **Sheet1** unten auf der Registerkarte.  
  
11. Wählen Sie nur die **erste Zeile mit Headern**. Wählen Sie keine andere Zeile aus. Sie möchten Entitäten auf der Grundlage der Excel-Spalten erstellen, aber keine Daten hochladen. Daher wählen Sie nur die erste Zeile mit den Headern aus.  
  
12. Klicken Sie auf **Masterdaten** in der Menüleiste.  
  
13. Klicken Sie auf **Entität erstellen** aus dem Menüband.  
  
14. In **Verbindungen verwalten** Dialogfeld, wenn die Verbindung mit nicht angezeigt wird **lokalen MDS-Server** unter **vorhandene Verbindungen**, gehen Sie folgendermaßen vor:  
  
    1.  Wählen Sie **erstellen Sie eine neue Verbindung**, und klicken Sie auf **neu** Schaltfläche.  
  
    2.  Geben Sie im Dialogfeld "neue Verbindung hinzufügen" die **Local MDS Server** für **Beschreibung** und **http://localhost/MDS** für **MDS-Serveradresse**, und klicken Sie auf **OK** um das Dialogfeld zu schließen.  
  
15. In **Verbindungen verwalten** wählen Sie im Dialogfeld **Local MDS Server** (http://localhost/MDS), klicken Sie auf **testen** zum Testen der Verbindung. Klicken Sie auf **OK** im Meldungsfeld auf.  
  
16. Klicken Sie auf **Connect** zum Herstellen eine Verbindung mit dem MDS-Server.  
  
17. In der **Entität erstellen** Dialogfeld Feld, gehen Sie folgendermaßen vor:  
  
    1.  Überprüfen Sie, ob **Bereich** nastaven NA hodnotu **$1: $1**.  
  
    2.  Wählen Sie **Lieferanten** für **Modell**.  
  
    3.  Wählen Sie **VERSION_1** für **Version**.  
  
    4.  Typ **Lieferanten** für **neuer Entitätsname**.  
  
    5.  Wählen Sie **SupplierID** für **Code**.  
  
    6.  Wählen Sie **Lieferantenname** für **Namen**.  
  
    7.  Klicken Sie auf **OK** zum Erstellen der Entität, und schließen Sie das Dialogfeld.  
  
18. Schließen **Excel** und **speichern nicht** der Datei.  
  
19. In **Master Data Manager**, aktualisieren Sie den Internet-Browser, und überprüfen Sie, ob **Lieferanten** Entität wird in der Liste angezeigt.  
  
20. Wechseln Sie zu der **Startseite** durch Klicken auf **SQL Server 2012 Master Data Services** oben.  
  
21. Überprüfen Sie, ob **Lieferanten** Modell ausgewählt ist **Modell** und **VERSION_1** ausgewählt ist **Version**.  
  
22. Klicken Sie auf **Explorer**. Beachten Sie, dass die **Lieferanten** Entität mit den Attributen wird erstellt, mit **keine Werte**.  
  
## <a name="next-step"></a>Nächster Schritt  
 [Aufgabe 2 &#40;Optional&#41;: Erstellen einer MDS-Abonnementsicht mithilfe von Master Data Manager](../../2014/tutorials/task-2-optional-creating-a-mds-subscription-view-using-master-data-manager.md)  
  
  
