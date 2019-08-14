---
title: 'Lernprogramm: Aktivieren des Erkenntniswidgets zur Nutzung des Tabellenspeicherplatzes'
titleSuffix: Azure Data Studio
description: Dieses Tutorial veranschaulicht, wie Sie das Beispielwidget für Erkenntnisse zur Nutzung des Tabellenspeicherplatzes auf dem Dashboard für Azure Data Studio-Datenbanken aktivieren.
ms.prod: sql
ms.technology: azure-data-studio
ms.topic: tutorial
author: markingmyname
ms.author: maghan
ms.reviewer: alayu; sstein
ms.custom: seodec18
ms.date: 09/24/2018
ms.openlocfilehash: 6ec653eac10da8c28f727277fc130722c3badef7
ms.sourcegitcommit: db9bed6214f9dca82dccb4ccd4a2417c62e4f1bd
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/25/2019
ms.locfileid: "67958984"
---
# <a name="tutorial-enable-the-table-space-usage-sample-insight-widget-using-includename-sosincludesname-sos-shortmd"></a>Lernprogramm: Aktivieren des Erkenntniswidgets zur Nutzung des Tabellenspeicherplatzes mithilfe von [!INCLUDE[name-sos](../includes/name-sos-short.md)]

Dieses Tutorial veranschaulicht, wie Sie ein Erkenntniswidget auf dem Datenbankdashboard aktivieren, um die Speicherplatznutzung für alle Tabellen in einer Datenbank auf einen Blick anzuzeigen. In diesem Tutorial lernen Sie Folgendes:

> [!div class="checklist"]
> * Aktivieren eines Erkenntniswidgets mithilfe eines integrierten Widgetbeispiels
> * Anzeigen der Details zur Nutzung des Tabellenspeicherplatzes
> * Filtern von Daten und Anzeigen von Bezeichnungsdetails in einem Diagramm mit Erkenntnissen

## <a name="prerequisites"></a>Voraussetzungen

Für dieses Tutorial ist die SQL Server- oder Azure SQL-Datenbank *TutorialDB* erforderlich. Um die *TutorialDB*-Datenbank zu erstellen, führen Sie eine der folgenden Schnellstartanleitungen vollständig aus:

- [Herstellen einer Verbindung mit und Abfragen von SQL Server mithilfe von [!INCLUDE[name-sos-short](../includes/name-sos-short.md)]](quickstart-sql-server.md)
- [Herstellen einer Verbindung mit und Abfragen von Azure SQL-Datenbank mithilfe von [!INCLUDE[name-sos-short](../includes/name-sos-short.md)]](quickstart-sql-database.md)


## <a name="turn-on-a-management-insight-on-includename-sosincludesname-sos-shortmds-database-dashboard"></a>Aktivieren von Verwaltungserkenntnissen auf dem Datenbankendashboard von [!INCLUDE[name-sos](../includes/name-sos-short.md)]
[!INCLUDE[name-sos](../includes/name-sos-short.md)] verfügt über ein integriertes Beispielwidget zum Überwachen des Speicherplatzes, der von Tabellen in einer Datenbank genutzt wird.

1. Öffnen Sie die *Benutzereinstellungen*, indem Sie **STRG+UMSCHALT+P** drücken, um die *Befehlspalette* zu öffnen.
2. Geben Sie *Einstellungen* in das Suchfeld ein, und wählen Sie Folgendes aus: **Einstellungen: Benutzereinstellungen öffnen**.
2. Geben Sie *Dashboard* in das Eingabefeld „Einstellungssuche“ ein, und suchen Sie nach **dashboard.database.widgets**.

3. Um die Einstellungen **dashboard.database.widgets** anzupassen, müssen Sie den Eintrag **dashboard.database.widgets** im Abschnitt **BENUTZEREINSTELLUNGEN** (die Spalte auf der rechten Seite) bearbeiten. Wenn im Abschnitt **BENUTZEREINSTELLUNGEN** kein Eintrag **dashboard.database.widgets** vorhanden ist, halten Sie den Mauszeiger über den Text **dashboard.database.widgets** in der Spalte STANDARDEINSTELLUNGEN. Klicken Sie auf das Stiftsymbol, das links neben dem Text angezeigt wird, und klicken Sie dann auf **In Einstellungen kopieren**. Wenn im Popupfenster **In Einstellungen ersetzen** angezeigt wird, klicken Sie nicht darauf! Wechseln Sie zur Spalte **BENUTZEREINSTELLUNGEN** auf der rechten Seite, suchen Sie den Abschnitt **dashboard.database.widgets**, und fahren Sie mit dem nächsten Schritt fort.

4. Fügen Sie im Abschnitt **dashboard.database.widgets** Folgendes hinzu:

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
Der Abschnitt **dashboard.database.widgets** sollte ähnlich wie die folgende Abbildung aussehen:

   ![Sucheinstellungen](./media/tutorial-table-space-sql-server/insight-table-space.png)

5. Drücken Sie **STRG+S**, um die Einstellungen zu speichern.

6. Öffnen Sie das Datenbankdashboard, indem Sie mit der rechten Maustaste auf **TutorialDB** klicken und dann auf **Verwalten** klicken.

7. Sehen Sie sich das Erkenntniswidget *Tabellenspeicherplatz* an, das in der folgenden Abbildung gezeigt wird: 

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
