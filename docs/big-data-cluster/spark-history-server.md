---
title: Diagnostizieren Sie/Debuggen von Spark-Anwendungen
titleSuffix: SQL Server big data clusters
description: Verwenden von Spark-Verlaufsserver zum Debuggen und Diagnostizieren von Spark-Anwendungen, die unter SQL Server-2019 big Data-Cluster.
author: jejiang
ms.author: jejiang
ms.reviewer: jroth
manager: craigg
ms.date: 12/06/2018
ms.topic: conceptual
ms.prod: sql
ms.technology: big-data-cluster
ms.custom: seodec18
ms.openlocfilehash: e7444a9f5bcdc480425ba02c8a068831c081b47a
ms.sourcegitcommit: 2de5446fbc57787f18a907dd5deb02a7831ec07d
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/02/2019
ms.locfileid: "58860332"
---
# <a name="debug-and-diagnose-spark-applications-on-sql-server-big-data-clusters-in-spark-history-server"></a>Debuggen und Diagnostizieren von Spark-Anwendungen in Clustern von SQL Server big Data in Spark-Verlaufsserver

[!INCLUDE[tsql-appliesto-ssver15-xxxx-xxxx-xxx](../includes/tsql-appliesto-ssver15-xxxx-xxxx-xxx.md)]

Dieser Artikel enthält Anleitungen zur Verwendung von erweiterten Spark-Verlaufsserver zum Debuggen und Diagnostizieren von Spark-Anwendungen in einer big Data-Cluster mit SQL Server-2019 (Vorschau). Diese Funktionen zum Debuggen und Diagnose sind in Spark-Verlaufsserver integriert und unterstützt von Microsoft. Die Erweiterung enthält die Registerkarte "Daten" und die Registerkarte "Graph" und die Registerkarte "Diagnose". Registerkarte "Daten" können Benutzer die Eingabe- und Daten des Spark-Auftrags überprüfen. Benutzer können in der Registerkarte "Graph" den den Datenfluss überprüfen und das auftragsdiagramm wiedergeben. Registerkarte "Diagnose" kann Benutzer von datenschiefe zeitabweichung und-Executor-Verwendungsanalyse verweisen.

## <a name="get-access-to-spark-history-server"></a>Erhalten Sie Zugriff auf die Spark-Verlaufsserver

Mit Informationen, die Auftrags-spezifische Daten und interaktive Visualisierung des Auftrags Graph und Datenfluss für big Data-Cluster enthält, wird die benutzerfreundlichkeit von open Source-Spark History Server erweitert. 

### <a name="open-the-spark-history-server-web-ui-by-url"></a>Öffnen Sie die Spark History Server-Benutzeroberfläche URL
Öffnen der Spark-Verlaufsserver durch Navigieren zu der folgenden URL ersetzen `<Ipaddress>` und `<Port>` mit big Data-Cluster spezifischen Informationen. Weitere Informationen kann bezeichnet werden: [Bereitstellen von SQL Server-big Data-cluster](quickstart-big-data-cluster-deploy.md)

```
https://<Ipaddress>:<Port>/gateway/default/sparkhistory
```

Die Spark-Verlaufsserver Web werden Webbenutzeroberfläche sieht wie folgt:

![Spark-Verlaufsserver](./media/apache-azure-spark-history-server/spark-history-server.png)


## <a name="data-tab-in-spark-history-server"></a>Registerkarte "Daten" in Spark-Verlaufsserver
Wählen Sie die Auftrags-ID, und klicken Sie auf **Daten** im Menü des Tools, um die Datenansicht abzurufen.

+ Überprüfen Sie die **Eingaben**, **Ausgaben**, und **Tabellenvorgänge** durch Registerkarten getrennt auswählen.

    ![Registerkarten der Spark-Verlaufsserver-Daten](./media/apache-azure-spark-history-server/sparkui-data-tabs.png)

+ Kopieren Sie alle Zeilen, indem Sie auf die Schaltfläche **Kopie**.

    ![Kopieren Sie alle Zeilen](./media/apache-azure-spark-history-server/sparkui-data-copy.png)

+ Speichern Sie alle Daten als CSV-Datei, indem Sie auf die Schaltfläche **Csv**.

    ![Speichern Sie Daten als CSV-Dateien](./media/apache-azure-spark-history-server/sparkui-data-save.png)

+ Suche durch Eingeben von Schlüsselwörtern im Feld **Suche**, das Suchergebnis wird sofort angezeigt.

    ![Mit den Schlüsselwörtern suchen](./media/apache-azure-spark-history-server/sparkui-data-search.png)

