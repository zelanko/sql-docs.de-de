---
title: 'Tutorial: Aktivieren Sie das Tabelle Speicherplatz Nutzung Beispiel Insight-widget'
titleSuffix: Azure Data Studio
description: In diesem Tutorial veranschaulicht, wie die Tabelle Speicherplatz Nutzung Beispiel Einblicke Widget auf dem Studio für Azure Data-Datenbank-Dashboard.
ms.prod: sql
ms.technology: azure-data-studio
ms.topic: tutorial
author: markingmyname
ms.author: maghan
manager: jroth
ms.reviewer: alayu; sstein
ms.custom: seodec18
ms.date: 09/24/2018
ms.openlocfilehash: 9fb9fd0c1c498c330b92b71d00b2c9f33667056c
ms.sourcegitcommit: ad2e98972a0e739c0fd2038ef4a030265f0ee788
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/07/2019
ms.locfileid: "66773659"
---
# <a name="tutorial-enable-the-table-space-usage-sample-insight-widget-using-includename-sosincludesname-sos-shortmd"></a>Tutorial: Aktivieren der Tabelle Speicherplatz Nutzung Beispiel Insight Widgets mithilfe von [!INCLUDE[name-sos](../includes/name-sos-short.md)]

Dieses Tutorial veranschaulicht, wie ein Insight-Widget auf die Datenbank-Dashboard, eine Ansicht auf einen Blick zur speicherplatznutzung von für alle Tabellen in einer Datenbank bereitstellen. In diesem Tutorial erfahren Sie, wie Sie:

> [!div class="checklist"]
> * Schalten Sie schnell eine anhand eines Beispiels der integrierten Insight-Widget Insight-widget
> * Zeigen Sie die Details der Speicherplatzverwendung für die Tabelle
> * Filtern von Daten und Bezeichnung-Informationen in einem Diagramm Einblicke anzeigen

## <a name="prerequisites"></a>Erforderliche Komponenten

In diesem Lernprogramm der SQL Server- oder Azure SQL-Datenbank *"tutorialdb"* . Zum Erstellen der *"tutorialdb"* Datenbank, führen Sie eine der folgenden schnellstartanleitungen:

- [Verbinden und Abfragen von SQL Server verwenden [!INCLUDE[name-sos-short](../includes/name-sos-short.md)]](quickstart-sql-server.md)
- [Verbinden und Abfragen von Azure SQL-Datenbank [!INCLUDE[name-sos-short](../includes/name-sos-short.md)]](quickstart-sql-database.md)


## <a name="turn-on-a-management-insight-on-includename-sosincludesname-sos-shortmds-database-dashboard"></a>Aktivieren Sie auf einem Einblick [!INCLUDE[name-sos](../includes/name-sos-short.md)]des Datenbank-Dashboard
[!INCLUDE[name-sos](../includes/name-sos-short.md)] verfügt über ein integriertes Widget zur Überwachung des Speicherplatzes von Tabellen in einer Datenbank.

1. Öffnen Sie *Benutzereinstellungen* durch Drücken von **STRG + UMSCHALT + P** zum Öffnen der *Befehlspalette*.
2. Typ *Einstellungen* in das Suchfeld ein, und wählen **Einstellungen: Öffnen Sie die Benutzereinstellungen**.
2. Typ *Dashboard* Eingabefeld in der Suche der Einstellungen, und suchen Sie **dashboard.database.widgets**.

3. Anpassen der **dashboard.database.widgets** Einstellungen, die Sie bearbeiten müssen die **dashboard.database.widgets** Eintrag in der **BENUTZEREINSTELLUNGEN** Abschnitt (die Spalte in der Rechte Seite). Liegt keine **dashboard.database.widgets** in die **BENUTZEREINSTELLUNGEN** Abschnitt, zeigen Sie auf die **dashboard.database.widgets** Text in den Standardeinstellungen-Spalte und klicken Sie auf das Stiftsymbol aus, das wird angezeigt, auf der linken Seite von Text und klicken Sie auf das **in Einstellungen kopieren**. Wenn das Popup angezeigt **ersetzen Sie in den Einstellungen**, nicht darauf klicken. Wechseln Sie zu der **BENUTZEREINSTELLUNGEN** Spalte rechts, und suchen Sie die **dashboard.database.widgets** Abschnitt und fahren Sie mit dem nächsten Schritt fort.

4. In der **dashboard.database.widgets** im Abschnitt Folgendes hinzu:

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
Die **dashboard.database.widgets** Abschnitt sollte wie in der folgenden Abbildung aussehen:

   ![Sucheinstellungen](./media/tutorial-table-space-sql-server/insight-table-space.png)

5. Drücken Sie **STRG + S** zum Speichern der Einstellungen.

6. Öffnen von Datenbank-Dashboard, mit der rechten Maustaste **"tutorialdb"** , und klicken Sie auf **verwalten**.

7. Anzeigen der *Tablespaces* Insight-Widget wie in der folgenden Abbildung gezeigt: 

   ![Widget](./media/tutorial-table-space-sql-server/insight-table-space-result.png)


## <a name="working-with-the-insight-chart"></a>Arbeiten mit den Insight-Diagramm

[!INCLUDE[name-sos](../includes/name-sos-short.md)]der Insight-Diagramm enthält Filter- und MouseHover-Details. Testen Sie die folgenden Schritte aus:

1. Klicken Sie auf, und aktivieren bzw. Deaktivieren der *Row_count* Legende des Diagramms. [!INCLUDE[name-sos](../includes/name-sos-short.md)] Zeigt an, und blendet die Datenreihe aus, wie Sie eine Legende ein- und auszuschalten.
    
2. Zeigen Sie den Mauszeiger auf das Diagramm ein. [!INCLUDE[name-sos](../includes/name-sos-short.md)] Zeigt weitere Informationen über die reihenbezeichnung Daten und der Wert, wie im folgenden Screenshot gezeigt.

   ![Diagramm umschalten und Legende](./media/tutorial-table-space-sql-server/insight-table-space-toggle.png)


## <a name="next-steps"></a>Nächste Schritte
In diesem Tutorial haben Sie gelernt, wie die folgenden Aufgaben ausgeführt werden:
> [!div class="checklist"]
> * Schalten Sie schnell eine Insight Widgets mithilfe einer Stichprobe von integrierten Insight-Widget aus.
> * Zeigen Sie die Details der Speicherplatzverwendung für die Tabelle ein.
> * Filtern von Daten und Bezeichnung-Informationen in einem Diagramm Einblicke anzeigen

Führen Sie im nächste Tutorial, um weitere Informationen zum Erstellen eines benutzerdefinierten Einblicks-Widgets:

> [!div class="nextstepaction"]
> [Erstellen ein benutzerdefinierten Einblicks Widgets](tutorial-build-custom-insight-sql-server.md).
