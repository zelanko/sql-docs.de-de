---
title: 'Aufgabe 15: entwickeln und Ausführen des SSIS-Projekts | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: data-quality-services
ms.topic: conceptual
ms.assetid: 13adf4e0-216a-4992-b13d-b7b1e1629e77
ms.author: lle
author: lrtoyou1223
ms.openlocfilehash: 50b313f63ae434a96d6c0e38f3c8b600914c806d
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/26/2020
ms.locfileid: "66822991"
---
# <a name="task-15-building-and-running-the-ssis-project"></a>Aufgabe 15: Erstellen und Ausführen des SSIS-Projekts

  In dieser Aufgabe erstellen Sie das SSIS-Projekt und führen es aus. Wenn die 64-Bit-Version von Excel 2010 auf dem Computer installiert ist, sollten Sie den Wert von **Run64BitRuntime** auf **false** festlegen, damit die Excel-Quelle funktioniert.  
  
1.  Klicken Sie im Fenster **Projektmappen-Explorer** im Menü auf **Projekt** , und klicken Sie dann auf **Eigenschaften von clean\andcurratesuppliers**.  
  
2.  Erweitern Sie im Dialogfeld **Eigenschaften** auf der linken Seite die Option **Konfigurations Eigenschaften** , und klicken Sie auf **Debuggen**.  
  
3.  Legen Sie **Run64BitRuntime** auf **false**fest.  
  
     ![CleanseAndCurateSuppliers (Projekteigenschaften)](../../2014/tutorials/media/et-buildingandrunningthessisproject-01.jpg "CleanseAndCurateSuppliers (Projekteigenschaften)")  
  
4.  Klicken Sie auf **OK**, um das Dialogfeld **Eigenschaften** zu schließen.  
  
5.  Klicken Sie in der Menüleiste auf **Erstellen** , und klicken Sie auf **Build cleanmenandcurratesuppliers**. Stellen Sie sicher, dass keine Erstellungsfehler vorliegen.  
  
6.  Klicken Sie in der Menüleiste auf **Debuggen** und dann auf **Debugging starten**  
  
7.  Überprüfen Sie die Meldungen im Fenster Status, und überprüfen Sie, **ob das Paket** erfolgreich ausgeführt und beendet wurde  
  
     ![Ergebnisse aus dem Statusfenster](../../2014/tutorials/media/et-buildingandrunningthessisproject-02.jpg "Ergebnisse aus dem Statusfenster")  
  
     ![Endstatus aus dem Statusfenster](../../2014/tutorials/media/et-buildingandrunningthessisproject-03.jpg "Endstatus aus dem Statusfenster")  
  
8.  Klicken Sie in der Menüleiste auf **Debuggen** , und klicken Sie dann auf **Debuggen Debuggen** Wenn das Paket fehlschlägt, aktivieren Sie Daten-Viewer, und beobachten Sie den Datenfluss zwischen Komponenten.  
  
## <a name="next-step"></a>Nächster Schritt  
 [Aufgabe 16: Überprüfung mit dem Master Data Manager](../../2014/tutorials/task-16-verifying-with-master-data-manager.md)  
  
  
