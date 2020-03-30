---
title: Erstellen von RxSqlServerData-Objekten
description: 'Tutorial 2 zu RevoScaleR: Erstellen von Datenobjekten mithilfe der R-Programmiersprache unter SQL Server'
ms.prod: sql
ms.technology: machine-learning
ms.date: 11/26/2018
ms.topic: tutorial
author: dphansen
ms.author: davidph
ms.custom: seo-lt-2019
monikerRange: '>=sql-server-2016||>=sql-server-linux-ver15||=sqlallproducts-allversions'
ms.openlocfilehash: 7869fc3fc67cb24542223c2300cd7b6ebcf1eb41
ms.sourcegitcommit: ff82f3260ff79ed860a7a58f54ff7f0594851e6b
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/29/2020
ms.locfileid: "76922571"
---
# <a name="create-sql-server-data-objects-using-rxsqlserverdata-sql-server-and-revoscaler-tutorial"></a>Erstellen von SQL Server-Datenobjekten mithilfe von RxSqlServerData (Tutorial zu SQL Server und RevoScaleR)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

Dies ist das zweite Tutorial der [Tutorialreihe zu RevoScaleR](deepdive-data-science-deep-dive-using-the-revoscaler-packages.md) zur Verwendung von [RevoScaleR-Funktionen](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/revoscaler) mit SQL Server.

Dieses Tutorial ist eine Fortsetzung der Datenbankerstellung „Hinzufügen von Tabellen und Laden von Daten“. Wenn ein DBA die Datenbank erstellt und sich bei [Tutorial 2](deepdive-work-with-sql-server-data-using-r.md) angemeldet hat, können Sie Tabellen mit einer R-IDE wie RStudio oder einem integrierten Tool wie **Rgui** hinzufügen.

Stellen Sie von R aus eine Verbindung mit SQL Server her, und führen Sie mit **RevoScaleR**-Funktionen die folgenden Aufgaben aus:

> [!div class="checklist"]
> * Erstellen von Tabellen für Trainingsdaten und Vorhersagen
> * Laden von Tabellen mit Daten aus einer lokalen CSV-Datei

Bei den Beispieldaten handelt es sich um simulierte Kreditkartenbetrugsdaten (das ccFraud-Dataset), die in Trainings- und Bewertungsdatasets unterteilt sind. Die Datendatei ist in **RevoScaleR** enthalten.

Verwenden Sie eine R-IDE oder **Rgui**, um diese Task abzuschließen. Stellen Sie sicher, dass Sie die ausführbaren R-Dateien aus diesem Verzeichnis verwenden: C:\Programme\Microsoft\R Client\R_SERVER\bin\x64 (entweder Rgui.exe, wenn Sie dieses Tool verwenden, oder eine R-IDE die auf C:\Programme\Microsoft\R Client\R_SERVER verweist). In diesem Tutorial wird vorausgesetzt, dass Sie eine [R-Clientarbeitsstation](../r/set-up-a-data-science-client.md) mit diesen ausführbaren Dateien verwenden.

## <a name="create-the-training-data-table"></a>Erstellen der Tabelle mit den Trainingsdaten

1. Speichern Sie die Datenbank-Verbindungszeichenfolge in einer R-Variablen. Im Folgenden sehen Sie zwei Beispiele gültiger ODBC-Verbindungszeichenfolgen für SQL Server: eine, die eine SQL-Anmeldung verwendet und eine für die integrierte Windows-Authentifizierung. 

   Achten Sie darauf, den Servernamen, den Benutzernamen und das Kennwort nach Bedarf zu ändern.

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
  
    Da die Serverinstanz- und Datenbanknamen bereits als Teil der Verbindungszeichenfolge beim Kombinieren der zwei Variablen angegeben werden, lautet der *vollqualifizierte* Name der neuen Tabelle *instance.database.schema.ccFraudSmall*.
  
