---
title: 'Aufgabe 5: Erstellen eines domänenbasierten Attributs aus Excel | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: data-quality-services
ms.topic: conceptual
ms.assetid: 07cbc624-2c6b-4568-96e4-f18663a05d80
author: lrtoyou1223
ms.author: lle
manager: craigg
ms.openlocfilehash: f7e88065ff66ea953d0a91ed080fc3d7159ab794
ms.sourcegitcommit: 5748d710960a1e3b8bb003d561ff7ceb56202ddb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/09/2019
ms.locfileid: "65489104"
---
# <a name="task-5-creating-a-domain-based-attribute-from-excel"></a>Aufgabe 5: Erstellen eines domänenbasierten Attributs aus Excel
  In dieser Aufgabe konvertieren Sie die **Zustand** Attribut der **Lieferanten** Entität als ein **domänenbasiertes Attribut**. Nach dem Konfigurieren der State-Attribut, um einen domänenbasierten werden, und veröffentlichen es in MDS, eine neue Entität mit dem Namen **Zustand** auf MDS-Server mit allen Werten in der Spalte erstellt werden und die **Zustand** Attribut der **Lieferanten** Entität gefüllt mit Werten aus der **Zustand** Entität. Jetzt die **Lieferanten** Modell sollten zwei Entitäten haben: **Lieferanten** und **Zustand** , in denen die **Zustand** Attribut der **Lieferanten** Entität ist ein domänenbasiertes Attribut, von denen abhängt **Zustand** Entität.  
  
1.  Wechseln Sie zur **Excel** Fenster mit **Cleansed and Matched Suppliers.xlsx** zu öffnen.  
  
2.  Klicken Sie auf **aktualisieren** Schaltfläche auf dem Menüband auf die neuesten Updates aus MDS abzurufen. Die zwei weiteren Datensätze sollte angezeigt werden, wenn Sie das optionale ausgeführt haben **Aufgabe 4**.  
  
3.  Klicken Sie auf Spaltennamen **Zustand** (Zelle **I1**) in der **Kopfzeile**.  
  
     ![Excel – Attributeigenschaften (Schaltfläche)](../../2014/tutorials/media/et-creatingadomainbasedattributefromexcel-01.jpg "Excel – Attributeigenschaften (Schaltfläche)")  
  
4.  Klicken Sie auf **Attributeigenschaften** auf dem Menüband.  
  
5.  In der **Attributeigenschaften** wählen Sie im Dialogfeld **eingeschränkte Liste (domänenbasiert)** für die **Attributtyp**.  
  
6.  Typ **Zustand** für die **neuer Entitätsname** , und klicken Sie auf **OK**.  
  
     ![Excel – wählen Sie im Dialogfeld Eigenschaften für Attribut](../../2014/tutorials/media/et-creatingadomainbasedattributefromexcel-02.jpg "Excel - Attribut Eigenschaften (Dialogfeld)")  
  
7.  Jetzt in Excel sollte **Pfeil nach unten** beim Klicken auf einen beliebigen Wert in der **Zustand** Spalte. Sie können den Wert bei Bedarf über die Dropdownliste ändern.  
  
     ![Excel – Dropdownliste mit Zuständen](../../2014/tutorials/media/et-creatingadomainbasedattributefromexcel-03.jpg "Excel – Dropdownliste mit Zuständen")  
  
## <a name="next-step"></a>Nächster Schritt  
 [Aufgabe 6: Stellen Sie sicher, dass das domänenbasierte Attribut mithilfe von Master Data Manager erstellt wird](../../2014/tutorials/task-6-verify-domain-based-attribute-master-data-manager.md)  
  
  
