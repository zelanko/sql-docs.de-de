---
title: 'Lektion 6: Hinzufügen eines ReportViewer-Steuerelements zur Anwendung | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- reporting-services-native
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: f9492a97-5609-4059-ae76-0fba111d4968
caps.latest.revision: 7
author: douglaslM
ms.author: douglasl
manager: mblythe
ms.openlocfilehash: 51b08dce6f232bb08fd1d5f41bc1976aaa410331
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/19/2018
ms.locfileid: "36056639"
---
# <a name="lesson-6-add-a-reportviewer-control-to-the-application"></a>Lektion 6: Hinzufügen eines ReportViewer-Steuerelements zur Anwendung
  Nachdem Sie den untergeordneten Bericht mit dem Berichts-Assistenten entworfen haben, fügen Sie der Websiteanwendung im nächsten Schritt ein ReportViewer-Steuerelement hinzu.  
  
### <a name="to-add-a-reportviewer-control-to-the-application"></a>So fügen Sie der Anwendung das ReportViewer-Steuerelement hinzu  
  
1.  Klicken Sie im **Projektmappen-Explorer**mit der rechten Maustaste auf **Default.aspx**, und klicken Sie auf **Sicht-Designer**.  
  
2.  Ziehen Sie ein **ScriptManager** -Steuerelement aus der Gruppe **AJAX-Erweiterungen** im Fenster **Toolbox** auf die Entwurfsoberfläche.  
  
3.  Ziehen Sie ein **ReportViewer** -Steuerelement aus der Gruppe **Berichterstellung** unterhalb des **ScriptManager** -Steuerelements auf die Entwurfsoberfläche.  
  
4.  Öffnen Sie das Fenster **ReportViewer-Aufgaben** , indem Sie auf den Pfeil in der oberen rechten Ecke des **ReportViewer** -Steuerelements klicken.  
  
5.  Wählen Sie im Feld **Bericht auswählen** den erstellten übergeordneten Bericht aus.  
  
     Nachdem Sie einen Bericht ausgewählt haben, werden automatisch Instanzen der im Bericht verwendeten Datenquellen erstellt. Code wird generiert, um jede DataTable instanziieren (und die zugehörige [DataSet](http://msdn.microsoft.com/library/system.data.dataset\(v=vs.100\).aspx) Container). Ein [ObjectDataSource](http://msdn.microsoft.com/library/system.web.ui.webcontrols.objectdatasource\(v=vs.100\).aspx) Steuerelement auf die Entwurfsoberfläche, die für jede Datenquelle im Bericht verwendeten hinzugefügt wird. Dieses Datenquellen-Steuerelement wird automatisch konfiguriert.  
  
     Wenn Sie Microsoft Visual Studio 2012 verwenden, stellen Sie sicher, dass das ObjectDataSource-Steuerelement mit DataSet1, die vollständig mit dem Projektnamespace qualifiziert ist gebunden ist, wenn der vollqualifizierte Name im aufgeführt ist die **wählen Sie das Geschäftsobjekt**im Dropdown Listenfeld (z. B. Projectnamespace.DataSet1TableAdapters.ProductTableAdapter). Sie greifen auf das Listenfeld ObjectDataSource mit der rechten Maustaste, und klicken Sie dann auf **Datenquelle konfigurieren**.  
  
6.  Klicken Sie im Menü Erstellen auf Website erstellen.  
  
     Der Bericht wird kompiliert und alle Fehler, z. B. Syntaxfehler in einem Berichtsausdruck, werden im Bereich **Fehlerliste** angezeigt. Klicken Sie unten im Visual Studio-Fenster auf **Fehlerliste** , um den Bereich **Fehlerliste** anzuzeigen.  
  
## <a name="next-task"></a>Nächste Aufgabe  
 Sie haben der Websiteanwendung erfolgreich ein ReportViewer-Steuerelement hinzugefügt. Als Nächstes fügen Sie dem übergeordneten Bericht eine Drillthroughaktion hinzu.  
  
  