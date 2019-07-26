---
title: Erstellen von SQL Server Datenobjekten mithilfe von revoscaler rxsqlserverdata
description: 'Tutorial: Exemplarische Vorgehensweise zum Erstellen von Datenobjekten mithilfe der Sprache R auf SQL Server.'
ms.prod: sql
ms.technology: machine-learning
ms.date: 11/26/2018
ms.topic: tutorial
author: dphansen
ms.author: davidph
ms.openlocfilehash: 423a90fe66749a3192c6f03c0efee314b4ceef37
ms.sourcegitcommit: 9062c5e97c4e4af0bbe5be6637cc3872cd1b2320
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/24/2019
ms.locfileid: "68469758"
---
# <a name="create-sql-server-data-objects-using-rxsqlserverdata-sql-server-and-revoscaler-tutorial"></a>Erstellen von SQL Server Datenobjekten mithilfe von rxsqlserverdata (SQL Server-und revoscaler-Tutorial)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

Diese Lektion ist Teil des [revoscaler-Tutorials](deepdive-data-science-deep-dive-using-the-revoscaler-packages.md) zur Verwendung von [revoscaler-Funktionen](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/revoscaler) mit SQL Server.

Lektion 2 ist eine Fortsetzung der Erstellung von Datenbanken: Hinzufügen von Tabellen und Laden von Daten. Wenn ein Datenbankadministrator die Datenbank erstellt und sich in [Lektion 1](deepdive-work-with-sql-server-data-using-r.md)Anmeldungs, können Sie Tabellen mit einer R-IDE wie rstudio oder einem integrierten Tool wie **rgui**hinzufügen.

Stellen Sie von R aus eine Verbindung mit SQL Server her, und verwenden Sie die **revoscaler** -Funktionen, um die folgenden Aufgaben auszuführen:

> [!div class="checklist"]
> * Erstellen von Tabellen für Trainingsdaten und Vorhersagen
> * Tabellen mit Daten aus einer lokalen CSV-Datei laden

Beispiel Daten sind simulierte Kreditkartenbetrugs Daten (das DataSet "ccbetrug"), die in Trainings-und Bewertungs Datasets partitioniert sind. Die Datendatei ist in **revoscaler**enthalten.

Verwenden Sie eine R-IDE oder **rgui** , um diese tachs abzuschließen. Stellen Sie sicher, dass Sie die ausführbaren R-Dateien an dieser Stelle verwenden: C:\programme\microsoft\r Client\R_SERVER\bin\x64 (entweder "rgui. exe", wenn Sie dieses Tool verwenden, oder eine R-IDE, die auf "c:\programme\microsoft\r Client\R_SERVER" zeigt). Eine [R-Client](../r/set-up-a-data-science-client.md) Arbeitsstation mit diesen ausführbaren Dateien wird als Voraussetzung für dieses Tutorial angesehen.

## <a name="create-the-training-data-table"></a>Erstellen der Trainingsdaten Tabelle

1. Speichert die Daten bankverbindungs Zeichenfolge in einer R-Variablen. Im folgenden finden Sie zwei Beispiele für gültige ODBC-Verbindungs Zeichenfolgen für SQL Server: eine mit einer SQL-Anmeldung und eine für die integrierte Windows-Authentifizierung. 

   Achten Sie darauf, den Servernamen, Benutzernamen und das Kennwort nach Bedarf zu ändern.

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
  
    Da die Serverinstanz und der Datenbankname bereits als Teil der Verbindungs Zeichenfolge angegeben sind, wird beim Kombinieren der beiden Variablen der *voll qualifizierte* Name der neuen Tabelle *instance. Database. Schema. ccbetrüsmall*.
  
