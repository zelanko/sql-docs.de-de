---
title: 'Schritt 1: Kopieren des Pakets aus Lektion 5 | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 01/11/2019
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.technology: integration-services
ms.topic: tutorial
ms.assetid: a25fcc13-987e-4f3d-8f0c-76f7e6e59920
author: janinezhang
ms.author: janinez
ms.openlocfilehash: d8b47f2da5e16e83abf6846d33ac7ce9e38aa6af
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "67911450"
---
# <a name="lesson-6-1-copy-the-lesson-5-package"></a>Lektion 6.1: Kopieren des Pakets aus Lektion 5

[!INCLUDE[ssis-appliesto](../includes/ssis-appliesto-ssvrpluslinux-asdb-asdw-xxx.md)]



In dieser Aufgabe erfahren Sie, wie Sie eine Kopie des Pakets **Lesson 5.dtsx** aus Lektion 5 erstellen. Wenn Sie Lektion 5 nicht abgeschlossen haben, können Sie stattdessen das abgeschlossene Paket aus dem Tutorial im Projekt hinzufügen und dann kopieren. Sie verwenden diese neue Kopie für den weiteren Verlauf von Lektion 6. 

> [!IMPORTANT]
> Wenn die Projektmappe nach dem Kopieren des Lektion 5-Pakets noch Pakete aus vorherigen Lektionen enthält, klicken Sie mit der rechten Maustaste auf die einzelnen Pakete aus Lektion 1 bis 5 und wählen dann **Aus Projekt ausschließen** aus. Anschließend sollte nur noch **Lesson 6.dtsx** in der Projektmappe enthalten sein.   
  
## <a name="create-the-lesson-6-package"></a>Erstellen des Pakets für Lektion 6  
  
Gehen Sie wie folgt vor, wenn Sie das fertige Paket aus Lektion 5 kopieren möchten.  Informationen zum Kopieren des Beispielpakets für Lektion 5 finden Sie im nächsten Abschnitt.

1.  Wenn [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Data Tools noch nicht geöffnet ist, klicken Sie auf **Start** > **All Programs** (Alle Programme)  > **Microsoft SQL Server 2017**, und wählen Sie **SQL Server Data Tools** aus.

2.  Klicken Sie im Menü **Datei** auf **Öffnen** > **Projekt/Projektmappe**, wählen Sie den Ordner **SSIS Tutorial** (SSIS-Tutorial) aus, und klicken Sie auf **Öffnen**. Doppelklicken Sie anschließend auf **SSIS Tutorial.sln**.

3.  Klicken Sie im **Projektmappen-Explorer** erst mit der rechten Maustaste auf **Lesson 5.dtsx**, und wählen Sie dann **Kopieren** aus.

4.  Klicken Sie im **Projektmappen-Explorer** mit der rechten Maustaste auf **SSIS-Pakete**, und klicken Sie dann auf **Einfügen**.

    Standardmäßig lautet der Name des kopierten Pakets **Lesson 5.dtsx**.

5.  Doppelklicken Sie im **Projektmappen-Explorer** auf **Lesson 5.dtsx**, um das Paket zu öffnen.

6.  Klicken Sie erst mit der rechten Maustaste auf eine beliebige Stelle im Hintergrund der Entwurfsoberfläche **Ablaufsteuerung**, und klicken Sie anschließend auf **Eigenschaften**.

7.  Ändern Sie im Fenster **Eigenschaften** die Eigenschaft **Name** in **Lesson 6** (Lektion 6).

8.  Aktivieren Sie zunächst das Kontrollkästchen für die Eigenschaft **ID**, klicken Sie dann auf den Dropdownpfeil und anschließend auf **\<Neue ID generieren>** .

## <a name="add-the-completed-lesson-5-package"></a>Hinzufügen des abgeschlossenen Pakets aus Lektion 5

1.  Öffnen Sie [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Data Tools und das SSIS-Lernprogrammprojekt.

2.  Klicken Sie im **Projektmappen-Explorer** mit der rechten Maustaste auf **SSIS-Pakete**, und klicken Sie auf **Vorhandenes Paket hinzufügen**.

3.  Wählen Sie im Dialogfeld **Kopie des vorhandenen Pakets hinzufügen** unter **Paketspeicherort**die Option **Dateisystem**aus.

4.  Klicken Sie auf die Schaltfläche zum Durchsuchen **(…)** , navigieren Sie zu **Lesson 5.dtsx** auf Ihrem Computer, und wählen Sie anschließend **Öffnen** aus.

5.  Kopieren Sie das Paket aus Lektion 5, und fügen Sie es wie in den Schritten 3 bis 8 im vorherigen Abschnitt beschrieben ein.

## <a name="go-to-next-task"></a>Weiter zur nächsten Aufgabe
[Schritt 2: Konvertieren des Projekts in das Projektbereitstellungsmodell](../integration-services/lesson-6-2-converting-the-project-to-the-project-deployment-model.md)  
  
