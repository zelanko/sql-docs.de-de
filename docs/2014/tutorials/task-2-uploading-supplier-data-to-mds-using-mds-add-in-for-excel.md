---
title: 'Aufgabe 2: Hochladen von Lieferantendaten in MDS mithilfe des MDS-Add-Ins für Excel | Microsoft Docs'
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: data-quality-services
ms.topic: conceptual
ms.assetid: 598deb57-e0cc-4e0a-aeb1-94432c094c67
author: lrtoyou1223
ms.author: lle
manager: craigg
ms.openlocfilehash: 4e3cd4cecd88bcad83c6e9f2a59ecd5f225fb02a
ms.sourcegitcommit: b2cc3f213042813af803ced37901c5c9d8016c24
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2020
ms.locfileid: "81487694"
---
# <a name="task-2-uploading-supplier-data-to-mds-using-mds-add-in-for-excel"></a>Aufgabe 2: Hochladen von Lieferantendaten in MDS mithilfe des MDS-Add-Ins für Excel
  In dieser Aufgabe veröffentlichen Sie die bereinigten und Lieferantendaten in **MDS** mit dem **MDS-Add-In für Excel**. Sie erstellen eine Entität mit dem Namen **Lieferant** im **Lieferantenmodell,** das Sie in der vorherigen Lektion erstellt haben. Die Entität weist ein Attribut für jede Spalte in der Excel-Datei auf. Die Attribute Code und Name der Lieferantenentität entsprechen den Spalten **SupplierID** und **Supplier Name** in Excel.  
  
1.  Öffnen **Sie Cleansed and Matched Suppliers.xls** in **Excel**.  
  
2.  Drücken Sie **STRG+A,** um ganze Daten auszuwählen. Es ist **wichtig,** dass Sie die gesamten Daten in der Kalkulationstabelle auswählen.  
  
3.  Klicken Sie in der Menüleiste auf **Stammdaten.**  
  
4.  Klicken Sie auf der Multifunktionsleiste auf die Schaltfläche **Entität erstellen.**  
  
     ![Excel – Masterdaten (Registerkarte) – Entität erstellen (Schaltfläche)](../../2014/tutorials/media/et-ulingsdtomdsusingmdsaddinforexcel-01.jpg "Excel – Masterdaten (Registerkarte) – Entität erstellen (Schaltfläche)")  
  
5.  Wenn im Dialogfeld **Verbindungen verwalten** die Verbindung zum **lokalen MDS-Server** unter **Vorhandene Verbindungen**nicht angezeigt wird, gehen Sie wie folgt vor:  
  
    1.  Wählen Sie **Neue Verbindung erstellen**aus, und klicken Sie auf **Neu.**  
  
    2.  Geben Sie im Dialogfeld **Neue Verbindung hinzufügen** ein, geben Sie Local **MDS Server** for **Description** und **http:\//localhost/MDS** für **MDS-Serveradresse**ein, und klicken Sie auf **OK,** um das Dialogfeld zu schließen.  
  
6.  Wählen Sie im Dialogfeld **Verbindungen verwalten** die Option **Lokaler MDS-Server** (`http://localhost/MDS`), auf **Testen** klicken, um die Verbindung zu testen. Klicken Sie im Meldungsfeld auf **OK.**  
  
7.  Klicken Sie auf **Verbinden,** um eine Verbindung mit dem MDS-Server herzustellen.  
  
8.  Wählen Sie im Dialogfeld **Entität erstellen** die Option **Lieferanten** für das **Modell**aus.  
  
9. Stellen Sie sicher, dass **VERSION_1** für **Version**ausgewählt ist.  
  
10. Geben Sie **Supplier** for **New entity name ein.**  
  
11. Wählen Sie **SupplierID** für **die Spalte aus, die ein eindeutiges Bezeichnerfeld enthält** (Sie können auch automatisch einen Code generieren). Sie ordnen die **SupplierID-Spalte** in **Excel** im Wesentlichen dem **Codeattribut** der **Supplier-Entität** zu.  
  
12. Wählen Sie **Lieferantenname** für **die Spalte aus, die das** Feld Namen enthält. Sie ordnen die Spalte **Lieferantenname** in **Excel** im Wesentlichen dem **Name-Attribut** der **Supplier-Entität** zu. Die **Attribute Code** und **Name** sind obligatorische Attribute für eine Entität in MDS.  
  
     ![Entität erstellen (Dialogfeld)](../../2014/tutorials/media/et-ulingsdtomdsusingmdsaddinforexcel-02.jpg "Entität erstellen (Dialogfeld)")  
  
13. Klicken Sie auf **OK,** um die Entität auf MDS zu erstellen, die Stammdaten in der Entität zu veröffentlichen und das Dialogfeld **Entität erstellen zu** schließen.  
  
14. Nun sollte ein neues Blatt mit dem Titel **Lieferant**, der der Name der Entität ist, der Excel-Tabelle hinzugefügt wird, und oben im Arbeitsblatt sollten Sie sehen, dass das Arbeitsblatt mit dem MDS-Server verbunden ist. Beachten Sie, dass das ursprüngliche Arbeitsblatt **(sheet1**) noch vorhanden ist.  
  
     ![Excel – Registerkarten für Lieferanten und Tabelle1](../../2014/tutorials/media/et-ulingsdtomdsusingmdsaddinforexcel-03.jpg "Excel – Registerkarten für Lieferanten und Tabelle1")  
  
     ![Excel – Anzeigen von Details zur MDS-Verbindung](../../2014/tutorials/media/et-ulingsdtomdsusingmdsaddinforexcel-04.jpg "Excel – Anzeigen von Details zur MDS-Verbindung")  
  
15. Halten Sie **Excel** geöffnet.  
  
## <a name="next-task"></a>Nächste Aufgabe  
 [Aufgabe 3: Überprüfen der Daten im Master Data Manager](../../2014/tutorials/task-3-verifying-the-data-in-master-data-manager.md)  
  
  
