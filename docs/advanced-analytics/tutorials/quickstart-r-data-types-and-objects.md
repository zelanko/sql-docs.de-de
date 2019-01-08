---
title: Schnellstart zu R und SQL-Datentypen und Objekte – SQL Server-Machine Learning
description: Erfahren Sie in dieser schnellstartanleitung, wie zum Arbeiten mit Datentypen und die Datenobjekte in R und SQL Server.
ms.prod: sql
ms.technology: machine-learning
ms.date: 01/04/2019
ms.topic: quickstart
author: dphansen
ms.author: davidph
manager: cgronlun
ms.openlocfilehash: df1c4c50e21ba5db5459da958f915be560500dc7
ms.sourcegitcommit: baca29731a1be4f8fa47567888278394966e2af7
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/04/2019
ms.locfileid: "54046931"
---
# <a name="quickstart-handle-data-types-and-objects-using-r-in-sql-server"></a>Schnellstart: Behandeln von Datentypen und Objekte, die mithilfe von R in SQL Server
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

Erhalten Sie in diesem Schnellstart eine praktische Einführung für häufig auftretende Probleme, die beim Verschieben von Daten zwischen R und SQL Server auftreten. Die Erfahrung, die Sie durch diese Übung erzielen enthält wichtige Hintergrundinformationen, bei der Arbeit mit Daten in Ihr eigenes Skript.

Häufige Probleme von vornherein wissen gehören:

+ Datentypen stimmen manchmal nicht überein
+ Implizite Konvertierungen können durchgeführt werden.
+ Cast- und Convert-Vorgänge sind manchmal erforderlich
+ R und SQL verwenden verschiedene Datenobjekte

## <a name="prerequisites"></a>Erforderliche Komponenten

Einen vorherigen schnellstartanleitung [R stellen Sie sicher, die in SQL Server vorhanden ist](quickstart-r-verify.md), enthält Informationen und links für das Einrichten der R-Umgebung, die im Rahmen dieser schnellstartanleitung benötigt.

## <a name="always-return-a-data-frame"></a>Immer einen Datenrahmen zurück

Wenn Ihr Skript Ergebnisse von R zum SQL Server zurückgibt, muss es die Daten als **data.frame** zurückgeben. Jede andere Art von Objekt, das Sie in Ihrem Skript – erstellen, ob die Freigabe, die eine Liste, Faktor, Vektor oder binäre Daten – muss zu einem Datenrahmen konvertiert werden, wenn es als Teil der gespeicherten prozedurergebnisse ausgegeben werden soll. Es gibt mehrere R-Funktionen, um die Änderung anderer Objekte zu einem Datenrahmen zu unterstützen. Sie können auch ein binäres Modell serialisieren und es in einen Datenrahmen zurückgeben. Mehr dazu erfahren Sie später in diesem Lernprogramm.

Zunächst lassen Sie uns mit einigen R grundlegende R-Objekten - Vektoren, Matrizen und Listen - experimentieren und sehen, wie die Konvertierung in einen Datenrahmen die Ausgabe an den SQL Server ändert.

Vergleichen Sie diese beiden "Hello World"-Skripts in r Suchen Sie die Skripts nahezu identisch, aber die erste gibt eine einzelne Spalte mit drei Werten zurück, während die zweite gibt drei Spalten mit einem einzelnen Wert jeder.

**Beispiel 1**

```sql
EXECUTE sp_execute_external_script
       @language = N'R'
     , @script = N' mytextvariable <- c("hello", " ", "world");
       OutputDataSet <- as.data.frame(mytextvariable);'
     , @input_data_1 = N' ';
```

**Beispiel 2**

```sql
EXECUTE sp_execute_external_script
        @language = N'R'
      , @script = N' OutputDataSet<- data.frame(c("hello"), " ", c("world"));'
      , @input_data_1 = N'  ';
```

## <a name="identify-schema-and-data-types"></a>Identifizieren Sie die Schemen- und Datenarten

Warum sind die Ergebnisse so unterschiedlich? 

Die Antwort finden Sie in der Regel mithilfe des R-`str()`-Befehls. Fügen Sie die Funktion `str(object_name)` in Ihrem R-Skript hinzu, um das Datenschema des festgelegten R-Objekts als Informationsmeldung zurückzugeben. Nachrichten finden Sie unter **Nachrichten**, im Bereich des Visual Studio-Code oder unter der **Nachrichten**-Registerkarte in SSMS.

Um zu ermitteln, warum Beispiel 1 und Beispiel 2 solch unterschiedliche Ergebnisse haben, fügen Sie die Zeile `str(OutputDataSet)` am Ende der _@script_-Variablendefinition in jeder Anweisung, wie folgt ein:

