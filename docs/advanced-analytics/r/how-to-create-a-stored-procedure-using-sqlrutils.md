---
title: Erstellen einer gespeicherten Prozedur mithilfe von sqlrutils
description: Verwenden Sie das sqlrutils-r-Paket in SQL Server, um r-Sprachcode in einer einzelnen Funktion zu bündeln, die als Argument an eine gespeicherte Prozedur weitergeleitet werden kann.
ms.prod: sql
ms.technology: machine-learning
ms.date: 04/15/2018
ms.topic: conceptual
author: dphansen
ms.author: davidph
ms.openlocfilehash: 0713a126a237f20b2de4e3b16225bb9e5ae26307
ms.sourcegitcommit: c1382268152585aa77688162d2286798fd8a06bb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/19/2019
ms.locfileid: "68345582"
---
# <a name="create-a-stored-pprocedure-using-sqlrutils"></a>Erstellen einer gespeicherten pprocedure mithilfe von sqlrutils
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

In diesem Artikel werden die Schritte zum Umrechnen des R-Codes beschrieben, der als gespeicherte T-SQL-Prozedur ausgeführt werden soll. Zum Erzielen bestmöglicher Ergebnisse kann es erforderlich sein, dass Ihr Code ein wenig geändert wird, damit sichergestellt ist, dass alle Eingaben parametrisiert werden können.

## <a name="bkmk_rewrite"></a>Schritt 1: R-Skript neu schreiben

Um die besten Ergebnisse zu erzielen, sollten Sie Ihren R-Code neu schreiben, um ihn als einzelne Funktion zu kapseln.

