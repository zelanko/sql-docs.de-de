---
title: 'Schritt 1: Kopieren des Pakets aus Lektion 4 | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: 8aa7d690-4649-4c0a-ac6f-9504637ee426
author: janinezhang
ms.author: janinez
ms.openlocfilehash: 6bd8de63662b070e317f7c01d1d60f15b6864787
ms.sourcegitcommit: f71e523da72019de81a8bd5a0394a62f7f76ea20
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/17/2020
ms.locfileid: "84968180"
---
# <a name="step-1-copying-the-lesson-4-package"></a>Schritt 1: Kopieren des Pakets aus Lektion 4
  In dieser Aufgabe erstellen Sie eine Kopie des in Lektion 4 erstellten Pakets namens „Lesson 4.dtsx“. Alternativ können Sie dem Projekt auch das im Tutorial enthaltene, abgeschlossene Paket aus Lektion 4 hinzufügen und anschließend eine Kopie dieses Pakets erstellen. Sie werden diese neue Kopie in der gesamten Lektion 5 verwenden.  
  
### <a name="to-copy-the-lesson-4-package"></a>So kopieren Sie das Paket aus Lektion 4  
  
1.  Wenn [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Data Tools noch nicht geöffnet ist, klicken Sie auf **Start**und zeigen Sie auf **Alle Programme**. Klicken Sie anschließend auf **Microsoft SQL Server 2012**und danach auf **SQL Server Data Tools**.  
  
2.  Klicken Sie im Menü **Datei** auf **Öffnen**, klicken Sie auf **Projekt/Projekt**Mappe, wählen Sie **SSIS Tutorial** aus, klicken Sie auf **Öffnen**, und doppelklicken Sie dann auf **SSIS Tutorial. sln**.  
  
3.  Klicken Sie im Projektmappen-Explorer mit der rechten Maustaste auf **Lesson 4.dtsx**, und klicken Sie anschließend auf **Kopieren**.  
  
4.  Klicken Sie in Projektmappen-Explorer mit der rechten Maustaste auf **SSIS-Pakete**, und klicken Sie dann auf **Einfügen**.  
  
     Standardmäßig wird das kopierte Paket „Lesson 5.dtsx“ benannt.  
  
5.  Doppelklicken Sie im Projektmappen-Explorer auf **Lesson 5.dtsx** , um das Paket zu öffnen.  
  
6.  Klicken Sie mit der rechten Maustaste auf eine beliebige Stelle im Hintergrund der Registerkarte **Ablauf Steuerung** und dann auf **Eigenschaften**.  
  
7.  Aktualisieren Sie im Eigenschaftenfenster die- `Name` Eigenschaft auf `Lesson 5` .  
  
8.  Aktivieren Sie das Kontrollkästchen für die **ID** -Eigenschaft, klicken Sie auf den Dropdown Pfeil, und klicken Sie dann auf **\<Generate New ID>** .  
  
### <a name="to-add-the-completed-lesson-4-package"></a>So fügen Sie das abgeschlossene Paket aus Lektion 4 hinzu  
  
1.  Öffnen Sie [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Data Tools und das SSIS-Lernprogrammprojekt.  
  
2.  Klicken Sie in Projektmappen-Explorer mit der rechten Maustaste auf **SSIS-Pakete**, und klicken Sie auf **vorhandenes Paket hinzufügen**  
  
3.  Wählen Sie im Dialogfeld **Kopie des vorhandenen Pakets hinzufügen** unter **Paket Speicherort**die Option **Dateisystem**aus.  
  
4.  Klicken Sie auf die Schaltfläche zum Durchsuchen **(…)**, navigieren Sie zu **Lesson 4.dtsx** auf Ihrem Computer, und klicken Sie anschließend auf **Öffnen**.  
  
     Um alle Lektionspakete für dieses Lernprogramm herunterzuladen, gehen Sie wie folgt vor.  
  
    1.  Klicken Sie [hier](https://go.microsoft.com/fwlink/?LinkId=275027), um zur Seite Integration Services Product Samples zu gelangen  
  
    2.  Klicken Sie auf die Registerkarte **DOWNLOADS** .  
  
    3.  Klicken Sie auf die Datei SQL2012.Integration_Services.Create_Simple_ETL_Tutorial.Sample.zip.  
  
5.  Kopieren Sie das Paket aus Lektion 4, und fügen Sie es gemäß den Schritten 3 bis 8 der vorherigen Prozedur ein.  
  
## <a name="next-task-in-lesson"></a>Nächste Aufgabe in der Lektion  
 [Schritt 2: Aktivieren und Konfigurieren von Paketkonfigurationen](lesson-5-2-enabling-and-configuring-package-configurations.md)  
  
  
