---
title: Revoscaler R-Funktionsbibliothek
description: Einführung in die revoscaler-Funktionsbibliothek in SQL Server 2016 R Services und SQL Server Machine Learning Services mit R.
ms.prod: sql
ms.technology: machine-learning
ms.date: 12/04/2018
ms.topic: conceptual
author: dphansen
ms.author: davidph
monikerRange: '>=sql-server-2016||>=sql-server-linux-ver15||=sqlallproducts-allversions'
ms.openlocfilehash: b5dcd2f14d1a1d8e23a62be299b1ff6f41814041
ms.sourcegitcommit: 321497065ecd7ecde9bff378464db8da426e9e14
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/01/2019
ms.locfileid: "68715065"
---
# <a name="revoscaler-r-library-in-sql-server"></a>Revoscaler (R-Bibliothek in SQL Server)

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

**Revoscaler** ist eine Bibliothek mit Hochleistungs Data Science Funktionen von Microsoft. Funktionen unterstützen Datenimport, Datentransformation, Zusammenfassung, Visualisierung und Analyse.

Im Gegensatz zu grundlegenden R-Funktionen können revoscaler-Vorgänge für sehr große Datasets parallel und für verteilte Dateisysteme ausgeführt werden. Funktionen können über Datasets, die nicht in den Arbeitsspeicher passen, mithilfe von segmentieren und durch neuzufügende Ergebnisse, wenn Vorgänge ausgeführt werden, funktionieren.

Revoscaler-Funktionen sind mit einem **RX** -oder **RX** -Präfix gekennzeichnet, damit Sie leichter zu identifizieren sind.

