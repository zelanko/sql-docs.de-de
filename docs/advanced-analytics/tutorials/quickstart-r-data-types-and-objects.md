---
title: 'Schnellstart: R-Datentypen'
titleSuffix: SQL Server Machine Learning Services
description: In diesem Schnellstart lernen Sie, wie Sie mit Datentypen und Datenobjekten in R und SQL Server mit SQL Server Machine Learning Services arbeiten.
ms.prod: sql
ms.technology: machine-learning
ms.date: 10/04/2019
ms.topic: quickstart
author: garyericson
ms.author: garye
ms.reviewer: davidph
ms.custom: seo-lt-2019
monikerRange: '>=sql-server-2016||>=sql-server-linux-ver15||=sqlallproducts-allversions'
ms.openlocfilehash: 4dab7cca8edcc01052ced81ec33a1f411da7ba9a
ms.sourcegitcommit: 09ccd103bcad7312ef7c2471d50efd85615b59e8
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 11/07/2019
ms.locfileid: "73726979"
---
# <a name="quickstart-handle-data-types-and-objects-using-r-in-sql-server-machine-learning-services"></a>Schnellstart: Verarbeiten von Datentypen und Objekten mithilfe von R in SQL Server Machine Learning Services
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

In diesem Schnellstart erfahren Sie etwas über häufige Probleme, die beim Verschieben von Daten zwischen R und SQL Server auftreten. In dieser Übung sammeln Sie praktische Erfahrungen, die Ihnen eine gute Grundlage für die Arbeit mit Daten in Ihrem eigenen Skript bieten.

Diese häufig auftretenden Probleme sollten Sie im Vorfeld kennen:

- Datentypen stimmen manchmal nicht überein
- Es können implizite Konvertierungen auftreten
- Cast- und Convert-Vorgänge sind manchmal erforderlich
- R und SQL verwenden verschiedene Datenobjekte

## <a name="prerequisites"></a>Voraussetzungen

