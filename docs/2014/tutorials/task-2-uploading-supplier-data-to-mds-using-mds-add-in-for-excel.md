---
title: 'Aufgabe 2: Hochladen von Lieferantendaten in MDS mithilfe des MDS-Add-in für Excel | Microsoft Docs'
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
ms.assetid: 598deb57-e0cc-4e0a-aeb1-94432c094c67
caps.latest.revision: 6
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.openlocfilehash: 1831fc9ea79027e24d752d05e3b50d3a58d6e06f
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/19/2018
ms.locfileid: "36048643"
---
# <a name="task-2-uploading-supplier-data-to-mds-using-mds-add-in-for-excel"></a>Aufgabe 2: Hochladen von Lieferantendaten in MDS mithilfe des MDS-Add-Ins für Excel
  In dieser Aufgabe veröffentlichen Sie die bereinigten Daten und Lieferantendaten zu **MDS** mithilfe der **MDS-Add-in für Excel**. Sie erstellen eine Entität namens **Lieferanten** in der **Lieferanten** Modell, die Sie in der vorherigen Lektion erstellt haben. Die Entität weist ein Attribut für jede Spalte in der Excel-Datei auf. Die Attribute Code und den Namen der Entität "Supplier" entsprechen die **SupplierID** und **Lieferantenname** Spalten in Excel.  
  
1.  Open **bereinigt und abgeglichen Suppliers.xls** in **Excel**.  
  
2.  Drücken Sie **STRG + A** um alle Daten auszuwählen. Es ist **wichtige** , dass Sie die gesamten Daten im Arbeitsblatt auszuwählen.  
  
3.  Klicken Sie auf **Masterdaten** in der Menüleiste.  
  
4.  Klicken Sie auf **Entität erstellen** Schaltfläche auf dem Menüband.  
  
     ![Excel – Masterdaten (Registerkarte) -, Entität-Schaltfläche "erstellen"](../../2014/tutorials/media/et-ulingsdtomdsusingmdsaddinforexcel-01.jpg "Excel – Masterdaten (Registerkarte) -, Entität-Schaltfläche \"erstellen\"")  
  
5.  In **Verbindungen verwalten** (Dialogfeld), wenn Sie nicht angezeigt, dass die Verbindung mit **lokale MDS-Server** unter **vorhandene Verbindungen**, gehen Sie folgendermaßen vor:  
  
    1.  Wählen Sie **erstellen Sie eine neue Verbindung**, und klicken Sie auf **neu** Schaltfläche.  
  
    2.  In der **neue Verbindung hinzufügen** Geben Sie im Dialogfeld **Local MDS Server** für **Beschreibung** und **http://localhost/MDS** für  **MDS-Serveradresse**, und klicken Sie auf **OK** um das Dialogfeld zu schließen.  
  
6.  In **Verbindungen verwalten** wählen Sie im Dialogfeld **Local MDS Server** (http://localhost/MDS), klicken Sie auf **testen** zum Testen der Verbindung. Klicken Sie auf **OK** im Meldungsfeld.  
  
7.  Klicken Sie auf **verbinden** zur Verbindung mit des MDS-Servers.  
  
8.  In der **Entität erstellen** wählen Sie im Dialogfeld **Lieferanten** für die **Modell**.  
  
9. Sicherstellen, dass **VERSION_1** ausgewählt ist, für die **Version**.  
  
10. Geben Sie **Lieferanten** für **neuer Entitätsname**.  
  
11. Wählen Sie **SupplierID** für **die Spalte, die einen eindeutigen Bezeichner enthält** Feld (Sie können auch einen Code automatisch generieren). Sie sind im Wesentlichen eine Zuordnung der **SupplierID** Spalte **Excel** auf die **Code** Attribut des **Lieferanten** Entität.  
  
12. Wählen Sie **Lieferantenname** für **die Spalte mit Namen** Feld. Sie sind im Wesentlichen eine Zuordnung der **Lieferantenname** Spalte in **Excel** auf die **Namen** Attribut des der **Lieferanten** Entität. Die **Code** und **Namen** Attribute sind obligatorische Attribute für eine Entität in MDS.  
  
     ![Erstellen Sie im Dialogfeld Entität](../../2014/tutorials/media/et-ulingsdtomdsusingmdsaddinforexcel-02.jpg "erstellen Entität (Dialogfeld)")  
  
13. Klicken Sie auf **OK** um die Entität in MDS zu erstellen, veröffentlichen Sie die Masterdaten für die Entität, und schließen **Entität erstellen** (Dialogfeld).  
  
14. Jetzt sehen Sie ein neues Arbeitsblatt mit dem Titel **Lieferanten**, dies ist der Name der Entität, die Excel-Arbeitsblatt hinzugefügt und am oberen Rand des Arbeitsblatts, sollten Sie sehen, dass das Arbeitsblatt mit dem MDS-Server verbunden ist. Beachten Sie, dass das ursprüngliche Arbeitsblatt (mit dem Titel **"Sheet1"**) noch vorhanden ist.  
  
     ![Excel – "Sheet1" Registerkarten "und" Supplier](../../2014/tutorials/media/et-ulingsdtomdsusingmdsaddinforexcel-03.jpg "Excel - Supplier \"und\" Registerkarten \"Sheet1\"")  
  
     ![Excel – mit MDS Verbindungsdetails](../../2014/tutorials/media/et-ulingsdtomdsusingmdsaddinforexcel-04.jpg "Excel – Verbindungsdetails MDS anzeigen")  
  
15. Behalten Sie **Excel** öffnen.  
  
## <a name="next-task"></a>Nächste Aufgabe  
 [Aufgabe 3: Überprüfen der Daten im Master Data Manager](../../2014/tutorials/task-3-verifying-the-data-in-master-data-manager.md)  
  
  