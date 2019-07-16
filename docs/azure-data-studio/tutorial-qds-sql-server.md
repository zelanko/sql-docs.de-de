---
title: 'Tutorial: Aktivieren Sie die fünf langsamsten Abfragen-Beispiel-widget'
titleSuffix: Azure Data Studio
description: Dieses Tutorial veranschaulicht, wie die fünf langsamsten Abfragen Beispiel-Widget auf die Datenbank-Dashboard.
ms.prod: sql
ms.technology: azure-data-studio
ms.topic: tutorial
author: markingmyname
ms.author: maghan
ms.reviewer: alayu; sstein
ms.custom: seodec18
ms.date: 09/24/2018
ms.openlocfilehash: 5c94d2cf8b80ad7724cc1f710dc67d3f4a13c59e
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "67959065"
---
# <a name="tutorial-add-the-five-slowest-queries-sample-widget-to-the-database-dashboard"></a>Tutorial: Hinzufügen der *fünf langsamsten Abfragen* Beispiel Widget aus, das die Datenbank-Dashboard

Dieses Tutorial veranschaulicht den Prozess des Hinzufügens eines [!INCLUDE[name-sos](../includes/name-sos-short.md)]des integrierte Beispiel-Widgets zum die *Datenbank-Dashboard* fünf langsamsten Abfragen mit einer Datenbank schnell anzeigen. Außerdem erfahren Sie, wie zum Anzeigen der Details der langsamen Abfragen und Abfragepläne mit [!INCLUDE[name-sos](../includes/name-sos-short.md)]des Features. In diesem Tutorial erfahren Sie, wie Sie:

> [!div class="checklist"]
> * Query Store in einer Datenbank zu aktivieren
> * Hinzufügen von Widgets vorab erstellte Einblicke zu der Datenbank-dashboard
> * Anzeigen von Details zu den langsamsten Abfragen der Datenbank
> * Anzeigen der Abfrageausführungspläne für langsamen Abfragen

[!INCLUDE[name-sos](../includes/name-sos-short.md)] enthält mehrere Einblicke Widgets außerhalb-des-the-Box. Dieses Tutorial veranschaulicht das Hinzufügen der *-Data-Speicher-Db-abfrageleistung* Widget, aber die Schritte entsprechen im Wesentlichen für jedes beliebige Widget hinzufügen.

## <a name="prerequisites"></a>Erforderliche Komponenten

In diesem Lernprogramm der SQL Server- oder Azure SQL-Datenbank *"tutorialdb"* . Zum Erstellen der *"tutorialdb"* Datenbank, führen Sie eine der folgenden schnellstartanleitungen:

- [Verbinden und Abfragen von SQL Server verwenden [!INCLUDE[name-sos-short](../includes/name-sos-short.md)]](quickstart-sql-server.md)
- [Verbinden und Abfragen von Azure SQL-Datenbank [!INCLUDE[name-sos-short](../includes/name-sos-short.md)]](quickstart-sql-database.md)



## <a name="turn-on-query-store-for-your-database"></a>Aktivieren Sie für Ihre Datenbank Query Store

Das Widget in diesem Beispiel erfordert *Query Store* aktiviert werden.

1. Klicken Sie mit der rechten Maustaste auf die **"tutorialdb"** Datenbank (in der **Server** Sidebar), und wählen Sie **neue Abfrage**.
2. Fügen Sie die folgende Transact-SQL (T-SQL)-Anweisung im Abfrage-Editor, und klicken Sie auf **ausführen**:

   ```sql
    ALTER DATABASE TutorialDB SET QUERY_STORE = ON
   ```

## <a name="add-the-slow-queries-widget-to-your-database-dashboard"></a>Fügen Sie das Widget langsamen Abfragen an Ihr datenbankdashboard

Hinzufügen der *langsame Abfragen Widget* bearbeiten an Ihr Dashboard, die *dashboard.database.widgets* festlegen in Ihre *Benutzereinstellungen* Datei.

1. Öffnen Sie *Benutzereinstellungen* durch Drücken von **STRG + UMSCHALT + P** zum Öffnen der *Befehlspalette*.
2. Typ *Einstellungen* in das Suchfeld ein, und wählen **Einstellungen: Öffnen Sie die Benutzereinstellungen**.

   ![Offene User-Befehl "Einstellungen"](./media/tutorial-qds-sql-server/open-user-settings.png)

2. Typ *Dashboard* in der Suche der Einstellungen im Feld ein, und suchen Sie nach **dashboard.database.widgets**.

   ![Sucheinstellungen](./media/tutorial-qds-sql-server/search-settings.png)

3. Anpassen der **dashboard.database.widgets** Einstellungen, die Sie bearbeiten müssen die **dashboard.database.widgets** Eintrag in der **BENUTZEREINSTELLUNGEN** Abschnitt (die Spalte in der Rechte Seite). Liegt keine **dashboard.database.widgets** in die **BENUTZEREINSTELLUNGEN** Abschnitt, zeigen Sie auf die **dashboard.database.widgets** Text in den Standardeinstellungen-Spalte und klicken Sie auf das Stiftsymbol aus, das wird angezeigt, auf der linken Seite von Text und klicken Sie auf das **in Einstellungen kopieren**. Wenn das Popup angezeigt **ersetzen Sie in den Einstellungen**, nicht darauf klicken. Wechseln Sie zu der **BENUTZEREINSTELLUNGEN** Spalte rechts, und suchen Sie die **dashboard.database.widgets** Abschnitt und fahren Sie mit dem nächsten Schritt fort.

