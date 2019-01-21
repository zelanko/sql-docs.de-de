---
title: 'Schritt 1: Kopieren des Pakets aus Lektion 3 | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 01/07/2019
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.technology: integration-services
ms.topic: tutorial
ms.assetid: 0d053786-5203-43f3-a613-27a8dd2bc44a
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: ba011dbb600ca2903aca6f9a3c6415f4663aea0a
ms.sourcegitcommit: e2fa721b6f46c18f1825dd1b0d56c0a6da1b2be1
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/11/2019
ms.locfileid: "54211071"
---
# <a name="lesson-4-1-copy-the-lesson-3-package"></a>Lektion 4.1: Kopieren des Pakets aus Lektion 3

In dieser Aufgabe erfahren Sie, wie Sie eine Kopie des Pakets „Lesson 3.dtsx“ aus Lektion 3 erstellen. Wenn Sie Lektion 3 nicht abgeschlossen haben, können Sie stattdessen das fertige Paket aus dem Tutorial im Projekt hinzufügen und dann kopieren. Sie verwenden diese neue Kopie für den weiteren Verlauf von Lektion 4.  
  
## <a name="create-the-lesson-4-package"></a>Erstellen des Pakets aus Lektion 4  
  
Gehen Sie wie folgt vor, wenn Sie das fertige Paket aus Lektion 3 kopieren möchten.  Informationen zum Kopieren des Beispielpakets aus Lektion 3 finden Sie im nächsten Abschnitt.

1.  Wenn [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Data Tools noch nicht geöffnet ist, klicken Sie auf **Start** > **All Programs** (Alle Programme)  > **Microsoft SQL Server 2017**, und wählen Sie **SQL Server Data Tools** aus.

2.  Klicken Sie im Menü **Datei** auf **Öffnen** > **Projekt/Projektmappe**, wählen Sie den Ordner **SSIS Tutorial** (SSIS-Tutorial) aus, und klicken Sie auf **Öffnen**. Doppelklicken Sie anschließend auf **SSIS Tutorial.sln**.

3.  Klicken Sie im **Projektmappen-Explorer** mit der rechten Maustaste auf **Lesson 3.dtsx**, und klicken Sie dann auf **Kopieren**.

4.  Klicken Sie im **Projektmappen-Explorer** mit der rechten Maustaste auf **SSIS-Pakete**, und klicken Sie dann auf **Einfügen**.

    Standardmäßig lautet der Name des kopierten Pakets **Lesson 4.dtsx**.

5.  Doppelklicken Sie im **Projektmappen-Explorer** auf **Lesson 4.dtsx**, um das Paket zu öffnen.

6.  Klicken Sie erst mit der rechten Maustaste auf eine beliebige Stelle im Hintergrund der Entwurfsoberfläche **Ablaufsteuerung**, und klicken Sie anschließend auf **Eigenschaften**.

7.  Ändern Sie im Fenster **Eigenschaften** die Eigenschaft **Name** in **Lesson 4** (Lektion 4).

8.  Aktivieren Sie zunächst das Kontrollkästchen für die Eigenschaft **ID**, klicken Sie dann auf den Dropdownpfeil und anschließend auf **\<Neue ID generieren>**.

## <a name="add-the-completed-lesson-3-package"></a>Hinzufügen des fertigen Pakets aus Lektion 3

1.  Öffnen Sie [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Data Tools und das SSIS-Lernprogrammprojekt.

2.  Klicken Sie im **Projektmappen-Explorer** mit der rechten Maustaste auf **SSIS-Pakete**, und klicken Sie auf **Vorhandenes Paket hinzufügen**.

3.  Wählen Sie im Dialogfeld **Kopie des vorhandenen Pakets hinzufügen** unter **Paketspeicherort**die Option **Dateisystem**aus.

4.  Klicken Sie auf die Schaltfläche zum Durchsuchen **(…)**, navigieren Sie zu **Lesson 3.dtsx** auf Ihrem Computer, und klicken Sie anschließend auf **Öffnen**.

5.  Kopieren Sie das Paket aus Lektion 3, und fügen Sie es wie in den Schritten 3 bis 8 im vorherigen Abschnitt beschrieben ein.

  
## <a name="go-to-next-task"></a>Weiter zur nächsten Aufgabe  
[Schritt 2: Erstellen einer beschädigten Datei](../integration-services/lesson-4-2-creating-a-corrupted-file.md)  
  