+ Klicken Sie auf die Spaltenüberschrift, um die Tabelle sortieren, klicken Sie auf das Pluszeichen, um eine Zeile, um weitere Details anzeigen zu erweitern, oder klicken Sie auf das Minuszeichen (-) um eine Zeile zu reduzieren.

    ![Data Table-Funktionen](./media/apache-azure-spark-history-server/sparkui-data-table.png)

+ Herunterladen einer einzelnen Datei durch Klicken auf Schaltfläche **teilweise herunterladen** , die auf der rechten Seite platzieren, und klicken Sie dann die ausgewählte Datei an lokalen Ort heruntergeladen wird. Wenn die Datei nicht mehr vorhanden ist, wird eine neue Registerkarte zum Anzeigen von Fehlermeldungen geöffnet.

    ![Herunterladen einer Datenzeile](./media/apache-azure-spark-history-server/sparkui-data-download-row.png)

+ Kopieren Sie den vollständigen oder relativen Pfad durch Auswählen der **Vollständiger_pfad kopieren**, **relativen Pfad kopieren** , die erweitert wird, aus dem Menü "herunterladen". Für Azure Data Lake-Speicher-Dateien **in Azure Storage-Explorer öffnen** startet Azure Storage-Explorer. Und suchen Sie bei der Anmeldung auf den genauen Ordnernamen.

    ![Einen vollständigen oder relativen Pfad kopieren](./media/apache-azure-spark-history-server/sparkui-data-copy-path.png)

+ Klicken Sie auf die Zahl unterhalb der Tabelle an, navigieren Seiten Wenn zu viele Zeilen auf einer Seite angezeigt. 

    ![Seite "Daten"](./media/apache-azure-spark-history-server/sparkui-data-page.png)

+ Zeigen Sie auf das Fragezeichen neben den Daten, um die QuickInfo anzuzeigen, oder klicken Sie auf das Fragezeichen, um weitere Informationen zu erhalten.

    ![Daten Weitere Informationen](./media/apache-azure-spark-history-server/sparkui-data-more-info.png)

+ Senden Sie Feedback mit Problemen, indem Sie auf **Feedback abgeben**.

    ![Graph-feedback](./media/apache-azure-spark-history-server/sparkui-graph-feedback.png)

## <a name="graph-tab-in-spark-history-server"></a>Registerkarte "Graph" im Spark-Verlaufsserver

Wählen Sie die Auftrags-ID, und klicken Sie auf **Graph** im Menü des Tools, um die Diagrammansicht des Auftrags zu erhalten.

+ Überprüfen Sie Überblick über den Auftrag, indem Sie den generierten auftragsgraphen. 

+ Standardmäßig wird allen Aufträgen angezeigt, und sie kann gefiltert werden, indem **Auftrags-ID**.

    ![Diagramm der Auftrags-ID](./media/apache-azure-spark-history-server/sparkui-graph-jobid.png)

+ Wir behalten jedoch **Fortschritt** als Standardwert. Benutzer sehen den Datenfluss dazu **lesen** oder ** Written *** in der Dropdownliste der **Anzeige**.

    ![Diagramm anzeigen](./media/apache-azure-spark-history-server/sparkui-graph-display.png)

    Die Graph-Knoten-Anzeige in Farbe, die der Heatmap anzeigt.

    ![Graph-wärmebild](./media/apache-azure-spark-history-server/sparkui-graph-heatmap.png)

+ Wiedergeben für den Auftrag aus, indem Sie auf die **Wiedergabe** Schaltfläche und jederzeit beenden, indem Sie auf die Schaltfläche "Beenden". Die Task-Anzeige in der Farbe an, die verschiedene Status angezeigt, bei der Wiedergabe:

    + Grün für Erfolg: Der Auftrag wurde erfolgreich abgeschlossen.
    + Orange für wiederholt: Instanzen von Aufgaben, die Fehler, aber wirken sich nicht auf das endgültige Ergebnis des Auftrags. Diese Aufgaben haben doppelte oder wiederholungsinstanzen, die später möglicherweise erfolgreich.
    + Blau, für die Ausführung: Der Task wird ausgeführt.
    + Für das Warten weiß oder übersprungen: Die Aufgabe wartet, ausgeführt, oder die Phase wurde übersprungen.
    + Fehler bei der Rot für: Fehler des Tasks.

    ![Farbbeispiel Graph, ausgeführt wird](./media/apache-azure-spark-history-server/sparkui-graph-color-running.png)
 
    Die übersprungenen Phase Anzeige in Weiß.
    ![Farbbeispiel Graph, überspringen](./media/apache-azure-spark-history-server/sparkui-graph-color-skip.png)

    ![Farbbeispiel Graph, Fehler](./media/apache-azure-spark-history-server/sparkui-graph-color-failed.png)
 
    > [!NOTE]
    > Wiedergabe für jeden Auftrag ist zulässig. Für unvollständiger Auftrag wird die Wiedergabe nicht unterstützt.


