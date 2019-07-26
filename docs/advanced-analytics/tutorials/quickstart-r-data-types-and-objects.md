---
title: Schnellstart zu R-und SQL-Datentypen und-Objekten
description: In dieser Schnellstartanleitung erfahren Sie, wie Sie in R und SQL Server mit Datentypen und Datenobjekten arbeiten.
ms.prod: sql
ms.technology: machine-learning
ms.date: 01/04/2019
ms.topic: quickstart
author: dphansen
ms.author: davidph
ms.openlocfilehash: 686ba69425dc9bc6554b369be3d5fadd24b5a234
ms.sourcegitcommit: 9062c5e97c4e4af0bbe5be6637cc3872cd1b2320
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/24/2019
ms.locfileid: "68469401"
---
# <a name="quickstart-handle-data-types-and-objects-using-r-in-sql-server"></a>Schnellstart: Verarbeiten von Datentypen und Objekten mithilfe von R in SQL Server
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

In diesem Schnellstart erhalten Sie eine praktische Einführung in häufige Probleme, die beim Verschieben von Daten zwischen R und SQL Server auftreten. Die Erfahrung, die Sie durch diese Übung gewinnen, bietet wesentliche Hintergrundinformationen, wenn Sie mit Daten in Ihrem eigenen Skript arbeiten.

Häufige Probleme, die im Vordergrund aufgeführt werden, sind:

+ Datentypen stimmen manchmal nicht überein
+ Implizite Konvertierungen können stattfinden.
+ Cast- und Convert-Vorgänge sind manchmal erforderlich
+ R und SQL verwenden verschiedene Datenobjekte

## <a name="prerequisites"></a>Vorraussetzungen

Eine vorherige Schnellstartanleitung, [überprüfen, ob R in SQL Server vorhanden](quickstart-r-verify.md)ist, enthält Informationen und Links zum Einrichten der r-Umgebung, die für diesen Schnellstart erforderlich ist.

## <a name="always-return-a-data-frame"></a>Immer einen Datenrahmen zurückgeben

Wenn Ihr Skript Ergebnisse von R zum SQL Server zurückgibt, muss es die Daten als **data.frame** zurückgeben. Jeder andere Objekttyp, den Sie im Skript generieren, und zwar unabhängig davon, ob es sich um eine Liste, einen Faktor, einen Vektor oder Binärdaten handelt, muss in einen Datenrahmen konvertiert werden, wenn Sie ihn als Teil der Ergebnisse der gespeicherten Prozedur ausgeben möchten. Es gibt mehrere R-Funktionen, um die Änderung anderer Objekte zu einem Datenrahmen zu unterstützen. Sie können auch ein binäres Modell serialisieren und es in einen Datenrahmen zurückgeben. Mehr dazu erfahren Sie später in diesem Lernprogramm.

Zuerst experimentieren wir mit einigen r-Basis-r-Objekten-Vectors, Matrizen und Listen. Sie sehen, wie die Konvertierung in einen Datenrahmen die an SQL Server übergebene Ausgabe ändert.

Vergleichen Sie diese beiden "Hallo Welt"-Skripts in R. Die Skripts sehen nahezu identisch aus, aber der erste gibt eine einzelne Spalte mit drei Werten zurück, während die zweite drei Spalten mit jeweils einem einzelnen Wert zurückgibt.

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

## <a name="identify-schema-and-data-types"></a>Identifizieren von Schema und Datentypen

Warum sind die Ergebnisse so unterschiedlich? 

Die Antwort finden Sie in der Regel mithilfe des R-`str()`-Befehls. Fügen Sie die Funktion `str(object_name)` in Ihrem R-Skript hinzu, um das Datenschema des festgelegten R-Objekts als Informationsmeldung zurückzugeben. Nachrichten finden Sie unter **Nachrichten**, im Bereich des Visual Studio-Code oder unter der **Nachrichten**-Registerkarte in SSMS.

Um zu ermitteln, warum Beispiel 1 und Beispiel 2 solch unterschiedliche Ergebnisse haben, fügen Sie die Zeile `str(OutputDataSet)` am Ende der _@script_ -Variablendefinition in jeder Anweisung, wie folgt ein:

