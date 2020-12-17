---
title: R-Paket „RevoScaleR“
description: „RevoScaleR“ ist ein R-Paket von Microsoft, das verteiltes Computing, Remotecomputekontexte und hochleistungsfähige Data Science-Algorithmen unterstützt. Außerdem werden Datenimport, Datentransformation, Zusammenfassung, Visualisierung und Analyse unterstützt. Das Paket ist in SQL Server Machine Learning Services und SQL Server 2016 R Services enthalten.
ms.prod: sql
ms.technology: machine-learning-services
ms.date: 07/14/2020
ms.topic: how-to
author: dphansen
ms.author: davidph
monikerRange: '>=sql-server-2016||>=sql-server-linux-ver15'
ms.openlocfilehash: 87d4fbcfa114b9f80f19495b3d3728c2dd7678ac
ms.sourcegitcommit: 1a544cf4dd2720b124c3697d1e62ae7741db757c
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 12/14/2020
ms.locfileid: "97470831"
---
# <a name="revoscaler-r-package-in-sql-server-machine-learning-services"></a>RevoScaleR (R-Paket in SQL Server Machine Learning Services)

[!INCLUDE [SQL Server 2016 and later](../../includes/applies-to-version/sqlserver2016.md)]

**RevoScaleR** ist ein R-Paket von Microsoft, das verteiltes Computing, Remotecomputekontexte und hochleistungsfähige Data Science-Algorithmen unterstützt. Außerdem werden Datenimport, Datentransformation, Zusammenfassung, Visualisierung und Analyse unterstützt. Das Paket ist in [SQL Server Machine Learning Services](../sql-server-machine-learning-services.md) und [SQL Server 2016 R Services](sql-server-r-services.md) enthalten.

Im Gegensatz zu den grundlegenden R-Funktionen können RevoScaleR-Vorgänge für große Datasets, parallel und für verteilte Dateisysteme ausgeführt werden. Die Funktionen können über Datasets, die nicht in den Arbeitsspeicher passen, durch Segmentierung und Neuzusammenstellung der Ergebnisse nach Beendigung der Vorgänge verwendet werden.

RevoScaleR-Funktionen sind mit einem rx**- oder **Rx**-Präfix gekennzeichnet, damit sie leichter zu identifizieren sind.

RevoScaleR fungiert als Plattform für verteilte Data Science-Prozesse. Sie können beispielsweise die RevoScaleR-Computekontexte und -Transformationen mit den modernen Algorithmen in [MicrosoftML](/machine-learning-server/r/concept-what-is-the-microsoftml-package) verwenden. Sie können auch [rxExec](/machine-learning-server/r-reference/revoscaler/rxexec) verwenden, um grundlegende R-Funktionen parallel auszuführen.

## <a name="full-reference-documentation"></a>Vollständige Referenzdokumentation

Das **RevoScaleR**-Paket wird in mehreren Microsoft-Produkten bereitgestellt. Die Verwendung ist jedoch immer identisch, unabhängig davon, ob Sie das Paket in SQL Server oder einem anderen Produkt abrufen. Aus diesem Grund wird die [Dokumentation für einzelne RevoScaleR-Funktionen](/machine-learning-server/r-reference/revoscaler/revoscaler) nur an einer Stelle in der [R-Referenz](/machine-learning-server/r-reference/introducing-r-server-r-package-reference) für Microsoft Machine Learning Server veröffentlicht. Abweichungen durch produktspezifisches Verhalten finden Sie ggf. auf der Hilfeseite der Funktion.

## <a name="versions-and-platforms"></a>Versionen und Plattformen

Das **RevoScaleR**-Paket basiert auf R 3.4.3 und ist nur verfügbar, wenn Sie eines der folgenden Microsoft-Produkte oder Downloads installieren:

+ [SQL Server 2016 R Services](../install/sql-r-services-windows-install.md)
+ [SQL Server Machine Learning Services](../install/sql-machine-learning-services-windows-install.md)
+ [Microsoft Machine Learning Server 9.2.0 oder höher](/machine-learning-server/)
+ [Microsoft R Client](set-up-a-data-science-client.md)

> [!NOTE]
> Vollständige Produktversionen sind in SQL Server 2017 nur unter Windows verfügbar. In [SQL Server 2019](../../linux/sql-server-linux-setup-machine-learning.md) wird **RevoScaleR** sowohl unter Windows als auch unter Linux unterstützt.

## <a name="functions-by-category"></a>Funktionen nach Kategorie

In diesem Abschnitt werden die Funktionen nach Kategorien aufgelistet, damit Sie einen Überblick über die Verwendung der einzelnen Funktionen erhalten. Im [Inhaltsverzeichnis](/machine-learning-server/r-reference/introducing-r-server-r-package-reference) können Sie in alphabetischer Reihenfolge nach den Funktionen suchen.

## <a name="1-data-source-and-compute"></a>1: Datenquelle und Compute

**RevoScaleR** enthält Funktionen zum Erstellen von Datenquellen und zum Festlegen des Speicherorts bzw. *Computekontexts*, in dem Berechnungen durchgeführt werden. Ein Datenquellenobjekt ist ein Container, der eine Verbindungszeichenfolge zusammen mit dem gewünschten Datensatz als Tabelle, Ansicht oder Abfrage definiert angibt. Aufrufe von gespeicherten Prozeduren werden nicht unterstützt. In der folgenden Tabelle sind die für SQL Server-Szenarios relevanten Funktionen aufgeführt.

SQL Server und R verwenden in bestimmten Fällen unterschiedliche Datentypen. Eine Liste der Zuordnungen zwischen SQL Server- und R-Datentypen finden Sie unter [Zuordnungen zwischen R- und SQL Server-Datentypen](r-libraries-and-data-types.md).

| Funktion| BESCHREIBUNG|
| ------- | ---------- |
| [RxInSqlServer](/machine-learning-server/r-reference/revoscaler/rxinsqlserver) |  Erstellt ein SQL Server-Computekontextobjekt, um Berechnungen in eine Remoteinstanz zu überführen. Mehrere **RevoScaleR**-Funktionen verwenden den Computekontext als Argument. |
|[rxGetComputeContext/rxSetComputeContext](/machine-learning-server/r-reference/revoscaler/rxsetcomputecontext) | Gibt den aktiven Computekontext an oder legt ihn fest |
| [RxSqlServerData](/machine-learning-server/r-reference/revoscaler/rxsqlserverdata) | Erstellt ein Datenobjekt basierend auf einer SQL Server-Abfrage oder -Tabelle |
| [RxOdbcData](/machine-learning-server/r-reference/revoscaler/rxodbcdata) | Erstellt eine Datenquelle basierend auf einer ODBC-Verbindung |
| [RxXdfData](/machine-learning-server/r-reference/revoscaler/rxxdfdata) | Erstellt eine Datenquelle basierend auf einer lokalen XDF-Datei. XDF-Dateien werden häufig verwendet, um In-Memory-Daten auf einen Datenträger auszulagern. Eine XDF-Datei kann nützlich sein, wenn Sie mit mehr Daten arbeiten als in einem Batch aus der Datenbank übertragen werden können oder als in den Arbeitsspeicher passen. Wenn Sie beispielsweise regelmäßig große Mengen von Daten aus einer Datenbank zu einer lokalen Arbeitsstation verschieben, anstatt die Datenbank wiederholt für jeden R-Vorgang abzufragen, können Sie die XDF-Datei als Cache verwenden, um die Daten lokal zu speichern und anschließend mit ihnen im R-Arbeitsbereich zu arbeiten.|