+ Maus führt einen Bildlauf durch vergrößern/verkleinern das auftragsdiagramm, oder klicken Sie auf **Zoom zum Einpassen** zu vereinfachen, die an Bildschirmgröße anpassen.
 
    ![mit diagrammzoom anpassen](./media/apache-azure-spark-history-server/sparkui-graph-zoom2fit.png)

+ Zeigen Sie auf die Graph-Knoten zu prüfen, ob die QuickInfo bei fehlgeschlagenen Aufgaben aus, und klicken Sie auf Phase zu Phase Seite zu öffnen.

    ![Graph-QuickInfo](./media/apache-azure-spark-history-server/sparkui-graph-tooltip.png)

+ In der Registerkarte "Graph" Auftrag, Phasen müssen QuickInfo und kleines Symbol angezeigt, wenn sie Aufgaben erfüllen die folgenden Bedingungen:
    + Datenschiefe: Datenlesevorgänge Größe > durchschnittliche Lesegröße aller Aufgaben in dieser Phase * 2 "und" gelesene Daten Größe > 10 MB
    + Zeitabweichung: Ausführungszeit > durchschnittliche Ausführungszeit aller Aufgaben in dieser Phase * 2 und Ausführungszeit > 2 Minuten

    ![datenschiefe Symbol "Diagramm"](./media/apache-azure-spark-history-server/sparkui-graph-skew-icon.png)

+ Der Auftrags-Graph-Knoten zeigt die folgende Informationen der einzelnen Phasen:
    + ID.
    + Name oder Beschreibung.
    + Anzahl der Tasks gesamt.
    + Gelesene Daten: die Summe der Eingabegröße und Shuffle Lesegröße.
    + Schreiben von Daten: die Summe der Größe der Ausgabe und Shuffle Größe zu schreiben.
    + Ausführungszeit: die Zeit zwischen der Startzeit des ersten Versuchs und Abschlusszeit des letzten Versuchs.
    + Zeilenanzahl: die Summe der Eingabedatensätze, erstellt, gelesen Datensätze zu mischen und Write-Datensätze zu mischen.
    + Wird ausgeführt.

    > [!NOTE]
    > In der Standardeinstellung dem Diagrammknoten Auftrag zeigen Informationen aus dem letzten Versuch der einzelnen Phasen (mit Ausnahme der Zeit für phasenausführung), aber während der Wiedergabe Graph Knoten Informationen jedem Versuch angezeigt werden.

    > [!NOTE]
    > Für die Datengröße der Lese- und Schreibvorgänge, die wir verwenden Sie 1 MB = 1000 KB = 1000 * 1000 Bytes.

+ Senden Sie Feedback mit Problemen, indem Sie auf **Feedback abgeben**.

    ![Graph-feedback](./media/apache-azure-spark-history-server/sparkui-graph-feedback.png)


## <a name="diagnosis-tab-in-spark-history-server"></a>Registerkarte "Diagnose" im Spark-Verlaufsserver
Wählen Sie die Auftrags-ID, und klicken Sie auf **Diagnose** im Menü des Tools zum Abrufen des Auftrags Diagnose anzeigen. Enthält die Registerkarte "Diagnose" **Datenschiefe**, **Zeitversatz**, und **Executor-Verwendungsanalyse**.
    
+ Überprüfen Sie die **Datenschiefe**, **Zeitversatz**, und **Executor-Verwendungsanalyse** dazu die Registerkarten.

    ![Diagnose-Registerkarten](./media/apache-azure-spark-history-server/sparkui-diagnosis-tabs.png)

### <a name="data-skew"></a>Datenschiefe
Klicken Sie auf **Datenschiefe** der entsprechenden Registerkarte Schiefe Aufgaben werden basierend auf den angegebenen Parametern angezeigt. 

+ **Geben Sie Parameter** -der erste Abschnitt zeigt die Parameter, die verwendet werden, um Probleme durch Datenschiefe zu erkennen. Die integrierte Regel lautet: Task-Datenlesevorgänge ist größer als dreimal das durchschnittliche Task-Datenlesevorgänge, und das Task-Datenlesevorgänge ist größer als 10 MB. Wenn Sie eine eigene Regel für den schiefen Tasks definieren möchten, können Sie die Parametern, die **verzerrt Phase**, und **neigen Char** Abschnitt entsprechend aktualisiert werden. 

