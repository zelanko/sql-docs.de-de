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
ms.openlocfilehash: 808dec10c92bffe66122bfa9a55d7db1cc64f62e
ms.sourcegitcommit: 63aef5a96905f0b026322abc9ccb862ee497eebe
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 09/25/2020
ms.locfileid: "91364170"
---
# <a name="tutorial-back-up-and-restore-databases-using-azure-data-studio"></a>Tutorial: Sichern und Wiederherstellen von Datenbanken mithilfe von Azure Data Studio

In diesem Tutorial lernen Sie, wie Sie Azure Data Studio für folgende Zwecke verwenden:
> [!div class="checklist"]
> * Sichern einer Datenbank
> * Anzeigen des Sicherungsstatus
> * Generieren des Skripts, mit dem die Sicherung durchgeführt wird
> * Wiederherstellen einer Datenbank
> * Anzeigen des Status der Wiederherstellungsaufgabe

## <a name="prerequisites"></a>Voraussetzungen

Für dieses Tutorial ist die SQL Server-Datenbank *TutorialDB* erforderlich. Führen Sie die im folgenden Schnellstart beschriebenen Schritte aus, um die TutorialDB-Datenbank zu erstellen:

* [Verwenden von Azure Data Studio zum Verbinden mit und Abfragen von SQL Server](quickstart-sql-server.md)

Für dieses Tutorial ist eine Verbindung mit einer SQL Server-Datenbank erforderlich. In Azure SQL-Datenbank gibt es automatisierte Sicherungen, sodass Azure Data Studio keine Azure SQL-Datenbank-Sicherung und -Wiederherstellung ausführt. Weitere Informationen finden Sie unter [Informationen zu automatischen Sicherungen von SQL-Datenbank](/azure/sql-database/sql-database-automated-backups).

## <a name="back-up-a-database"></a>So sichern Sie eine Datenbank

1. Öffnen Sie das Dashboard der TutorialDB-Datenbank über die Seitenleiste **SERVER**. Drücken Sie dann **STRG+G**, erweitern Sie die Option **Datenbanken**, klicken Sie mit der rechten Maustaste auf **TutorialDB**, und klicken Sie anschließend auf **Verwalten**.

1. Öffnen Sie das Dialogfeld **Datenbank sichern**, indem Sie im Widget **Aufgaben** auf **Sichern** klicken.

   ![Screenshot des Widgets „Aufgaben“](./media/tutorial-backup-restore-sql-server/tasks.png)

1. In diesem Tutorial werden die Standardsicherungsoptionen verwendet. Klicken Sie deshalb auf **Sichern**.

   ![Screenshot des Dialogfelds „Sichern“](./media/tutorial-backup-restore-sql-server/backup-dialog.png)

Nachdem Sie auf **Sichern** geklickt haben, wird das Dialogfeld **Datenbank sichern** ausgeblendet, und der Sicherungsvorgang wird gestartet.

## <a name="view-the-backup-status-and-the-backup-script"></a>Anzeigen des Sicherungsstatus und des Sicherungsskripts

1. Dann wird der Bereich **Aufgabenverlauf** angezeigt. Alternativ können Sie auch **STRG+T** drücken, um ihn zu öffnen.

   ![Screenshot des Bereichs „Aufgabenverlauf“](./media/tutorial-backup-restore-sql-server/task-history.png)

1. Um das Sicherungsskript im Editor anzuzeigen, klicken Sie mit der rechten Maustaste auf **Datenbank sichern erfolgreich**, und wählen Sie **Skript** aus.

   ![Screenshot des Sicherungsskripts](./media/tutorial-backup-restore-sql-server/task-script.png)

## <a name="restore-a-database-from-a-backup-file"></a>Wiederherstellen einer Datenbank aus einer Sicherungsdatei

1. Öffnen Sie die Seitenleiste **SERVER**, indem Sie **STRG+G** drücken. Klicken Sie erst mit der rechten Maustaste auf Ihren Server und anschließend mit der linken auf **Verwalten**.

1. Öffnen Sie das Dialogfeld **Datenbank wiederherstellen**, indem Sie im Widget **Aufgaben** auf **Wiederherstellen** klicken.

   ![Screenshot der Aufgabe „Wiederherstellen“](media/tutorial-backup-restore-sql-server/tasks-restore.png)

1. Klicken Sie im Feld **Wiederherstellen aus** auf **Sicherungsdatei**.

1. Klicken Sie auf die Auslassungspunkte (...) im Feld **Pfad zur Sicherungsdatei**, und wählen Sie die aktuelle Sicherungsdatei für *TutorialDB* aus.

1. Geben Sie **TutorialDB_Restored** in das Feld **Zieldatenbank** im Abschnitt **Ziel** ein, um die Sicherungsdatei in einer neuen Datenbank wiederherzustellen. Dann wählen Sie **Wiederherstellen** aus.

   ![Screenshot zur Wiederherstellung der Sicherung](./media/tutorial-backup-restore-sql-server/restore.png)

1. Den Status des Wiederherstellungsvorgangs können Sie abrufen, indem Sie **STRG+T** drücken, um den **Aufgabenverlauf** zu öffnen.

   ![Screenshot zur Wiederherstellung des Aufgabenverlaufs](./media/tutorial-backup-restore-sql-server/task-history-restore.png)