Revoscaler fungiert als Plattform für verteilte Data Science. Beispielsweise können Sie die revoscaler-computekontexte und-Transformationen mit den modernen Algorithmen in [microsoftml](https://docs.microsoft.com/machine-learning-server/r/concept-what-is-the-microsoftml-package)verwenden. Sie können [rxexec](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxexec) auch verwenden, um Basis-R-Funktionen parallel auszuführen.

## <a name="full-reference-documentation"></a>Vollständige Referenz Dokumentation

Die **revoscaler** -Bibliothek ist in mehreren Microsoft-Produkten verteilt, aber die Verwendung ist identisch, unabhängig davon, ob Sie die Bibliothek in SQL Server oder einem anderen Produkt erhalten. Da die-Funktionen identisch sind, wird die [Dokumentation für einzelne revoscaler-Funktionen](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/revoscaler) nur an einem Speicherort unter der [R-Referenz](https://docs.microsoft.com/machine-learning-server/r-reference/introducing-r-server-r-package-reference) für Microsoft Machine Learning Server veröffentlicht. Wenn produktspezifische Verhalten vorhanden sind, werden auf der Hilfeseite der Funktion Abweichungen festgestellt.

## <a name="versions-and-platforms"></a>Versionen und Plattformen

Die **revoscaler** -Bibliothek basiert auf R 3.4.3 und ist nur verfügbar, wenn Sie eines der folgenden Microsoft-Produkte oder-Downloads installieren:

+ [SQL Server 2016 R-Dienste](../install/sql-r-services-windows-install.md)
+ [SQL Server-Machine Learning-Dienste](../install/sql-machine-learning-services-windows-install.md)
+ [Microsoft Machine Learning Server 9.2.0 oder höher](https://docs.microsoft.com/machine-learning-server/)
+ [Microsoft R-Client](set-up-a-data-science-client.md)

> [!NOTE]
> Vollversion der Produktversion ist nur Windows, beginnend mit SQL Server 2017. Die Linux-Unterstützung für **revoscaler** ist neu in [SQL Server 2019 Preview](../../linux/sql-server-linux-setup-machine-learning.md).

## <a name="functions-by-category"></a>Funktionen nach Kategorie

In diesem Abschnitt werden die Funktionen nach Kategorie aufgelistet, um Ihnen einen Überblick darüber zu verschaffen, wie die einzelnen Funktionen verwendet werden. Sie können auch das Inhalts [Verzeichnis](https://docs.microsoft.com/machine-learning-server/r-reference/introducing-r-server-r-package-reference) verwenden, um Funktionen in alphabetischer Reihenfolge zu suchen.

## <a name="1-data-source-and-compute"></a>1: Datenquelle und Compute

**Revoscaler** enthält Funktionen zum Erstellen von Datenquellen und zum Festlegen des SpeicherOrts bzw. des computekontexts, in dem Berechnungen durchgeführt werden. Ein Datenquellenobjekt ist ein Container, der eine Verbindungszeichenfolge zusammen mit dem gewünschten Datensatz als Tabelle, Ansicht oder Abfrage definiert angibt. Aufrufe von gespeicherten Prozeduren werden nicht unterstützt. In der folgenden Tabelle sind die für SQL Server Szenarien relevanten Funktionen aufgeführt.

SQL Server und R verwenden in einigen Fällen unterschiedliche Datentypen. Eine Liste der Zuordnungen zwischen SQL-und r-Datentypen finden [Sie unter R-zu-SQL-Datentypen](r-libraries-and-data-types.md).

| Funktion| Beschreibung|
| ------- | ---------- |
| [RxInSqlServer](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxinsqlserver) |  Erstellen Sie ein SQL Server computekontext-Objekt, um Berechnungen in eine Remote Instanz zu überführen. Mehrere **revoscaler** -Funktionen nehmen den computekontext als Argument an. |
|[rxgetcomputecontext/rxsetcomputecontext](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxsetcomputecontext) | Gibt den aktiven computekontext an oder legt ihn fest. |
| [RxSqlServerData](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxsqlserverdata) | Erstellen Sie ein Datenobjekt, das auf einer SQL Server Abfrage oder Tabelle basiert. |
| [RxOdbcData](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxodbcdata) | Erstellen Sie eine Datenquelle basierend auf einer ODBC-Verbindung. |
| [Rxxdfdata](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxxdfdata) | Erstellen Sie eine Datenquelle basierend auf einer lokalen Xdf-Datei. Xdf-Dateien werden häufig verwendet, um in-Memory-Daten auf den Datenträger zu laden. Eine Xdf-Datei kann nützlich sein, wenn Sie mit mehr Daten arbeiten, als aus der Datenbank in einem Batch übertragen werden können, oder mehr Daten als in den Arbeitsspeicher passen. Wenn Sie z. b. regelmäßig große Datenmengen aus einer Datenbank auf eine lokale Arbeitsstation verschieben, anstatt die Datenbank für jeden R-Vorgang wiederholt abzufragen, können Sie die Xdf-Datei als eine Art Cache verwenden, um die Daten lokal zu speichern und dann in Ihrem R-Arbeitsbereich zu arbeiten.|

> [!TIP]
> Wenn Sie mit der Idee von Datenquellen oder computekontexten noch nicht vertraut sind, empfehlen wir Ihnen, mit der [verteilten Verarbeitung](https://docs.microsoft.com/machine-learning-server/r/how-to-revoscaler-distributed-computing) in der Microsoft Machine Learning Server-Dokumentation zu beginnen.

### <a name="perform-ddl-statements"></a>Ausführen von DDL-Anweisungen

Sie können DDL-Anweisungen von R ausführen, wenn Sie über die erforderlichen Berechtigungen für die-Instanz und die-Datenbank verfügen. Die folgenden Funktionen verwenden ODBC-Aufrufe zum Ausführen von DDL-Anweisungen oder zum Abrufen des Datenbankschemas.

| Funktion| Beschreibung|
| ------- | ---------- |
| [rxsqlservertableist und rxsqlserverdroptable](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxsqlserverdroptable) | Löschen Sie [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)] eine Tabelle, oder überprüfen Sie, ob eine Datenbanktabelle oder ein Objekt vorhanden ist. |
| [rxExecuteSQLDDL](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxexecutesqlddl) | Führen Sie einen DDL-Befehl (Data Definition Language) aus, der Datenbankobjekte definiert oder bearbeitet. Diese Funktion kann keine Daten zurückgeben und wird nur zum Abrufen oder Ändern des Objekt Schemas oder der Metadaten verwendet.|

## <a name="2-data-manipulation-etl"></a>2-Datenbearbeitung (ETL)

Nachdem Sie ein Datenquellen Objekt erstellt haben, können Sie das-Objekt verwenden, um Daten in das-Objekt zu laden, Daten zu transformieren oder neue Daten in das angegebene Ziel zu schreiben. Abhängig von der Größe der Daten in der Quelle können Sie die Batchgröße auch als Teil der Datenquelle definieren und Daten in Blöcken verschieben.

| Funktion | Beschreibung |
|----------|-------------|
| [rxopen-Methoden](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxopen-methods) | Überprüfen Sie, ob eine Datenquelle verfügbar ist, öffnen oder schließen Sie eine Datenquelle, lesen Sie Daten aus einer Quelle, schreiben Sie Daten in das Ziel, und schließen Sie eine Datenquelle.|
| [rxImport](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rximport) | Verschieben von Daten aus einer Datenquelle in den Dateispeicher oder in einen Datenrahmen.|
| [rxDataStep](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxdatastep) | Transformieren Sie Daten, während Sie Sie zwischen Datenquellen verschieben.|

<a name="graphing-functions"></a>

## <a name="3-graphing-functions"></a>3-graphingfunktionen

| Funktionsname | Beschreibung |
|---------------|-------------|
|[rxHistogram](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxhistogram)  |Erstellt ein Histogramm aus Daten. | 
|[rxLinePlot](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxlineplot) |Erstellt ein Liniendiagramm aus Daten. | 
|[rxLorenz](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxlorenz)  |Berechnet eine Lorenz-Kurve, die gezeichnet werden kann. | 
|[rxRocCurve](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxroc)  |Berechnet und zeichnet ROC-Kurven aus tatsächlichen und vorhergesagten Daten. | 

<a name="statistics-functions"></a>

## <a name="4-descriptive-statistics"></a>4: beschreibende Statistik

| Funktionsname | Beschreibung |
|---------------|-------------|
|[rxquantile](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxquantile)<sup>*</sup> |Berechnet ungefähre Quantilen für Xdf-Dateien und-Datenrahmen ohne Sortierung. | 
|[rxsummary](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxsummary)<sup>*</sup> |Grundlegende Zusammenfassungs Statistiken der Daten, einschließlich der Berechnungen nach Gruppe. Das Schreiben von Gruppen Berechnungen in eine Xdf-Datei wird nicht unterstützt. | 
|[rxCrossTabs](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxcrosstabs) <sup>*</sup> |Formelbasierte Kreuz Tabellen übergreifende Daten. | 
|[rxcube](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxcube)<sup>*</sup> |Alternative formelbasierte Kreuz Tabellen, die für eine effiziente Darstellung entworfen wurden, die Cube-Ergebnisse zurückgibt. Das Schreiben der Ausgabe in eine Xdf-Datei wird nicht unterstützt. | 
|[rxmarginals](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxmarginals)  |Marginale Zusammenfassungen von übergreifenden Tabulationen. | 
|[as.xtabs](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/as.xtabs)  |Konvertiert Kreuz Tabellen Ergebnisse in ein xtabs-Objekt. | 
|[rxChiSquaredTest](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxchisquaredtest)  |Führt einen Chi-Quadrat-Test für das xtabs-Objekt aus. Wird mit kleinen Datasets verwendet, und es werden keine Daten segmentieren. | 
|[rxFisherTest](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxchisquaredtest)  |Führt den exakten Test von Fisher für das xtabs-Objekt aus. Wird mit kleinen Datasets verwendet, und es werden keine Daten segmentieren. | 
|[rxKendallCor](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxchisquaredtest)  |Berechnet mithilfe des xtabs-Objekts den Tau-Rang Korrelationskoeffizient. | 
|[rxPairwiseCrossTab](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxpairwisecrosstab)  |Wendet eine Funktion auf paar Weise Kombinationen von Zeilen und Spalten eines xtabs-Objekts an. | 
|[rxRiskRatio](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxriskratio)  |Berechnen Sie das relative Risiko für ein zwei-bis zwei xtabs-Objekt. | 
|[rxOddsRatio](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxriskratio)  |Berechnen Sie das Quoten Verhältnis für ein zwei-bis-zwei xtabs-Objekt. | 

<sup>*</sup>Gibt die am häufigsten verwendeten Funktionen in dieser Kategorie an.

<a name="prediction-functions"></a>

## <a name="5-prediction-functions"></a>5-Vorhersagefunktionen

| Funktionsname | Beschreibung |
|---------------|-------------|
|[rxlinmod](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxlinmod)<sup>*</sup> |Passt ein lineares Modell auf Daten an. | 
|[rxLogit](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxlogit) <sup>*</sup> |Passt ein logistisches Regressionsmodell auf Daten an. | 
|[rxGlm](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxglm) <sup>*</sup> |Passt ein verallgemeinertes lineares Modell auf Daten an. | 
|[rxCovCor](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxcovcor) <sup>*</sup> |Berechnen Sie die Kovarianz, Korrelation oder Summe der Quadrate/der Kreuz Produkt Matrix für einen Satz von Variablen. | 
|[rxDTree](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxdtree) <sup>*</sup> |Passt eine Klassifizierung oder Regressions Struktur auf Daten an. | 
|[rxbtrees](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxbtrees)<sup>*</sup> |Passt eine Klassifizierung oder Regressions Entscheidungs Gesamtstruktur mithilfe eines stochastischen Gradient-Verstärkungs Algorithmus auf Daten an. | 
|[rxdforest](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxdforest)<sup>*</sup> |Passt eine Klassifizierung oder Regressions Entscheidungs Gesamtstruktur auf Daten an. | 
|[rxvorhersage](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxPredict)<sup>*</sup> |Berechnet Vorhersagen für angepasste Modelle. Die Ausgabe muss eine Xdf-Datenquelle sein. | 
|[rxkmeans](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxkmeans)<sup>*</sup> |Führt das k-Means-Clustering aus. | 
|[rxNaiveBayes](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxnaivebayes) <sup>*</sup> |Führt eine Naive Bayes-Klassifizierung aus. | 
|[rxCov](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxcovcor) |Berechnen der Kovarianz Matrix für einen Satz von Variablen. | 
|[rxCor](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxcovcor)  |Berechnen Sie die Korrelationsmatrix für einen Satz von Variablen. | 
|[rxSSCP](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxcovcor)  |Berechnen Sie die Summe der Quadrate/der Kreuz Produkt Matrix für einen Satz von Variablen. | 
|[rxRoc](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxroc)  |Roc-Berechnungen (Receiver Operating Merkmal), die tatsächliche und vorhergesagte Werte aus dem binären Klassifizierungssystem verwenden. | 

<sup>*</sup>Gibt die am häufigsten verwendeten Funktionen in dieser Kategorie an.


## <a name="how-to-work-with-revoscaler"></a>Arbeiten mit revoscaler

Funktionen in **revoscaler** können in R-Code in gespeicherten Prozeduren gekapselt werden. Die meisten Entwickler erstellen **revoscaler** -Lösungen lokal und Migrieren den fertiggestellten R-Code als Bereitstellungs Übung zu gespeicherten Prozeduren.

Wenn Sie lokal ausgeführt werden, führen Sie in der Regel ein R-Skript über die Befehlszeile oder aus einer r-Entwicklungsumgebung aus, und geben Sie einen SQL Server computekontext mit einer der **revoscaler** -Funktionen an. Sie können den remotecomputekontext für den gesamten Code oder für einzelne Funktionen verwenden. Beispielsweise können Sie die Modell Schulung auf den Server auslagern, um die neuesten Daten zu verwenden und die Daten Verschiebung zu vermeiden.

Wenn Sie bereit sind, das R-Skript in einer gespeicherten Prozedur, [sp_execute_external_script](https://docs.microsoft.com/sql/relational-databases/system-stored-procedures/sp-execute-external-script-transact-sql), zu kapseln, empfiehlt es sich, den Code als einzelne Funktion zu umschreiben, die klar definierte Eingaben und Ausgaben aufweist. 

## <a name="see-also"></a>Siehe auch

+ [R-Tutorials](../tutorials/sql-server-r-tutorials.md)
+ [Weitere Informationen zur Verwendung von computekontexten](../tutorials/deepdive-data-science-deep-dive-using-the-revoscaler-packages.md)
+ [R für SQL-Entwickler: Trainieren und operationalisieren eines Modells](../tutorials/sqldev-in-database-r-for-sql-developers.md)
+ [Microsoft-Produktbeispiele auf GitHub](https://github.com/Microsoft/SQL-Server-R-Services-Samples)
+ [R-Verweis (Microsoft Machine Learning Server)](https://docs.microsoft.com/machine-learning-server/r-reference/introducing-r-server-r-package-reference) 
