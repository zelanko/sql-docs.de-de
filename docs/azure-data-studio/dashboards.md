---
title: Schneller Zugriff auf Einblicke und allgemeine Aufgaben
titleSuffix: Azure Data Studio
description: Erfahren Sie, zum Anzeigen von Widgets auf dem datenbankdashboard in Azure Data Studio.
ms.custom: seodec18
ms.date: 09/24/2018
ms.prod: sql
ms.technology: azure-data-studio
ms.reviewer: alayu; sstein
ms.topic: conceptual
author: yualan
ms.author: alayu
manager: craigg
ms.openlocfilehash: faaa59e8607f707bb43f31638880f771ae7ae6ab
ms.sourcegitcommit: 189a28785075cd7018c98e9625c69225a7ae0777
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/07/2018
ms.locfileid: "53030484"
---
# <a name="dashboards-in-includename-sosincludesname-sos-shortmd"></a>Dashboards in [!INCLUDE[name-sos](../includes/name-sos-short.md)]

Ein Dashboard, mit der rechten Maustaste einen Server oder Datenbank anzuzeigen, und wählen Sie **verwalten**.

![Beispiel-Dashboard](media/dashboards/sample-dashboard.png)

**Servereigenschaften** enthält die Eigenschaften des Servers, einschließlich Version, Edition, Name des Computers und Betriebssystemversion.

**Aufgaben** Commons-Aufgaben wie das Wiederherstellen und neue Abfrage enthält.

**Suchen Sie die Datenbanken** Nachschlagen vorhandener Datenbanken auf dem Server, einschließlich Tabellen gespeichert.

**Sicherungsstatus** Nachschlagen der Status der Sicherung für vorhandene Datenbanken.

## <a name="configuring-insight-widgets"></a>Konfigurieren von Einblickwidgets
Es wird dringend empfohlen, dass Sie das Tutorial zum Einrichten von Ihrem Dashboards aus, das sich [hier](tutorial-build-custom-insight-sql-server.md).

Darüber hinaus stellen Sie sicher, sehen Sie sich die [zur Vorgehensweise zum Konfigurieren von einblickwidgets]().

Nach dem Lesen dieses Lernprogramms auf Weitere Informationen zu bestimmten Widgets, die in diesem Tutorial nicht behandelt werden.

## <a name="insight-detail"></a>Insight-Details
Flyout Details Insight bietet detailliertere Informationen zu einem Widget verwandte Einblicke. 
- Ein Widget Insight wird eine Zusammenfassungsansicht für einen Blick die Anzahl, Linie, Diagramm usw. gerendert. 
- Flyout Details Insight bietet es sich um "Eingehend" Details, Auflisten von Data-Einblicke für jedes Element im Widget Einblicke auf hoher Ebene aufgeführt. 
  - Die Details Flyout-Inhalte werden durch eine separate SQL-Abfrage an das wichtigste Widget-Abfrage definiert.

Besteht keine Notwendigkeit Satz für eine Abfrage der Insight-Details, aber das Layout ist standard.
- Die obere Hälfte der Ansicht ist immer eine 2-Spalten "Zusammenfassung". Welche Spalten werden durch die Eigenschaften "Label" und "Value" der JSON-Konfiguration definiert.
- Auf, wenn auf eine Zeile in der Zusammenfassungstabelle, der unteren Hälfte des Flyouts Listet den vollständigen Satz von Spalteninformationen für diese Zeile.

### <a name="insight-detail-configuration-in-packagejson"></a>Konfiguration für speichereinblicke Details in "Package.JSON"

