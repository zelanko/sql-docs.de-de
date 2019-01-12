---
title: Speichern von Skripts als Projekte oder Projektmappen | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
ms.assetid: 72dfd37f-dbe7-4d1d-bda6-7eb54c7922d3
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 6d17dd44f597d7b3ddfce574670e9e6bfd55f908
ms.sourcegitcommit: 7aa6beaaf64daf01b0e98e6c63cc22906a77ed04
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/09/2019
ms.locfileid: "54134830"
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
  
11. Klicken Sie im Projektmappen-Explorer mit der rechten Maustaste auf **SQLQuery1**und anschließend auf **Umbenennen**. Typ **Check Workorders.sql** als neuen Namen für die Abfrage, und drücken Sie die EINGABETASTE.  
  
12. Zum Speichern Ihrer Projektmappe und Ihres Skriptprojekts klicken Sie im Menü **Datei** auf **Alles speichern**.  
  
## <a name="next-task-in-lesson"></a>Nächste Aufgabe in dieser Lektion  
 [Zusammenfassung: Projektmappen und Skriptprojekte](lesson-3-4-summary-solutions-and-script-projects.md)  
  
  
