---
title: Speichern von Skripts als Projekte oder Projektmappen | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- tools-ssms
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 72dfd37f-dbe7-4d1d-bda6-7eb54c7922d3
caps.latest.revision: 32
author: craigg-msft
ms.author: craigg
manager: jhubbard
ms.openlocfilehash: 84e56a0fdcf6847b582cd85c7e75947cec8557c8
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/19/2018
ms.locfileid: "36159679"
---
# <a name="save-scripts-as-projects-or-solutions"></a>Speichern von Skripts als Projekte oder Lösungen
  Entwickler, die mit [!INCLUDE[msCoName](../../includes/msconame-md.md)] Visual Studio vertraut sind, werden die Einführung des Projektmappen-Explorers in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]begrüßen. Die Skripts, die Ihre Geschäftsaktivitäten unterstützen, können in Skriptprojekten zusammengestellt werden, und die Skriptprojekte können zusammen als Projektmappe verwaltet werden. Wenn Skripts in Skriptprojekten und Projektmappen verwaltet werden, können sie zusammen als Gruppe geöffnet werden. Sie können aber auch gemeinsam in einem Quellcodeverwaltungsprogramm wie Visual SourceSafe gespeichert werden. Skriptprojekte umfassen die Verbindungsinformationen für die Skripts, sodass diese ordnungsgemäß ausgeführt werden. Sie können auch andere Dateien enthalten, wie z. B. eine unterstützende Textdatei.  
  
 In der folgenden Übung erstellen Sie ein kurzes Skript, mit dem die [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] -Datenbank abgefragt wird und das in einem Skriptprojekt und einer Projektmappe gespeichert wird.  
  
## <a name="using-script-projects-and-solutions"></a>Verwenden von Skriptprojekten und Projektmappen  
  
#### <a name="to-create-a-script-project-and-solution"></a>So erstellen Sie ein Skriptprojekt und eine Projektmappe  
  
1.  Öffnen Sie [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)], und stellen Sie eine Verbindung mit einem Server her, auf dem Objekt-Explorer installiert ist.  
  
2.  Zeigen Sie im Menü **Datei** auf **Neu**, und klicken Sie dann auf **Projekt**. Das Dialogfeld **Neues Projekt** wird geöffnet.  
  
3.  Geben Sie im Textfeld **Name** den Namen **StatusCheck**ein, klicken Sie unter **Vorlagen** auf **SQL Server-Skripts**, und klicken Sie dann auf **OK** , um eine neue Projektmappe und ein neues Skriptprojekt zu öffnen.  
  
4.  Klicken Sie im Objekt-Explorer mit der rechten Maustaste auf **Verbindungen**, und klicken Sie anschließend auf **Neue Verbindung**. Das Dialogfeld **Verbindung mit Server herstellen** wird geöffnet.  
  
5.  Geben Sie im Listenfeld **Servername** den Namen Ihres Servers ein.  
  
6.  Klicken Sie auf **Optionen**, und klicken Sie dann auf die Registerkarte **Verbindungseigenschaften** .  
  
7.  Wählen Sie im Dialogfeld **Verbindung mit Datenbank herstellen** die [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] -Datenbank aus, und klicken Sie dann auf **Verbinden**. Dem Projekt werden die Verbindungsinformationen einschließlich der Datenbank hinzugefügt.  
  
8.  Wenn das Eigenschaftenfenster nicht angezeigt wird, klicken Sie im Projektmappen-Explorer auf die neue Verbindung und drücken dann F4. Daraufhin werden die Verbindungseigenschaften angezeigt, in denen als **Ausgangsdatenbank** die [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)]-Datenbank enthalten ist.  
  
9. Klicken Sie im Projektmappen-Explorer mit der rechten Maustaste auf die Verbindung, und klicken Sie anschließend auf **Neue Abfrage**. Eine neue Abfrage mit der Bezeichnung **SQLQuery1.sql** wird erstellt, für die eine Verbindung mit der [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] -Datenbank auf Ihrem Server hergestellt wird und die Ihrem Skriptprojekt hinzugefügt wird.  
  
10. Geben Sie im Abfrage-Editor die folgende Abfrage ein, um festzustellen, bei wie vielen Aufträgen die Fälligkeitstermine vor den Startterminen der Aufträge liegen. (Sie können den Code im Fenster des Lernprogramms kopieren und dann einfügen.)  
  
    ```  
    USE AdventureWorks2012;  
    GO  
    SELECT COUNT(WorkOrderID)  
    FROM Production.WorkOrder  
    WHERE DueDate < StartDate;  
  
    ```  
  
    > [!NOTE]  
    >  Wenn Sie zum Eingeben der Abfrage mehr Platz brauchen, drücken Sie UMSCHALT+ALT+EINGABE, um in den Vollbildmodus zu wechseln.  
  
11. Klicken Sie im Projektmappen-Explorer mit der rechten Maustaste auf **SQLQuery1**und anschließend auf **Umbenennen**. Geben Sie als neuen Namen für die Abfrage **Check Workorders****.sql** ein, und drücken Sie anschließend die EINGABETASTE.  
  
12. Zum Speichern Ihrer Projektmappe und Ihres Skriptprojekts klicken Sie im Menü **Datei** auf **Alles speichern**.  
  
## <a name="next-task-in-lesson"></a>Nächste Aufgabe in dieser Lektion  
 [Zusammenfassung: Projektmappen und Skriptprojekte](lesson-3-4-summary-solutions-and-script-projects.md)  
  
  