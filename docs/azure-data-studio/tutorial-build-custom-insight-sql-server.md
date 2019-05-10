---
title: 'Tutorial: Erstellen eines benutzerdefinierten Einblicks-Widgets'
titleSuffix: Azure Data Studio
description: Dieses Tutorial veranschaulicht das Erstellen von benutzerdefinierten einblickwidgets und-Datenbank und Server-Dashboards in Azure Data Studio hinzufügen.
ms.prod: sql
ms.technology: azure-data-studio
ms.topic: tutorial
author: markingmyname
ms.author: maghan
manager: craigg
ms.reviewer: alayu; sstein
ms.custom: seodec18
ms.date: 09/24/2018
ms.openlocfilehash: 4a2aee7f7ca9c61306e0241ff77a87c1c7dae112
ms.sourcegitcommit: bb5484b08f2aed3319a7c9f6b32d26cff5591dae
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/06/2019
ms.locfileid: "65089734"
---
# <a name="tutorial-build-a-custom-insight-widget"></a>Tutorial: Erstellen eines benutzerdefinierten Einblicks-Widgets

Dieses Tutorial veranschaulicht, wie Ihre eigenen Einblicke-Abfragen verwenden, um benutzerdefinierte einblickwidgets zu erstellen.

In diesem Tutorial erfahren Sie, wie Sie:
> [!div class="checklist"]
> * Führen Sie Ihre eigene Abfrage und zeigen Sie ihn in einem Diagramm
> * Erstellen eines benutzerdefinierten Einblicks Widgets aus dem Diagramm
> * Hinzufügen des Diagramms zu einem Server oder Datenbank-dashboard
> * Hinzufügen von Details zu Ihrer benutzerdefinierten Einblicks-widget

## <a name="prerequisites"></a>Voraussetzungen

In diesem Lernprogramm der SQL Server- oder Azure SQL-Datenbank *"tutorialdb"*. Zum Erstellen der *"tutorialdb"* Datenbank, führen Sie eine der folgenden schnellstartanleitungen:

- [Verbinden und Abfragen von SQL Server verwenden [!INCLUDE[name-sos-short](../includes/name-sos-short.md)]](quickstart-sql-server.md)
- [Verbinden und Abfragen von Azure SQL-Datenbank [!INCLUDE[name-sos-short](../includes/name-sos-short.md)]](quickstart-sql-database.md)


## <a name="run-your-own-query-and-view-the-result-in-a-chart-view"></a>Führen Sie Ihre eigene Abfrage und zeigen das Ergebnis in eine Diagrammsicht an
Führen Sie in diesem Schritt ein Sql-Skript zum Abfragen der aktuellen aktiven Sitzungen.

1. Um einen neuen Editor zu öffnen, drücken Sie die **STRG + N**. 

2. Ändern den Verbindungskontext für **"tutorialdb"**.

3. Fügen Sie die folgende Abfrage in der Abfrage-Editor ein:

   ```sql
   SELECT count(session_id) as [Active Sessions]
   FROM sys.dm_exec_sessions
   WHERE status = 'running'
   ```

4. Speichern Sie die Abfrage in Editor, um eine \*.sql-Datei. In diesem Tutorial speichern Sie das Skript *activeSession.sql*.

5. Um die Abfrage auszuführen, drücken Sie die **F5**.

6. Nachdem die Ergebnisse der Abfrage angezeigt werden, klicken Sie auf **als Diagramm anzeigen**, klicken Sie dann auf die **Diagramm Viewer** Registerkarte.

7. Änderung **Diagrammtyp** zu **Anzahl**. Diese Einstellungen werden einem Count-Diagramm gerendert.

## <a name="add-the-custom-insight-to-the-database-dashboard"></a>Hinzufügen der benutzerdefinierten Einblicks an das datenbankdashboard

1. Um die Konfiguration des Widgets für Einblicke zu öffnen, klicken Sie auf **erstellen Sie einen Einblick** auf *Diagramm Viewer*:

   ![Konfiguration](./media/tutorial-build-custom-insight-sql-server/create-insight.png)
   
2. Kopieren Sie die Konfiguration für speichereinblicke (die JSON-Daten). 

3. Drücken Sie **STRG + Komma** öffnen *Benutzereinstellungen*.