> [!TIP]
> Wenn Sie mit dem Konzept von Datenquellen oder Computekontexten noch nicht vertraut sind, empfiehlt es sich, zunächst den Artikel über [verteiltes Computing](/machine-learning-server/r/how-to-revoscaler-distributed-computing) in der Microsoft Machine Learning Server-Dokumentation zu lesen.

### <a name="perform-ddl-statements"></a>Ausführen von DDL-Anweisungen

Sie können DDL-Anweisungen von R ausführen, wenn Sie über die erforderlichen Berechtigungen für die Instanz und die Datenbank verfügen. Die folgenden Funktionen verwenden ODBC-Aufrufe zum Ausführen von DDL-Anweisungen oder zum Abrufen des Datenbankschemas.

| Funktion| BESCHREIBUNG|
| ------- | ---------- |
| [rxSqlServerTableExists und rxSqlServerDropTable](/machine-learning-server/r-reference/revoscaler/rxsqlserverdroptable) | Löscht eine [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)]-Tabelle oder überprüft, ob eine Datenbanktabelle oder ein -objekt vorhanden ist |
| [rxExecuteSQLDDL](/machine-learning-server/r-reference/revoscaler/rxexecutesqlddl) | Führt einen DDL-Befehl (Data Definition Language) aus, der Datenbankobjekte definiert oder bearbeitet. Diese Funktion kann keine Daten zurückgeben und wird nur zum Abrufen oder Ändern des Objektschemas oder der Metadaten verwendet.|

## <a name="2-data-manipulation-etl"></a>2: Datenbearbeitung (ETL)

Nachdem Sie ein Datenquellenobjekt erstellt haben, können Sie das Objekt verwenden, um Daten in das Objekt zu laden, Daten zu transformieren oder neue Daten in das angegebene Ziel zu schreiben. Abhängig von der Größe der Daten in der Quelle können Sie die Batchgröße auch als Teil der Datenquelle definieren und Daten in Blöcken verschieben.

| Funktion | BESCHREIBUNG |
|----------|-------------|
| [rxOpen-methods](/machine-learning-server/r-reference/revoscaler/rxopen-methods) | Überprüft, ob eine Datenquelle verfügbar ist, öffnet oder schließt eine Datenquelle, liest Daten aus einer Quelle, schreibt Daten in das Ziel, und schließt eine Datenquelle|
| [rxImport](/machine-learning-server/r-reference/revoscaler/rximport) | Verschiebt Daten aus einer Datenquelle in den Dateispeicher oder in einen Datenrahmen|
| [rxDataStep](/machine-learning-server/r-reference/revoscaler/rxdatastep) | Transformiert Daten, während sie zwischen Datenquellen verschoben werden|

<a name="graphing-functions"></a>

## <a name="3-graphing-functions"></a>3: Diagrammerstellungsfunktionen

| Funktionsname | BESCHREIBUNG |
|---------------|-------------|
|[rxHistogram](/machine-learning-server/r-reference/revoscaler/rxhistogram)  |Erstellt ein Histogramm aus Daten | 
|[rxLinePlot](/machine-learning-server/r-reference/revoscaler/rxlineplot) |Erstellt ein Liniendiagramm aus Daten | 
|[rxLorenz](/machine-learning-server/r-reference/revoscaler/rxlorenz)  |Berechnet eine Lorenz-Kurve, die dargestellt werden kann | 
|[rxRocCurve](/machine-learning-server/r-reference/revoscaler/rxroc)  |Berechnet und zeichnet ROC-Kurven aus Ist- und vorhergesagten Daten | 

<a name="statistics-functions"></a>

## <a name="4-descriptive-statistics"></a>4: Beschreibende Statistik