**Beispiel 1 mit hinzugefügter Str-Funktion**

```sql
EXECUTE sp_execute_external_script
        @language = N'R'
      , @script = N' mytextvariable <- c("hello", " ", "world");
      OutputDataSet <- as.data.frame(mytextvariable);
      str(OutputDataSet);'
      , @input_data_1 = N'  '
;
```

**Beispiel 2 mit hinzugefügter Str-Funktion**

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

Wie Sie sehen können, hatte eine geringfügige Änderung in der R-Syntax einen großen Einfluss auf das Schema der Ergebnisse. Wir gehen nicht in den Grund ein, aber die Unterschiede in R-Datentypen werden im *Abschnitt* ["Advanced R" von Hadley Wickham](http://adv-r.had.co.nz)ausführlich erläutert.

Jetzt müssen Sie nur Bedenken, dass Sie die erwarteten Ergebnisse überprüfen müssen, wenn Sie R-Objekte in Datenrahmen umwandeln müssen.

> [!TIP]
> Sie können auch R-Identitäts Funktionen, wie z `is.matrix`. `is.vector`b., verwenden, um Informationen über die interne Datenstruktur zurückzugeben.

## <a name="implicit-conversion-of-data-objects"></a>Implizite Konvertierung von Datenobjekten

Jedes R-Datenobjekt verfügt über seine eigenen Regeln darüber, wie Werte verarbeitet werden, wenn sie mit anderen Datenobjekten kombiniert werden, sofern die beiden Datenobjekte über die gleiche Anzahl an Dimensionen verfügen oder jedes Datenobjekt heterogene Datentypen enthält.

Angenommen, Sie führen die folgende Anweisung aus, um die Matrix Multiplikation mithilfe von R durchzuführen. Sie multiplizieren eine einspaltige Matrix mit den drei Werten nach einem Array mit vier Werten und erwarten daher eine 4 x 3-Matrix.

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

Beachten Sie jedoch, was geschieht, wenn Sie die Größe des Arrays `y`ändern.

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

Warum? Da die beiden Argumente in diesem Fall als Vektoren derselben Länge behandelt werden können, gibt R das innere Produkt als Matrix zurück.  Dies ist das erwartete Verhalten gemäß der Regeln der linearen Algebra. Es kann jedoch Probleme verursachen, wenn die Downstream-Anwendung erwartet, dass das Ausgabeschema sich nie ändert!

> [!TIP]
> 
> Sie erhalten Fehler? Für diese Beispiele ist die Tabelle **rtestdata**erforderlich. Wenn Sie die Test Datentabelle noch nicht erstellt haben, kehren Sie zu diesem Thema zurück, um die Tabelle zu erstellen: [Behandeln von Eingaben und Ausgaben](../tutorials/rtsql-working-with-inputs-and-outputs.md).
> 
> Wenn Sie die Tabelle erstellt haben, aber trotzdem einen Fehler erhalten, stellen Sie sicher, dass Sie die gespeicherte Prozedur im Kontext der Datenbank ausführen, die die Tabelle enthält, nicht in der **Master** Datenbank oder in einer anderen Datenbank.
> 
> Außerdem wird empfohlen, für diese Beispiele keine temporären Tabellen zu verwenden. Einige R-Clients beenden eine Verbindung zwischen Batches und löschen temporäre Tabellen.

## <a name="merge-or-multiply-columns-of-different-length"></a>Zusammenführen oder Multiplizieren von Spalten mit unterschiedlicher Länge

R bietet hervorragend für die Arbeit mit Vektoren verschiedener Größen und für die Kombination dieser Spalten ähnlichen Strukturen in Datenrahmen. Vektorenlisten können aussehen wie eine Tabelle, aber sie befolgen nicht alle Regeln, die Datenbanktabellen steuern.

Zum Beispiel legt das folgende Skript ein numerisches Array der Länge 6 fest und speichert es in der R-Variable `df1`. Das numerische Array wird anschließend mit den ganzen Zahlen der rtestdata-Tabelle kombiniert, die drei (3) Werte enthält, um einen neuen Datenrahmen,, `df2`zu erstellen.

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

- SQL Server überträgt die Daten aus der Abfrage an den vom Launchpad-Dienst verwalteten R-Prozess und konvertiert ihn in eine interne Darstellung, um die Effizienz zu erhöhen.
- Die R-Laufzeit lädt die Daten in eine data.frame-Variable und führt ihre eigenen Vorgänge für die Daten aus.
- Die Datenbank-Engine gibt die Daten über eine sichere interne Verbindung an den SQL Server zurück und zeigt die Daten in Form von SQL Server-Datentypen.
- Sie rufen Sie Daten über eine Verbindung mit dem SQL Server mithilfe einer Client- oder Netzwerk-Bibliothek auf, die SQL-Abfragen und tabellarische Datensätze verarbeiten kann. Diese Clientanwendung kann die Daten auf andere Weise beeinträchtigen.

Um zu sehen, wie dies funktioniert, führen Sie eine Abfrage wie diese auf dem Data Warehouse " [AdventureWorksDW](https://github.com/Microsoft/sql-server-samples/releases/tag/adventureworks) " aus. In dieser Ansicht werden Verkaufsdaten zurückgegeben, die zum Erstellen von Prognosen verwendet werden.

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
> Sie können eine beliebige Version von AdventureWorks verwenden oder eine andere Abfrage mit einer eigenen Datenbank erstellen. Der Punkt ist der Versuch, einige Daten zu verarbeiten, die Text-, DateTime-und numerische Werte enthalten.

Versuchen Sie jetzt, diese Abfrage als Eingabe für die gespeicherte Prozedur einfügen.

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
+ Die Text Spalte "productseries" wurde als **Faktor**identifiziert, also eine kategorische Variable. Zeichenfolgenwerte werden standardmäßig als Faktoren verarbeitet. Wenn Sie R eine Zeichenfolge übergeben, wird diese in eine ganze Zahl für die interne Verwendung konvertiert und dann zurück in die Ausgabe der Zeichenfolge zugeordnet.

### <a name="summary"></a>Zusammenfassung

In diesen kurzen Beispielen sehen Sie, wie die Auswirkungen der Datenkonvertierung bei der Übergabe von SQL-Abfragen als Eingabe überprüft werden müssen. Da einige SQL Server-Datentypen von R nicht unterstützt werden, sollten Sie die folgenden Methoden zur Vermeidung von Fehlern in Erwägung gezogen

+ Testen Sie Ihre Daten im voraus, und überprüfen Sie die Spalten oder Werte in Ihrem Schema, die bei der Übergabe an R-Code ein Problem darstellen könnten.
+ Legen Sie Spalten in der Eingabedatenquelle einzeln fest, anstatt `SELECT *` zu verwenden, und verstehen Sie, wie jede Spalte verarbeitet wird.
+ Führen Sie explizite Umwandlungen nach Bedarf beim Vorbereiten der Eingabedaten durch, um Überraschungen zu vermeiden.
+ Vermeiden Sie das Übergeben von Datenspalten (z. b. GUIDs oder ROWGUIDS), die Fehler verursachen und nicht für die Modellierung nützlich sind.

Weitere Informationen zu unterstützten und nicht unterstützten Datentypen finden Sie unter [R-Bibliotheken und-Datentypen](../r/r-libraries-and-data-types.md).

Informationen zu den Auswirkungen der Lauf Zeit Konvertierung von Zeichen folgen in numerische Faktoren auf die Leistung finden Sie unter [SQL Server R Services Leistungs](../r/sql-server-r-services-performance-tuning.md)Optimierung.

## <a name="next-step"></a>Nächster Schritt

In der nächsten Schnellstartanleitung erfahren Sie, wie Sie R-Funktionen auf SQL Server Daten anwenden.

> [!div class="nextstepaction"]
> [Schnellstart: Verwenden von R-Funktionen mit SQL Server Daten](quickstart-r-functions.md)
