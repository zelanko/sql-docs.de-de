---
title: 'Aufgabe 15: Erstellen und Ausführen des SSIS-Projekts | Microsoft Docs'
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
ms.assetid: 13adf4e0-216a-4992-b13d-b7b1e1629e77
caps.latest.revision: 6
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.openlocfilehash: 9a63fcf03591626d5b4c1351d5ce868ef7a9fb65
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/19/2018
ms.locfileid: "36058611"
---
# <a name="task-15-building-and-running-the-ssis-project"></a>Aufgabe 15: Erstellen und Ausführen des SSIS-Projekts
  In dieser Aufgabe erstellen Sie das SSIS-Projekt und führen es aus. Wenn Sie die 64-Bit-Version von Excel 2010 auf Ihrem Computer installiert haben, legen Sie den Wert der **Run64BitRuntime** auf **"false"** für die Excel-Quelle funktioniert.  
  
1.  In der **Projektmappen-Explorer** Fenster, klicken Sie auf **Projekt** auf das Menü, und klicken Sie auf **Eigenschaften von CleanseAndCurateSuppliers**.  
  
2.  In der **Eigenschaften** Dialogfeld erweitern Sie **Konfigurationseigenschaften** auf Links, und klicken Sie auf **Debuggen**.  
  
3.  Legen Sie **Run64BitRuntime** auf **"false"**.  
  
     ![CleanseAndCurateSuppliers Projekteigenschaften](../../2014/tutorials/media/et-buildingandrunningthessisproject-01.jpg "CleanseAndCurateSuppliers-Projekteigenschaften")  
  
4.  Klicken Sie auf **OK** schließen die **Eigenschaften** (Dialogfeld).  
  
5.  Klicken Sie auf **erstellen** auf der Menüleiste, und klicken Sie auf **CleanseAndCurateSuppliers erstellen**. Stellen Sie sicher, dass keine Erstellungsfehler vorliegen.  
  
6.  Klicken Sie auf **Debuggen** auf der Menüleiste und auf **Debuggen**.  
  
7.  Überprüfen Sie die Nachrichten in der **Fortschritt** Fenster, und überprüfen Sie das Paket ausgeführt und beendet wurde.  
  
     ![Ergebnisse aus dem Statusfenster](../../2014/tutorials/media/et-buildingandrunningthessisproject-02.jpg "Ergebnisse aus dem Statusfenster")  
  
     ![Endstatus aus dem Statusfenster](../../2014/tutorials/media/et-buildingandrunningthessisproject-03.jpg "Endstatus aus dem Statusfenster")  
  
8.  Klicken Sie auf **Debuggen** auf der Menüleiste, und klicken Sie auf **Beenden des Debuggens** um die Debugsitzung zu beenden. Wenn das Paket fehlschlägt, aktivieren Sie Daten-Viewer, und beobachten Sie den Datenfluss zwischen Komponenten.  
  
## <a name="next-step"></a>Nächster Schritt  
 [Aufgabe 16: Überprüfung mit Master Data Manager](../../2014/tutorials/task-16-verifying-with-master-data-manager.md)  
  
  