- Für diesen Schnellstart benötigen Sie Zugriff auf eine SQL Server-Instanz mit [SQL Server Machine Learning Services](../install/sql-machine-learning-services-windows-install.md), in der die R-Sprache installiert ist.

  Ihre SQL Server-Instanz kann sich auf einem virtuellen Azure-Computer oder einem lokalen Computer befinden. Achten Sie darauf, dass das externe Skripterstellungsfeature standardmäßig deaktiviert ist. Sie müssen die [externe Skripterstellung](../install/sql-machine-learning-services-windows-install.md#bkmk_enableFeature) also möglicherweise aktivieren und überprüfen, ob das **SQL Server-Launchpad** ausgeführt wird, bevor Sie beginnen.

- Außerdem benötigen Sie ein Tool zum Ausführen von SQL-Abfragen, die R-Skripts enthalten. Sie können diese Skripts mit einem beliebigen Tool für die Datenbankverwaltung oder -abfrage verwalten, sofern dieses eine Verbindung mit SQL Server-Instanzen herstellen und T-SQL-Abfragen oder gespeicherte Prozeduren ausführen kann. Für diesen Schnellstart wird [SQL Server Management Studio (SSMS)](https://docs.microsoft.com/sql/ssms/sql-server-management-studio-ssms) verwendet.

## <a name="always-return-a-data-frame"></a>Geben Sie immer einen Datenrahmen zurück

Wenn Ihr Skript Ergebnisse von R zum SQL Server zurückgibt, muss es die Daten als **data.frame** zurückgeben. Jede andere Objektart, die Sie in Ihrem Skript generieren –, d.h. eine Liste, ein Faktor, ein Vektor oder binäre Daten – müssen zu einem Datenrahmen konvertiert werden, wenn sie als Teil der gespeicherten Prozedurergebnisse ausgegeben werden sollen. Es gibt mehrere R-Funktionen, um die Änderung anderer Objekte zu einem Datenrahmen zu unterstützen. Sie können auch ein binäres Modell serialisieren und es in einen Datenrahmen zurückgeben. Mehr dazu erfahren Sie später in diesem Schnellstart.

Zunächst experimentieren wir mit einigen R-basierten R-Objekten, Vektoren, Matrizen und Listen – und sehen, wie die Konvertierung in einen Datenrahmen die Ausgabe an die SQL Server-Instanz ändert.

Vergleichen Sie diese beiden „Hallo Welt“-Skripts in R. Die Skripts sehen fast identisch aus, aber das erste gibt eine einzelne Spalte mit drei Werten zurück, während das zweite drei Spalten mit jeweils einem einzigen Wert zurückgibt.

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

## <a name="identify-schema-and-data-types"></a>Identifizieren von Schema- und Datentypen

Warum sind die Ergebnisse so unterschiedlich?

Die Antwort finden Sie in der Regel mithilfe des R-`str()`-Befehls. Fügen Sie die Funktion `str(object_name)` in Ihrem R-Skript hinzu, um das Datenschema des festgelegten R-Objekts als Informationsmeldung zurückzugeben. Nachrichten finden Sie unter **Nachrichten**, im Bereich des Visual Studio-Code oder unter der **Nachrichten**-Registerkarte in SSMS.

Um zu ermitteln, warum Beispiel 1 und Beispiel 2 solch unterschiedliche Ergebnisse haben, fügen Sie die Zeile `str(OutputDataSet)` am Ende der _@script_ -Variablendefinition in jeder Anweisung, wie folgt ein:

**Beispiel 1 mit hinzugefügter str-Funktion**

```sql
EXECUTE sp_execute_external_script
        @language = N'R'
      , @script = N' mytextvariable <- c("hello", " ", "world");
      OutputDataSet <- as.data.frame(mytextvariable);
      str(OutputDataSet);'
      , @input_data_1 = N'  '
;
```

**Beispiel 2 mit hinzugefügter str-Funktion**

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

Wie Sie sehen können, hatte eine geringfügige Änderung in der R-Syntax einen großen Einfluss auf das Schema der Ergebnisse. Wir gehen nicht näher auf den Grund dafür ein, da die Unterschiede der R-Datentypen detaillierter im Abschnitt *Data Structures (Datenstrukturen)* des Artikels [„Advanced R“ von Hadley Wickham](http://adv-r.had.co.nz) erläutert werden.

Jetzt müssen Sie nur Bedenken, dass Sie die erwarteten Ergebnisse überprüfen müssen, wenn Sie R-Objekte in Datenrahmen umwandeln müssen.

> [!TIP]
> Sie können auch R-Identitätsfunktionen wie `is.matrix`, `is.vector`, verwenden, um Informationen über die interne Datenstruktur zurückzugeben.

## <a name="implicit-conversion-of-data-objects"></a>Implizite Konvertierung von Datenobjekten

Jedes R-Datenobjekt verfügt über seine eigenen Regeln darüber, wie Werte verarbeitet werden, wenn sie mit anderen Datenobjekten kombiniert werden, sofern die beiden Datenobjekte über die gleiche Anzahl an Dimensionen verfügen oder jedes Datenobjekt heterogene Datentypen enthält.

Erstellen Sie zunächst eine kleine Tabelle mit Testdaten.

```sql
CREATE TABLE RTestData (col1 INT NOT NULL)

INSERT INTO RTestData
VALUES (1);

INSERT INTO RTestData
VALUES (10);

INSERT INTO RTestData
VALUES (100);
GO
```

Nehmen wir beispielsweise an, dass Sie die folgende Anweisung zur Matrixmultiplikation mit R ausführen. Sie vervielfältigen eine einspaltige Matrix mit den drei Werten durch ein Array mit vier Werten und erwarten daher, dass eine 4 x 3-Matrix entsteht.

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

Beachten Sie jedoch, was geschieht, wenn Sie die Größe des Arrays `y` ändern.

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

Warum? In diesem Fall, gibt R das innere Produkt als Matrix zurück, da die beiden Argumente als Vektoren derselben Länge verarbeitet werden können.  Dies ist das erwartete Verhalten gemäß der Regeln der linearen Algebra. Es kann jedoch Probleme verursachen, wenn die Downstream-Anwendung erwartet, dass das Ausgabeschema sich nie ändert!

> [!TIP]
> 
> Erhalten Sie Fehler? Stellen Sie sicher, dass Sie die gespeicherte Prozedur im Kontext der Datenbank ausführen, die die Tabelle enthält, und nicht in **Master** oder einer anderen Datenbank.
>
> Außerdem wird empfohlen, für diese Beispiele keine temporären Tabellen zu verwenden. Einige R-Clients beenden eine Verbindung zwischen Batches und löschen temporäre Tabellen.

## <a name="merge-or-multiply-columns-of-different-length"></a>Zusammenführen oder Multiplizieren von Spalten mit unterschiedlicher Länge

R bietet ein hohes Maß an Flexibilität für die Arbeit mit Vektoren verschiedener Größen und für die Kombination dieser spaltenähnlichen Strukturen in Datenrahmen. Vektorenlisten können aussehen wie eine Tabelle, aber sie befolgen nicht alle Regeln, die Datenbanktabellen steuern.

Zum Beispiel legt das folgende Skript ein numerisches Array der Länge 6 fest und speichert es in der R-Variable `df1`. Das numerische Array wird anschließend mit den ganzen Zahlen der RTestData-Tabelle kombiniert, die drei Werte enthält, um einen neuen Datenrahmen, `df2`, zu erstellen.

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

- SQL Server überträgt die Daten aus der Abfrage an den vom Launchpad-Dienst verwalteten R-Prozess und konvertiert sie in eine interne Darstellung zur Effizienzsteigerung.
- Die R-Laufzeit lädt die Daten in eine data.frame-Variable und führt ihre eigenen Vorgänge für die Daten aus.
- Die Datenbank-Engine gibt die Daten über eine sichere interne Verbindung an den SQL Server zurück und zeigt die Daten in Form von SQL Server-Datentypen.
- Sie rufen Sie Daten über eine Verbindung mit dem SQL Server mithilfe einer Client- oder Netzwerk-Bibliothek auf, die SQL-Abfragen und tabellarische Datensätze verarbeiten kann. Diese Clientanwendung kann die Daten auf andere Weise beeinträchtigen.

Um zu sehen, wie dies funktioniert, führen Sie eine Abfrage, wie diese im Datawarehouse [AdventureWorksDW](https://github.com/Microsoft/sql-server-samples/releases/tag/adventureworks) durch. In dieser Ansicht werden Verkaufsdaten zurückgegeben, die zum Erstellen von Prognosen verwendet werden.

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
> Sie können eine beliebige Version von AdventureWorks verwenden oder eine andere Abfrage mit einer eigenen Datenbank erstellen. Es geht darum zu versuchen, einige Daten mit Text, Datum/Uhrzeit und numerischen Werten zu verarbeiten.

Versuchen Sie jetzt, diese Abfrage als Eingabe für die gespeicherte Prozedur einzufügen.

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

- Die datetime-Spalte wurde als R-Datentyp **POSIXct** verarbeitet.
- Die Text-Spalte „ProductSeries“ wurde als ein **Faktor** erkannt, d.h. eine kategorische Variable. Zeichenfolgenwerte werden standardmäßig als Faktoren verarbeitet. Wenn Sie R eine Zeichenfolge übergeben, wird diese in eine ganze Zahl für die interne Verwendung konvertiert und dann zurück in die Ausgabe der Zeichenfolge zugeordnet.

### <a name="summary"></a>Zusammenfassung

Aus diesen kurzen Beispielen können Sie ersehen, dass die Auswirkungen der Datenkonvertierung überprüft werden müssen, wenn SQL-Abfragen als Eingabe übergeben werden. Da einige SQL Server-Datentypen von R nicht unterstützt werden, ziehen Sie die folgenden Methoden in Betracht, um Fehler zu vermeiden:

- Testen Sie die Daten im Voraus, und überprüfen Sie Spalten oder Werte in Ihrem Schema, die ein Problem darstellen können, wenn sie dem R-Code übergeben werden.
- Legen Sie Spalten in der Eingabedatenquelle einzeln fest, anstatt `SELECT *` zu verwenden, und verstehen Sie, wie jede Spalte verarbeitet wird.
- Führen Sie explizite Umwandlungen nach Bedarf beim Vorbereiten der Eingabedaten durch, um Überraschungen zu vermeiden.
- Vermeiden Sie das Übergeben von Datenspalten (z. B. GUIDs oder RowGUIDS), die Fehler verursachen und nicht für die Modellierung nützlich sind.

Weitere Informationen zu unterstützten und nicht unterstützten Datentypen finden Sie unter [R-Bibliotheken und -Datentypen](../r/r-libraries-and-data-types.md).

Informationen über die Leistungseinbußen bei der Laufzeitkonvertierung von Zeichenfolgen zu numerischen Faktoren finden Sie unter [Leistungsoptimierung für SQL Server R Services](../r/sql-server-r-services-performance-tuning.md).

## <a name="next-steps"></a>Nächste Schritte

Weitere Informationen zum Schreiben von erweiterten R-Funktionen in SQL Server finden Sie in diesem Schnellstart:

> [!div class="nextstepaction"]
> [Schreiben erweiterter R-Funktionen mit SQL Server Machine Learning Services](quickstart-r-functions.md)

Weitere Informationen zur Verwendung von R in SQL Server Machine Learning Services finden Sie in den folgenden Artikeln:

- [Erstellen und Bewerten eines Vorhersagemodells in R mit SQL Server Machine Learning Services](quickstart-r-train-score-model.md)
- [Was ist SQL Server Machine Learning Services (Python und R)?](../what-is-sql-server-machine-learning.md)