| Funktionsname | BESCHREIBUNG |
|---------------|-------------|
|[rxQuantile](/machine-learning-server/r-reference/revoscaler/rxquantile) <sup>*</sup> |Berechnet die ungefähren Quantilen für XDF-Dateien oder Datenrahmen ohne Sortierung | 
|[rxSummary](/machine-learning-server/r-reference/revoscaler/rxsummary) <sup>*</sup> |Generiert eine grundlegende, zusammenfassende Statistik für Daten, einschließlich der Berechnungen nach Gruppe. Das Schreiben von Gruppenberechnungen in eine XDF-Datei wird nicht unterstützt. | 
|[rxCrossTabs](/machine-learning-server/r-reference/revoscaler/rxcrosstabs) <sup>*</sup> |Erstellt formelbasierte Kreuztabellen von Daten | 
|[rxCube](/machine-learning-server/r-reference/revoscaler/rxcube) <sup>*</sup> |Erstellt alternative formelbasierte Kreuztabellen, die für eine effiziente Darstellung der zurückgegebenen Cubeergebnisse konzipiert wurden. Das Schreiben der Ausgabe in eine XDF-Datei wird nicht unterstützt. | 
|[rxMarginals](/machine-learning-server/r-reference/revoscaler/rxmarginals)  |Erstellt marginale Zusammenfassungen von Kreuztabellen | 
|[as.xtabs](/machine-learning-server/r-reference/revoscaler/as.xtabs)  |Konvertiert Kreuztabellenergebnisse in ein xtabs-Objekt | 
|[rxChiSquaredTest](/machine-learning-server/r-reference/revoscaler/rxchisquaredtest)  |Führt einen Chi-Quadrat-Test für ein xtabs-Objekt durch. Wird für kleine Datasets verwendet, und es werden keine Daten segmentiert. | 
|[rxFisherTest](/machine-learning-server/r-reference/revoscaler/rxchisquaredtest)  |Führt einen exakten Test nach Fisher für ein xtab-Objekt durch. Wird für kleine Datasets verwendet, und es werden keine Daten segmentiert. | 
|[rxKendallCor](/machine-learning-server/r-reference/revoscaler/rxchisquaredtest)  |Berechnet den Kendalls Tau-Rangkorrelationskoeffizienten mithilfe eines xtabs-Objekts | 
|[rxPairwiseCrossTab](/machine-learning-server/r-reference/revoscaler/rxpairwisecrosstab)  |Wendet eine Funktion auf paarweise Kombinationen von Zeilen und Spalten eines xtab-Objekts an | 
|[rxRiskRatio](/machine-learning-server/r-reference/revoscaler/rxriskratio)  |Berechnet das relative Risiko für ein paarweises xtab-Objekt | 
|[rxOddsRatio](/machine-learning-server/r-reference/revoscaler/rxriskratio)  |Berechnet das Wahrscheinlichkeitsverhältnis für ein paarweises xtab-Objekt | 

<sup>*</sup> Gibt die am häufigsten verwendeten Funktionen in dieser Kategorie an

<a name="prediction-functions"></a>

## <a name="5-prediction-functions"></a>5: Partitionsfunktionen

