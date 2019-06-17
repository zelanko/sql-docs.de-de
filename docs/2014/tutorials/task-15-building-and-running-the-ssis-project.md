---
title: 'Aufgabe 15: Erstellen und Ausführen des SSIS-Projekts | Microsoft-Dokumentation'
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
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "66822991"
---
# <a name="task-15-building-and-running-the-ssis-project"></a>Aufgabe 15: Erstellen und Ausführen des SSIS-Projekts

  In dieser Aufgabe erstellen Sie das SSIS-Projekt und führen es aus. Wenn Sie die 64-Bit-Version von Excel 2010 auf Ihrem Computer installiert haben, legen Sie den Wert der **Run64BitRuntime** zu **"false"** für die Excel-Quelle funktioniert.  
  
1.  In der **Projektmappen-Explorer** Fenster, klicken Sie auf **Projekt** auf das Menü, und klicken Sie auf **Eigenschaften von CleanseAndCurateSuppliers**.  
  
2.  In der **Eigenschaften** Dialogfeld erweitern Sie **Konfigurationseigenschaften** auf der linken Seite, und klicken Sie auf **Debuggen**.  
  
3.  Legen Sie **Run64BitRuntime** zu **"false"** .  
  
     ![CleanseAndCurateSuppliers Projekteigenschaften](../../2014/tutorials/media/et-buildingandrunningthessisproject-01.jpg "CleanseAndCurateSuppliers-Projekteigenschaften")  
  
4.  Klicken Sie auf **OK** schließen die **Eigenschaften** Dialogfeld.  
  
5.  Klicken Sie auf **erstellen** auf der Menüleiste, und klicken Sie auf **CleanseAndCurateSuppliers erstellen**. Stellen Sie sicher, dass keine Erstellungsfehler vorliegen.  
  
6.  Klicken Sie auf **Debuggen** auf der Menüleiste und auf **Debuggen starten**.  
  
7.  Überprüfen Sie die Meldungen in die **Fortschritt** Fenster und vergewissern Sie sich das Paket ausgeführt und beendet wurde.  
  
     ![Führt Sie aus dem Statusfenster](../../2014/tutorials/media/et-buildingandrunningthessisproject-02.jpg "führt Sie aus dem Statusfenster")  
  
     ![Endstatus aus dem Statusfenster](../../2014/tutorials/media/et-buildingandrunningthessisproject-03.jpg "Endstatus aus dem Statusfenster")  
  
8.  Klicken Sie auf **Debuggen** auf der Menüleiste, und klicken Sie auf **Debuggen beenden** um die Debugsitzung zu beenden. Wenn das Paket fehlschlägt, aktivieren Sie Daten-Viewer, und beobachten Sie den Datenfluss zwischen Komponenten.  
  
## <a name="next-step"></a>Nächster Schritt  
 [Aufgabe 16: Überprüfung mit Master Data Manager](../../2014/tutorials/task-16-verifying-with-master-data-manager.md)  
  
  
