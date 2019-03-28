---
title: 'Gewusst wie: Erstellen einer gespeicherten Prozedur mithilfe von Sqlrutils - SQL Server Machine Learning Services'
description: Verwenden Sie das Sqlrutils R-Paket in SQL Server-Sprache R-Code in eine einzelne Funktion gebündelt werden, die als Argument an eine gespeicherte Prozedur übergeben werden können.
ms.prod: sql
ms.technology: machine-learning
ms.date: 04/15/2018
ms.topic: conceptual
author: dphansen
ms.author: davidph
manager: cgronlun
ms.openlocfilehash: 014fb8344a0b2cf93dc7f375fffc717663f53a46
ms.sourcegitcommit: 2827d19393c8060eafac18db3155a9bd230df423
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/27/2019
ms.locfileid: "58509887"
---
# <a name="create-a-stored-pprocedure-using-sqlrutils"></a>Erstellen Sie eine gespeicherte pProcedure mithilfe von sqlrutils
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

Dieser Artikel beschreibt die Schritte zum Konvertieren von R-Code als gespeicherte T-SQL-Prozedur ausgeführt wird. Zum Erzielen bestmöglicher Ergebnisse kann es erforderlich sein, dass Ihr Code ein wenig geändert wird, damit sichergestellt ist, dass alle Eingaben parametrisiert werden können.

## <a name="bkmk_rewrite"></a>Schritt 1: Schreiben Sie R-Skript

Schreiben Sie die besten Ergebnisse erzielen Sie Ihren R-Code, um als einzelne Funktion gekapselt werden.

