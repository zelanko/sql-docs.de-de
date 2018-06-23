---
title: 'Aufgabe 5: Erstellen eines domänenbasierten Attributs aus Excel | Microsoft Docs'
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
ms.assetid: 07cbc624-2c6b-4568-96e4-f18663a05d80
caps.latest.revision: 6
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.openlocfilehash: 5e7a8dda16d8f513b2c4b07b9f41712be806b8a9
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/19/2018
ms.locfileid: "36147797"
---
# <a name="task-5-creating-a-domain-based-attribute-from-excel"></a>Aufgabe 5: Erstellen eines domänenbasierten Attributs aus Excel
  In dieser Aufgabe konvertieren Sie die **Status** Attribut von der **Lieferanten** Entität als ein **domänenbasiertes Attribut**. Nachdem Sie das Attribut "State" in MDS, eine neue Entität mit dem Namen veröffentlicht und werden von einem domänenbasierten konfiguriert **Status** auf MDS-Server mit allen Werten in der Spalte erstellt werden und die **Zustand** Attribut des der **Lieferanten** Entität wird mit Werten aufgefüllt werden die **Zustand** Entität. Jetzt die **Lieferanten** Modell sollten zwei Entitäten haben: **Lieferanten** und **Status** , in dem die **Status** Attribut des der  **Lieferanten** Entität ist ein domänenbasiertes Attribut, von denen abhängt **Zustand** Entität.  
  
1.  Wechseln Sie zur **Excel** Fenster mit **Cleansed and Matched Suppliers.xlsx** öffnen.  
  
2.  Klicken Sie auf **aktualisieren** Schaltfläche im Menüband auf die neuesten Updates aus MDS abzurufen. Die zwei weiteren Datensätze sollte angezeigt werden, wenn Sie das optionale ausgeführt haben **Aufgabe 4**.  
  
3.  Klicken Sie auf Spaltennamen **Status** (Zelle **I1**) in der **Kopfzeile**.  
  
     ![Excel – Attributeigenschaften (Schaltfläche)](../../2014/tutorials/media/et-creatingadomainbasedattributefromexcel-01.jpg "Excel – Attributeigenschaften (Schaltfläche)")  
  
4.  Klicken Sie auf **Attributeigenschaften** auf dem Menüband.  
  
5.  In der **Attributeigenschaften** wählen Sie im Dialogfeld **eingeschränkte Liste (domänenbasiert)** für die **Attributtyp**.  
  
6.  Typ **Status** für die **neuer Entitätsname** , und klicken Sie auf **OK**.  
  
     ![Excel - Attribut Eigenschaftendialogfeld](../../2014/tutorials/media/et-creatingadomainbasedattributefromexcel-02.jpg "Excel - Attribut Eigenschaften (Dialogfeld)")  
  
7.  Jetzt in Excel, Sie sollten sehen **Pfeil nach unten** beim Klicken auf einen beliebigen Wert in der **Zustand** Spalte. Sie können den Wert bei Bedarf über die Dropdownliste ändern.  
  
     ![Excel – Dropdownliste mit Zuständen](../../2014/tutorials/media/et-creatingadomainbasedattributefromexcel-03.jpg "Excel – Dropdownliste mit Zuständen")  
  
## <a name="next-step"></a>Nächster Schritt  
 [Aufgabe 6: Überprüfen, ob das domänenbasierte Attribut mithilfe von Master Data Manager erstellt wird](../../2014/tutorials/task-6-verify-domain-based-attribute-master-data-manager.md)  
  
  