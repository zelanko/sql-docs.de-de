---
title: 'Schritt 1: Kopieren des Pakets aus Lektion 1 | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 01/03/2019
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.technology: integration-services
ms.topic: tutorial
ms.assetid: 7f1616c2-2b4e-4010-be50-27d7b897403a
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 31979c1515fa54a059bddf562ddb42e4ff6131f4
ms.sourcegitcommit: dd794633466b1da8ead9889f5e633bdf4b3389cd
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/09/2019
ms.locfileid: "54143180"
---
# <a name="lesson-2-1-copy-the-lesson-1-package"></a>Lektion 2.1: Kopieren des Pakets aus Lektion 1

In dieser Übung erfahren Sie, wie Sie eine Kopie des Pakets **Lesson 1.dtsx** erstellen. Wenn Sie Lektion 1 nicht abgeschlossen haben, können Sie das fertige Paket verwenden, das in diesem Tutorial enthalten ist. Sie verwenden die neue Kopie für den weiteren Verlauf von Lektion 2.  
  
## <a name="create-the-lesson-2-package"></a>Erstellen des Pakets für Lektion 2  

Gehen Sie wie folgt vor, wenn Sie das fertige Paket aus Lektion 1 kopieren möchten.  Informationen zum Kopieren des Beispielpakets für Lektion 1 finden Sie im nächsten Abschnitt.
  
1.  Wenn [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Data Tools noch nicht geöffnet ist, klicken Sie auf **Start** > **All Programs** (Alle Programme)  > **Microsoft SQL Server 2017**, und wählen Sie **SQL Server Data Tools** aus.  
  
2.  Klicken Sie im Menü **Datei** auf **Öffnen** > **Projekt/Projektmappe**, wählen Sie den Ordner **SSIS Tutorial** (SSIS-Tutorial) aus, und klicken Sie auf **Öffnen**. Doppelklicken Sie anschließend auf **SSIS Tutorial.sln**.  
  
3.  Klicken Sie im **Projektmappen-Explorer** mit der rechten Maustaste auf **Lesson 1.dtsx**, und klicken Sie dann auf **Kopieren**.  
  
4.  Klicken Sie im **Projektmappen-Explorer** mit der rechten Maustaste auf **SSIS-Pakete**, und klicken Sie dann auf **Einfügen**.  
  
    Standardmäßig wird das kopierte Paket **Lesson 2.dtsx** genannt.  
  
5.  Doppelklicken Sie im **Projektmappen-Explorer** auf **Lesson 2.dtsx**, um das Paket zu öffnen.  
  
6.  Klicken Sie erst mit der rechten Maustaste auf eine beliebige Stelle im Hintergrund der Entwurfsoberfläche **Ablaufsteuerung**, und klicken Sie anschließend auf **Eigenschaften**.  
  
7.  Ändern Sie im Fenster **Eigenschaften** die Eigenschaft **Name** in **Lesson 2** (Lektion 2).  
  
8.  Aktivieren Sie zunächst das Kontrollkästchen für die Eigenschaft **ID**, klicken Sie dann auf den Dropdownpfeil und anschließend auf **\<Neue ID generieren>**.  
  
## <a name="use-the-sample-lesson-1-package"></a>Verwenden des Beispielpakets aus Lektion 1  
  
1.  Öffnen Sie [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Data Tools und das SSIS-Lernprogrammprojekt.  
  
2.  Klicken Sie im **Projektmappen-Explorer** mit der rechten Maustaste auf **SSIS-Pakete**, und klicken Sie auf **Vorhandenes Paket hinzufügen**.  
  
3.  Wählen Sie im Dialogfeld **Add Copy of Existing Package** (Kopie des vorhandenen Pakets hinzufügen) unter **Paketspeicherort** die Option **Dateisystem** aus.  
  
4.  Klicken Sie auf die Schaltfläche zum Durchsuchen **(…)**, navigieren Sie zu **Lesson 1.dtsx** auf Ihrem Computer, und klicken Sie anschließend auf **Öffnen**.  
  
5.  Kopieren Sie das Paket aus Lektion 1, und fügen Sie es wie in den Schritten 3 bis 8 im vorherigen Abschnitt beschrieben ein.  
  
## <a name="go-to-next-task"></a>Weiter zur nächsten Aufgabe

[Schritt 2: Hinzufügen und Konfigurieren des Foreach-Schleifencontainers](../integration-services/lesson-2-2-adding-and-configuring-the-foreach-loop-container.md)  
  
