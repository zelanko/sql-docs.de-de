---
title: 'Aufgabe 2: Hochladen von Lieferantendaten in MDS mithilfe MDS-Add-in für Excel | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: data-quality-services
ms.topic: conceptual
ms.assetid: 598deb57-e0cc-4e0a-aeb1-94432c094c67
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: 5e825829eb70b695a619df8caaa59788d0ad413f
ms.sourcegitcommit: 57f1d15c67113bbadd40861b886d6929aacd3467
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/18/2020
ms.locfileid: "85064773"
---
# <a name="task-2-uploading-supplier-data-to-mds-using-mds-add-in-for-excel"></a>Aufgabe 2: Hochladen von Lieferantendaten in MDS mithilfe des MDS-Add-Ins für Excel
  In dieser Aufgabe veröffentlichen Sie die bereinigten und Lieferantendaten mithilfe der **MDS-Add-in für Excel**in **MDS** . Sie erstellen eine Entität mit dem Namen **Lieferant** in dem Modell **Suppliers** , das Sie in der vorherigen Lektion erstellt haben. Die Entität weist ein Attribut für jede Spalte in der Excel-Datei auf. Die Attribute "Code" und "Name" der Entität "Supplier" entsprechen den Spalten **SupplierID** und **Supplier Name** in Excel.  
  
1.  Öffnen Sie **bereinigt und abgeglichen Suppliers.xls** in **Excel**.  
  
2.  Drücken Sie **STRG + A** , um die gesamten Daten auszuwählen. Es ist **wichtig** , dass Sie die gesamten Daten in der Tabelle auswählen.  
  
3.  Klicken Sie in der Menüleiste auf **Master Daten** .  
  
4.  Klicken Sie im Menüband auf Schaltfläche **Entität erstellen** .  
  
     ![Excel – Masterdaten (Registerkarte) – Entität erstellen (Schaltfläche)](../../2014/tutorials/media/et-ulingsdtomdsusingmdsaddinforexcel-01.jpg "Excel – Masterdaten (Registerkarte) – Entität erstellen (Schaltfläche)")  
  
5.  Wenn im Dialogfeld **Verbindungen verwalten** die Verbindung mit dem **lokalen MDS-Server** unter **vorhandene Verbindungen**nicht angezeigt wird, gehen Sie wie folgt vor:  
  
    1.  Wählen Sie **neue Verbindung erstellen**aus, und klicken Sie auf die Schaltfläche **neu** .  
  
    2.  Geben Sie im Dialogfeld **neue Verbindung hinzufügen** den **Namen local MDS Server** for **Description** und **http: \/ /localhost/MDS** für die **MDS-Server Adresse**ein, und klicken Sie auf **OK** , um das Dialogfeld zu schließen.  
  
6.  Wählen Sie im Dialogfeld **Verbindungen verwalten** die Option **lokaler MDS-Server** ( `http://localhost/MDS` ) aus, klicken Sie auf **Testen** , um die Verbindung zu testen. Klicken Sie im Meldungs Feld auf **OK** .  
  
7.  Klicken Sie auf **verbinden** , um eine Verbindung zum MDS-Server herzustellen.  
  
8.  Wählen Sie im Dialogfeld **Entität erstellen** die Option **Suppliers** für das **Modell**aus.  
  
9. Stellen Sie sicher, dass für die **Version** **VERSION_1** ausgewählt ist.  
  
10. Geben Sie **Supplier** als **neuen Entitäts Namen**ein.  
  
11. Wählen Sie **SupplierID** für **die Spalte aus, die ein eindeutiges Bezeichnerfeld enthält** (Sie können auch automatisch einen Code generieren). Sie ordnen die **SupplierID-** Spalte in **Excel** im Wesentlichen dem Attribut " **Code** " der Entität " **Supplier** " zu.  
  
12. Wählen Sie **Lieferanten Name** für **die Spalte aus, die das Feld Namen enthält** . Im wesentlichen ordnen Sie die Spalte " **Supplier Name** " in **Excel** dem **namens** Attribut der Entität " **Supplier** " zu. Die Attribute " **Code** " und " **Name** " sind obligatorische Attribute für eine Entität in MDS.  
  
     ![Entität erstellen (Dialogfeld)](../../2014/tutorials/media/et-ulingsdtomdsusingmdsaddinforexcel-02.jpg "Entität erstellen (Dialogfeld)")  
  
13. Klicken Sie auf **OK** , um die Entität in MDS zu erstellen, die Master Daten in der Entität zu veröffentlichen und das Dialogfeld **Entität erstellen** zu schließen.  
  
14. Nun sollte das neue Blatt **Lieferant**angezeigt werden, bei dem es sich um den Namen der Entität handelt, der dem Excel-Arbeitsblatt hinzugefügt wird. oben im Arbeitsblatt sollten Sie sehen, dass das Arbeitsblatt mit dem MDS-Server verbunden ist. Beachten Sie, dass das ursprüngliche Arbeitsblatt (mit dem Namen **Sheet1**) noch vorhanden ist.  
  
     ![Excel – Registerkarten für Lieferanten und Tabelle1](../../2014/tutorials/media/et-ulingsdtomdsusingmdsaddinforexcel-03.jpg "Excel – Registerkarten für Lieferanten und Tabelle1")  
  
     ![Excel – Anzeigen von Details zur MDS-Verbindung](../../2014/tutorials/media/et-ulingsdtomdsusingmdsaddinforexcel-04.jpg "Excel – Anzeigen von Details zur MDS-Verbindung")  
  
15. Lassen Sie **Excel** geöffnet.  
  
## <a name="next-task"></a>Nächste Aufgabe  
 [Aufgabe 3: Überprüfen der Daten im Master Data Manager](../../2014/tutorials/task-3-verifying-the-data-in-master-data-manager.md)  
  
  
