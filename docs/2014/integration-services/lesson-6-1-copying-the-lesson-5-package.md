---
title: 'Schritt 1: Kopieren des Pakets aus Lektion 5 | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: a25fcc13-987e-4f3d-8f0c-76f7e6e59920
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: ede34999b9ca7a18a2bb5ec997c4a93735b82be2
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/26/2020
ms.locfileid: "62890756"
---
# <a name="step-1-copying-the-lesson-5-package"></a>Schritt 1: Kopieren des Pakets aus Lektion 5
  In dieser Aufgabe erstellen Sie eine Kopie des in Lektion 5 erstellten Pakets Lesson 5.dtsx. Wahlweise können Sie dem Projekt auch das im Lernprogramm enthaltene abgeschlossene Paket aus Lektion 5 hinzufügen und dann von diesem Paket eine Kopie erstellen. Sie verwenden diese neue Kopie im gesamten Rest der Lektion 6.  
  
### <a name="to-copy-the-lesson-5-package"></a>So kopieren Sie das Lektion 5-Paket aus  
  
1.  Wenn SQL Server Data Tools noch nicht geöffnet sind, klicken Sie auf Start, zeigen auf Alle Programme und auf Microsoft SQL Server 2012 und klicken dann auf SQL Server Data Tools.  
  
2.  Klicken Sie im Menü Datei auf Öffnen, klicken Sie auf Projekt/Projektmappe, wählen Sie SSIS Tutorial aus, klicken Sie auf Öffnen, und doppelklicken Sie dann auf SSIS Tutorial.sln.  
  
3.  Klicken Sie im Projektmappen-Explorer mit der rechten Maustaste auf Lesson 5.dtsx, und klicken Sie dann auf Kopieren.  
  
4.  Klicken Sie im Projektmappen-Explorer mit der rechten Maustaste auf SSIS Packages, und klicken Sie dann auf Einfügen.  
  
     Standardmäßig wird das kopierte Paket Lesson 6.dtsx genannt.  
  
5.  Doppelklicken Sie im Projektmappen-Explorer auf Lesson 6.dtsx, um das Paket zu öffnen.  
  
6.  Klicken Sie mit der rechten Maustaste auf eine beliebige Stelle im Hintergrund der Registerkarte Ablaufsteuerung, und klicken Sie dann auf Eigenschaften.  
  
7.  Aktualisieren Sie im Eigenschaftenfenster die Name-Eigenschaft in Lesson 6.  
  
8.  Aktivieren Sie das Kontrollkästchen für die ID-Eigenschaft, klicken Sie auf den Dropdown Pfeil \<, und klicken Sie dann auf neue ID generieren>.  
  
### <a name="to-add-the-completed-lesson-5-package"></a>So fügen Sie das abgeschlossene Lektion 5-Paket hinzu  
  
1.  Öffnen Sie SQL Server Data Tools und das SSIS-Lernprogrammprojekt.  
  
2.  Klicken Sie im Projektmappen-Explorer mit der rechten Maustaste auf SSIS-Pakete, und klicken Sie auf Vorhandenes Paket hinzufügen.  
  
3.  Wählen Sie im Dialogfeld Kopie des vorhandenen Pakets hinzufügen unter Paketspeicherort die Option Dateisystem aus.  
  
4.  Klicken Sie auf die Schaltfläche zum Durchsuchen (…), navigieren Sie auf dem Computer zu „Lesson 5.dtsx“, und klicken Sie anschließend auf **Öffnen**.  
  
     Um alle Lektionspakete für dieses Lernprogramm herunterzuladen, gehen Sie wie folgt vor.  
  
    1.  Klicken Sie [hier](https://go.microsoft.com/fwlink/?LinkId=275027), um zur Seite Integration Services Product Samples zu gelangen  
  
    2.  Klicken Sie auf die Registerkarte **DOWNLOADS** .  
  
    3.  Klicken Sie auf die Datei SQL2012.Integration_Services.Create_Simple_ETL_Tutorial.Sample.zip.  
  
5.  Kopieren Sie das Paket aus Lektion 5, und fügen Sie es wie in den Schritten 3 bis 8 der vorherigen Prozedur beschrieben ein.  
  
     Wenn die Projektmappe nach dem Kopieren des Lektion 5-Pakets noch Pakete aus vorherigen Lektionen enthält, klicken Sie mit der rechten Maustaste auf die einzelnen Pakete aus Lektion 1 bis 5 und klicken dann auf Aus Projekt ausschließen. Anschließend sollte nur noch Lesson 6.dtsx in der Projektmappe enthalten sein.  
  
## <a name="next-task-in-lesson"></a>Nächste Aufgabe in der Lektion  
 [Schritt 2: Konvertieren des Projekts in das Projektbereitstellungsmodell](lesson-6-2-converting-the-project-to-the-project-deployment-model.md)  
  
  