| Funktionsname | BESCHREIBUNG |
|---------------|-------------|
|[rxLinMod](/machine-learning-server/r-reference/revoscaler/rxlinmod) <sup>*</sup> |Passt ein lineares Modell auf Daten an | 
|[rxLogit](/machine-learning-server/r-reference/revoscaler/rxlogit) <sup>*</sup> |Passt ein logistisches Regressionsmodell auf Daten an | 
|[rxGlm](/machine-learning-server/r-reference/revoscaler/rxglm) <sup>*</sup> |Passt ein verallgemeinertes lineares Modell auf Daten an | 
|[rxCovCor](/machine-learning-server/r-reference/revoscaler/rxcovcor) <sup>*</sup> |Berechnet die Kovarianz, Korrelation oder die Matrix der Summe der Quadrate (Kreuzprodukt) für unterschiedliche Variablen | 
|[rxDTree](/machine-learning-server/r-reference/revoscaler/rxdtree) <sup>*</sup> |Passt einen Klassifizierungs- oder Regressionsbaum auf Daten an | 
|[rxBTrees](/machine-learning-server/r-reference/revoscaler/rxbtrees) <sup>*</sup> |Passt einen Klassifizierungs- oder Regressionsentscheidungswald mithilfe eines stochastischen Gradient Boosting-Algorithmus auf Daten an | 
|[rxDForest](/machine-learning-server/r-reference/revoscaler/rxdforest) <sup>*</sup> |Passt einen Klassifizierungs- oder Regressionsentscheidungsbaum auf Daten an | 
|[rxPredict](/machine-learning-server/r-reference/revoscaler/rxPredict) <sup>*</sup> |Berechnet Vorhersagen für angepasste Modelle. Die Ausgabe muss eine XDF-Datenquelle sein. | 
|[rxKmeans](/machine-learning-server/r-reference/revoscaler/rxkmeans) <sup>*</sup> |Führt ein K-Means-Clustering durch | 
|[rxNaiveBayes](/machine-learning-server/r-reference/revoscaler/rxnaivebayes) <sup>*</sup> |Führt eine Naive Bayes-Klassifizierung aus | 
|[rxCov](/machine-learning-server/r-reference/revoscaler/rxcovcor) |Berechnet die Kovarianzmatrix für unterschiedliche Variablen | 
|[rxCor](/machine-learning-server/r-reference/revoscaler/rxcovcor)  |Berechnet die Korrelationsmatrix für unterschiedliche Variablen | 
|[rxSSCP](/machine-learning-server/r-reference/revoscaler/rxcovcor)  |Berechnet die Matrix der Summe der Quadrate (Kreuzprodukt) für unterschiedliche Variablen | 
|[rxRoc](/machine-learning-server/r-reference/revoscaler/rxroc)  |Berechnet eine Beobachterkennlinie (Receiver Operating Characteristic, ROC) mithilfe der Ist- und vorhergesagten Werte aus einem binären Klassifizierungssystem | 

<sup>*</sup> Gibt die am häufigsten verwendeten Funktionen in dieser Kategorie an


## <a name="how-to-work-with-revoscaler"></a>Arbeiten mit RevoScaleR

Funktionen in **RevoScaleR** können in R-Code aufgerufen werden, der in gespeicherten Prozeduren gekapselt ist. Die meisten Entwickler erstellen **RevoScaleR**-Lösungen lokal, und migrieren den fertigen R-Code anschließend als Bereitstellungsübung in gespeicherte Prozeduren.

Für eine lokale Ausführung führen Sie in der Regel ein R-Skript über die Befehlszeile oder eine R-Entwicklungsumgebung aus, und geben einen SQL Server-Computekontext an, indem Sie eine der **RevoScaleR**-Funktionen verwenden. Sie können den Remotecomputekontext für den gesamten Code oder für einzelne Funktionen verwenden. Sie können beispielsweise das Modelltraining auf den Server auslagern, um die neuesten Daten zu verwenden und Datenverschiebung zu vermeiden.

Wenn Sie bereit sind, ein R-Skript in einer gespeicherten Prozedur, [sp_execute_external_script](../../relational-databases/system-stored-procedures/sp-execute-external-script-transact-sql.md), zu kapseln, empfiehlt es sich, den Code als eine einzelne Funktion mit klar definierte Eingaben und Ausgaben neu zu schreiben. 

## <a name="see-also"></a>Weitere Informationen

+ [R-Tutorials](../tutorials/r-tutorials.md)
+ [Informationen zur Verwendung von Computekontexten](../tutorials/deepdive-data-science-deep-dive-using-the-revoscaler-packages.md)
+ [R für SQL-Entwickler: Trainieren und Operationalisieren eines Modells](../tutorials/r-taxi-classification-introduction.md)
+ [Microsoft-Produktbeispiele auf GitHub](https://github.com/Microsoft/SQL-Server-R-Services-Samples)
+ [R-Referenz (Microsoft Machine Learning Server)](/machine-learning-server/r-reference/introducing-r-server-r-package-reference)