3.  Geben Sie wahlweise *rowsPerRead* an, um zu steuern, wie viele Datenzeilen in jeden Batch eingelesen werden.
  
    ```R
    sqlRowsPerRead = 5000
    ```
  
    Obwohl dieser Parameter optional ist, lassen sich dadurch effizientere Berechnungen erzielen. Die meisten der erweiterten Analysefunktionen in **RevoScaleR** und **MicrosoftML** verarbeiten Daten in Blöcken. Der *rowsPerRead*-Parameter bestimmt die Anzahl der Zeilen in jedem Block.
  
    Möglicherweise müssen Sie mit dieser Einstellung experimentieren, um das richtige Gleichgewicht zu finden. Bei einem zu großen Wert kann der Datenzugriff langsam sein, wenn nicht genügend Speicherplatz vorhanden ist, um Daten in Blöcken dieser Größe zu verarbeiten. Umgekehrt verhält es sich, wenn der Wert *rowsPerRead* zu niedrig ist, denn dies kann in einigen Systemen die Leistung verringern.
  
    Verwenden Sie als Anfangswert die von der Datenbank-Engine-Instanz definierte Standardgröße für die Batchverarbeitung, um die Anzahl der Zeilen in jedem Block (5.000 Zeilen) zu steuern. Speichern Sie den Wert in der Variablen *sqlRowsPerRead*.
  
4.  Definieren Sie eine Variable für das neue Datenquellenobjekt, und übergeben Sie die zuvor definierten Argumente an den **RxSqlServerData**-Konstruktor. Beachten Sie, dass dadurch nur das neue Datenquellenobjekt erstellt wird, es jedoch nicht aufgefüllt wird. Das Laden der Daten erfolgt in einem separaten Schritt.
  
    ```R
    sqlFraudDS <- RxSqlServerData(connectionString = sqlConnString,
       table = sqlFraudTable,
       rowsPerRead = sqlRowsPerRead)
    ```

## <a name="create-the-scoring-data-table"></a>Erstellen der Tabelle mit den Bewertungsdaten

Gehen Sie genauso vor, um die Tabelle zu erstellen, in der die Bewertungsdaten erhalten sind.

1. Erstellen Sie eine neue R-Variable, *sqlScoreTable*, um den Namen der Tabelle für die Bewertung zu speichern.
  
    ```R
    sqlScoreTable <- "ccFraudScoreSmall"
    ```
  
2. Geben Sie die Variable als Argument an die Funktion **RxSqlServerData** , um ein zweites Datenquellenobjekt, *sqlScoreDS*, zu definieren.
  
    ```R
    sqlScoreDS <- RxSqlServerData(connectionString = sqlConnString,
       table = sqlScoreTable, rowsPerRead = sqlRowsPerRead)
    ```

Da Sie bereits die Verbindungszeichenfolge und andere Parameter als Variablen im R-Arbeitsbereich definiert haben, können Sie sie für neue Datenquellen wiederverwenden, die verschiedene Tabellen, Ansichten oder Abfragen darstellen.

> [!NOTE]
> In der Funktion werden für die Definition einer Datenquelle basierend auf einer ganzen Tabelle andere Argumente verwendet als für eine abfragebasierte Datenquelle. Dies liegt daran, dass die Abfragen von der SQL Server-Datenbank-Engine anders vorbereitet werden müssen. Später in diesem Tutorial erfahren Sie, wie Sie ein Datenquellenobjekt auf Grundlage einer SQL-Abfrage erstellen.

## <a name="load-data-into-sql-tables-using-r"></a>Laden von Daten in SQL-Tabellen mithilfe von R

Sie haben die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Tabellen nun erstellt und können Daten in die Tabellen laden mithilfe der entsprechenden **Rx** -Funktion.

Das **RevoScaleR**-Paket enthält Funktionen, die spezifisch für Datenquellentypen sind. Verwenden Sie für Textdaten [RxTextData](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxtextdata), um das Datenquellenobjekt zu generieren. Es gibt weitere Funktionen zum Erstellen von Datenquellenobjekten von Hadoop-Daten, ODBC-Daten, usw.

> [!NOTE]
> Für diesen Abschnitt müssen Sie über Berechtigungen vom Typ **DDL ausführen** für die Datenbank verfügen.

### <a name="load-data-into-the-training-table"></a>Laden von Daten in die Trainingstabelle

