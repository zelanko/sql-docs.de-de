---
title: 'Aufgabe 5: Erstellen eines domänenbasierten Attributs aus Excel | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: data-quality-services
ms.topic: conceptual
ms.assetid: 07cbc624-2c6b-4568-96e4-f18663a05d80
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: 6f7287091ddd64ef9df1c63706a2f562feed4a5d
ms.sourcegitcommit: 57f1d15c67113bbadd40861b886d6929aacd3467
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/18/2020
ms.locfileid: "84999666"
---
# <a name="task-5-creating-a-domain-based-attribute-from-excel"></a>Aufgabe 5: Erstellen eines domänenbasierten Attributs aus Excel
  In dieser Aufgabe konvertieren Sie das Attribut **State** der Entität **Supplier** in ein **domänenbasiertes Attribut**. Nachdem Sie das State-Attribut als domänenbasiertes Verzeichnis konfiguriert und in MDS veröffentlicht haben, wird eine neue Entität mit dem Namen **State** auf dem MDS-Server mit allen Werten in der Spalte erstellt, und das **State** -Attribut der Entität " **Supplier** " wird mit Werten aus der Entität " **State** " aufgefüllt. Das Modell **Suppliers** sollte nun über zwei Entitäten verfügen: **Supplier** und **State** , wobei das **State** -Attribut der Entität **Supplier** ein domänenbasiertes Attribut ist, das von der **State** -Entität abhängt.  
  
1.  Wechseln Sie zum **Excel** -Fenster, das **bereinigt wurde und #b0** geöffnet ist.  
  
2.  Klicken Sie im Menüband auf die Schaltfläche **Aktualisieren** , um die neuesten Updates von MDS zu erhalten. Wenn Sie die optionale **Aufgabe 4**ausgeführt haben, sollten Sie die zwei weiteren Datensätze sehen.  
  
3.  Klicken Sie in der **Kopfzeile**auf Column Name **State** (Zelle **I1**).  
  
     ![Excel – Attributeigenschaften (Schaltfläche)](../../2014/tutorials/media/et-creatingadomainbasedattributefromexcel-01.jpg "Excel – Attributeigenschaften (Schaltfläche)")  
  
4.  Klicken Sie im Menüband auf **Attribut Eigenschaften** .  
  
5.  Wählen Sie im Dialogfeld **Attribut Eigenschaften** für den **Attributtyp**die Option **eingeschränkte Liste (Domänen basiert)** aus.  
  
6.  Geben Sie **State** als **neuen Entitäts Namen** ein, und klicken Sie auf **OK**.  
  
     ![Excel – Attributeigenschaften (Dialogfeld)](../../2014/tutorials/media/et-creatingadomainbasedattributefromexcel-02.jpg "Excel – Attributeigenschaften (Dialogfeld)")  
  
7.  In Excel sollte nun ein **Pfeil nach unten** angezeigt werden, wenn Sie auf einen beliebigen Wert in der Spalte **Status** klicken. Sie können den Wert bei Bedarf über die Dropdownliste ändern.  
  
     ![Excel – Dropdownliste mit Bundesstaaten](../../2014/tutorials/media/et-creatingadomainbasedattributefromexcel-03.jpg "Excel – Dropdownliste mit Bundesstaaten")  
  
## <a name="next-step"></a>Nächster Schritt  
 [Aufgabe 6: Überprüfen, ob das domänenbasierte Attribut mithilfe von Master Data Manager erstellt wurde](../../2014/tutorials/task-6-verify-domain-based-attribute-master-data-manager.md)  
  
  
