---
title: RevoScaleR-R-Funktion-Bibliothek – SQL Server Machine Learning Services
description: Einführung in die RevoScaleR-Funktionsbibliothek in SQL Server 2016 R Services und SQL Server 2017 Machine Learning Services mit R.
ms.prod: sql
ms.technology: machine-learning
ms.date: 12/04/2018
ms.topic: conceptual
author: HeidiSteen
ms.author: heidist
manager: cgronlun
ms.openlocfilehash: c67fd63af6ed3492b8064be037ed4f8f5dff338f
ms.sourcegitcommit: 1e28f923cda9436a4395a405ebda5149202f8204
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/25/2019
ms.locfileid: "55044407"
---
# <a name="revoscaler-r-library-in-sql-server"></a>RevoScaleR (R-Bibliothek in SQL Server)

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

**RevoScaleR** ist eine Bibliothek von Hochleistungs-Data-Science-Funktionen von Microsoft. Funktionen unterstützen das Importieren von Daten, die Datentransformation, Zusammenfassung, Visualisierung und Analyse.

Im Gegensatz zur Basis-R-Funktionen können die RevoScaleR-Vorgänge für sehr große Datasets, parallele und bei DFS-Systemen ausgeführt werden. Funktionen können über Datasets verwendet werden, die nicht im Speicher mithilfe von Aufteilung und vereiteln Ergebnisse Wenn Vorgänge abgeschlossen wurden.

RevoScaleR-Funktionen werden mit bezeichnet ein **Rx** oder **Rx** Präfix, das sie einfach identifizieren zu können.