1. Erstellen Sie eine R-Variable, *ccFraudCsv*, und weisen Sie der Variable den Dateipfad für die CSV-Datei zu, die die Beispieldatei enthält. Dieses Dataset wird in **RevoScaleR** bereitgestellt. Bei „sampleDataDir“ handelt es sich um ein Schlüsselwort der **rxGetOption**-Funktion.
  
    ```R
    ccFraudCsv <- file.path(rxGetOption("sampleDataDir"), "ccFraudSmall.csv")
    ```
  
    Achten Sie auf den Aufruf von **rxGetOption**, der die GET-Methode ist, die mit [rxOptions](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxoptions) in **RevoScaleR** verknüpft ist. Verwenden Sie dieses Hilfsprogramm zum Festlegen und Auflisten von Optionen mit Bezug auf lokale und Remotecomputekontexte, z. B. das freigegebene Standardverzeichnis oder die verwendete Anzahl der Prozessoren (Kerne) in Berechnungen.
    
    Dieser spezielle Aufruf ruft die Beispiele aus der richtigen Bibliothek ab, unabhängig vom Ausführungsort Ihres Codes. Versuchen Sie z.B. die Funktion auf SQL Server und auf Ihrem Entwicklungscomputer auszuführen, und beachten Sie, wie sich die Pfade unterscheiden.
  
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
  
3. Sehen Sie sich jetzt einmal die Datenbank in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] an. Aktualisieren Sie die Liste der Tabellen in der Datenbank.
  
    Sie sehen, dass zwar die R-Datenobjekte im lokalen Arbeitsbereich erstellt wurden, die Tabellen aber in der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Datenbank noch nicht erstellt wurden. Außerdem wurden keine Daten aus der Textdatei in die R-Variable geladen.
  
4. Geben Sie die Daten ein, indem Sie die Funktion [rxDataStep](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxdatastep) aufrufen.
  
    ```R
    rxDataStep(inData = inTextData, outFile = sqlFraudDS, overwrite = TRUE)
    ```
    
    Wenn nach einer kurzen Pause keine Probleme mit der Verbindungszeichenfolge auftreten, sollten Sie Ergebnisse wie diese sehen:
  
    *Geschriebene Zeilen gesamt: 10.000, Gesamtzeit: 0,466* *Gelesene Zeilen: 10.000, Gesamte verarbeitete Zeilen: 10.000, Gesamte Blockzeit: 0,577 Sekunden*
  
5. Aktualisieren Sie die Liste der Tabellen. Um sicherzustellen, dass jede Variable über die korrekten Datentypen verfügt und erfolgreich importiert wurde, können Sie auch mit der rechten Maustaste in die Tabelle in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] klicken und die Option **Oberste 1000 Zeilen auswählen** auswählen.

### <a name="load-data-into-the-scoring-table"></a>Laden von Daten in die Bewertungstabelle

1. Wiederholen Sie die Schritte zum Laden des Datasets für die Bewertung in die Datenbank.
  
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
  
    - Wenn die Tabelle bereits vorhanden ist und Sie nicht die Option *overwrite* verwenden, werden Ergebnisse ungekürzt eingefügt.
  
Wenn die Verbindung erfolgreich hergestellt wurde, sollte eine Nachricht angezeigt werden, die den Abschluss und die Zeit anzeigt, die zum Schreiben von Dateien in die Tabelle benötigt wurde:

*Geschriebene Zeilen gesamt: 10.000, Gesamtzeit: 0,384*
*Gelesene Zeilen: 10.000, Gesamte verarbeitete Zeilen: 10.000, Gesamte Blockzeit: 0,456 Sekunden*

## <a name="more-about-rxdatastep"></a>Weitere Informationen zu rxDataStep

[rxDataStep](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxdatastep) ist eine leistungsstarke Funktion, die mehrere Transformationen an einem R-Datenrahmen durchführen kann. Darüber hinaus können Sie mit „rxDataStep“ Daten in die vom Ziel gewünschte Darstellung konvertieren: in diesem Fall [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].

Optional haben Sie die Möglichkeit, Transformationen für die Daten anzugeben, indem Sie R-Funktionen in den Argumenten zu **rxDataStep** verwenden. Beispiele für diese Vorgänge werden später in diesem Tutorial erläutert.

## <a name="next-steps"></a>Nächste Schritte

> [!div class="nextstepaction"]
> [Abfragen und Ändern der SQL Server-Daten](../../advanced-analytics/tutorials/deepdive-query-and-modify-the-sql-server-data.md)