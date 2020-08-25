---
title: Aktivieren des Erkenntniswidgets zur Nutzung des Tabellenspeicherplatzes
description: Dieses Tutorial veranschaulicht, wie Sie das Beispielwidget für Erkenntnisse zur Nutzung des Tabellenspeicherplatzes auf dem Dashboard für Azure Data Studio-Datenbanken aktivieren.
ms.prod: azure-data-studio
ms.technology: azure-data-studio
ms.topic: tutorial
author: markingmyname
ms.author: maghan
ms.reviewer: alayu, maghan, sstein
ms.custom: seodec18; seo-lt-2019
ms.date: 09/10/2019
ms.openlocfilehash: 276cb3535e3ee0623816aa329446e81b2feaf12e
ms.sourcegitcommit: dc8a30a4a27e15fc6671ca2674da9b7c637ec255
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 08/21/2020
ms.locfileid: "88745620"
---
# <a name="tutorial-enable-the-table-space-usage-sample-insight-widget-using-azure-data-studio"></a>Tutorial: Aktivieren des Erkenntniswidgets zur Nutzung des Tabellenspeicherplatzes mithilfe von Azure Data Studio

Dieses Tutorial veranschaulicht, wie Sie ein Erkenntniswidget auf dem Datenbankdashboard aktivieren, um die Speicherplatznutzung für alle Tabellen in einer Datenbank auf einen Blick anzuzeigen. In diesem Tutorial lernen Sie Folgendes:

> [!div class="checklist"]
> * Aktivieren eines Erkenntniswidgets mithilfe eines integrierten Widgetbeispiels
> * Anzeigen der Details zur Nutzung des Tabellenspeicherplatzes
> * Filtern von Daten und Anzeigen von Bezeichnungsdetails in einem Diagramm mit Erkenntnissen

## <a name="prerequisites"></a>Voraussetzungen

Für dieses Tutorial ist die SQL Server- oder Azure SQL-Datenbank *TutorialDB* erforderlich. Um die *TutorialDB*-Datenbank zu erstellen, führen Sie eine der folgenden Schnellstartanleitungen vollständig aus:

* [Herstellen einer Verbindung mit und Abfragen von SQL Server mithilfe von [!INCLUDE[name-sos-short](../includes/name-sos-short.md)]](quickstart-sql-server.md)
* [Herstellen einer Verbindung mit und Abfragen von Azure SQL-Datenbank mithilfe von [!INCLUDE[name-sos-short](../includes/name-sos-short.md)]](quickstart-sql-database.md)

## <a name="turn-on-a-management-insight-on-azure-data-studios-database-dashboard"></a>Aktivieren von Verwaltungserkenntnissen auf dem Datenbankendashboard von Azure Data Studio

Azure Data Studio verfügt über ein integriertes Beispielwidget zum Überwachen des Speicherplatzes, der von Tabellen in einer Datenbank genutzt wird.

1. Öffnen Sie die *Benutzereinstellungen*, indem Sie **STRG+UMSCHALT+P** drücken, um die *Befehlspalette* zu öffnen.

2. Geben Sie *Einstellungen* in das Suchfeld ein, und wählen Sie Folgendes aus: **Einstellungen: Benutzereinstellungen öffnen**.

3. Geben Sie *Dashboard* in das Eingabefeld „Einstellungssuche“ ein, und suchen Sie nach **dashboard.database.widgets**.

4. Wenn Sie die Einstellungen **dashboard.database.widgets** anpassen möchten, müssen Sie im Abschnitt **BENUTZEREINSTELLUNGEN** den Eintrag **dashboard.database.widgets** bearbeiten.

   ![Sucheinstellungen](media/tutorial-table-space-sql-server/search-settings.png)

   Wenn im Abschnitt **BENUTZEREINSTELLUNGEN** kein Eintrag **dashboard.database.widgets** vorhanden ist, zeigen Sie mit dem Mauszeiger in der Spalte „STANDARDEINSTELLUNGEN“ auf den Text **dashboard.database.widgets**. Klicken Sie auf das *Zahnradsymbol*, das links neben dem Text angezeigt wird, und klicken Sie dann auf **Als JSON-Einstellung kopieren**. Wenn im Popupfenster **In Einstellungen ersetzen** angezeigt wird, klicken Sie nicht darauf! Wechseln Sie zur Spalte **BENUTZEREINSTELLUNGEN** auf der rechten Seite, suchen Sie den Abschnitt **dashboard.database.widgets**, und fahren Sie mit dem nächsten Schritt fort.

5. Fügen Sie im Abschnitt **dashboard.database.widgets** die folgenden Zeilen hinzu:

   ```json
        {
            "name": "Space Used by Tables",
            "gridItemConfig": {
                "sizex": 2,
                "sizey": 1
            },
            "widget": {
                "table-space-db-insight": null
            }
        },
    ```

   Der Abschnitt **dashboard.database.widgets** sollte in etwa wie die folgende Abbildung aussehen:

    ![Sucheinstellungen](./media/tutorial-table-space-sql-server/insight-table-space.png)

6. Drücken Sie **STRG+S**, um die Einstellungen zu speichern.

7. Öffnen Sie das Datenbankdashboard, indem Sie mit der rechten Maustaste auf **TutorialDB** klicken und dann auf **Verwalten** klicken.

8. Sehen Sie sich das Erkenntniswidget *Tabellenspeicherplatz* an, das in der folgenden Abbildung gezeigt wird:

   ![Widget](./media/tutorial-table-space-sql-server/insight-table-space-result.png)

## <a name="working-with-the-insight-chart"></a>Arbeiten im Erkenntnisdiagramm

Im Erkenntnisdiagramm von Azure Data Studio können Sie Daten filtern und Details anzeigen, in dem Sie mit dem Mauszeiger darauf zeigen. Zum Ausprobieren führen Sie die folgenden Schritte aus:

1. Klicken Sie auf die Legende *row_count* im Diagramm, und schalten Sie die Anzeige um. Azure Data Studio blendet Datenreihen ein und aus, wenn Sie eine Legende ein- und ausschalten.

2. Halten Sie den Mauszeiger über das Diagramm. Azure Data Studio zeigt weitere Informationen zur Datenreihenbezeichnung und der zugehörigen Bezeichnung, wie im folgenden Screenshot gezeigt.

   ![Umschalten von Diagramm und Legende](./media/tutorial-table-space-sql-server/insight-table-space-toggle.png)

## <a name="next-steps"></a>Nächste Schritte

In diesem Tutorial haben Sie Folgendes gelernt:
> [!div class="checklist"]
> * Aktivieren eines Erkenntniswidgets mithilfe eines integrierten Widgetbeispiels
> * Anzeigen der Details zur Nutzung des Tabellenspeicherplatzes
> * Filtern von Daten und Anzeigen von Bezeichnungsdetails in einem Diagramm mit Erkenntnissen

Um zu erfahren, wie Sie ein benutzerdefiniertes Erkenntniswidget erstellen, arbeiten Sie das nächste Tutorial durch:

> [!div class="nextstepaction"]
> [Erstellen eines benutzerdefinierten Erkenntniswidgets](tutorial-build-custom-insight-sql-server.md)