4. In der **dashboard.database.widgets** im Abschnitt Folgendes hinzu:

   ```json
        {
            "name": "slow queries widget",
            "gridItemConfig": {
                "sizex": 2,
                "sizey": 1
            },
            "widget": {
                "query-data-store-db-insight": null
            }
        },
    ```

1. Ist dies beim ersten Hinzufügen eines neuen Widgets, die **dashboard.database.widgets** Abschnitt sollte etwa wie folgt aussehen:

   ```json
   "dashboard.database.widgets": [
       {
           "name": "slow queries widget",
           "gridItemConfig": {
               "sizex": 2,
               "sizey": 1
           },
           "widget": {
               "query-data-store-db-insight": null
           }
       },
       {
           "name": "Tasks",
           "gridItemConfig": {
               "sizex": 1,
               "sizey": 1
           },
           "widget": {
               "tasks-widget": {}
           }
       },
       {
           "gridItemConfig": {
               "sizex": 1,
               "sizey": 2
           },
           "widget": {
               "explorer-widget": {}
           }
       }
   ]
   ```

1. Drücken Sie **STRG + S** , speichern Sie die geänderte **Benutzereinstellungen**.

6. Öffnen der *datenbankdashboard* durch Navigieren zu **"tutorialdb"** in die **Server** Randleiste, mit der rechten Maustaste und wählen Sie **verwalten**.

   ![Dashboard öffnen](./media/tutorial-qds-sql-server/insight-open-dashboard.png)

7. Das Widget Einblicke, die auf dem Dashboard angezeigt werden: 

   ![QDS-widget](./media/tutorial-qds-sql-server/insight-qds-result.png)


## <a name="view-insight-details-for-more-information"></a>Insight-Details für Weitere Informationen anzeigen

1. Um zusätzliche Informationen für ein Widget Einblicke anzuzeigen, klicken Sie auf die Auslassungspunkte ( **...** ) in der oberen, rechten, und wählen **Details anzeigen**.
2. Um weitere Details für ein Element anzuzeigen, wählen Sie ein Element im **Diagrammdaten** Liste.

   ![Insight-Detail-Dialogfeld](./media/tutorial-qds-sql-server/insight-details-dialog.png)

3. Mit der rechten Maustaste in der Zelle rechts neben **Query_sql_txt** in **Elementdetails** , und klicken Sie auf **Zelle kopieren**.

4. Schließen der **Insights** Bereich.

## <a name="view-the-query-plan"></a>Anzeigen des Abfrageplans 

1. Öffnen Sie einen neues Abfrage-Editor, indem Sie mit **STRG + N**.

2. Geben Sie den Abfragetext aus den vorherigen Schritten in den Editor ein.

3. Klicken Sie auf **erläutern**.

   ![Insight QDS erläutern.](./media/tutorial-qds-sql-server/insight-qds-explain.png)

4. Zeigen Sie den Abfrageausführungsplan an:

   ![Showplan](./media/tutorial-qds-sql-server/showplan.png)

## <a name="save-and-open-a-query-plan"></a>Speichern Sie und öffnen Sie einen Abfrageplan 

1. Öffnen Sie das Dialogfeld "Insight-Details" ein.
2. Wählen Sie eines der Abfrageelemente aus der.
2. Mit der rechten Maustaste **Query_plan** Wert ein, und wählen Sie **Zelle kopieren**

   ![Insights QDS-plan](./media/tutorial-qds-sql-server/insight-qds-plan.png)

3. Drücken Sie **STRG + N** um einen neuen Editor zu öffnen.

4. Fügen Sie den kopierten Plan in den Editor ein.

5. Drücken Sie **STRG + S** , speichern Sie die Datei, und ändern die Dateierweiterung *.sqlplan*. *.sqlplan* nicht in der Datei Erweiterung-Dropdownliste angezeigt wird, geben Sie ihn also. Für dieses Tutorial nennen Sie die Datei *slowquery.sqlplan*.

6. Der Abfrageplan wird geöffnet, [!INCLUDE[name-sos](../includes/name-sos-short.md)]des Abfrage-Plan-Viewer:

   ![Insights QDS-plan](./media/tutorial-qds-sql-server/sqlplan.png)


## <a name="next-steps"></a>Nächste Schritte
In diesem Tutorial haben Sie gelernt, wie die folgenden Aufgaben ausgeführt werden:
> [!div class="checklist"]
> * Query Store in einer Datenbank zu aktivieren
> * Fügen Sie ein Insight-Widget hinzu, um die Datenbank-dashboard
> * Anzeigen von Details zu den langsamsten Abfragen der Datenbank
> * Anzeigen der Abfrageausführungspläne für langsamen Abfragen


Informationen zum Aktivieren der **tablespacenutzung** einblickbeispiel, führen Sie im nächste Tutorial:

> [!div class="nextstepaction"]
> [Aktivieren Sie die Tabelle Speicherplatz Beispiel Insight-widget](tutorial-table-space-sql-server.md)
