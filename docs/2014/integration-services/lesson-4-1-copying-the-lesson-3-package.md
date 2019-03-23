---
title: 'Schritt 1: Kopieren des Pakets aus Lektion 3 | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: 0d053786-5203-43f3-a613-27a8dd2bc44a
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: c3a765f23b4bfcdd4d8f0ff84ac8d363424882bc
ms.sourcegitcommit: 5a8678bf85f65be590676745a7fe4fcbcc47e83d
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/22/2019
ms.locfileid: "58377498"
---
# <a name="step-1-copying-the-lesson-3-package"></a>Schritt 1: Kopieren des Pakets aus Lektion 3
  In dieser Aufgabe erstellen Sie eine Kopie des in Lektion 3 erstellten Pakets Lesson 3.dtsx. Wenn Sie Lektion 3 nicht abgeschlossen haben, können Sie stattdessen das vollständige Lektion 3-Paket, das im Lernprogramm des Projekts enthalten ist, hinzufügen und dann kopieren. Sie verwenden diese neue Kopie im gesamten Rest der Lektion 4.  
  
### <a name="to-create-the-lesson-4-package"></a>So erstellen Sie das Lektion 4-Paket  
  
1.  Wenn [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Data Tools noch nicht geöffnet ist, klicken Sie auf **Start**und zeigen Sie auf **Alle Programme**. Klicken Sie auf **Microsoft SQL Server**und anschließend auf **SQL Server Data Tools**.  
  
2.  Klicken Sie im Menü **Datei** auf **Öffnen**&gt; **Projekt/Projektmappe**. Wählen Sie **SSIS Tutorial** aus, klicken Sie auf **Öffnen**und anschließend auf **SSIS Tutorial.sln**.  
  
3.  Klicken Sie im Projektmappen-Explorer mit der rechten Maustaste auf **Lesson 3.dtsx**, und klicken Sie anschließend auf **Kopieren**.  
  
4.  Klicken Sie im Projektmappen-Explorer mit der rechten Maustaste auf **SSIS-Pakete**und anschließend auf **Einfügen**.  
  
     Standardmäßig wird das kopierte Paket Lesson 4.dtsx genannt.  
  
5.  Doppelklicken Sie im Projektmappen-Explorer auf **Lesson 4.dtsx** , um das Paket zu öffnen.  
  
6.  Klicken Sie mit der rechten Maustaste an einer beliebigen Stelle im Hintergrund der Registerkarte **Ablaufsteuerung** , und klicken Sie auf **Eigenschaften**.  
  
7.  Aktualisieren Sie im Fenster Eigenschaften die `Name` Eigenschaft `Lesson 4`.  
  
8.  Klicken Sie auf das Kontrollkästchen für die **ID** -Eigenschaft, und klicken Sie dann in der Liste auf  **\<neue ID generieren >**.  
  
### <a name="to-add-the-completed-lesson-3-package"></a>So fügen Sie das abgeschlossene Lektion 3-Paket hinzu  
  
1.  Öffnen Sie [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] , und öffnen Sie das SSIS-Lernprogrammprojekt.  
  
2.  Klicken Sie im Projektmappen-Explorer mit der rechten Maustaste auf **SSIS-Pakete**, und klicken Sie auf **Vorhandenes Paket hinzufügen**.  
  
3.  Wählen Sie im Dialogfeld **Kopie des vorhandenen Pakets hinzufügen** unter **Paketspeicherort**die Option **Dateisystem**aus.  
  
4.  Klicken Sie auf die Schaltfläche zum Durchsuchen **(…)**, navigieren Sie zu „Lesson 3.dtsx“ auf Ihrem Computer, und klicken Sie anschließend auf **Öffnen**.  
  
     Um alle Lektionspakete für dieses Lernprogramm herunterzuladen, gehen Sie wie folgt vor.  
  
    1.  Klicken Sie [hier](https://go.microsoft.com/fwlink/?LinkId=275027), um zur Seite Integration Services Product Samples zu gelangen  
  
    2.  Klicken Sie auf die Registerkarte **DOWNLOADS** .  
  
    3.  Klicken Sie auf die Datei SQL2012.Integration_Services.Create_Simple_ETL_Tutorial.Sample.zip.  
  
5.  Kopieren Sie das Paket aus Lektion 3, und fügen Sie es wie in den Schritten 3 bis 8 der vorherigen Prozedur beschrieben ein.  
  
## <a name="next-task-in-lesson"></a>Nächste Aufgabe in dieser Lektion  
 [Schritt 2: Erstellen einer beschädigten Datei](lesson-4-2-creating-a-corrupted-file.md)  
  
  
