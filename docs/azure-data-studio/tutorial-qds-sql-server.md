---
title: 'Lernprogramm: Aktivieren des Beispielwidgets für die fünf langsamsten Abfragen'
titleSuffix: Azure Data Studio
description: In diesem Tutorial wird veranschaulicht, wie das Beispielwidget für die fünf langsamsten Abfragen auf dem Datenbankdashboard aktiviert wird.
ms.prod: sql
ms.technology: azure-data-studio
ms.topic: tutorial
author: markingmyname
ms.author: maghan
ms.reviewer: alayu; sstein
ms.custom: seodec18
ms.date: 09/24/2018
ms.openlocfilehash: 5c94d2cf8b80ad7724cc1f710dc67d3f4a13c59e
ms.sourcegitcommit: db9bed6214f9dca82dccb4ccd4a2417c62e4f1bd
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/25/2019
ms.locfileid: "67959065"
---
# <a name="tutorial-add-the-five-slowest-queries-sample-widget-to-the-database-dashboard"></a>Lernprogramm: Hinzufügen des Beispielwidgets für die *fünf langsamsten Abfragen* zum Datenbankdashboard

Dieses Tutorial veranschaulicht, wie Sie eins der integrierten Beispielwidgets von [!INCLUDE[name-sos](../includes/name-sos-short.md)] zum *Datenbankdashboard* hinzufügen, um die fünf langsamsten Abfragen einer Datenbank auf einen Blick erkennen zu können. Sie erfahren auch, wie Sie mithilfe der Features von [!INCLUDE[name-sos](../includes/name-sos-short.md)] Details zu langsamen Abfragen und Abfrageplänen anzeigen. In diesem Tutorial lernen Sie Folgendes:

> [!div class="checklist"]
> * Aktivieren des Abfragespeichers in einer Datenbank
> * Hinzufügen eines vorab erstellten Erkenntniswidgets zum Datenbankdashboard
> * Anzeigen von Details zu den langsamsten Abfragen einer Datenbank
> * Anzeigen der Abfrageausführungspläne für langsame Abfragen

[!INCLUDE[name-sos](../includes/name-sos-short.md)] enthält mehrere integrierte Erkenntniswidgets. Dieses Tutorial zeigt, wie Sie das Widget *query-data-store-db-insight* hinzufügen, grundsätzlich sind die Schritte aber für alle Widgets gleich.

## <a name="prerequisites"></a>Voraussetzungen

Für dieses Tutorial ist die SQL Server- oder Azure SQL-Datenbank *TutorialDB* erforderlich. Um die *TutorialDB*-Datenbank zu erstellen, führen Sie eine der folgenden Schnellstartanleitungen vollständig aus:

- [Herstellen einer Verbindung mit und Abfragen von SQL Server mithilfe von [!INCLUDE[name-sos-short](../includes/name-sos-short.md)]](quickstart-sql-server.md)
- [Herstellen einer Verbindung mit und Abfragen von Azure SQL-Datenbank mithilfe von [!INCLUDE[name-sos-short](../includes/name-sos-short.md)]](quickstart-sql-database.md)



## <a name="turn-on-query-store-for-your-database"></a>Aktivieren des Abfragespeichers für Ihre Datenbank

Das Widget in diesem Beispiel erfordert die Aktivierung des *Abfragespeichers*.

1. Klicken Sie mit der rechten Maustaste auf die Datenbank **TutorialDB** (in der Randleiste **SERVER**), und wählen Sie **Neue Abfrage** aus.
2. Fügen Sie die folgende Transact-SQL-Anweisung (T-SQL) in den Abfrage-Editor ein, und klicken Sie auf **Ausführen**:

   ```sql
    ALTER DATABASE TutorialDB SET QUERY_STORE = ON
   ```

## <a name="add-the-slow-queries-widget-to-your-database-dashboard"></a>Hinzufügen des Widgets für langsame Abfragen zum Datenbankdashboard

Um das *Widget für langsame Abfragen* zu Ihrem Dashboard hinzuzufügen, bearbeiten Sie die Einstellung *dashboard.database.widgets* in Ihrer Datei *Benutzereinstellungen*.

1. Öffnen Sie die *Benutzereinstellungen*, indem Sie **STRG+UMSCHALT+P** drücken, um die *Befehlspalette* zu öffnen.
2. Geben Sie *Einstellungen* in das Suchfeld ein, und wählen Sie Folgendes aus: **Einstellungen: Benutzereinstellungen öffnen**.

   ![Befehl „Benutzereinstellungen öffnen“](./media/tutorial-qds-sql-server/open-user-settings.png)

2. Geben Sie *Dashboard* in das Feld „Einstellungssuche“ ein, und suchen Sie nach **dashboard.database.widgets**.

   ![Sucheinstellungen](./media/tutorial-qds-sql-server/search-settings.png)

