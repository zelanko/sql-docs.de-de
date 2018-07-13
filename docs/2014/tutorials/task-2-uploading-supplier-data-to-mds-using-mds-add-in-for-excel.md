---
title: 'Aufgabe 2: Hochladen von Lieferantendaten in MDS mithilfe des MDS-Add-in für Excel | Microsoft-Dokumentation'
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
ms.topic: conceptual
ms.assetid: 598deb57-e0cc-4e0a-aeb1-94432c094c67
caps.latest.revision: 6
author: douglaslms
ms.author: douglasl
manager: craigg
ms.openlocfilehash: a296db8f933ceef5d3e17e2f3f3b8034cf8a0e2c
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/02/2018
ms.locfileid: "37272176"
---
# <a name="task-2-uploading-supplier-data-to-mds-using-mds-add-in-for-excel"></a>Aufgabe 2: Hochladen von Lieferantendaten in MDS mithilfe des MDS-Add-Ins für Excel
  In dieser Aufgabe veröffentlichen Sie die bereinigten Daten und Lieferantendaten zu **MDS** mithilfe der **MDS-Add-in für Excel**. Sie erstellen eine Entität mit dem Namen **Lieferanten** in die **Lieferanten** Modell, die Sie in der vorherigen Lektion erstellt haben. Die Entität weist ein Attribut für jede Spalte in der Excel-Datei auf. Die Attribute der Entität "Supplier" Code und den Namen entsprechen den **SupplierID** und **Lieferantenname** Spalten in Excel.  
  
1.  Open **bereinigt und abgeglichen Suppliers.xls** in **Excel**.  
  
2.  Drücken Sie **STRG + A** um alle Daten auszuwählen. Es ist **wichtig** , dass Sie die gesamten Daten im Arbeitsblatt auszuwählen.  
  
3.  Klicken Sie auf **Masterdaten** in der Menüleiste.  
  
4.  Klicken Sie auf **Entität erstellen** Schaltfläche auf dem Menüband.  
  
     ![Excel – Masterdaten (Registerkarte) - erstellen-Schaltfläche "Entität"](../../2014/tutorials/media/et-ulingsdtomdsusingmdsaddinforexcel-01.jpg "Excel – Masterdaten (Registerkarte) - Entity-Schaltfläche \"erstellen\"")  
  
5.  In **Verbindungen verwalten** Dialogfeld, wenn die Verbindung mit nicht angezeigt wird **lokalen MDS-Server** unter **vorhandene Verbindungen**, gehen Sie folgendermaßen vor:  
  
    1.  Wählen Sie **erstellen Sie eine neue Verbindung**, und klicken Sie auf **neu** Schaltfläche.  
  
    2.  In der **neue Verbindung hinzufügen** (Dialogfeld), Typ **Local MDS Server** für **Beschreibung** und **http://localhost/MDS** für  **MDS-Serveradresse**, und klicken Sie auf **OK** um das Dialogfeld zu schließen.  
  
6.  In **Verbindungen verwalten** wählen Sie im Dialogfeld **Local MDS Server** (http://localhost/MDS), klicken Sie auf **testen** zum Testen der Verbindung. Klicken Sie auf **OK** im Meldungsfeld auf.  
  
7.  Klicken Sie auf **Connect** zur Verbindung mit des MDS-Servers.  
  
8.  In der **Entität erstellen** wählen Sie im Dialogfeld **Lieferanten** für die **Modell**.  
  
9. Sicherstellen, dass **VERSION_1** ausgewählt ist **Version**.  
  
10. Geben Sie **Lieferanten** für **neuer Entitätsname**.  
  
11. Wählen Sie **SupplierID** für **die Spalte, die einen eindeutigen Bezeichner enthält** Feld (Sie können auch einen Code automatisch generieren). Sie sind im Wesentlichen eine Zuordnung der **SupplierID** -Spalte in **Excel** auf die **Code** Attribut **Lieferanten** Entität.  
  
12. Wählen Sie **Lieferantenname** für **die Spalte mit Namen** Feld. Sie sind im Wesentlichen eine Zuordnung der **Supplier Name** -Spalte in **Excel** auf die **Namen** Attribut der **Lieferanten** Entität. Die **Code** und **Namen** Attribute sind obligatorische Attribute für eine Entität in MDS.  
  
     ![Erstellen Sie im Dialogfeld Entität](../../2014/tutorials/media/et-ulingsdtomdsusingmdsaddinforexcel-02.jpg "erstellen Entität (Dialogfeld)")  
  
13. Klicken Sie auf **OK** um die Entität in MDS zu erstellen, veröffentlichen Sie die Masterdaten in der Entität aus, und schließen **Entität erstellen** Dialogfeld.  
  
14. Nun sollte ein neues Arbeitsblatt mit dem Titel **Lieferanten**, dies ist der Name der Entität, in Ihrer Excel-Arbeitsblatt hinzugefügt, und Sie sollte am oberen Rand des Arbeitsblatts angezeigt werden, dass das Arbeitsblatt mit dem MDS-Server verbunden ist. Beachten Sie, dass das ursprüngliche Arbeitsblatt (mit dem Titel **Sheet1**) noch vorhanden ist.  
  
     ![Excel – Lieferanten und Tabelle1 Registerkarten](../../2014/tutorials/media/et-ulingsdtomdsusingmdsaddinforexcel-03.jpg "Excel – Lieferanten und Tabelle1-Registerkarten")  
  
     ![Excel – anzeigen von Details zur MDS-Verbindung](../../2014/tutorials/media/et-ulingsdtomdsusingmdsaddinforexcel-04.jpg "Excel – anzeigen von Details zur MDS-Verbindung")  
  
15. Behalten Sie **Excel** zu öffnen.  
  
## <a name="next-task"></a>Nächste Aufgabe  
 [Aufgabe 3: Überprüfen der Daten im Master Data Manager](../../2014/tutorials/task-3-verifying-the-data-in-master-data-manager.md)  
  
  
