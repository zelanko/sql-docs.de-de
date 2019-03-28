---
title: Erstellen von SQL Server-Datenobjekten mithilfe von RevoScaleR RxSqlServerData – SQL Server-Machine Learning
description: Exemplarische Vorgehensweise im Lernprogramm zum Erstellen von Datenobjekten, die Verwendung der Sprache R auf SQL Server.
ms.prod: sql
ms.technology: machine-learning
ms.date: 11/26/2018
ms.topic: tutorial
author: dphansen
ms.author: davidph
manager: cgronlun
ms.openlocfilehash: 45643dbcdc2876fe0794ddb731abe6334537169c
ms.sourcegitcommit: 2827d19393c8060eafac18db3155a9bd230df423
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/27/2019
ms.locfileid: "58510357"
---
# <a name="create-sql-server-data-objects-using-rxsqlserverdata-sql-server-and-revoscaler-tutorial"></a>Erstellen von SQL Server-Datenobjekten mithilfe von RxSqlServerData (SQL Server und die RevoScaleR-Lernprogramm)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

Diese Lektion ist Teil der [RevoScaleR Tutorial](deepdive-data-science-deep-dive-using-the-revoscaler-packages.md) zur Verwendung von [RevoScaleR-Funktionen](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/revoscaler) mit SQL Server.

Lektion 2 ist eine Fortsetzung der Datenbankerstellung: Hinzufügen von Tabellen und Laden von Daten. Wenn ein Datenbankadministrator die Datenbank und die Anmeldung erstellt [Lektion eine](deepdive-work-with-sql-server-data-using-r.md), können Sie Tabellen mit einer R-IDE wie RStudio oder Hinzufügen eines integrierten Tools wie **Rgui**.

Von R mit SQL Server verbinden, und verwenden **RevoScaleR** Funktionen, um die folgenden Aufgaben ausführen:

> [!div class="checklist"]
> * Erstellen von Tabellen für Training und Vorhersage
> * Laden von Tabellen mit Daten aus einer lokalen CSV-Datei

Beispieldaten sind simulierte Daten über Kreditkartenbetrug (CcFraud-Dataset) in trainieren und Bewerten von Datasets aufgeteilt. Die Datei befindet sich im **RevoScaleR**.

Verwenden Sie eine R-IDE oder **Rgui** diese doppelt ausführen. Achten Sie darauf, dass die ausführbaren R-Dateien finden Sie unter diesem Speicherort verwendet: C:\Programme\Microsoft Files\Microsoft\R Client\R_SERVER\bin\x64 (entweder Rgui.exe bei Verwendung dieses Tools oder einer R-IDE auf c:\Programme\Microsoft Files\Microsoft\R Client\R_SERVER verweist). Mit einer [R-Clientarbeitsstation](../r/set-up-a-data-science-client.md) ausführbare Dateien gilt diese Voraussetzung für dieses Tutorial.

## <a name="create-the-training-data-table"></a>Schulung-Datentabelle erstellen

1. Store die Datenbankverbindungszeichenfolge in einer R-Variablen an. Nachfolgend finden Sie zwei Beispiele gültiger ODBC-Verbindungszeichenfolgen für SQL Server: eine, die mit einer SQL-Anmeldung und eine für die integrierte Windows-Authentifizierung. 

   Achten Sie darauf, dass der Servername, Benutzername und das Kennwort nach Bedarf ändern.

    **SQL-Anmeldename**
    ```R
    sqlConnString <- "Driver=SQL Server;Server=<server-name>; Database=RevoDeepDive;Uid=<user_name>;Pwd=<password>"
    ```

    **Windows-Authentifizierung**
    ```R
    sqlConnString <- "Driver=SQL Server;Server=<server-name>;Database=RevoDeepDive;Trusted_Connection=True"
    ```

2. Geben Sie den Namen der Tabelle an, die Sie erstellen möchten, und speichern Sie ihn in einer R-Variablen.
  
    ```R
    sqlFraudTable <- "ccFraudSmall"
    ```
  
    Da der Server-Instanz und Datenbankname bereits als Teil der Verbindungszeichenfolge beim Kombinieren der zwei Variablen angegeben werden, die *vollqualifizierte* wird der Name der neuen Tabelle  *instance.database.schema.ccFraudSmall*.
  
3.  Geben Sie optional *RowsPerRead* steuern, wie viele Datenzeilen in jeden Batch eingelesen werden.
  
    ```R
    sqlRowsPerRead = 5000
    ```
  
    Obwohl dieser Parameter optional ist, kann die Festlegung zu effizienter Berechnungen führen. Die meisten analytischen Funktionen in **RevoScaleR** und **MicrosoftML** verarbeiten Daten in Segmenten. Die *RowsPerRead* Parameter bestimmt die Anzahl der Zeilen in jedem Segment.
  
    Sie müssen möglicherweise das Experimentieren mit diese Einstellung, um das richtige Gleichgewicht finden. Wenn der Wert zu groß ist, ist Datenzugriff möglicherweise langsam, wenn nicht genügend Arbeitsspeicher zum Verarbeiten von Daten in Blöcken von dieser Größe vorhanden ist. Im Gegensatz dazu auf einigen Systemen Wenn der Wert des *RowsPerRead* ist zu klein, Leistung kann auch verlangsamen.
  
    Verwenden Sie die Standard-batchprozessgröße, definiert, die von der Datenbank-Engine-Instanz als Anfangswert zum Steuern der Anzahl der Zeilen in jedem Segment (5.000 Zeilen). Speichern Sie diesen Wert in der Variablen *SqlRowsPerRead*.
  