+ **Phase verzerrt** – der zweite Abschnitt zeigt die Phasen, mit der Schiefe Aufgaben, die die oben angegebenen Kriterien erfüllen. Wenn mehr als eine verfälschte Aufgabe in einer Phase vorhanden ist, zeigt die Schiefe Phase-Tabelle nur die am häufigsten Schiefe Aufgabe (z. B. die größten Data für datenschiefe). 

    !["Section2" Probleme durch datenschiefe](./media/apache-azure-spark-history-server/sparkui-diagnosis-dataskew-section2.png)

+ **Diagramm verzerren** – Wenn eine Zeile in der datenschiefe ausgewählt ist, die datenschiefe Diagramm zeigt weitere Aufgabendetails Verteilungen auf Daten, die gelesen und die Ausführungszeit basierend. Die schiefen Aufgaben werden in rot markiert, und die normalen Vorgänge sind in blau markiert. Für die leistungsoptimierung zeigt das Diagramm nur bis zu 100 Beispielaufgaben. Die Taskdetails werden im unteren rechten Bereich angezeigt.

    ![Abschnitt3 Probleme durch datenschiefe](./media/apache-azure-spark-history-server/sparkui-diagnosis-dataskew-section3.png)

### <a name="time-skew"></a>Zeitabweichung
Die **Zeitversatz** Registerkarte Schiefe Aufgaben, die basierend auf der Ausführungszeit der Aufgabe angezeigt. 

+ **Geben Sie Parameter** -der erste Abschnitt zeigt die Parameter, die verwendet werden, um Zeitversatz zu erkennen. Die Standardkriterien zeitabweichung erkannt wird: Ausführungszeit der Aufgabe ist größer als drei Mal durchschnittliche Ausführungszeit und Ausführungszeit der Aufgabe ist größer als 30 Sekunden. Sie können die Parameter basierend auf Ihren Anforderungen ändern. Die **verzerrt Phase** und **Diagramm verzerren** den entsprechenden Phasen und Aufgabeninformationen angezeigt werden wie das **Datenschiefe** aus.

+ Klicken Sie auf **Zeitversatz**, wird in gefilterte Ergebnis angezeigt wird **verzerrt Phase** Abschnitt gemäß den Parametern, legen Sie im Abschnitt **angeben von Parametern**. Klicken Sie auf ein Element im **verzerrt Phase** Abschnitt, und klicken Sie dann das entsprechende Diagramm in Abschnitt3 entworfen wird, und die Taskdetails werden im unteren rechten Bereich angezeigt.

    ![Zeit datenschiefe "section2"](./media/apache-azure-spark-history-server/sparkui-diagnosis-timeskew-section2.png)

### <a name="executor-usage-analysis"></a>Executor-Verwendungsanalyse
Im Auslastungsdiagramm Executor visualisiert Spark Status des Auftrags konkreter Executor Zuordnung und ausgeführt wird.  

+ Klicken Sie auf **Executor-Verwendungsanalyse**, und klicken Sie dann wir vier Typen Kurven zur Nutzung von Executor Entwurf. Dazu gehören **zugeordneten Executors**, **ausgeführten Executors**, **im Leerlauf Executors**, und **Max-Executor-Instanzen**. In Bezug auf die zugeordneten Executors wird jede "Executor hinzugefügt" oder "Executor entfernte"-Ereignis erhöhen oder verringern die zugeordneten Executors. Sie können "Event Timeline" auf der Registerkarte "Aufträge" mehr Vergleich überprüfen.

    ![Registerkarte "Executors"](./media/apache-azure-spark-history-server/sparkui-diagnosis-executors.png)

+ Klicken Sie auf das Symbol "ordnerfarbe" zum Aktivieren oder deaktivieren Sie den entsprechenden Inhalt in allen Entwürfen.

    ![Wählen Sie Diagramm](./media/apache-azure-spark-history-server/sparkui-diagnosis-select-chart.png)


## <a name="known-issues"></a>Bekannte Probleme
Der Spark-Verlaufsserver hat die folgenden bekannten Probleme:

+ Es ist derzeit nur auf 2.3 von Spark-Cluster.

+ Ein-/Ausgabedaten, die mithilfe von RDDS werden in der Registerkarte "Daten" nicht angezeigt.

## <a name="next-steps"></a>Nächste Schritte

* [Verwalten von Ressourcen für Spark-Cluster in HDInsight](https://docs.microsoft.com/azure/hdinsight/spark/apache-spark-resource-manager)
* [Konfigurieren von Spark-Einstellungen](https://docs.microsoft.com/azure/hdinsight/spark/apache-spark-settings)