RevoScaleR dient als eine Plattform für verteilte Data Science. Beispielsweise können Sie die RevoScaleR-computekontexten und Transformationen mit den Stand der Technik-Algorithmen in [MicrosoftML](https://docs.microsoft.com/machine-learning-server/r/concept-what-is-the-microsoftml-package). Sie können auch [RxExec](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxexec) Basis-R-Funktionen parallel ausgeführt.

## <a name="full-reference-documentation"></a>Vollständige Referenz-Dokumentation

Die **RevoScaleR** Bibliothek wird in mehreren Microsoft-Produkte verteilt, aber wird, ob Sie die Bibliothek in SQL Server oder einem anderen Produkt erhalten. Da die Funktionen identisch sind, [Dokumentation für die einzelnen RevoScaleR-Funktionen](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/revoscaler) in nur einem Ort unter veröffentlicht wird die [R Verweis](https://docs.microsoft.com/machine-learning-server/r-reference/introducing-r-server-r-package-reference) für Microsoft Machine Learning Server. Sollten Sie jede Produkt-spezifische Verhalten vorhanden ist, wird Diskrepanzen auf der Hilfeseite für die Funktion angegeben.

## <a name="versions-and-platforms"></a>Versionen und Plattformen

Die **RevoScaleR** Bibliothek basierend auf R 3.4.3 und verfügbar ist, nur, wenn Sie eine der folgenden Microsoft-Produkten oder Downloads installieren:

+ [SQL Server 2016 R Services](../install/sql-r-services-windows-install.md)
+ [SQL Server 2017-Machine Learning-Dienste](../install/sql-machine-learning-services-windows-install.md)
+ [Microsoft Machine Learning Server 9.2.0 oder höher](https://docs.microsoft.com/machine-learning-server/)
+ [Microsoft R client](set-up-a-data-science-client.md)

> [!NOTE]
> Releaseversionen der Vollversion des Produkts sind Windows ausschließlich ab SQL Server 2017. Linux-Unterstützung für **RevoScaleR** ist neu in [Vorschau von SQL Server-2019](../../linux/sql-server-linux-setup-machine-learning.md).

## <a name="functions-by-category"></a>Funktionen, die nach Kategorie

Dieser Abschnitt listet die Funktionen nach Kategorie, erhalten Sie einen Überblick darüber, wie jeweils verwendet wird. Sie können auch die [Inhaltsverzeichnis](https://docs.microsoft.com/machine-learning-server/r-reference/introducing-r-server-r-package-reference) Sie Funktionen in alphabetischer Reihenfolge suchen.

## <a name="1-data-source-and-compute"></a>1-Datenquelle und compute

**RevoScaleR** enthält Funktionen zum Erstellen von Datenquellen und Festlegen des Speicherorts, oder *computekontext*, der, in dem Berechnungen ausgeführt werden. Ein Datenquellenobjekt ist ein Container, der eine Verbindungszeichenfolge zusammen mit dem gewünschten Datensatz als Tabelle, Ansicht oder Abfrage definiert angibt. Aufrufe von gespeicherten Prozeduren werden nicht unterstützt. Funktionen, die relevant für SQL Server-Szenarien werden in der folgenden Tabelle aufgeführt.

Verwenden unterschiedliche Datentypen in einigen Fällen, SQL Server und R. Eine Liste der Zuordnungen zwischen SQL und R-Datentypen, finden Sie unter [R-an-SQL-Datentypen](r-libraries-and-data-types.md).

| Funktion| Description|
| ------- | ---------- |
| [RxInSqlServer](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxinsqlserver) |  Erstellen Sie eine SQL Server Compute Context-Objekt, Push-Berechnungen auf einer remote-Instanz. Mehrere **RevoScaleR** Funktionen nehmen computekontext als Argument. |
|[rxGetComputeContext / rxSetComputeContext](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxsetcomputecontext) | Abrufen oder den aktiven computekontext festlegen. |
| [RxSqlServerData](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxsqlserverdata) | Erstellen Sie ein Datenobjekt, das basierend auf einer SQL Server-Abfrage oder Tabelle. |
| [RxOdbcData](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxodbcdata) | Erstellen Sie eine Datenquelle basierend auf einer ODBC-Verbindung. |
| [RxXdfData](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxxdfdata) | Erstellen Sie eine Datenquelle basierend auf eine lokale XDF-Datei. XDF-Dateien werden häufig verwendet, um in-Memory-Daten auf den Datenträger auszulagern. Eine XDF-Datei kann nützlich sein, bei der Verwendung von mehr Daten als aus der Datenbank in einem einzigen Batch übertragen werden kann, oder mehr Daten als in den Speicher passen. Z. B. Wenn Sie regelmäßig große Mengen von Daten aus einer Datenbank zu einer lokalen Arbeitsstation verschieben, anstatt die Abfrage der Datenbank wiederholt für jede R-Vorgang können Sie die XDF-Datei als eine Art von Cache die Daten lokal speichern, und klicken Sie dann mit Ihren R-Arbeitsbereich bearbeiten.|

> [!TIP]
> Wenn Sie noch nicht mit der Vorstellung von Datenquellen oder computekontexte, es wird empfohlen, zunächst [verteilte Verarbeitung](https://docs.microsoft.com/machine-learning-server/r/how-to-revoscaler-distributed-computing) in der Microsoft Machine Learning Server-Dokumentation.

### <a name="perform-ddl-statements"></a>Ausführen von DDL-Anweisungen

Sie können DDL-Anweisungen von R ausführen, wenn Sie die erforderlichen Berechtigungen für die Instanz und Datenbank haben. Die folgenden Funktionen verwenden die ODBC-Aufrufe zum Ausführen von DDL-Anweisungen oder das Schema der Datenbank abzurufen.

| Funktion| Description|
| ------- | ---------- |
| [RxSqlServerTableExists und rxSqlServerDropTable](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxsqlserverdroptable) | Löschen einer [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)] -Tabelle ab, oder Überprüfen Sie das Vorhandensein einer Datenbanktabelle oder -Objekt. |
| [rxExecuteSQLDDL](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxexecutesqlddl) | Führen Sie einen Befehl (Data Definition Language, Datendefinitionssprache) definiert, oder Datenbankobjekte bearbeitet. Diese Funktion kann keine Daten zurückgeben, und wird nur zum Abrufen oder Ändern der Objektschemas oder von Metadaten verwendet.|

## <a name="2-data-manipulation-etl"></a>2 – datenbearbeitung (ETL)

Nachdem Sie ein Datenquellenobjekt erstellt haben, können Sie das Objekt, das Laden von Daten in diese oder Transformieren von Daten schreiben neue Daten in das angegebene Ziel. Abhängig von der Größe der Daten in der Quelle können Sie die Batchgröße auch als Teil der Datenquelle definieren und Daten in Blöcken verschieben.

| Funktion | Description |
|----------|-------------|
| [rxOpen-methods](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxopen-methods) | Überprüfen, ob eine Datenquelle verfügbar ist, öffnen oder schließen Sie eine Datenquelle, Lesen von Daten aus einer Quelle, Schreiben von Daten in das Ziel und schließt eine Datenquelle.|
| [rxImport](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rximport) | Verschieben von Daten aus einer Datenquelle in File Storage oder in einen Datenrahmen.|
| [rxDataStep](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxdatastep) | Transformieren von Daten beim Verschieben zwischen Datenquellen.|

<a name="graphing-functions"></a>

## <a name="3-graphing-functions"></a>3-diagrammerstellung Funktionen

| Funktionsname | Description |
|---------------|-------------|
|[rxHistogram](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxhistogram)  |Erstellt ein Histogramm aus Daten. | 
|[rxLinePlot](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxlineplot) |Erstellt ein Liniendiagramm aus Daten. | 
|[rxLorenz](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxlorenz)  |Berechnet eine Lorenz-Kurve der dargestellt werden kann. | 
|[rxRocCurve](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxroc)  |Berechnet und zeichnet ROC-Kurven aus ist- und vorhergesagten Daten. | 

<a name="statistics-functions"></a>

## <a name="4-descriptive-statistics"></a>4-aussagekräftige statistische Daten

| Funktionsname | Description |
|---------------|-------------|
|[rxQuantile](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxquantile) <sup>*</sup> |Berechnet ungefähren quantilen für xdf-Dateien und -Datenrahmen ohne Sortierung. | 
|[rxSummary](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxsummary) <sup>*</sup> |Grundlegende Statistiken der Zusammenfassung von Daten, einschließlich der Berechnungen nach Gruppe. Schreiben von Gruppe-Berechnungen in xdf-Datei, die nicht unterstützt. | 
|[rxCrossTabs](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxcrosstabs) <sup>*</sup> |Formel-basierte Kreuztabelle von Daten. | 
|[rxCube](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxcube) <sup>*</sup> |Alternative Formel basierende Kreuztabelle entwickelt, die für die effiziente Darstellung, die Cube-Ergebnisse zurückgegeben. Schreiben der Ausgabe in xdf-Datei, die nicht unterstützt. | 
|[rxMarginals](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxmarginals)  |Marginale Zusammenfassungen von Cross-Tabulatorzeichen. | 
|[as.xtabs](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/as.xtabs)  |Konvertiert kreuztabellenergebnisse in ein Xtabs-Objekt. | 
|[rxChiSquaredTest](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxchisquaredtest)  |Führt einen Chi-Test für Xtabs-Objekt. Bei kleinen Datasets verwendet und keine Daten segmentieren. | 
|[rxFisherTest](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxchisquaredtest)  |Führt exakten Test nach Fisher für Xtabs-Objekt. Bei kleinen Datasets verwendet und keine Daten segmentieren. | 
|[rxKendallCor](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxchisquaredtest)  |Berechnet den Kendalls Tau-Rangkorrelationskoeffizienten mithilfe Xtabs-Objekts. | 
|[rxPairwiseCrossTab](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxpairwisecrosstab)  |Wendet eine Funktion auf paarweise Kombinationen von Zeilen und Spalten eines Xtabs-Objekts. | 
|[rxRiskRatio](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxriskratio)  |Berechnet das relative Risiko für ein Objekt zwei und zwei Xtabs an. | 
|[rxOddsRatio](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxriskratio)  |Berechnet das wahrscheinlichkeitsverhältnis für ein Objekt zwei und zwei Xtabs an. | 

<sup>*</sup> Gibt an, die am häufigsten verwendeten Funktionen in dieser Kategorie.

<a name="prediction-functions"></a>

## <a name="5-prediction-functions"></a>5-Vorhersagefunktionen

| Funktionsname | Description |
|---------------|-------------|
|[rxLinMod](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxlinmod) <sup>*</sup> |Passt ein Lineares Modell auf Daten. | 
|[rxLogit](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxlogit) <sup>*</sup> |Passt ein Logistisches Regressionsmodell auf Daten. | 
|[rxGlm](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxglm) <sup>*</sup> |Passt ein Verallgemeinertes Lineares Modell auf Daten. | 
|[rxCovCor](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxcovcor) <sup>*</sup> |Berechnet die Kovarianz, Korrelation oder Summe der Quadrate Kreuzprodukt Matrix für einen Satz von Variablen. | 
|[rxDTree](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxdtree) <sup>*</sup> |Passen die Struktur klassifizierungs- oder Regressionsmodells aus, die Daten. | 
|[rxBTrees](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxbtrees) <sup>*</sup> |Passen einen entscheidungswald klassifizierungs- oder Regressionsmodell auf Daten mithilfe einer stochastic Gradient-boosting-Algorithmus. | 
|[rxDForest](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxdforest) <sup>*</sup> |Passen einen entscheidungswald klassifizierungs- oder Regressionsmodell auf Daten. | 
|[rxPredict](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxPredict) <sup>*</sup> |Berechnet Vorhersagen für angepasste Modelle. Ausgabe muss es sich um eine XDF-Datenquelle sein. | 
|[rxKmeans](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxkmeans) <sup>*</sup> |Führt die k-Means-clustering. | 
|[rxNaiveBayes](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxnaivebayes) <sup>*</sup> |Führt die Naive Bayes-Klassifikation. | 
|[rxCov](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxcovcor) |Berechnet die kovarianzmatrix für einen Satz von Variablen. | 
|[rxCor](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxcovcor)  |Berechnet die Korrelationsmatrix für einen Satz von Variablen. | 
|[rxSSCP](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxcovcor)  |Berechnen der Summe der Quadrate Kreuzprodukt Matrix für einen Satz von Variablen. | 
|[rxRoc](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxroc)  |Receiver Operating Merkmal (ROC)-Berechnungen mithilfe der ist- und vorhergesagten Werte aus binären Klassifizierer System. | 

<sup>*</sup> Gibt an, die am häufigsten verwendeten Funktionen in dieser Kategorie.


## <a name="how-to-work-with-revoscaler"></a>Arbeiten mit RevoScaleR

Funktionen in **RevoScaleR** in R-Code gekapselt, die in gespeicherten Prozeduren können aufgerufen werden. Die meisten Entwickler erstellen **RevoScaleR** Lösungen lokal, und migrieren Sie dann die fertig gestellten R-Code zu gespeicherten Prozeduren als eine Übung für die Bereitstellung.

Bei lokaler Ausführung Sie in der Regel ein R-Skript ausführen, über die Befehlszeile oder aus einer R-Entwicklungsumgebung, und geben Sie einen SQL Server-computekontext mithilfe eines der **RevoScaleR** Funktionen. Sie können den entfernten computekontext für den gesamten Code oder für einzelne Funktionen verwenden. Beispielsweise empfiehlt es sich zum Trainieren des Modells mit dem Server verwenden die neuesten Daten und vermeiden datenverschiebungen auslagern.

Wenn Sie bereit sind, kapseln R-Skript innerhalb einer gespeicherten Prozedur, [Sp_execute_external_script](https://docs.microsoft.com/sql/relational-databases/system-stored-procedures/sp-execute-external-script-transact-sql), es wird empfohlen, den Code umzuschreiben, als einzelne Funktion, die eindeutig die Eingaben und Ausgaben definiert wurde. 

## <a name="see-also"></a>Siehe auch

+ [R-tutorials](../tutorials/sql-server-r-tutorials.md)
+ [Informationen Sie zur Verwendung von berechneten Kontexten](../tutorials/deepdive-data-science-deep-dive-using-the-revoscaler-packages.md)
+ [R für SQL-Entwickler: Trainieren und zu operationalisieren eines Modells](../tutorials/sqldev-in-database-r-for-sql-developers.md)
+ [Microsoft-Produkt-Beispielen auf GitHub](https://github.com/Microsoft/SQL-Server-R-Services-Samples)
+ [R-Verweis (Microsoft Machine Learning Server)](https://docs.microsoft.com/machine-learning-server/r-reference/introducing-r-server-r-package-reference) 