4.  Definieren Sie eine Variable für das neue Datenquellenobjekt, und übergeben Sie die zuvor definierten Argumente an die **RxSqlServerData** Konstruktor. Beachten Sie, dass dadurch nur das neue Datenquellenobjekt erstellt wird, es jedoch nicht aufgefüllt wird. Laden von Daten ist ein separater Schritt.
  
    ```R
    sqlFraudDS <- RxSqlServerData(connectionString = sqlConnString,
       table = sqlFraudTable,
       rowsPerRead = sqlRowsPerRead)
    ```

## <a name="create-the-scoring-data-table"></a>Bewertungs-Datentabelle erstellen

Verwenden die gleichen Schritte aus, erstellen Sie in der Tabelle, die die Bewerten von Daten mithilfe des gleichen Prozesses enthält.

1. Erstellen Sie eine neue R-Variable, *sqlScoreTable*, um den Namen der Tabelle für die Bewertung zu speichern.
  
    ```R
    sqlScoreTable <- "ccFraudScoreSmall"
    ```
  
2. Geben Sie die Variable als Argument an die Funktion **RxSqlServerData** , um ein zweites Datenquellenobjekt, *sqlScoreDS*, zu definieren.
  
    ```R
    sqlScoreDS <- RxSqlServerData(connectionString = sqlConnString,
       table = sqlScoreTable, rowsPerRead = sqlRowsPerRead)
    ```

Da Sie bereits die Verbindungszeichenfolge und andere Parameter als Variablen im R-Arbeitsbereich definiert haben, können Sie es für neue Datenquellen darstellt, unterschiedliche Tabellen, Sichten oder Abfragen wiederverwenden.

> [!NOTE]
> Die Funktion verwendet unterschiedliche Argumente für das Definieren einer Datenquelle basierend auf einer ganzen Tabelle als für eine Datenquelle basierend auf einer Abfrage. Dies ist, da die SQL Server-Datenbank-Engine Abfragen anders vorbereiten muss. Weiter unten in diesem Tutorial erfahren Sie, wie Sie ein Datenquellenobjekt basierend auf einer SQL-Abfrage zu erstellen.

## <a name="load-data-into-sql-tables-using-r"></a>Laden von Daten in SQL-Tabellen mithilfe von R

Sie haben die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Tabellen nun erstellt und können Daten in die Tabellen laden mithilfe der entsprechenden **Rx** -Funktion.

Die **RevoScaleR** -Paket enthält Funktionen, die spezifisch für die Typen von Datenquellen. Verwenden Sie für Textdaten, [RxTextData](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxtextdata) das Datenquellenobjekt zu generieren. Es gibt weitere Funktionen zum Erstellen von Datenquellenobjekten von Hadoop-Daten, ODBC-Daten, usw.

> [!NOTE]
> In diesem Abschnitt müssen Sie **' DDL ausführen '** Berechtigungen für die Datenbank.

### <a name="load-data-into-the-training-table"></a>Daten in die schulungstabelle laden

1. Erstellen Sie eine R-Variable, *CcFraudCsv*, und weisen Sie der Variablen den Dateipfad für die CSV-Datei, die die Beispieldaten enthält. Dieses Dataset finden Sie im **RevoScaleR**. Die "SampleDataDir" ist ein Schlüsselwort für die **RxGetOption** Funktion.
  
    ```R
    ccFraudCsv <- file.path(rxGetOption("sampleDataDir"), "ccFraudSmall.csv")
    ```
  
    Beachten Sie, dass den Aufruf von **RxGetOption**, die die GET-Methode zugeordnet ist [RxOptions](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxoptions) in **RevoScaleR**. Mit diesem Dienstprogramm können festgelegt und sind Optionen aufgeführt, im Zusammenhang mit der lokalen und remote computekontexte, z. B. das freigegebene Standardverzeichnis, oder die Anzahl der Prozessoren (Kerne) in Berechnungen verwenden.
    
    Dieser bestimmte Aufruf ruft die Beispiele aus der richtigen Bibliothek, unabhängig davon, wo Sie Ihr Code ausgeführt werden. Versuchen Sie z.B. die Funktion auf SQL Server und auf Ihrem Entwicklungscomputer auszuführen, und beachten Sie, wie sich die Pfade unterscheiden.
  
