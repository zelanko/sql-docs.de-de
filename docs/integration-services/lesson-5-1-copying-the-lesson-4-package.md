---
title: 'Schritt 1: Kopieren des Pakets aus Lektion 4 | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 01/08/2019
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.technology: integration-services
ms.topic: tutorial
ms.assetid: 8aa7d690-4649-4c0a-ac6f-9504637ee426
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: 16dde3b03f85834a66c0cdddbc9c530997affde9
ms.sourcegitcommit: 7ccb8f28eafd79a1bddd523f71fe8b61c7634349
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/20/2019
ms.locfileid: "58279914"
---
# <a name="lesson-5-1-copy-the-lesson-4-package"></a>Lektion 5.1: Kopieren des Pakets aus Lektion 4

In dieser Aufgabe erfahren Sie, wie Sie eine Kopie des Pakets **Lesson 4.dtsx** aus Lektion 4 erstellen. Wenn Sie Lektion 4 nicht abgeschlossen haben, können Sie stattdessen das abgeschlossene Paket aus dem Tutorial im Projekt hinzufügen und dann kopieren. Sie verwenden diese neue Kopie für den weiteren Verlauf von Lektion 5.  
  
## <a name="create-the-lesson-5-package"></a>Erstellen des Pakets für Lektion 5  
  
Gehen Sie wie folgt vor, wenn Sie das abgeschlossene Paket aus Lektion 4 kopieren möchten.  Informationen zum Kopieren des Beispielpakets für Lektion 4 finden Sie im nächsten Abschnitt.

1.  Wenn [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Data Tools noch nicht geöffnet ist, klicken Sie auf **Start** > **All Programs** (Alle Programme)  > **Microsoft SQL Server 2017**, und wählen Sie **SQL Server Data Tools** aus.

2.  Klicken Sie im Menü **Datei** auf **Öffnen** > **Projekt/Projektmappe**, wählen Sie den Ordner **SSIS Tutorial** (SSIS-Tutorial) und dann **Öffnen** aus.  Doppelklicken Sie anschließend auf **SSIS Tutorial.sln**.

3.  Klicken Sie im **Projektmappen-Explorer** erst mit der rechten Maustaste auf **Lesson 4.dtsx**, und wählen Sie dann **Kopieren** aus.

4.  Klicken Sie im **Projektmappen-Explorer** mit der rechten Maustaste auf **SSIS-Pakete**, und wählen Sie dann **Einfügen** aus.

    Standardmäßig lautet der Name des kopierten Pakets **Lesson 4.dtsx**.

5.  Doppelklicken Sie im **Projektmappen-Explorer** auf **Lesson 4.dtsx**, um das Paket zu öffnen.

6.  Klicken Sie erst mit der rechten Maustaste auf eine beliebige Stelle im Hintergrund der Entwurfsoberfläche **Ablaufsteuerung**, und klicken Sie anschließend auf **Eigenschaften**.

7.  Ändern Sie im Fenster **Eigenschaften** die Eigenschaft **Name** in **Lesson 5** (Lektion 5).

8.  Aktivieren Sie zunächst das Kontrollkästchen für die Eigenschaft **ID**, klicken Sie dann auf den Dropdownpfeil und anschließend auf **\<Neue ID generieren>**.

## <a name="add-the-completed-lesson-4-package"></a>Hinzufügen des abgeschlossenen Pakets aus Lektion 4

1.  Öffnen Sie [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Data Tools und das SSIS-Lernprogrammprojekt.

2.  Klicken Sie im **Projektmappen-Explorer** mit der rechten Maustaste auf **SSIS-Pakete**, und klicken Sie auf **Vorhandenes Paket hinzufügen**.

3.  Wählen Sie im Dialogfeld **Kopie des vorhandenen Pakets hinzufügen** unter **Paketspeicherort**die Option **Dateisystem**aus.

4.  Klicken Sie auf die Schaltfläche zum Durchsuchen **(…)**, navigieren Sie zu **Lesson 4.dtsx** auf Ihrem Computer, und wählen Sie anschließend **Öffnen** aus.

5.  Kopieren Sie das Paket aus Lektion 4, und fügen Sie es wie in den Schritten 3 bis 8 im vorherigen Abschnitt beschrieben ein.
  
## <a name="go-to-next-task"></a>Weiter zur nächsten Aufgabe  
[Schritt 2: Aktivieren und Konfigurieren von Paketkonfigurationen](../integration-services/lesson-5-2-enabling-and-configuring-package-configurations.md)  
  