Alle Variablen, die von der Funktion verwendet werden, sollten innerhalb der Funktion definiert oder als Eingabeparameter definiert werden. Weitere Informationen finden Sie im [Beispielcode](#samples) in diesem Artikel.

Da die Eingabeparameter für die R-Funktion zu den Eingabe Parametern der gespeicherten SQL-Prozedur werden, müssen Sie sicherstellen, dass Ihre Eingaben und Ausgaben den folgenden typanforderungen entsprechen:

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

## <a name="step-2-generate-required-objects"></a>Schritt 2: Erforderliche Objekte generieren

Nachdem der R-Code bereinigt wurde und als einzelne Funktion aufgerufen werden kann, verwenden Sie die Funktionen im **sqlrutils** -Paket, um die Eingaben und Ausgaben in einem Formular vorzubereiten, das an den Konstruktor übergeben werden kann, der die gespeicherte Prozedur erstellt.

**sqlrutils** stellt Funktionen bereit, die das Eingabedaten Schema und den Typ definieren, und definiert das Ausgabedaten Schema und den Typ. Sie enthält auch Funktionen, die R-Objekte in den erforderlichen Ausgabetyp konvertieren können. Sie können mehrere Funktionsaufrufe vornehmen, um die erforderlichen Objekte zu erstellen, abhängig von den Datentypen, die im Code verwendet werden.

### <a name="inputs"></a>Eingaben

Wenn Ihre Funktion Eingaben annimmt, müssen Sie für jede Eingabe die folgenden Funktionen aufzurufen:

- `setInputData`Wenn die Eingabe ein Datenrahmen ist
- `setInputParameter`für alle anderen Eingabetypen

Wenn Sie jeden Funktions Aufrufvorgang ausführen, wird ein R-Objekt erstellt, das Sie später als Argument `StoredProcedure`an übergeben, um die gesamte gespeicherte Prozedur zu erstellen.

### <a name="outputs"></a>Ausgaben

**sqlrutils** stellt mehrere Funktionen zum Umrechnen von R-Objekten, z. b. Listen, in den von SQL Server erforderlichen Datenrahmen bereit.
Gibt Ihre Funktion direkt einen Datenrahmen aus, ohne diesen erst in eine Liste einzuschließen, können Sie diesen Schritt überspringen.
Sie können die Konvertierung auch überspringen, wenn die Funktion NULL zurückgibt.

Beim Umrechnen einer Liste oder beim erhalten eines bestimmten Elements aus einer Liste Wählen Sie eine der folgenden Funktionen aus:

- `setOutputData`Wenn die Variable, die aus der Liste abgeleitet werden soll, ein Datenrahmen ist.
- `setOutputParameter`für alle anderen Mitglieder der Liste

Wenn Sie jeden Funktions Aufrufvorgang ausführen, wird ein R-Objekt erstellt, das Sie später als Argument `StoredProcedure`an übergeben, um die gesamte gespeicherte Prozedur zu erstellen.

## <a name="step-3-generate-the-stored-procedure"></a>Schritt 3: Generieren der gespeicherten Prozedur

Wenn alle Eingabe-und Ausgabeparameter bereit sind, können Sie den `StoredProcedure` -Konstruktor aufzurufen.

**Verwendung**

`StoredProcedure (func, spName, ..., filePath = NULL ,dbName = NULL, connectionString = NULL, batchSeparator = "GO")`

Angenommen, Sie möchten eine gespeicherte Prozedur mit dem Namen **sp_rsample** mit den folgenden Parametern erstellen:

- Verwendet eine vorhandene Funktion **foosql**. Die Funktion basiert auf vorhandenem Code in R-Funktion **foo**, aber Sie haben die Funktion so umgeschrieben, dass Sie den in [diesem Abschnitt](#bkmk_rewrite)beschriebenen Anforderungen entspricht und die aktualisierte Funktion als **foosql**bezeichnet.
- Verwendet den Datenrahmen **queryinput** als Eingabe.
- Generiert als Ausgabe eines Daten Rahmens mit dem R-Variablennamen **SQLOutput** .
- Sie möchten den T-SQL-Code als Datei im `C:\Temp` Ordner erstellen, damit Sie ihn später mithilfe SQL Server Management Studio ausführen können.

```R
StoredProcedure (foosql, sp_rsample, queryinput, sqloutput, filePath = "C:\\Temp")
```

> [!NOTE]
> Da Sie die Datei in das Dateisystem schreiben, können Sie die Argumente weglassen, die die Datenbankverbindung definieren.

Bei der Ausgabe der-Funktion handelt es sich um eine gespeicherte T-SQL-Prozedur, die auf einer Instanz von SQL Server 2016 (erfordert r Services) oder SQL Server 2017 (erfordert Machine Learning Services mit R) ausgeführt werden kann. 

Weitere Beispiele finden Sie in der Paket Hilfe, indem Sie `help(StoredProcedure)` aus einer R-Umgebung aufrufen.

## <a name="step-4-register-and-run-the-stored-procedure"></a>Schritt 4. Registrieren und Ausführen der gespeicherten Prozedur

Die gespeicherte Prozedur kann auf zwei Arten ausgeführt werden:

- Verwenden von T-SQL, von jedem Client, der Verbindungen mit der SQL Server 2016-oder SQL Server 2017-Instanz unterstützt
- Aus einer R-Umgebung

Beide Methoden erfordern, dass die gespeicherte Prozedur in der Datenbank registriert wird, in der Sie die gespeicherte Prozedur verwenden möchten.

### <a name="register-the-stored-procedure"></a>Registrieren der gespeicherten Prozedur

Sie können die gespeicherte Prozedur mithilfe von R registrieren, oder Sie können die CREATE PROCEDURE-Anweisung in T-SQL ausführen.

- Verwenden von T-SQL.  Wenn Sie mit T-SQL besser vertraut sind, öffnen Sie SQL Server-Management Studio (oder einen anderen Client, der SQL-DDL-Befehle ausführen kann), und führen Sie die CREATE PROCEDURE `StoredProcedure` -Anweisung mit dem von der Funktion vorbereiteten Code aus.
- Verwenden von R. Obwohl Sie sich noch in Ihrer R-Umgebung befinden, können Sie `registerStoredProcedure` die-Funktion in **sqlrutils** verwenden, um die gespeicherte Prozedur bei der Datenbank zu registrieren.

  Sie können z. b. die gespeicherte Prozedur **sp_rsample** in der Instanz und in der Datenbank registrieren, die in *sqldinnstr*definiert ist, indem Sie diesen R-Befehl ausführen:

  ```R
  registerStoredProcedure(sp_rsample, sqlConnStr)
  ```


> [!IMPORTANT]
> Unabhängig davon, ob Sie R oder SQL verwenden, müssen Sie die Anweisung mit einem Konto ausführen, das über Berechtigungen zum Erstellen neuer Datenbankobjekte verfügt.

### <a name="run-using-sql"></a>Ausführen mithilfe von SQL

Nachdem die gespeicherte Prozedur erstellt wurde, öffnen Sie mithilfe eines beliebigen Clients, der T-SQL unterstützt, eine Verbindung mit der SQL-Datenbank, und übergeben Sie Werte für alle Parameter, die für die gespeicherte Prozedur erforderlich sind.

### <a name="run-using-r"></a>Ausführen mithilfe von R

Eine weitere Vorbereitung ist erforderlich, wenn Sie die gespeicherte Prozedur aus R-Code ausführen möchten, anstatt SQL Server. Wenn die gespeicherte Prozedur z. b. Eingabewerte erfordert, müssen Sie diese Eingabeparameter festlegen, bevor die Funktion ausgeführt werden kann, und diese Objekte dann an die gespeicherte Prozedur in Ihrem R-Code übergeben.

Der Gesamtprozess des Aufrufs der vorbereiteten gespeicherten SQL-Prozedur lautet wie folgt:

1. Rufen Sie `getInputParameters` auf, um eine Liste der Eingabeparameterobjekte abzurufen.
2. Definieren Sie eine Abfrage ( `$query` ) für jeden Parameter, oder legen Sie einen Wert ( `$value` ) für jeden Parameter fest.
3. Verwenden Sie `executeStoredProcedure` , um die gespeicherte Prozedur aus der R-Entwicklungsumgebung auszuführen. Übergeben Sie dazu die Liste der Eingabeparameterobjekte, die Sie festgelegt haben.

## <a name = "samples"></a>Beispiel

In diesem Beispiel werden die Versionen vor und nach der Ausführung eines R-Skripts veranschaulicht, das Daten aus einer SQL Server Datenbank abruft, einige Transformationen für die Daten ausführt und Sie in einer anderen Datenbank speichert.

Dieses einfache Beispiel wird nur verwendet, um zu veranschaulichen, wie Sie Ihren R-Code neu anordnen können, um die Konvertierung in eine gespeicherte Prozedur zu vereinfachen.

### <a name="before-code-preparation"></a>Vor der Code Vorbereitung


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
> Wenn Sie eine ODBC-Verbindung verwenden, anstatt die *rxsqlserverdata* -Funktion aufzurufen, müssen Sie die Verbindung mithilfe von *rxopen* öffnen, bevor Sie Vorgänge für die Datenbank ausführen können.


### <a name="after-code-preparation"></a>Nach der Code Vorbereitung

In der aktualisierten Version definiert die erste Zeile den Funktionsnamen. Sämtlicher anderer Code aus der ursprünglichen R-Lösung wird Teil dieser Funktion.

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