3. Um die Einstellungen **dashboard.database.widgets** anzupassen, müssen Sie den Eintrag **dashboard.database.widgets** im Abschnitt **BENUTZEREINSTELLUNGEN** (die Spalte auf der rechten Seite) bearbeiten. Wenn im Abschnitt **BENUTZEREINSTELLUNGEN** kein Eintrag **dashboard.database.widgets** vorhanden ist, halten Sie den Mauszeiger über den Text **dashboard.database.widgets** in der Spalte STANDARDEINSTELLUNGEN. Klicken Sie auf das Stiftsymbol, das links neben dem Text angezeigt wird, und klicken Sie dann auf **In Einstellungen kopieren**. Wenn im Popupfenster **In Einstellungen ersetzen** angezeigt wird, klicken Sie nicht darauf! Wechseln Sie zur Spalte **BENUTZEREINSTELLUNGEN** auf der rechten Seite, suchen Sie den Abschnitt **dashboard.database.widgets**, und fahren Sie mit dem nächsten Schritt fort.

4. Fügen Sie im Abschnitt **dashboard.database.widgets** Folgendes hinzu:

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

1. Wenn Sie zum ersten Mal ein neues Widget hinzufügen, sollte der Abschnitt **dashboard.database.widgets** wie folgt aussehen:

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

1. Drücken Sie **STRG+S**, um die geänderten **Benutzereinstellungen** zu speichern.

6. Öffnen Sie das *Datenbankdashboard*, indem Sie in der Randleiste **SERVER** zu **TutorialDB** navigieren, mit der rechten Maustaste klicken und **Verwalten** auswählen.

   ![Öffnen des Dashboards](./media/tutorial-qds-sql-server/insight-open-dashboard.png)

7. Das Erkenntniswidget wird auf dem Dashboard angezeigt: 

   ![QDS-Widget](./media/tutorial-qds-sql-server/insight-qds-result.png)


## <a name="view-insight-details-for-more-information"></a>Anzeigen von Details

1. Um weitere Informationen zu einem Erkenntniswidget anzuzeigen, klicken Sie in der oberen rechten Ecke auf die drei Auslassungspunkte ( **...** ), und wählen Sie **Details anzeigen** aus.
2. Um weitere Details zu einem Element anzuzeigen, wählen Sie ein beliebiges Element in der Liste **Diagrammdaten** aus.

   ![Dialogfeld für Details zu Erkenntnissen](./media/tutorial-qds-sql-server/insight-details-dialog.png)

3. Klicken Sie in **Elementdetails** mit der rechten Maustaste rechts neben **query_sql_txt**, und klicken Sie auf **Zelle kopieren**.

4. Schließen Sie den Bereich **Erkenntnisse**.

## <a name="view-the-query-plan"></a>Anzeigen des Abfrageplans 

1. Öffnen Sie einen neuen Abfrage-Editor, indem Sie **STRG+N** drücken.

2. Fügen Sie den Abfragetext aus dem vorherigen Schritt in den Editor ein.

3. Klicken Sie auf **Erklären**.

   ![Erläuterung im QDS-Erkenntniswidget](./media/tutorial-qds-sql-server/insight-qds-explain.png)

4. Sehen Sie sich den Ausführungsplan der Abfrage an:

   ![Showplan](./media/tutorial-qds-sql-server/showplan.png)

## <a name="save-and-open-a-query-plan"></a>Speichern und Öffnen eines Abfrageplans 

1. Öffnen Sie das Dialogfeld für Details zu Erkenntnissen.
2. Wählen Sie eins der Abfrageelemente aus.
2. Klicken Sie mit der rechten Maustaste auf den Wert **query_plan**, und wählen Sie **Zelle kopieren** aus.

   ![Insights QDS-Plan](./media/tutorial-qds-sql-server/insight-qds-plan.png)

3. Drücken Sie **STRG+N**, um einen neuen Editor zu öffnen.

4. Fügen Sie den kopierten Plan in den Editor ein.

5. Drücken Sie **STRG+S**, um die Datei zu speichern, und ändern Sie die Dateierweiterung zu *.sqlplan*. *.sqlplan* wird in der Dropdownliste mit Dateierweiterungen nicht angezeigt. Geben Sie die Zeichenfolge einfach ein. Nennen Sie die Datei für diese Tutorial *slowquery.sqlplan*.

6. Der Abfrageplan wird in der Abfrageplanansicht von [!INCLUDE[name-sos](../includes/name-sos-short.md)] geöffnet:

   ![Insights QDS-Plan](./media/tutorial-qds-sql-server/sqlplan.png)


## <a name="next-steps"></a>Nächste Schritte
In diesem Tutorial haben Sie Folgendes gelernt:
> [!div class="checklist"]
> * Aktivieren des Abfragespeichers in einer Datenbank
> * Hinzufügen eines Erkenntniswidgets zum Datenbankdashboard
> * Anzeigen von Details zu den langsamsten Abfragen einer Datenbank
> * Anzeigen der Abfrageausführungspläne für langsame Abfragen


Um zu erfahren, wie Sie die Beispielerkenntnis **Nutzung des Tabellenspeicherplatzes** aktivieren, arbeiten Sie das nächste Tutorial durch:

> [!div class="nextstepaction"]
> [Aktivieren des Erkenntniswidgets zur Nutzung des Tabellenspeicherplatzes](tutorial-table-space-sql-server.md)
