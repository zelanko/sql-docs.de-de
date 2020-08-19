---
description: 'Lektion 3.1: Kopieren des Pakets aus Lektion 2'
title: 'Schritt 1: Kopieren des Pakets aus Lektion 2 | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 01/04/2019
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.technology: integration-services
ms.topic: tutorial
ms.assetid: 4bd91402-4e37-41de-ab78-8ca5a1948a37
author: chugugrace
ms.author: chugu
ms.openlocfilehash: d5916961ea33dd7534d6b98ff2c158f718ea6db7
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 08/17/2020
ms.locfileid: "88390716"
---
# <a name="lesson-3-1-copy-the-lesson-2-package"></a>Lektion 3.1: Kopieren des Pakets aus Lektion 2

[!INCLUDE[sqlserver-ssis](../includes/applies-to-version/sqlserver-ssis.md)]



In dieser Aufgabe erfahren Sie, wie Sie eine Kopie des Pakets „Lesson 2.dtsx“ aus Lektion 2 erstellen. Falls Sie Lektion 2 nicht abgeschlossen haben, können Sie stattdessen das vollständige Paket aus Lektion 2, das im Tutorial des Projekts enthalten ist, hinzufügen und anschließend kopieren. Sie verwenden diese neue Kopie für den weiteren Verlauf von Lektion 3.

## <a name="create-the-lesson-3-package"></a>Erstellen des Pakets für Lektion 3

Gehen Sie wie folgt vor, wenn Sie das fertige Paket aus Lektion 2 kopieren möchten.  Informationen zum Kopieren des Beispielpakets aus Lektion 2 finden Sie im nächsten Abschnitt.

1.  Wenn [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Data Tools noch nicht geöffnet ist, klicken Sie auf **Start** > **All Programs** (Alle Programme)  > **Microsoft SQL Server 2017**, und wählen Sie **SQL Server Data Tools** aus.

2.  Klicken Sie im Menü **Datei** auf **Öffnen** > **Projekt/Projektmappe**, wählen Sie den Ordner **SSIS Tutorial** (SSIS-Tutorial) aus, und klicken Sie auf **Öffnen**. Doppelklicken Sie anschließend auf **SSIS Tutorial.sln**.

3.  Klicken Sie im **Projektmappen-Explorer** erst mit der rechten Maustaste auf **Lesson 2.dtsx**, und klicken Sie dann auf **Kopieren**.

4.  Klicken Sie im **Projektmappen-Explorer** mit der rechten Maustaste auf **SSIS-Pakete**, und klicken Sie dann auf **Einfügen**.

    Standardmäßig lautet der Name des kopierten Pakets „Lesson 3.dtsx“.

5.  Doppelklicken Sie im **Projektmappen-Explorer** auf **Lesson 3.dtsx**, um das Paket zu öffnen.

6.  Klicken Sie erst mit der rechten Maustaste auf eine beliebige Stelle im Hintergrund der Entwurfsoberfläche **Ablaufsteuerung**, und klicken Sie anschließend auf **Eigenschaften**.

7.  Ändern Sie im Fenster **Eigenschaften** die Eigenschaft **Name** in **Lesson 3** (Lektion 3).

8.  Aktivieren Sie zunächst das Kontrollkästchen für die Eigenschaft **ID**, klicken Sie dann auf den Dropdownpfeil und anschließend auf **\<Generate New ID>** .

## <a name="add-the-completed-lesson-2-package"></a>Hinzufügen des fertigen Pakets aus Lektion 2

1.  Öffnen Sie [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Data Tools und das SSIS-Lernprogrammprojekt.

2.  Klicken Sie im **Projektmappen-Explorer** erst mit der rechten Maustaste auf **SSIS-Pakete**, und klicken Sie anschließend auf **Vorhandenes Paket hinzufügen**.

3.  Wählen Sie im Dialogfeld **Add Copy of Existing Package** (Kopie des vorhandenen Pakets hinzufügen) unter **Paketspeicherort** die Option **Dateisystem** aus.

4.  Klicken Sie auf die Schaltfläche zum Durchsuchen **(…)** , navigieren Sie zu **Lesson 2.dtsx** auf Ihrem Computer, und klicken Sie anschließend auf **Öffnen**.

5.  Kopieren Sie das Paket aus Lektion 3, und fügen Sie es wie in den Schritten 3 bis 8 im vorherigen Abschnitt beschrieben ein.  
  
## <a name="go-to-next-task"></a>Weiter zur nächsten Aufgabe
[Schritt 2: Hinzufügen und Konfigurieren der Protokollierung](../integration-services/lesson-3-2-adding-and-configuring-logging.md)  
  
