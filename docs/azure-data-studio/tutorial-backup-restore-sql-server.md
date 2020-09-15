---
title: Sichern und Wiederherstellen einer Datenbank
description: In diesem Tutorial erfahren Sie, wie Sie Datenbanken mithilfe von Azure Data Studio sichern und wiederherstellen.
ms.prod: azure-data-studio
ms.technology: azure-data-studio
ms.topic: tutorial
author: markingmyname
ms.author: maghan
ms.reviewer: alayu
ms.custom: seodec18
ms.date: 11/04/2019
ms.openlocfilehash: a7d3ca36634e449dd26dfdb0df75f09608d25f51
ms.sourcegitcommit: 5da46e16b2c9710414fe36af9670461fb07555dc
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 09/01/2020
ms.locfileid: "89283691"
---
# <a name="tutorial-backup-and-restore-databases-using-azure-data-studio"></a>Tutorial: Sichern und Wiederherstellen von Datenbanken mithilfe von Azure Data Studio

In diesem Tutorial lernen Sie, wie Sie Azure Data Studio für folgende Zwecke verwenden:
> [!div class="checklist"]
> * So sichern Sie eine Datenbank 
> * Anzeigen des Sicherungsstatus
> * Generieren des Skripts, mit dem die Sicherung ausgeführt wird
> * Wiederherstellen einer Datenbank
> * Anzeigen des Status der Wiederherstellungsaufgabe

## <a name="prerequisites"></a>Voraussetzungen

Für dieses Tutorial ist die SQL Server-Datenbank *TutorialDB* erforderlich. Um die *TutorialDB*-Datenbank zu erstellen, führen Sie eine der folgenden Schnellstartanleitungen vollständig aus:

* [Herstellen einer Verbindung mit und Abfragen von SQL Server mithilfe von [!INCLUDE[name-sos-short](../includes/name-sos-short.md)]](quickstart-sql-server.md)

In diesem Tutorial muss eine Verbindung mit einer SQL Server-Datenbank hergestellt werden. In Azure SQL-Datenbank gibt es automatisierte Sicherungen, sodass Azure Data Studio keine Azure SQL-Datenbank-Sicherung und -Wiederherstellung ausführt. Ausführliche Informationen finden Sie unter [Automatisierte Sicherungen](/azure/sql-database/sql-database-automated-backups).

## <a name="back-up-a-database"></a>So sichern Sie eine Datenbank

1. Öffnen Sie das Dashboard der TutorialDB-Datenbank (öffnen Sie die Seitenleiste **SERVER** (**STRG+G**), erweitern Sie **Datenbanken**, klicken Sie mit der rechten Maustaste auf **TutorialDB**, und wählen Sie **Verwalten** aus).

2. Öffnen Sie das Dialogfeld **Datenbank sichern** (klicken Sie auf **Sichern** auf dem Widget **Aufgaben**).

   ![Widget „Aufgaben“](./media/tutorial-backup-restore-sql-server/tasks.png)

3. In diesem Tutorial werden die Standardsicherungsoptionen verwendet. Klicken Sie deshalb auf **Sichern**.
   ![Dialogfeld für Sichern](./media/tutorial-backup-restore-sql-server/backup-dialog.png)

Nachdem Sie auf **Sichern** geklickt haben, wird das Dialogfeld **Datenbank sichern** ausgeblendet, und der Sicherungsvorgang beginnt.

## <a name="view-the-backup-status-and-view-the-backup-script"></a>Anzeigen des Sicherungsstatus und Anzeigen des Sicherungsskripts

1. Der Bereich  **Taskverlauf** wird angezeigt, oder drücken Sie **STRG+T**.

   ![Aufgabenverlauf](./media/tutorial-backup-restore-sql-server/task-history.png)

2. Um das Sicherungsskript im Editor anzuzeigen, klicken Sie mit der rechten Maustaste auf **Datenbank sichern erfolgreich**, und wählen Sie **Skript** aus.

   ![Sicherungsskript](./media/tutorial-backup-restore-sql-server/task-script.png)

## <a name="restore-a-database-from-a-backup-file"></a>Wiederherstellen einer Datenbank aus einer Sicherungsdatei

1. Öffnen Sie die Seitenleiste **SERVER** (**STRG+G**), klicken Sie mit der rechten Maustaste auf Ihren Server, und wählen Sie **Verwalten** aus.

2. Öffnen Sie das Dialogfeld **Datenbank wiederherstellen** (klicken Sie auf **Wiederherstellen** auf dem Widget **Aufgaben**).

   ![Aufgabe wiederherstellen](media/tutorial-backup-restore-sql-server/tasks-restore.png)

3. Wählen Sie **Sicherungsdatei** im Feld **Wiederherstellen von** aus.

4. Klicken Sie auf die Auslassungspunkte (...) im Feld **Pfad zur Sicherungsdatei**, und wählen Sie die aktuelle Sicherungsdatei für *TutorialDB* aus.

5. Geben Sie **TutorialDB_Restored** in das Feld **Zieldatenbank** im Abschnitt **Ziel** ein, um die Sicherungsdatei in einer neuen Datenbank wiederherzustellen. Dann wählen Sie **Wiederherstellen** aus.

   ![Sicherung wiederherstellen](./media/tutorial-backup-restore-sql-server/restore.png)

6. Um den Status des Wiederherstellungsvorgangs anzuzeigen, drücken Sie **STRG+T**, um den **Taskverlauf** zu öffnen.

   ![Verlauf „Aufgabe wiederherstellen“](./media/tutorial-backup-restore-sql-server/task-history-restore.png)