Alle Variablen, die von der Funktion verwendeten sollte innerhalb der Funktion definiert werden, oder als Eingabeparameter definiert werden soll. Finden Sie unter den [Beispielcode](#samples) in diesem Artikel.

Darüber hinaus, da die Eingabeparameter für die R-Funktion werden die Eingabeparameter des SQL-Prozedur, müssen Sie sicherstellen, dass Ihre Eingaben und Ausgaben an den folgenden typanforderungen entsprechen:

### <a name="inputs"></a>Eingaben

In den Eingabeparametern darf es höchstens einen Datenrahmen geben.

Der Objekte in dem Datenrahmen müssen, so wie alle anderen Eingabeparameter der Funktion, die folgenden R-Datentypen haben:
- POSIXct
- NUMERIC
- character
- integer
- Logisch
- raw

Ist ein Eingabetyp keiner der hier genannten Typen, muss es serialisiert und als *raw*an die Funktion übergeben werden. In diesem Fall muss die Funktion auch Code enthalten, in dem die Eingabe deserialisiert wird.

### <a name="outputs"></a>Ausgaben

Die Ausgabe der Funktion kann eines der folgenden Objekte sein:

- Ein Datenrahmen, der die unterstützten Datentypen enthält. Jedes Objekt im Datenrahmen muss einen der unterstützten Datentypen haben.
- Eine benannte Liste, die höchstens einen Datenrahmen enthält. Jedes Element der Liste muss einen der unterstützten Datentypen haben.
- NULL, wenn die Funktion kein Ergebnis zurückgibt.

## <a name="step-2-generate-required-objects"></a>Schritt 2: Generieren der erforderlichen Objekte

Nachdem Ihr R-Code bereinigt wurden und als einzelne Funktion aufgerufen werden kann, verwenden Sie die Funktionen in der **Sqlrutils** Paket vorbereiten, die Eingaben und Ausgaben in ein Formular, das an den Konstruktor übergeben werden kann, die tatsächlich erstellt die gespeicherte Prozedur.

**Sqlrutils** bietet Funktionen, die definieren, die eingabedatenschema und den Typ und die Ausgabe-Data-Schema und den Typ zu definieren. Darüber hinaus Funktionen, die R-Objekte in der erforderlichen Ausgabetyp konvertieren können. Sie können mehrere Funktionsaufrufe, um die erforderlichen Objekte, abhängig von den Datentypen zu erstellen, die Ihr Code verwendet, vornehmen.

### <a name="inputs"></a>Eingaben

Wenn Ihre Funktion Eingaben akzeptiert, für jeden Eingabe-, rufen Sie die folgenden Funktionen:

- `setInputData` Wenn die Eingabe einen Datenrahmen ist.
- `setInputParameter` für alle anderen Eingabetypen

Wenn Sie jede Funktion aufgerufen haben, wird ein R-Objekt erstellt, wenn Sie später als Argument übergeben werden `StoredProcedure`, um die vollständige gespeicherte Prozedur zu erstellen.

### <a name="outputs"></a>Ausgaben

**Sqlrutils** stellt mehrere Funktionen bereit, für das Konvertieren von R z. Objekte b. auf der SQL Server erforderlichen Datenrahmen (Data.Frame) enthält.
Gibt Ihre Funktion direkt einen Datenrahmen aus, ohne diesen erst in eine Liste einzuschließen, können Sie diesen Schritt überspringen.
Sie können auch der Konvertierung diesen Schritt überspringen, wenn die Funktion NULL zurückgibt.

Beim Konvertieren einer Liste oder für das Abrufen eines bestimmten Elements aus einer Liste, wählen Sie diese Funktionen:

- `setOutputData` Wenn die Variable zum Abrufen aus der Liste einen Datenrahmen.
- `setOutputParameter` für alle anderen Elemente der Liste

Wenn Sie jede Funktion aufgerufen haben, wird ein R-Objekt erstellt, wenn Sie später als Argument übergeben werden `StoredProcedure`, um die vollständige gespeicherte Prozedur zu erstellen.

## <a name="step-3-generate-the-stored-procedure"></a>Schritt 3: Generieren der gespeicherten Prozedur

Wenn Sie alle Eingabe- und Ausgabeparameter vorbereitet sind, stellen Sie einen Aufruf der `StoredProcedure` Konstruktor.

**Usage**

`StoredProcedure (func, spName, ..., filePath = NULL ,dbName = NULL, connectionString = NULL, batchSeparator = "GO")`

Um zu veranschaulichen, wird davon ausgegangen, dass Sie eine gespeicherte Prozedur, die mit dem Namen erstellen möchten **Sp_rsample** mit folgenden Parametern:

- Verwendet eine vorhandene Funktion **Foosql**. Die Funktion wurde auf Grundlage von vorhandenem Code im R-Funktion **"Foo"**, aber Sie mussten die Funktion, um den Anforderungen entsprechen, wie in beschrieben [in diesem Abschnitt](#bkmk_rewrite), und die aktualisierte Funktion als benannte  **Foosql**.
- Verwendet den Datenrahmen **Queryinput** als Eingabe
- Generiert als Ausgabe einen Datenrahmen mit dem R-Variablennamen **Sqloutput**
- Den T-SQL-Code als in-Datei erstellen möchten die `C:\Temp` Ordner, damit Sie es später noch Mal mit der SQL Server Management Studio ausführen können

```R
StoredProcedure (foosql, sp_rsample, queryinput, sqloutput, filePath = "C:\\Temp")
```

> [!NOTE]
> Da Sie die Datei in das Dateisystem schreiben, können Sie die Argumente auslassen, die Verbindung mit der Datenbank zu definieren.

Die Ausgabe der Funktion ist eine gespeicherte T-SQL-Prozedur, die auf einer Instanz von SQL Server 2016 (erfordert R Services) oder SQL Server 2017 (erfordert die Machine Learning-Dienste mit R) ausgeführt werden können. 

Weitere Beispiele finden Sie in der Paket-Hilfe, durch den Aufruf `help(StoredProcedure)` aus einer R-Umgebung.

## <a name="step-4-register-and-run-the-stored-procedure"></a>Schritt 4. Registrieren und Ausführen der gespeicherten Prozedur

Es gibt zwei Möglichkeiten, dass Sie die gespeicherte Prozedur ausführen können:

- Mithilfe von T-SQL, von jedem Client aus, die Verbindungen mit der Instanz von SQL Server 2016 oder SQL Server 2017 unterstützt.
- Aus einer R-Umgebung

Beide Methoden erfordern, dass die gespeicherte Prozedur registriert werden, in der Datenbank, in dem Sie die gespeicherte Prozedur verwenden möchten.

### <a name="register-the-stored-procedure"></a>Die gespeicherte Prozedur registrieren

Sie können die gespeicherte Prozedur mit R registrieren, oder Sie können die CREATE PROCEDURE-Anweisung im T-SQL ausführen.

- Mithilfe von T-SQL.  Wenn Sie mehr mit T-SQL vertraut sind, öffnen Sie SQl Server Management Studio (oder einem anderen Client, der SQL-DDL Befehle ausgeführt werden kann), und führen Sie die CREATE PROCEDURE-Anweisung, die mithilfe des Codes vorbereitet, indem die `StoredProcedure` Funktion.
- Mit R. Während Sie weiterhin in Ihrem R-Umgebung befinden, können Sie die `registerStoredProcedure` -Funktion in **Sqlrutils** um die gespeicherte Prozedur mit der Datenbank zu registrieren.

  Beispielsweise können Sie die gespeicherte Prozedur registrieren **Sp_rsample** in der Instanz und die Datenbank, die in definierten *SqlConnStr*, indem Sie diesen R-Aufruf:

  ```R
  registerStoredProcedure(sp_rsample, sqlConnStr)
  ```


> [!IMPORTANT]
> Unabhängig davon, ob Sie R- oder SQL verwenden müssen Sie die Anweisung mit einem Konto mit Berechtigungen zum Erstellen neuer Datenbankobjekte ausführen.

### <a name="run-using-sql"></a>Führen Sie mithilfe von SQL

Nachdem die gespeicherte Prozedur erstellt wurde, öffnen Sie eine Verbindung mit der SQL-Datenbank, die mit einem beliebigen Client, der T-SQL unterstützt, und übergeben Sie Werte für alle Parameter von der gespeicherten Prozedur erforderlich sind.

### <a name="run-using-r"></a>Führen Sie mithilfe von R

Einige zusätzlicher Vorbereitung ist erforderlich, wenn die gespeicherte Prozedur aus R-Code, von SQL Server ausgeführt werden soll. Z. B. wenn die gespeicherte Prozedur Eingabewerte erfordert, müssen Sie diese Eingabeparameter festlegen, bevor die Funktion ausgeführt werden kann, und klicken Sie dann die Objekte an die gespeicherte Prozedur in Ihrem R-Code übergeben.

Der Gesamtprozess des Aufrufs von vorbereiteten gespeicherten SQL-Prozedur lautet wie folgt aus:

1. Rufen Sie `getInputParameters` auf, um eine Liste der Eingabeparameterobjekte abzurufen.
2. Definieren Sie eine Abfrage ( `$query` ) für jeden Parameter, oder legen Sie einen Wert ( `$value` ) für jeden Parameter fest.
3. Verwenden Sie `executeStoredProcedure` , um die gespeicherte Prozedur aus der R-Entwicklungsumgebung auszuführen. Übergeben Sie dazu die Liste der Eingabeparameterobjekte, die Sie festgelegt haben.

## <a name = "samples"></a>Beispiel

Dieses Beispiel zeigt, die vor und nach der Versionen eines R-Skripts, die Ruft Daten aus einer SQL Server-Datenbank ab und führt einige Transformationen für die Daten in einer anderen Datenbank gespeichert.

In diesem einfache Beispiel dient nur zu veranschaulichen, wie Sie Ihren R-Code zum Konvertieren einer gespeicherten Prozedur zu vereinfachen, neu anordnen können.

### <a name="before-code-preparation"></a>Bevor Sie Code zur Vorbereitung


```R
sqlConnFrom <- "Driver={ODBC Driver 13 for SQL Server};Server=MyServer01;Database=AirlineSrc;Trusted_Connection=Yes;"
  
sqlConnTo <- "Driver={ODBC Driver 13 for SQL Server};Server=MyServer01;Database=AirlineTest;Trusted_Connection=Yes;"
  
sqlQueryAirline <- "SELECT TOP 10000 ArrDelay, CRSDepTime, DayOfWeek FROM [AirlineDemoSmall]"
  
dsSqlFrom <- RxSqlServerData(sqlQuery = sqlQueryAirline, connectionString = sqlConnFrom)
  
dsSqlTo <- RxSqlServerData(table = "cleanData", connectionString = sqlConnTo)
  
xFunc <- function(data) {
    data$CRSDepHour <- as.integer(trunc(data$CRSDepTime))
    return(data)
    }
  
xVars <- c("CRSDepTime")
  
sqlCompute <- RxInSqlServer(numTasks = 4, connectionString = sqlConnTo)
  
rxOpen(dsSqlFrom)
rxOpen(dsSqlTo)
  
if (rxSqlServerTableExists("cleanData", connectionString = sqlConnTo))   {
    rxSqlServerDropTable("cleanData")}
  
rxDataStep(inData = dsSqlFrom, 
     outFile = dsSqlTo,
     transformFunc = xFunc,
     transformVars = xVars,
     overwrite = TRUE)
```

> [!NOTE]
> 
> Bei Verwendung eine ODBC-Verbindung statt Aufrufen der *RxSqlServerData* -Funktion müssen Sie die Verbindung mit öffnen *RxOpen* bevor Sie Vorgänge in der Datenbank ausführen können.


### <a name="after-code-preparation"></a>Nach der Vorbereitung von code

In der aktualisierten Version definiert die erste Zeile den Namen der Funktion. Gesamte Weitere Code aus der ursprünglichen R-Lösung wird Teil dieser Funktion.

```R
myetl1function <- function() { 
   sqlConnFrom <- "Driver={ODBC Driver 13 for SQL Server};Server=MyServer01;Database=Airline01;Trusted_Connection=Yes;"
   sqlConnTo <- "Driver={ODBC Driver 13 for SQL Server};Server=MyServer02;Database=Airline02;Trusted_Connection=Yes;"
    
   sqlQueryAirline <- "SELECT TOP 10000 ArrDelay, CRSDepTime, DayOfWeek FROM [AirlineDemoSmall]"

   dsSqlFrom <- RxSqlServerData(sqlQuery = sqlQueryAirline, connectionString = sqlConnFrom)
  
   dsSqlTo <- RxSqlServerData(table = "cleanData", connectionString = sqlConnTo)
  
   xFunc <- function(data) {
     data$CRSDepHour <- as.integer(trunc(data$CRSDepTime))
     return(data)}
  
   xVars <- c("CRSDepTime")
  
   sqlCompute <- RxInSqlServer(numTasks = 4, connectionString = sqlConnTo)
  
   if (rxSqlServerTableExists("cleanData", connectionString = sqlConnTo)) {rxSqlServerDropTable("cleanData")}
  
   rxDataStep(inData = dsSqlFrom, 
        outFile = dsSqlTo,
        transformFunc = xFunc,
        transformVars = xVars,
        overwrite = TRUE)
   return(NULL)
}
```

> [!NOTE]
> 
> Obwohl Sie die ODBC-Verbindung nicht explizit in Ihrem Code öffnen müssen, ist weiterhin eine ODBC-Verbindung erforderlich, um **sqlrutils**zu verwenden.

## <a name="see-also"></a>Siehe auch

[sqlrutils (SQL)](ref-r-sqlrutils.md)