**Beispiel 1 mit str-Funktion hinzugefügt**

```sql
EXECUTE sp_execute_external_script
        @language = N'R'
      , @script = N' mytextvariable <- c("hello", " ", "world");
      OutputDataSet <- as.data.frame(mytextvariable);
      str(OutputDataSet);'
      , @input_data_1 = N'  '
;
```

**Beispiel 2 mit str-Funktion hinzugefügt**

```sql
EXECUTE sp_execute_external_script
  @language = N'R', 
  @script = N' OutputDataSet <- data.frame(c("hello"), " ", c("world"));
    str(OutputDataSet);' , 
  @input_data_1 = N'  ';
```

Überprüfen Sie nun den Text in **Nachrichten**, um festzustellen aus welchem Grund die Ausgabe anders ist.

**Ergebnisse - Beispiel 1**

```sql
STDOUT message(s) from external script:
'data.frame':   3 obs. of  1 variable:
$ mytextvariable: Factor w/ 3 levels " ","hello","world": 2 1 3
```

**Ergebnisse - Beispiel 2**

```sql
STDOUT message(s) from external script:
'data.frame':   1 obs. of  3 variables:
$ c..hello..: Factor w/ 1 level "hello": 1
$ X...      : Factor w/ 1 level " ": 1
$ c..world..: Factor w/ 1 level "world": 1
```

