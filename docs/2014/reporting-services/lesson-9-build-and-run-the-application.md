---
title: 'Lektion 9: Erstellen und Ausführen der Anwendung | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- reporting-services-native
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: f52d3f3a-0b09-4b34-9112-0b3655271587
caps.latest.revision: 8
author: douglaslM
ms.author: douglasl
manager: mblythe
ms.openlocfilehash: fdb619e98fe28742ac6b96acc6419513addfae25
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/19/2018
ms.locfileid: "36049405"
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
  
     ![SSRS mithilfe von ReportViewer Drillthrough](../../2014/tutorials/media/ssrs-drillthrough-report.png "Ssrs mithilfe von ReportViewer Drillthrough")  
  
5.  Schließen Sie den Browser, um den Vorgang zu beenden.  
  
  