---
title: Aktivieren des Beispielwidgets für die fünf langsamsten Abfragen
description: In diesem Tutorial wird veranschaulicht, wie das Beispielwidget für die fünf langsamsten Abfragen auf dem Datenbankdashboard aktiviert wird.
ms.prod: azure-data-studio
ms.technology: ''
ms.topic: tutorial
author: markingmyname
ms.author: maghan
ms.reviewer: alayu; sstein
ms.custom: seodec18; seo-lt-2019
ms.date: 06/01/2020
ms.openlocfilehash: f4e8e76583a90ce64a9f99ef3c94875b2c1fc6dd
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/01/2020
ms.locfileid: "85774545"
---
# <a name="tutorial-add-the-five-slowest-queries-sample-widget-to-the-database-dashboard"></a>Tutorial: Hinzufügen des Beispielwidgets für die *fünf langsamsten Abfragen* zum Datenbankdashboard

In diesem Tutorial wird das Hinzufügen eines integrierten Azure Data Studio-Beispielwidgets zum *Datenbankdashboard* veranschaulicht, um die fünf langsamsten Abfragen schnell anzuzeigen. Außerdem erfahren Sie, wie Sie mithilfe der Azure Data Studio-Features Details zu den langsamen Abfragen und Abfrageplänen anzeigen. In diesem Tutorial lernen Sie Folgendes:

> [!div class="checklist"]
> * Aktivieren des Abfragespeichers in einer Datenbank
> * Hinzufügen eines vorab erstellten Erkenntniswidgets zum Datenbankdashboard
> * Anzeigen von Details zu den langsamsten Abfragen einer Datenbank
> * Anzeigen der Abfrageausführungspläne für langsame Abfragen

Azure Data Studio enthält mehrere integrierte Erkenntniswidgets. Dieses Tutorial zeigt, wie Sie das Widget *query-data-store-db-insight* hinzufügen, grundsätzlich sind die Schritte aber für alle Widgets gleich.

## <a name="prerequisites"></a>Voraussetzungen

Für dieses Tutorial ist die SQL Server- oder Azure SQL-Datenbank *TutorialDB* erforderlich. Um die *TutorialDB*-Datenbank zu erstellen, führen Sie eine der folgenden Schnellstartanleitungen vollständig aus:

* [Herstellen einer Verbindung mit und Abfragen von SQL Server mithilfe von [!INCLUDE[name-sos-short](../includes/name-sos-short.md)]](quickstart-sql-server.md)

* [Herstellen einer Verbindung mit und Abfragen von Azure SQL-Datenbank mithilfe von [!INCLUDE[name-sos-short](../includes/name-sos-short.md)]](quickstart-sql-database.md)

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

3. Geben Sie *Dashboard* in das Feld „Einstellungssuche“ ein, suchen Sie nach **dashboard.database.widgets**, und klicken Sie dann auf *In settings.json bearbeiten*.

   ![Sucheinstellungen](./media/tutorial-qds-sql-server/search-settings.png)

4. Fügen Sie in „settings.json“ folgenden Code hinzu:

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

5. Drücken Sie **STRG+S**, um die geänderten **Benutzereinstellungen** zu speichern.

6. Öffnen Sie das *Datenbankdashboard*, indem Sie in der Randleiste **SERVER** zu **TutorialDB** navigieren, mit der rechten Maustaste klicken und **Verwalten** auswählen.

   ![Öffnen des Dashboards](./media/tutorial-qds-sql-server/insight-open-dashboard.png)

7. Das Erkenntniswidget wird auf dem Dashboard angezeigt:

   ![QDS-Widget](./media/tutorial-qds-sql-server/insight-qds-result.png)

## <a name="view-insight-details-for-more-information"></a>Anzeigen von Details

1. Um weitere Informationen zu einem Erkenntniswidget anzuzeigen, klicken Sie in der oberen rechten Ecke auf die drei Auslassungspunkte ( **...** ), und wählen Sie **Details anzeigen** aus.

2. Um weitere Details zu einem Element anzuzeigen, wählen Sie ein beliebiges Element in der Liste **Diagrammdaten** aus.

   ![Dialogfeld für Details zu Erkenntnissen](./media/tutorial-qds-sql-server/insight-details-dialog.png)

3. Schließen Sie den Bereich **Erkenntnisse**.

## <a name="view-the-query-plan"></a>Anzeigen des Abfrageplans

1. Klicken Sie mit der rechten Maustaste auf die Datenbank **TutorialDB**, und wählen Sie *Verwalten* aus.

2. Wenn Sie über das *langsame Abfragewidget* weitere Informationen zu einem Erkenntniswidget anzeigen möchten, klicken Sie in der oberen rechten Ecke auf die drei Auslassungspunkte ( **...** ), und wählen Sie **Details anzeigen** aus.

    ![Ausführen der Abfrage](media/tutorial-qds-sql-server/run-query.png)

3. Nun sollte ein neues Abfragefenster mit den Ergebnissen angezeigt werden.

    ![Abfrageergebnisse ausführen](media/tutorial-qds-sql-server/run-query-results.png)

4. Klicken Sie auf **Erklären**.

   ![Erläuterung im QDS-Erkenntniswidget](./media/tutorial-qds-sql-server/insight-qds-explain.png)

5. Sehen Sie sich den Ausführungsplan der Abfrage an:

   ![Showplan](./media/tutorial-qds-sql-server/showplan.png)

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