4. Typ *Dashboard* in *Sucheinstellungen*.

5. Klicken Sie auf **bearbeiten** für *dashboard.database.widgets*.

   ![dashboardeinstellungen](./media/tutorial-build-custom-insight-sql-server/dashboard-settings.png)

6. Fügen Sie die Konfiguration für speichereinblicke JSON in *dashboard.database.widgets*. Datenbank-Dashboard Einstellungen sieht wie folgt aus:

   ```json
    "dashboard.database.widgets": [
        {
            "name": "My-Widget",
            "gridItemConfig": {
                "sizex": 2,
                "sizey": 1
            },
            "widget": {
                "insights-widget": {
                    "type": {
                        "count": {
                            "dataDirection": "vertical",
                            "dataType": "number",
                            "legendPosition": "none",
                            "labelFirstColumn": false,
                            "columnsAsLabels": false
                        }
                    },
                    "queryFile": "{your file folder}/activeSession.sql"
                }
            }
        }
    ]
   ```

7. Speichern Sie die *Benutzereinstellungen* , und öffnen Sie die *"tutorialdb"* datenbankdashboard, um das Widget "aktive Sitzungen" finden Sie unter:

   ![Activesession Einblicke](./media/tutorial-build-custom-insight-sql-server/insight-activesession-dashboard.png)

## <a name="add-details-to-custom-insight"></a>Hinzufügen von Details zu benutzerdefinierten Einblicks

1. Um einen neuen Editor zu öffnen, drücken Sie die **STRG + N**.

2. Ändern den Verbindungskontext für **"tutorialdb"**.

3. Fügen Sie die folgende Abfrage in der Abfrage-Editor ein:

   ```sql
    SELECT session_id AS [SID], login_time AS [Login Time], host_name AS [Host Name], program_name AS [Program Name], login_name AS [Login Name]
    FROM sys.dm_exec_sessions
    WHERE status = 'running'
   ```

4. Speichern Sie die Abfrage in Editor, um eine \*.sql-Datei. In diesem Tutorial speichern Sie das Skript *activeSessionDetail.sql*.

5. Drücken Sie **STRG + Komma** öffnen *Benutzereinstellungen*.

6. Bearbeiten Sie den vorhandenen *dashboard.database.widgets* Knoten in der Einstellungsdatei angegeben:

   ```json
    "dashboard.database.widgets": [
        {
            "name": "My-Widget",
            "gridItemConfig": {
                "sizex": 2,
                "sizey": 1
            },
            "widget": {
                "insights-widget": {
                    "type": {
                        "count": {
                            "dataDirection": "vertical",
                            "dataType": "number",
                            "legendPosition": "none",
                            "labelFirstColumn": false,
                            "columnsAsLabels": false
                        }
                    },
                    "queryFile": "{your file folder}/activeSession.sql",
                    "details": {
                        "queryFile": "{your file folder}/activeSessionDetail.sql",
                        "label": "SID",
                        "value": "Login Name"
                    }
                }
            }
        }
    ]
   ```

7. Speichern Sie die *Benutzereinstellungen* , und öffnen Sie die *"tutorialdb"* Datenbank-Dashboard. Klicken Sie auf die Schaltfläche mit den Auslassungspunkten (...) neben *Meine-Widget* um die Details anzuzeigen:

    ![Activesession Einblicke](./media/tutorial-build-custom-insight-sql-server/insight-activesession-detail.png)

## <a name="next-steps"></a>Nächste Schritte
In diesem Tutorial haben Sie gelernt, wie die folgenden Aufgaben ausgeführt werden:
> [!div class="checklist"]
> * Führen Sie Ihre eigene Abfrage und zeigen Sie ihn in einem Diagramm
> * Erstellen eines benutzerdefinierten Einblicks Widgets aus dem Diagramm
> * Hinzufügen des Diagramms zu einem Server oder Datenbank-dashboard
> * Hinzufügen von Details zu Ihrer benutzerdefinierten Einblicks-widget

Weitere Informationen zum Sichern und Wiederherstellen von Datenbanken, führen Sie im nächste Tutorial:

> [!div class="nextstepaction"]
> [Sichern und Wiederherstellen von Datenbanken](tutorial-backup-restore-sql-server.md).