Wie Sie sehen können, hatte eine geringfügige Änderung in der R-Syntax einen großen Einfluss auf das Schema der Ergebnisse. Wir gehen deshalb nicht, aber die Unterschiede in R-Datentypen werden detailliert erläutert die *Datenstrukturen* im Abschnitt ["Advanced R" von Hadley Wickham](http://adv-r.had.co.nz).

Jetzt müssen Sie nur Bedenken, dass Sie die erwarteten Ergebnisse überprüfen müssen, wenn Sie R-Objekte in Datenrahmen umwandeln müssen.

> [!TIP]
> Sie können R-Identitätsfunktionen, z. B. auch `is.matrix`, `is.vector`, um Informationen über die interne Datenstruktur zurückzugeben.

## <a name="implicit-conversion-of-data-objects"></a>Implizite Konvertierung von Datenobjekten

Jedes R-Datenobjekt verfügt über seine eigenen Regeln darüber, wie Werte verarbeitet werden, wenn sie mit anderen Datenobjekten kombiniert werden, sofern die beiden Datenobjekte über die gleiche Anzahl an Dimensionen verfügen oder jedes Datenobjekt heterogene Datentypen enthält.

Nehmen wir beispielsweise an, dass Sie die folgende Anweisung aus, um die Matrixmultiplikation mithilfe von r ausführen Sie multiplizieren Sie eine einspaltige Matrix mit den drei Werten durch ein Array mit vier Werten und erwarten daher eine 4 x 3-Matrix.

```sql
EXECUTE sp_execute_external_script
    @language = N'R'
    , @script = N'
        x <- as.matrix(InputDataSet);
        y <- array(12:15);
    OutputDataSet <- as.data.frame(x %*% y);'
    , @input_data_1 = N' SELECT [Col1]  from RTestData;'
    WITH RESULT SETS (([Col1] int, [Col2] int, [Col3] int, Col4 int));
```

Im Hintergrund wird die Spalte mit drei Werten in eine einspaltige Matrix konvertiert. Das Array `y` wird implizit in eine einspaltige Matrix umgewandelt, um die beiden Argumente anzupassen, da eine Matrix nur ein Sonderfall eines Arrays in R ist.

**Ergebnisse**

|Col1|Col2|Col3|Col4|
|---|---|---|---|
|12|13|14|15|
|120|130|140|150|
|1200|1300|1400|1500|

Beachten Sie jedoch, was geschieht, wenn Sie die Größe des Arrays ändern `y`.

```sql
execute sp_execute_external_script
   @language = N'R'
   , @script = N'
        x <- as.matrix(InputDataSet);
        y <- array(12:14);
   OutputDataSet <- as.data.frame(y %*% x);'
   , @input_data_1 = N' SELECT [Col1]  from RTestData;'
   WITH RESULT SETS (([Col1] int ));
```

Jetzt gibt R einen einzelnen Wert als Ergebnis zurück.

**Ergebnisse**
    
|Col1|
|---|
|1542|

Warum? Da die beiden Argumente als Vektoren derselben Länge verarbeitet werden können, gibt R das innere Produkt in diesem Fall als Matrix.  Dies ist das erwartete Verhalten gemäß der Regeln der linearen Algebra. Es kann jedoch Probleme verursachen, wenn die Downstream-Anwendung erwartet, dass das Ausgabeschema sich nie ändert!

> [!TIP]
> 
> Abrufen von Fehler? Diese Beispiele erfordern in der Tabelle **RTestData**. Wenn Sie die Test-Datentabelle erstellt haben, wechseln Sie zurück zu diesem Thema, um die Tabelle zu erstellen: [Verarbeiten von Eingaben und Ausgaben](../tutorials/rtsql-working-with-inputs-and-outputs.md).
> 
> Wenn Sie die Tabelle erstellt haben, aber trotzdem eine Fehlermeldung erhalten, stellen Sie sicher, dass Sie die gespeicherte Prozedur ausgeführt werden, im Kontext der Datenbank, die die Tabelle enthält, und nicht in **master** oder einer anderen Datenbank.
> 
> Darüber hinaus wird empfohlen, dass Sie die Verwendung von temporären Tabellen für diese Beispiele vermeiden. Einige R Clients werden eine Verbindung zwischen dem Löschen von temporären Tabellen Batches beendet.

## <a name="merge-or-multiply-columns-of-different-length"></a>Zusammenführen oder Multiplizieren von Spalten mit unterschiedlicher Länge

R bietet mehr Flexibilität für die Arbeit mit Vektoren mit verschiedenen Größen und für die Kombination dieser Spalten-ähnlichen Strukturen in Datenrahmen. Vektorenlisten können aussehen wie eine Tabelle, aber sie befolgen nicht alle Regeln, die Datenbanktabellen steuern.

Zum Beispiel legt das folgende Skript ein numerisches Array der Länge 6 fest und speichert es in der R-Variable `df1`. Das numerische Array wird anschließend mit den ganzen Zahlen der RTestData-Tabelle, die drei (3) Werte enthält, um einen neuen Datenrahmen, kombiniert `df2`.

```sql
EXECUTE sp_execute_external_script
    @language = N'R'
    , @script = N'
               df1 <- as.data.frame( array(1:6) );
               df2 <- as.data.frame( c( InputDataSet , df1 ));
               OutputDataSet <- df2'
    , @input_data_1 = N' SELECT [Col1]  from RTestData;'
    WITH RESULT SETS (( [Col2] int not null, [Col3] int not null ));
```

Zum Ausfüllen eines Datenrahmens, wiederholt R die Elemente, die aus RTestData aufgerufen wurden, so oft wie erforderlich, um die Anzahl der Elemente im Array `df1` zuzuordnen.

**Ergebnisse**
    
|*Col2*|*Col3*|
|----|----|
|1|1|
|10|2|
|100|3|
|1|4|
|10|5|
|100|6|

Beachten Sie, dass der Datenrahmen nur wie eine Tabelle aussieht, aber eigentlich eine Vektorenliste ist.

## <a name="cast-or-convert-sql-server-data"></a>Cast und Convert von SQL Serverdaten

R und SQL Server verwenden nicht die gleichen Datentypen, sodass Sie eine Abfrage im SQL Server durchführen können, um Daten abzurufen und diese an die R-Laufzeit zu übergeben, erfolgt in der Regel eine Art implizite Konvertierung. Eine weitere Reihe von Konvertierungen findet statt, wenn Sie Daten von R an SQL Server zurückgeben.

- SQL Server überträgt die Daten aus der Abfrage an den vom Launchpad-Dienst verwalteten R-Prozess und konvertiert es in einer internen Darstellung für mehr Effizienz.
- Die R-Laufzeit lädt die Daten in eine data.frame-Variable und führt ihre eigenen Vorgänge für die Daten aus.
- Die Datenbank-Engine gibt die Daten über eine sichere interne Verbindung an den SQL Server zurück und zeigt die Daten in Form von SQL Server-Datentypen.
- Sie rufen Sie Daten über eine Verbindung mit dem SQL Server mithilfe einer Client- oder Netzwerk-Bibliothek auf, die SQL-Abfragen und tabellarische Datensätze verarbeiten kann. Diese Clientanwendung kann die Daten auf andere Weise beeinträchtigen.

Um anzuzeigen, wie dies funktioniert, führen Sie eine Abfrage wie diese auf die ["AdventureWorksDW"](https://github.com/Microsoft/sql-server-samples/releases/tag/adventureworks) -Datawarehouse. In dieser Ansicht werden Verkaufsdaten zurückgegeben, die zum Erstellen von Prognosen verwendet werden.

```sql
USE AdventureWorksDW
GO

SELECT ReportingDate
         , CAST(ModelRegion as varchar(50)) as ProductSeries
         , Amount
           FROM [AdventureWorksDW].[dbo].[vTimeSeries]
           WHERE [ModelRegion] = 'M200 Europe'
           ORDER BY ReportingDate ASC
```

> [!NOTE]
> 
> Sie können eine beliebige Version von AdventureWorks verwenden, oder Sie können eine andere Abfrage, die über eine eigene Datenbank erstellen. Der Punkt besteht darin, einige Daten zu behandeln, die Text, Datetime und numerische Werte enthält.

Probieren Sie diese Abfrage als Eingabe für die gespeicherte Prozedur einfügen.

```sql
EXECUTE sp_execute_external_script
       @language = N'R'
      , @script = N' str(InputDataSet);
      OutputDataSet <- InputDataSet;'
      , @input_data_1 = N'
           SELECT ReportingDate
         , CAST(ModelRegion as varchar(50)) as ProductSeries
         , Amount
           FROM [AdventureWorksDW].[dbo].[vTimeSeries]
           WHERE [ModelRegion] = ''M200 Europe''
           ORDER BY ReportingDate ASC ;'
WITH RESULT SETS undefined;
```

Wenn Sie eine Fehlermeldung erhalten, müssen Sie wahrscheinlich einige Änderungen am Abfragetext vornehmen. Zum Beispiel das Zeichenfolgenprädikat in der WHERE-Klausel muss von jeweils zwei einfachen Anführungszeichen umschlossen sein.

Nachdem die Abfrage funktioniert, überprüfen Sie die Ergebnisse der `str`-Funktion, um zu sehen wie R die Eingabedaten behandelt.

**Ergebnisse**

```sql
STDOUT message(s) from external script: 'data.frame':    37 obs. of  3 variables:
STDOUT message(s) from external script: $ ReportingDate: POSIXct, format: "2010-12-24 23:00:00" "2010-12-24 23:00:00"
STDOUT message(s) from external script: $ ProductSeries: Factor w/ 1 levels "M200 Europe",..: 1 1 1 1 1 1 1 1 1 1
STDOUT message(s) from external script: $ Amount       : num  3400 16925 20350 16950 16950
```

+ Die datetime-Spalte wurde als R-Datentyp **POSIXct** verarbeitet.
+ Die Textspalte "ProductSeries" wurde als identifiziert eine **Faktor**, d.h. eine kategorische Variable. Zeichenfolgenwerte werden standardmäßig als Faktoren verarbeitet. Wenn Sie R eine Zeichenfolge übergeben, wird diese in eine ganze Zahl für die interne Verwendung konvertiert und dann zurück in die Ausgabe der Zeichenfolge zugeordnet.

### <a name="summary"></a>Zusammenfassung

Aus, werden diese kurzen Beispiele können Sie sehen die Notwendigkeit, überprüfen die Auswirkungen der Datenkonvertierung, bei der Übergabe von SQL-Abfragen als Eingabe. Da einige SQL Server-Datentypen von R nicht unterstützt werden, berücksichtigen Sie die folgenden Methoden zur Vermeidung von Fehlern:

+ Testen Sie die Daten im voraus, und überprüfen Sie, Spalten oder Werte in Ihrem Schema, das ein Problem, wenn Sie R-Code übergeben werden konnte.
+ Legen Sie Spalten in der Eingabedatenquelle einzeln fest, anstatt `SELECT *` zu verwenden, und verstehen Sie, wie jede Spalte verarbeitet wird.
+ Führen Sie explizite Umwandlungen nach Bedarf beim Vorbereiten der Eingabedaten durch, um Überraschungen zu vermeiden.
+ Vermeiden Sie Spalten übergeben, der Daten (z. B. GUIDS oder Rowguids), die Fehler verursachen und nicht für die Modellierung nützlich sind.

Weitere Informationen zu unterstützten und nicht unterstützten Datentypen finden Sie unter [R-Bibliotheken und-Datentypen](../r/r-libraries-and-data-types.md).

Weitere Informationen zu Auswirkungen auf die Leistung der Laufzeit-Konvertierung von Zeichenfolgen zu numerischen Faktoren, finden Sie unter [leistungsoptimierung für SQL Server R Services](../r/sql-server-r-services-performance-tuning.md).

## <a name="next-step"></a>Nächster Schritt

In der nächsten schnellstartanleitung erfahren Sie, wie R-Funktionen auf SQL Server-Daten angewendet werden.

> [!div class="nextstepaction"]
> [Schnellstart: Verwenden von R-Funktionen mit SQL Server-Daten](quickstart-r-functions.md)
