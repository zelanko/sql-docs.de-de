---
title: 'Lektion 9: Erstellen und Ausführen der Anwendung | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: f52d3f3a-0b09-4b34-9112-0b3655271587
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: b21ee398eade4878d4f2273f17314dd184af2310
ms.sourcegitcommit: 2d4067fc7f2157d10a526dcaa5d67948581ee49e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/28/2020
ms.locfileid: "78176866"
---
# <a name="lesson-9-build-and-run-the-application"></a>Lesson 9: Build and Run the Application
  Nachdem Sie einen Datenfilter für die Datentabelle erstellt haben, erstellen Sie im nächsten Schritt eine Websiteanwendung und führen diese aus.

### <a name="to-build-and-run-the-application"></a>So erstellen Sie die Anwendung und führen sie aus

1.  Drücken Sie **STRG+F5** , um die Seite Default.aspx ohne Debuggen auszuführen, oder drücken Sie F5, um die Seite mit Debuggen auszuführen.

     Der Bericht wird im Rahmen des Erstellungsprozesses kompiliert und alle Fehler (z.B. Syntaxfehler in einem Berichtsausdruck) werden der **Aufgabenliste** unten im Visual Studio-Fenster hinzugefügt.

     Die Webseite wird im Browser geöffnet. Der Bericht wird vom ReportViewer-Steuerelement angezeigt. Sie können die Symbolleiste zum Navigieren, Zoomen und Exportieren des Berichts in Excel verwenden.

2.  Zeigen Sie mit der Maus auf eine der Zeilen unter der Spalte **Name** . Der Mauszeiger wird als Handsymbol angezeigt.

3.  Klicken Sie auf einen Wert in der Spalte **Name** . Der untergeordnete Bericht wird mit den entsprechenden gefilterten Daten angezeigt.

4.  Klicken Sie in der **ReportViewer**-Symbolleiste auf das Symbol **Zurück zum übergeordneten Bericht** , um zurück zum **übergeordneten** Bericht zu navigieren.

     ![SSRS-Drillthrough mithilfe von Report Viewer](../../2014/tutorials/media/ssrs-drillthrough-report.png "SSRS-Drillthrough mithilfe von Report Viewer")

5.  Schließen Sie den Browser, um den Vorgang zu beenden.