2. Definieren Sie eine Variable, um die neuen Daten zu speichern, und verwenden Sie die Funktion **RxTextData** zur Angabe der Text-Datenquelle.
  
    ```R
    inTextData <- RxTextData(file = ccFraudCsv,      colClasses = c(
        "custID" = "integer", "gender" = "integer", "state" = "integer",
        "cardholder" = "integer", "balance" = "integer",
        "numTrans" = "integer",
        "numIntlTrans" = "integer", "creditLine" = "integer",
        "fraudRisk" = "integer"))
    ```
  
    Das Argument *colClasses* ist wichtig. Sie verwenden es zur Angabe des Datentyps jeder Spalte von Daten, die aus der Textdatei geladen wird. In diesem Beispiel werden alle Spalten als Text behandelt, mit Ausnahme der benannten Spalten, die als ganze Zahlen verarbeitet werden.
  
3. An diesem Punkt sollten Sie zum Anhalten einen Moment Zeit, und die Datenbank in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]. Aktualisieren Sie die Liste der Tabellen in der Datenbank.
  
    Sie sehen, dass, obwohl die R-Datenobjekte im lokalen Arbeitsbereich erstellt wurden, die Tabellen nicht in erstellt wurden die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Datenbank. Darüber hinaus wurde keine Daten in der R-Variable aus der Textdatei geladen.
  
4. Fügen Sie die Daten durch Aufrufen der Funktion [RxDataStep](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxdatastep) Funktion.
  
    ```R
    rxDataStep(inData = inTextData, outFile = sqlFraudDS, overwrite = TRUE)
    ```
    
    Wenn nach einer kurzen Pause keine Probleme mit der Verbindungszeichenfolge auftreten, sollten Sie Ergebnisse wie diese sehen:
  
    *Geschriebene Zeilen gesamt: 10000, Gesamtzeit: 0.466* *Gelesene Zeilen: 10000, Ergebniszeilen verarbeitet: 10000, total Chunk Time: 0.577 Sekunden*
  
5. Aktualisieren Sie die Liste der Tabellen ein. Um sicherzustellen, dass jede Variable über die korrekten Datentypen verfügt und erfolgreich importiert wurde, Sie können auch mit der rechten Maustaste in der Tabelle im [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] , und wählen Sie **oberste 1000 Zeilen auswählen**.

### <a name="load-data-into-the-scoring-table"></a>Daten in die Bewertungstabelle laden

1. Wiederholen Sie die Schritte zum Laden des Datasets für die Bewertung in der Datenbank aus.
  
    Starten Sie über den Pfad zur Quelldatei.
  
    ```R
    ccScoreCsv <- file.path(rxGetOption("sampleDataDir"), "ccFraudScoreSmall.csv")
    ```
  
2. Verwenden Sie die Funktion **RxTextData** , um die Daten abzurufen, und speichern Sie sie in der Variablen *inTextData*.
  
    ```R
    inTextData <- RxTextData(file = ccScoreCsv,      colClasses = c(
        "custID" = "integer", "gender" = "integer", "state" = "integer",
        "cardholder" = "integer", "balance" = "integer",
        "numTrans" = "integer",
        "numIntlTrans" = "integer", "creditLine" = "integer"))
    ```
  
3.  Rufen Sie die Funktion **rxDataStep** auf, um die aktuelle Tabelle mit dem neuen Schema und Daten zu überschreiben.
  
    ```R
    rxDataStep(inData = inTextData, sqlScoreDS, overwrite = TRUE)
    ```
  
    - Das *inData* -Argument definiert die zu verwendende Datenquelle.
  
    - Das *outFile* -Argument gibt die Tabelle in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] an, in der Sie die Daten speichern möchten.
  
    - Wenn die Tabelle bereits vorhanden ist und Sie nicht die *überschreiben* auswählen, werden Ergebnisse ungekürzt eingefügt.
  
Wenn die Verbindung erfolgreich hergestellt wurde, sollte eine Nachricht angezeigt werden, die den Abschluss und die Zeit anzeigt, die zum Schreiben von Dateien in die Tabelle benötigt wurde:

*Geschriebene Zeilen gesamt: 10000, Gesamtzeit: 0.384*
*Gelesene Zeilen: 10000, Ergebniszeilen verarbeitet: 10000, total Chunk Time: 0.456 Sekunden*

## <a name="more-about-rxdatastep"></a>Weitere Informationen zu rxDataStep

[RxDataStep](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxdatastep) ist eine leistungsstarke Funktion, die mehrere Transformationen auf einen R-Datenrahmen durchführen kann. Sie können auch RxDataStep verwenden, um Daten in die erforderliche Ziel-Darstellung zu konvertieren: in diesem Fall [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].

Sie können optional Transformationen auf die Daten angeben, unter Verwendung von R-Funktionen in den Argumenten von **RxDataStep**. Beispiele für diese Vorgänge werden weiter unten in diesem Tutorial bereitgestellt.

## <a name="next-steps"></a>Nächste Schritte

> [!div class="nextstepaction"]
> [Abfragen und Ändern der SQL Server-Daten](../../advanced-analytics/tutorials/deepdive-query-and-modify-the-sql-server-data.md)