3.  Geben Sie optional *rowsperread* an, um zu steuern, wie viele Daten Zeilen in jedem Batch gelesen werden.
  
    ```R
    sqlRowsPerRead = 5000
    ```
  
    Obwohl dieser Parameter optional ist, kann er durch Festlegen des Parameters effizientere Berechnungen verursachen. Die meisten der erweiterten analytischen Funktionen in **revoscaler** und **microsoftml** verarbeiten Daten in Blöcken. Der *rowsperread* -Parameter bestimmt die Anzahl der Zeilen in jedem Segment.
  
    Möglicherweise müssen Sie mit dieser Einstellung experimentieren, um das richtige Gleichgewicht zu finden. Wenn der Wert zu groß ist, kann der Datenzugriff langsam sein, wenn nicht genügend Arbeitsspeicher zum Verarbeiten von Daten in Blöcken dieser Größe verfügbar ist. Umgekehrt kann es bei manchen Systemen, wenn der Wert von *rowsperread* zu klein ist, auch zu einer Verlangsamung der Leistung kommen.
  
    Verwenden Sie als Anfangswert die standardmäßige Batch Prozess Größe, die von der Datenbank-Engine-Instanz definiert wird, um die Anzahl der Zeilen in jedem Segment (5.000 Zeilen) zu steuern. Speichern Sie diesen Wert in der Variablen *sqlrowsperread*.
  
4.  Definieren Sie eine Variable für das neue Datenquellen Objekt, und übergeben Sie die zuvor definierten Argumente an den **rxsqlserverdata** -Konstruktor. Beachten Sie, dass dadurch nur das neue Datenquellenobjekt erstellt wird, es jedoch nicht aufgefüllt wird. Das Laden von Daten ist ein separater Schritt.
  
    ```R
    sqlFraudDS <- RxSqlServerData(connectionString = sqlConnString,
       table = sqlFraudTable,
       rowsPerRead = sqlRowsPerRead)
    ```

## <a name="create-the-scoring-data-table"></a>Erstellen der Bewertungsdaten Tabelle

Erstellen Sie mithilfe der gleichen Schritte die Tabelle, in der die Bewertungsdaten mit demselben Prozess enthalten sind.

1. Erstellen Sie eine neue R-Variable, *sqlScoreTable*, um den Namen der Tabelle für die Bewertung zu speichern.
  
    ```R
    sqlScoreTable <- "ccFraudScoreSmall"
    ```
  
2. Geben Sie die Variable als Argument an die Funktion **RxSqlServerData** , um ein zweites Datenquellenobjekt, *sqlScoreDS*, zu definieren.
  
    ```R
    sqlScoreDS <- RxSqlServerData(connectionString = sqlConnString,
       table = sqlScoreTable, rowsPerRead = sqlRowsPerRead)
    ```

Da Sie bereits die Verbindungs Zeichenfolge und andere Parameter als Variablen im R-Arbeitsbereich definiert haben, können Sie Sie für neue Datenquellen wieder verwenden, die unterschiedliche Tabellen, Sichten oder Abfragen darstellen.

> [!NOTE]
> Die-Funktion verwendet unterschiedliche Argumente zum Definieren einer Datenquelle basierend auf einer ganzen Tabelle als für eine Datenquelle, die auf einer Abfrage basiert. Dies liegt daran, dass die SQL Server Datenbank-Engine die Abfragen anders vorbereiten muss. Später in diesem Tutorial erfahren Sie, wie Sie ein Datenquellen Objekt auf der Grundlage einer SQL-Abfrage erstellen.

## <a name="load-data-into-sql-tables-using-r"></a>Laden von Daten in SQL-Tabellen mithilfe von R

Sie haben die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Tabellen nun erstellt und können Daten in die Tabellen laden mithilfe der entsprechenden **Rx** -Funktion.

Das **revoscaler** -Paket enthält Funktionen, die für Datenquellen Typen spezifisch sind. Verwenden Sie für Textdaten [rxtextdata](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxtextdata) , um das Datenquellen Objekt zu generieren. Es gibt weitere Funktionen zum Erstellen von Datenquellenobjekten von Hadoop-Daten, ODBC-Daten, usw.

> [!NOTE]
> Für diesen Abschnitt müssen Sie über die Berechtigung **DDL ausführen** für die Datenbank verfügen.

### <a name="load-data-into-the-training-table"></a>Laden von Daten in die Trainings Tabelle

