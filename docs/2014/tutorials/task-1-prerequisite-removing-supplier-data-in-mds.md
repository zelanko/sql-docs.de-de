---
title: 'Aufgabe 1 (Voraussetzung): Entfernen von Lieferantendaten in MDS | Microsoft Docs'
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
ms.assetid: 6f0a4287-7fd4-4f18-b7e4-a5191a9d4a3c
caps.latest.revision: 6
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.openlocfilehash: 1189c064ec1a55da1c77837d1533855266ed4274
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/19/2018
ms.locfileid: "36163042"
---
# <a name="task-1-prerequisite-removing-supplier-data-in-mds"></a>Aufgabe 1 (Voraussetzung): Entfernen von Lieferantendaten in MDS
  In dieser Aufgabe entfernen Sie die Lieferantendaten, die in MDS gespeichert werden. Die Daten manuell mit hochgeladenen **MDS-Excel-Add-in** in der vorherigen Lektion. Das SSIS-Paket, das Sie in dieser Lektion erstellen, lädt die Daten für Sie automatisch in MDS hoch. Bevor Sie das SSIS-Paket testen, müssen Sie daher die Lieferantendaten aus MDS entfernen, die abgeleitete Hierarchie entfernen, die Entitäten "Supplier" und "State" entfernen und die Entität "Supplier" ohne Daten erstellen.  
  
1.  Starten Sie **Master Data Manager** empfängerrollenbildschirm **http://localhost/MDS** oder konfigurieren Sie die Website und die Anwendung, die Sie, wann angegeben MDS. Weiterhin die **Master Data Manager** öffnen, klicken Sie auf **SQL Server 2012 Master Data Services** oben, um zum Wechseln der **Startseite**.  
  
2.  Klicken Sie auf **Systemverwaltung** in der **Verwaltungsaufgaben** Abschnitt.  
  
3.  Zeigen Sie mit der Maus auf **verwalten** auf das Menü, und klicken Sie auf **abgeleitete Hierarchien**. Sie müssen die abgeleitete Hierarchie löschen **SuppliersInState** vor dem Löschen von Entitäten in der **Lieferanten** Modell.  
  
4.  Wählen Sie **SuppliersInState** aus der **abgeleitete Hierarchie** aus, und klicken Sie auf **X (löschen)** auf der Symbolleiste.  
  
5.  Klicken Sie auf **OK** zu bestätigen.  
  
6.  Zeigen Sie mit der Maus auf **verwalten** auf das Menü, und klicken Sie auf **Entitäten**.  
  
7.  Klicken Sie auf **Lieferanten** , und klicken Sie auf **löschen (X)** Schaltfläche auf der Symbolleiste, um die Entität zu löschen. Klicken Sie auf **OK** in den Meldungsfeldern.  
  
8.  Wiederholen Sie den vorherigen Schritt gelöscht **Zustand** Entität.  
  
9. Schließen Sie nicht **Master Data Manager**.  
  
10. Wechseln Sie zu der Excel-Fenster **Cleansed and Matched Suppliers.xls** Datei geöffnet. Wechseln Sie zu der **"Sheet1"** Registerkarte unten.  
  
11. Wählen Sie nur die **zuerst Zeile mit Headern**. Wählen Sie keine andere Zeile aus. Sie möchten Entitäten auf der Grundlage der Excel-Spalten erstellen, aber keine Daten hochladen. Daher wählen Sie nur die erste Zeile mit den Headern aus.  
  
12. Klicken Sie auf **Masterdaten** in der Menüleiste.  
  
13. Klicken Sie auf **Entität erstellen** aus dem Menüband.  
  
14. In **Verbindungen verwalten** (Dialogfeld), wenn Sie nicht angezeigt, dass die Verbindung mit **lokale MDS-Server** unter **vorhandene Verbindungen**, gehen Sie folgendermaßen vor:  
  
    1.  Wählen Sie **erstellen Sie eine neue Verbindung**, und klicken Sie auf **neu** Schaltfläche.  
  
    2.  Geben Sie im Dialogfeld "neue Verbindung hinzufügen" **Local MDS Server** für **Beschreibung** und **http://localhost/MDS** für **MDS-Serveradresse**, und klicken Sie auf **OK** um das Dialogfeld zu schließen.  
  
15. In **Verbindungen verwalten** wählen Sie im Dialogfeld **Local MDS Server** (http://localhost/MDS), klicken Sie auf **testen** zum Testen der Verbindung. Klicken Sie auf **OK** im Meldungsfeld.  
  
16. Klicken Sie auf **verbinden** zum Herstellen einer Verbindung mit dem MDS-Server.  
  
17. In der **Entität erstellen** Dialogfeld Feld, gehen Sie folgendermaßen vor:  
  
    1.  Überprüfen Sie, ob **Bereich** festgelegt ist, um **$1: $1**.  
  
    2.  Wählen Sie **Lieferanten** für **Modell**.  
  
    3.  Wählen Sie **VERSION_1** für **Version**.  
  
    4.  Typ **Lieferanten** für **neuer Entitätsname**.  
  
    5.  Wählen Sie **SupplierID** für **Code**.  
  
    6.  Wählen Sie **Lieferantenname** für **Namen**.  
  
    7.  Klicken Sie auf **OK** die Entität erstellen und das Dialogfeld zu schließen.  
  
18. Schließen **Excel** und **nicht speichern** der Datei.  
  
19. In **Master Data Manager**, aktualisieren Sie den Internet-Browser, und überprüfen Sie, ob **Lieferanten** Entität in der Liste angezeigt wird.  
  
20. Wechseln Sie zu der **Startseite** durch Klicken auf **SQL Server 2012 Master Data Services** oben.  
  
21. Überprüfen Sie, ob **Lieferanten** Modell ausgewählt ist **Modell** und **VERSION_1** ausgewählt ist, für die **Version**.  
  
22. Klicken Sie auf **Explorer**. Beachten Sie, dass die **Lieferanten** Entität mit allen Attributen mit erstellt **keine Werte**.  
  
## <a name="next-step"></a>Nächster Schritt  
 [Aufgabe 2 &#40;Optional&#41;: Erstellen einer MDS-Abonnementsicht mithilfe von Master Data Manager](../../2014/tutorials/task-2-optional-creating-a-mds-subscription-view-using-master-data-manager.md)  
  
  