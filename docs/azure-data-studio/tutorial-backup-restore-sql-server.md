---
title: Sichern und Wiederherstellen einer Datenbank
titleSuffix: Azure Data Studio
description: Informationen Sie zum Sichern und Wiederherstellen einer Datenbank mithilfe von Azure Data Studio
ms.prod: sql
ms.technology: azure-data-studio
ms.topic: tutorial
author: markingmyname
ms.author: maghan
manager: craigg
ms.reviewer: alayu; sstein
ms.custom: seodec18
ms.date: 09/24/2018
ms.openlocfilehash: 5550a1151ed0fb71a769e7990d9cd47b3e9b0e47
ms.sourcegitcommit: bb5484b08f2aed3319a7c9f6b32d26cff5591dae
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/06/2019
ms.locfileid: "65089698"
---
# <a name="backup-and-restore-databases-using-includename-sosincludesname-sos-shortmd"></a>Sichern und Wiederherstellen von Datenbanken mithilfe von [!INCLUDE[name-sos](../includes/name-sos-short.md)]

In diesem Tutorial erfahren Sie, wie Sie mit [!INCLUDE[name-sos](../includes/name-sos-short.md)] auf:
> [!div class="checklist"]
> * Sichern einer Datenbank 
> * Anzeigen des Status den Sicherungen
> * Generiert das Skript verwendet, um die Sicherung durchzuführen.
> * Wiederherstellen einer Datenbank
> * Anzeigen des Status des Wiederherstellungstasks

## <a name="prerequisites"></a>Voraussetzungen

In diesem Tutorial ist die SQL Server *"tutorialdb"*. Zum Erstellen der *"tutorialdb"* Datenbank, führen Sie eine der folgenden schnellstartanleitungen:

- [Verbinden und Abfragen von SQL Server verwenden [!INCLUDE[name-sos-short](../includes/name-sos-short.md)]](quickstart-sql-server.md)

Dieses Lernprogramm erfordert die Verbindung mit einer SQL Server-Datenbank. Azure SQL-Datenbank hat Sicherungen, automatisiert werden, damit Azure Data Studio keine Azure SQL-Datenbank sicherungs- und Wiederherstellungsvorgänge auszuführen. Weitere Informationen finden Sie unter [erfahren Sie mehr über die automatischen Sicherungen von SQL-Datenbank](https://docs.microsoft.com/azure/sql-database/sql-database-automated-backups).

## <a name="backup-a-database"></a>Sichern einer Datenbank

1. Öffnen Sie das Datenbank-Dashboard "tutorialdb" (Öffnen Sie die **Server** Randleiste (**STRG + G**), erweitern Sie **Datenbanken**, mit der rechten Maustaste **"tutorialdb"**, und wählen Sie **verwalten**).

2. Öffnen der **datenbanksicherung** Dialogfeld (klicken Sie auf **Sicherung** auf die **Aufgaben** Widget).

   ![Aufgaben-widget](./media/tutorial-backup-restore-sql-server/tasks.png)

3. In diesem Tutorial verwendet die Standard-Sicherungsoptionen, klicken Sie daher auf **Backup**.
   ![Dialogfeld-Sicherung](./media/tutorial-backup-restore-sql-server/backup-dialog.png)

Nach dem Klicken auf **Backup**, **datenbanksicherung** Dialogfeld nicht mehr angezeigt, und der Sicherungsvorgang beginnt.

## <a name="view-the-backup-status-and-view-the-backup-script"></a>Zeigen Sie des Status den Sicherungen an und zeigen das sicherungs-Skript an

1. Öffnen der **Taskverlauf** Randleiste, indem Sie auf das Uhrsymbol auf der *Aktionsleiste* , oder drücken Sie **STRG + T**.

   ![Taskverlauf](./media/tutorial-backup-restore-sql-server/task-history.png)

2. Um das sicherungs-Skript im Editor anzuzeigen, Maustaste **Sicherungsdatenbank erfolgreich** , und wählen Sie **Skript**.

   ![Sicherungsskript](./media/tutorial-backup-restore-sql-server/task-script.png) 

## <a name="restore-a-database-from-a-backup-file"></a>Wiederherstellen einer Datenbank aus einer Sicherungsdatei


1. Öffnen der **Server** Randleiste (**STRG + G**) mit der rechten Maustaste auf den Server, und wählen Sie **verwalten**. 

2. Öffnen der **Wiederherstellen einer Datenbank** Dialogfeld (klicken Sie auf **wiederherstellen** auf die **Aufgaben** Widget).

2. Wählen Sie **Sicherungsdatei** in die **wiederherstellen aus** Feld. 

3. Klicken Sie auf die Auslassungspunkte (...) in der **Dateipfad der Zertifikatsicherung** ein, und wählen Sie die neuesten Sicherungsdatei für *"tutorialdb"*.

3. Typ **TutorialDB_Restored** in die **Zieldatenbank** -Feld in der **Ziel** Abschnitt aus, um die Sicherungsdatei in einer neuen Datenbank wiederherzustellen.

   ![Wiederherstellungsprozess](./media/tutorial-backup-restore-sql-server/restore.png)

4. Klicken Sie auf **wiederherstellen**

5. Drücken Sie zum Anzeigen des Status des Wiederherstellungsvorgangs **STRG + T** zum Öffnen der **Taskverlauf** Randleiste.

   ![Wiederherstellungsprozess](./media/tutorial-backup-restore-sql-server/task-history-restore.png)


In diesem Tutorial haben Sie gelernt, wie die folgenden Aufgaben ausgeführt werden:
> [!div class="checklist"]
> * Sichern einer Datenbank 
> * Anzeigen des Status den Sicherungen
> * Generiert das Skript verwendet, um die Sicherung durchzuführen.
> * Wiederherstellen einer Datenbank
> * Anzeigen des Status des Wiederherstellungstasks

