---
title: Aktivieren des Erkenntniswidgets zur Nutzung des Tabellenspeicherplatzes
titleSuffix: Azure Data Studio
description: Dieses Tutorial veranschaulicht, wie Sie das Beispielwidget für Erkenntnisse zur Nutzung des Tabellenspeicherplatzes auf dem Dashboard für Azure Data Studio-Datenbanken aktivieren.
ms.prod: sql
ms.technology: azure-data-studio
ms.topic: tutorial
author: markingmyname
ms.author: maghan
ms.reviewer: alayu; sstein
ms.custom: seodec18; seo-lt-2019
ms.date: 09/10/2019
ms.openlocfilehash: f22aba3fd2f2d006355fdd30aef6f196f2795f6c
ms.sourcegitcommit: b2e81cb349eecacee91cd3766410ffb3677ad7e2
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/01/2020
ms.locfileid: "74957014"
---
# <a name="tutorial-enable-the-table-space-usage-sample-insight-widget-using-includename-sosincludesname-sos-shortmd"></a>Tutorial: Aktivieren des Erkenntniswidgets zur Nutzung des Tabellenspeicherplatzes mithilfe von [!INCLUDE[name-sos](../includes/name-sos-short.md)]

Dieses Tutorial veranschaulicht, wie Sie ein Erkenntniswidget auf dem Datenbankdashboard aktivieren, um die Speicherplatznutzung für alle Tabellen in einer Datenbank auf einen Blick anzuzeigen. In diesem Tutorial lernen Sie Folgendes:

> [!div class="checklist"]
> * Aktivieren eines Erkenntniswidgets mithilfe eines integrierten Widgetbeispiels
> * Anzeigen der Details zur Nutzung des Tabellenspeicherplatzes
> * Filtern von Daten und Anzeigen von Bezeichnungsdetails in einem Diagramm mit Erkenntnissen

## <a name="prerequisites"></a>Voraussetzungen

Für dieses Tutorial ist die SQL Server- oder Azure SQL-Datenbank *TutorialDB* erforderlich. Um die *TutorialDB*-Datenbank zu erstellen, führen Sie eine der folgenden Schnellstartanleitungen vollständig aus:

* [Herstellen einer Verbindung mit und Abfragen von SQL Server mithilfe von [!INCLUDE[name-sos-short](../includes/name-sos-short.md)]](quickstart-sql-server.md)
* [Herstellen einer Verbindung mit und Abfragen von Azure SQL-Datenbank mithilfe von [!INCLUDE[name-sos-short](../includes/name-sos-short.md)]](quickstart-sql-database.md)

## <a name="turn-on-a-management-insight-on-includename-sosincludesname-sos-shortmds-database-dashboard"></a>Aktivieren von Verwaltungserkenntnissen auf dem Datenbankendashboard von [!INCLUDE[name-sos](../includes/name-sos-short.md)]

[!INCLUDE[name-sos](../includes/name-sos-short.md)] verfügt über ein integriertes Beispielwidget zum Überwachen des Speicherplatzes, der von Tabellen in einer Datenbank genutzt wird.

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

Im Erkenntnisdiagramm von [!INCLUDE[name-sos](../includes/name-sos-short.md)] können Sie Daten filtern und Details anzeigen, in dem Sie mit dem Mauszeiger darauf zeigen. Zum Ausprobieren führen Sie die folgenden Schritte aus:

1. Klicken Sie auf die Legende *row_count* im Diagramm, und schalten Sie die Anzeige um. [!INCLUDE[name-sos](../includes/name-sos-short.md)] blendet Datenreihen ein und aus, wenn Sie eine Legende ein- und ausschalten.

2. Halten Sie den Mauszeiger über das Diagramm. [!INCLUDE[name-sos](../includes/name-sos-short.md)] zeigt weitere Informationen zur Datenreihenbezeichnung und der zugehörigen Bezeichnung, wie im folgenden Screenshot gezeigt.

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