Beispielkonfiguration für Insight-Details-flyout
```json
"details": {
    "queryFile": "./relative_path_to_sqlfile_from_package_json_file.sql",
    "label": {
        "icon": "database",
        "column": "first_column_name_for_summary_list_view",
        "state": [
            {
                "condition": {
                    "if": "equals",
                    "equals": "0"
                },
                "color": "red"
            },
            {
                "condition": {
                    "if": "equals",
                    "equals": "1"
                },
                "color": "orange"
            },
            {
                "condition": {
                    "if": "equals",
                    "equals": "2"
                },
                "color": "green"
            }
        ]
    },
    "value": "second_column_and_condition_check_value_column_for_summary_list_view",
```
|property|Typ|Wert|Standardwert|description|comment|
|:---|:---|:---|:---|:---|:---|
|Details|JSON-Objekt|||erforderliche Eigenschaft Insight-Detail-Definitionen in ihrer Struktur definieren.||
|queryFile|Zeichenfolge|||den Dateipfad für den Insight Details Sql-Abfrage und der Dateiname relativ zum Speicherort der Datei "Package.JSON"||
|Bezeichnung|JSON-Objekt|||erforderliche Eigenschaft, die zum Definieren von jedes Zeilenelement in der Liste "Zusammenfassung" anzeigen|in Zukunft den Namen dieser Eigenschaft wie "SummaryList" ändern|
|Symbol "|String|||Geben Sie das Symbol ein, die für jedes Element der Liste "Zusammenfassung" Anzeigen dargestellt.|(tbd) Liste der unterstützten Symbole werden dokumentiert werden|
|column|Zeichenfolge|||Geben Sie den Namen der ersten Spalte in der Liste "Zusammenfassung" Ansicht aus dem Resultset der Abfrage|der Name dieser Eigenschaft wird in Zukunft intuitiver Namen geändert werden|
|Wert|Zeichenfolge|||Geben Sie den Namen der zweiten Spalte in der Liste "Zusammenfassung" Ansicht aus dem Resultset der Abfrage. Der Wert dieser Spalte wird zum Überprüfen von Bedingungen, und legen die Farbe für jede Liste "Zusammenfassung" anzeigen Elemente Farbe Punkt|der Name dieser Eigenschaft wird in Zukunft etwas intuitiver ändern.|
|Bedingung|JSON-Objekt|||die Überprüfung der Bedingung für den Wert der Spalte definiert, und bestimmen Sie die Farbe für jedes Element der Liste "Zusammenfassung" anzeigen||
|wenn|String|immer, equals, NotEquals, GreaterThan, LessThan, GreaterThanOrEquals, lessThanOrEquals||Bedingung überprüfen-operator|Namen der Eigenschaft wird in Zukunft an Operator ändern.|
|Ist gleich|Zeichenfolge|||Wert der Bedingung-Überprüfung|Diese Eigenschaftsnamen werden in Zukunft auf 'Value' ändern.|

## <a name="insight-actions"></a>Insight-Aktionen
Mit einem Insight-Widget und Details zu den Insight können Sie problemlos hierher, um einem Aktionsplan ein Problem verringern oder zu verwalten. Sie werden z. B. Ausführen von DBCC CHECKDB vorstellen, lesen die Fehlerprotokolle oder die Datenbank wiederherstellen, wenn eine Datenbank in eine Wiederherstellung ausstehend ist. Oder es kann eine der Aktionen, die Sie durchführen möchten.

Mithilfe von [!INCLUDE[name-sos](../includes/name-sos-short.md)]des Insight Aktionen Konfiguration können Sie eine integrierte Aktionen wie z. B. wiederherstellen, oder bringen Ihre eigenen mit einem SQL­Skript definierte Aktion zuordnen.

> Konfiguration von benutzerdefinierten Aktionen, die mit Sql-Skript befindet sich in der Entwicklung, und es ist noch nicht in der privaten Vorschauversion verfügbar.

## <a name="sample-insight-action-definition"></a>Beispiel Einblicke Aktionsdefinition

```"actions"{}``` definiert eine Insight-Aktion. Aktion kann z. B. über einen bestimmten Bereich definiert werden ```"server"```, ```"database"``` und so weiter und [!INCLUDE[name-sos](../includes/name-sos-short.md)] übergibt den aktuellen Kontext Verbindungsinformationen an die Aktion.

Z. B. bei Aktion "Wiederherstellen" wird gestartet für Datenbank "wideworldimporters" ```"database": "${Database}"``` Definition gibt an, dass übergeben ```Database``` Spaltenwert in die Abfrageergebnisse auf die Aktion "Wiederherstellen". Dann beginnt die Aktion "Wiederherstellen" für die Datenbank. ```"types"``` ist ein Json-Array, und können mehrere Aktionen aufgeführt, in das Array. Es wird im Grunde ein Kontextmenü Insight-Details im Dialogfeld ", Benutzer auf und führen Sie die Aktion kann. 

> [!INCLUDE[name-sos](../includes/name-sos-short.md)] Vorschau 0.17.1 hat "Sicherung", "Restore", "neue Abfrage" und "neue-Datenbank" als Aktionstypen aktiviert.

```json
"details": {
    "queryFile": "./sql/database_state_detail.sql",
    "label": {...},
    "value": "state",
    "actions": {
        "database": "${Database}",
        "types": ["restore"]
    }
}
```