1. Erstellen Sie eine R-Variable, *ccbetrücsv*, und weisen Sie der Variablen den Dateipfad für die CSV-Datei mit den Beispiel Daten zu. Dieses DataSet wird in **revoscaler**bereitgestellt. "Sampledatadir" ist ein Schlüsselwort für die Funktion **rxgetoption** .
  
    ```R
    ccFraudCsv <- file.path(rxGetOption("sampleDataDir"), "ccFraudSmall.csv")
    ```
  
    Beachten Sie den Aufrufen von **rxgetoption**. Dies ist die Get-Methode, die [rxoptions](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxoptions) in **revoscaler**zugeordnet ist. Mit diesem Hilfsprogramm können Sie Optionen für lokale und remotecomputekontexte festlegen und auflisten, z. b. das standardmäßige freigegebene Verzeichnis oder die Anzahl der Prozessoren (Kerne), die in Berechnungen verwendet werden sollen.
    
    Dieser spezielle-Befehl ruft die Beispiele aus der richtigen Bibliothek ab, unabhängig davon, wo Sie den Code ausführen. Versuchen Sie z.B. die Funktion auf SQL Server und auf Ihrem Entwicklungscomputer auszuführen, und beachten Sie, wie sich die Pfade unterscheiden.
  
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
  
3. An diesem Punkt können Sie einen Moment anhalten und Ihre Datenbank in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]anzeigen. Aktualisieren Sie die Liste der Tabellen in der Datenbank.
  
    Sie sehen, dass zwar die R-Datenobjekte im lokalen Arbeitsbereich erstellt wurden, die Tabellen jedoch nicht in der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Datenbank erstellt wurden. Außerdem wurden keine Daten aus der Textdatei in die R-Variable geladen.
  
4. Fügen Sie die Daten ein, indem Sie die [rxdatastep](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxdatastep) -Funktion der Funktion aufrufen.
  
    ```R
    rxDataStep(inData = inTextData, outFile = sqlFraudDS, overwrite = TRUE)
    ```
    
    Wenn nach einer kurzen Pause keine Probleme mit der Verbindungszeichenfolge auftreten, sollten Sie Ergebnisse wie diese sehen:
  
    *Geschriebene Zeilen gesamt: 10000, Gesamtzeit:*  0,466*gelesene Zeilen: 10000, verarbeitete Zeilen gesamt: 10000, gesamte Segment Zeit: 0,577 Sekunden*
  
5. Aktualisieren Sie die Liste der Tabellen. Um sicherzustellen, dass jede Variable über die korrekten Datentypen verfügt und erfolgreich importiert wurde, können Sie auch mit der rechten [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] Maustaste auf die Tabelle in klicken und die Option erste **1000 Zeilen auswählen**auswählen.

### <a name="load-data-into-the-scoring-table"></a>Laden von Daten in die Bewertungstabelle

1. Wiederholen Sie die Schritte zum Laden des Datasets, das für die Bewertung in der Datenbank verwendet wurde.
  
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
  
    - Wenn die Tabelle bereits vorhanden ist und Sie nicht die Option zum über *Schreiben* verwenden, werden die Ergebnisse ohne Abschneiden eingefügt.
  
Wenn die Verbindung erfolgreich hergestellt wurde, sollte eine Nachricht angezeigt werden, die den Abschluss und die Zeit anzeigt, die zum Schreiben von Dateien in die Tabelle benötigt wurde:

*Geschriebene Zeilen gesamt: 10000, Gesamtzeit: 0,384*gelesene*Zeilen:
 10000, verarbeitete Zeilen gesamt: 10000, gesamte Segment Zeit: 0,456 Sekunden*

## <a name="more-about-rxdatastep"></a>Weitere Informationen zu rxDataStep

[rxdatastep](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxdatastep) ist eine leistungsstarke Funktion, die mehrere Transformationen für einen R-Datenrahmen durchführen kann. Sie können auch rxdatastep verwenden, um Daten in die für das Ziel erforderliche Darstellung zu konvertieren: in diesem [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Fall.

Optional können Sie Transformationen für die Daten angeben, indem Sie R-Funktionen in den Argumenten für **rxdatastep**verwenden. Beispiele für diese Vorgänge werden später in diesem Tutorial bereitgestellt.

## <a name="next-steps"></a>Nächste Schritte

> [!div class="nextstepaction"]
> [Abfragen und Ändern der SQL Server-Daten](../../advanced-analytics/tutorials/deepdive-query-and-modify-the-sql-server-data.md)