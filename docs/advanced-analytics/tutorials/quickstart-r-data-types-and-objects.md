---
title: 'Schnellstart: R-Datenstrukturen, -Datentypen und -Objekte'
description: In dieser Schnellstartanleitung erfahren Sie, wie Sie Datenstrukturen, Datentypen und Objekte bei Verwendung von R in SQL Server Machine Learning Services verwenden können. Sie erhalten Informationen zum Verschieben von Daten zwischen R und SQL Server und zu Fehlern, die in diesem Zusammenhang häufig auftreten.
ms.prod: sql
ms.technology: machine-learning
ms.date: 01/27/2019
ms.topic: quickstart
author: garyericson
ms.author: garye
ms.reviewer: davidph
ms.custom: seo-lt-2019
monikerRange: '>=sql-server-2016||>=sql-server-linux-ver15||=sqlallproducts-allversions'
ms.openlocfilehash: a3f978865d2fdd643650a7c7308adb65d2c79fa7
ms.sourcegitcommit: b2e81cb349eecacee91cd3766410ffb3677ad7e2
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/01/2020
ms.locfileid: "76916404"
---
# <a name="quickstart-data-structures-data-types-and-objects-using-r-in-sql-server-machine-learning-services"></a>Schnellstart: Datenstrukturen, Datentypen und Objekte bei Verwendung von R in SQL Server Machine Learning Services
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

In dieser Schnellstartanleitung erfahren Sie, wie Sie Datenstrukturen, und Datentypen bei Verwendung von R in SQL Server Machine Learning Services verwenden können. Sie erhalten Informationen zum Verschieben von Daten zwischen R und SQL Server und zu Fehlern, die in diesem Zusammenhang häufig auftreten.

Diese häufig auftretenden Probleme sollten Sie im Vorfeld kennen:

- Datentypen stimmen manchmal nicht überein
- Es können implizite Konvertierungen auftreten
- Umwandlungs- und Konvertierungsvorgänge sind ggf. erforderlich
- Für R und SQL werden unterschiedliche Datenobjekte genutzt

## <a name="prerequisites"></a>Voraussetzungen

- Für diesen Schnellstart benötigen Sie Zugriff auf eine SQL Server-Instanz mit [SQL Server Machine Learning Services](../install/sql-machine-learning-services-windows-install.md), in der die R-Sprache installiert ist.

  Ihre SQL Server-Instanz kann sich auf einem virtuellen Azure-Computer oder einem lokalen Computer befinden. Achten Sie darauf, dass das externe Skripterstellungsfeature standardmäßig deaktiviert ist. Sie müssen die [externe Skripterstellung](../install/sql-machine-learning-services-windows-install.md#bkmk_enableFeature) also möglicherweise aktivieren und überprüfen, ob das **SQL Server-Launchpad** ausgeführt wird, bevor Sie beginnen.

- Außerdem benötigen Sie ein Tool zum Ausführen von SQL-Abfragen, die R-Skripts enthalten. Sie können diese Skripts mit einem beliebigen Tool für die Datenbankverwaltung oder -abfrage verwalten, sofern dieses eine Verbindung mit SQL Server-Instanzen herstellen und T-SQL-Abfragen oder gespeicherte Prozeduren ausführen kann. Für diesen Schnellstart wird [SQL Server Management Studio (SSMS)](https://docs.microsoft.com/sql/ssms/sql-server-management-studio-ssms) verwendet.

## <a name="always-return-a-data-frame"></a>Geben Sie immer einen Datenrahmen zurück

Wenn Ihr Skript Ergebnisse von R zum SQL Server zurückgibt, muss es die Daten als **data.frame** zurückgeben. Jede andere Objektart, die Sie in Ihrem Skript generieren –, d.h. eine Liste, ein Faktor, ein Vektor oder binäre Daten – müssen zu einem Datenrahmen konvertiert werden, wenn sie als Teil der gespeicherten Prozedurergebnisse ausgegeben werden sollen. Glücklicherweise gibt es mehrere R-Funktionen zur Unterstützung von sich ändernden Objekten in einem Datenrahmen. Sie können auch ein binäres Modell serialisieren und es in einen Datenrahmen zurückgeben. Mehr dazu erfahren Sie später in diesem Schnellstart.

Zunächst experimentieren wir mit einigen R-basierten R-Objekten, Vektoren, Matrizen und Listen – und sehen, wie die Konvertierung in einen Datenrahmen die Ausgabe an die SQL Server-Instanz ändert.

Vergleichen Sie diese beiden „Hallo Welt“-Skripts in R. Die Skripts sehen fast identisch aus, aber das erste gibt eine einzelne Spalte mit drei Werten zurück, während das zweite drei Spalten mit jeweils einem einzigen Wert zurückgibt.

**Beispiel 1**

```sql
EXECUTE sp_execute_external_script
       @language = N'R'
     , @script = N' mytextvariable <- c("hello", " ", "world");
       OutputDataSet <- as.data.frame(mytextvariable);'
     , @input_data_1 = N' ';
```

**Beispiel 2**

```sql
EXECUTE sp_execute_external_script
        @language = N'R'
      , @script = N' OutputDataSet<- data.frame(c("hello"), " ", c("world"));'
      , @input_data_1 = N'  ';
```

## <a name="identify-schema-and-data-types"></a>Identifizieren von Schema- und Datentypen

Warum sind die Ergebnisse so unterschiedlich?

Die Antwort kann normalerweise mit dem R-Befehl `str()` ermittelt werden. Fügen Sie die Funktion `str(object_name)` an einer beliebigen Stelle in Ihrem R-Skript hinzu, damit das Datenschema des angegebenen R-Objekts als Informationsnachricht zurückgegeben wird. Nachrichten finden Sie unter **Nachrichten**, im Bereich des Visual Studio-Code oder unter der **Nachrichten**-Registerkarte in SSMS.

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

Überprüfen Sie nun den Text unter **Nachrichten**, um zu ermitteln, warum sich die Ausgabe unterscheidet.

**Ergebnisse: Beispiel 1**

```sql
STDOUT message(s) from external script:
'data.frame':   3 obs. of  1 variable:
$ mytextvariable: Factor w/ 3 levels " ","hello","world": 2 1 3
```

**Ergebnisse: Beispiel 2**

```sql
STDOUT message(s) from external script:
'data.frame':   1 obs. of  3 variables:
$ c..hello..: Factor w/ 1 level "hello": 1
$ X...      : Factor w/ 1 level " ": 1
$ c..world..: Factor w/ 1 level "world": 1
```

Sie sehen, dass eine geringfügige Änderung der R-Syntax eine große Auswirkung auf das Schema mit den Ergebnissen hat. Wir gehen nicht näher auf den Grund dafür ein, da die Unterschiede der R-Datentypen detaillierter im Abschnitt *Data Structures (Datenstrukturen)* des Artikels [„Advanced R“ von Hadley Wickham](http://adv-r.had.co.nz) erläutert werden.

Vorerst sollten Sie nur bedenken, dass Sie die erwarteten Ergebnisse überprüfen sollten, wenn Sie für R-Objekte Datenrahmen verwenden.

> [!TIP]
> Sie können auch R-Identitätsfunktionen wie `is.matrix`, `is.vector`, verwenden, um Informationen über die interne Datenstruktur zurückzugeben.

## <a name="implicit-conversion-of-data-objects"></a>Implizite Konvertierung von Datenobjekten

Jedes R-Datenobjekt verfügt über eigene Regeln zur Verarbeitung von Werten, wenn diese mit anderen Datenobjekten kombiniert werden. Es wird auch überprüft, ob die beiden Datenobjekte die gleiche Anzahl von Dimensionen aufweisen oder ob ein Datenobjekt heterogene Datentypen enthält.

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

Im Hintergrund wird die Spalte mit drei Werten in eine Matrix mit einer Spalte konvertiert. Da eine Matrix lediglich einen Sonderfall eines Arrays in R darstellt, wird das Array `y` implizit in eine Matrix mit nur einer Spalte umgewandelt, damit die beiden Argumente konform sind.

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

R gibt jetzt einen einzelnen Wert als Ergebnis zurück.

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

## <a name="merge-or-multiply-columns-of-different-length"></a>Zusammenführen oder Multiplizieren von Spalten unterschiedlicher Länge

R bietet ein hohes Maß an Flexibilität für die Arbeit mit Vektoren verschiedener Größen und für die Kombination dieser spaltenähnlichen Strukturen in Datenrahmen. Die Liste mit den Vektoren kann wie eine Tabelle aussehen, aber es werden nicht alle Regeln eingehalten, die für Datenbanktabellen gelten.

Mit dem folgenden Skript wird beispielsweise ein numerisches Array der Länge 6 definiert und unter der R-Variablen `df1` gespeichert. Das numerische Array wird anschließend mit den ganzen Zahlen der RTestData-Tabelle kombiniert, die drei Werte enthält, um einen neuen Datenrahmen, `df2`, zu erstellen.

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

Zum Ausfüllen des Datenrahmens wiederholt R die aus „RTestData“ abgerufenen Elemente so oft wie nötig, um die gleiche Anzahl von Elementen wie im Array `df1` zu erzielen.

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
- Die R-Runtime lädt die Daten in eine data.frame-Variable und führt eigene Vorgänge für die Daten durch.
- Die Datenbank-Engine gibt die Daten über eine sichere interne Verbindung an den SQL Server zurück und zeigt die Daten in Form von SQL Server-Datentypen.
- Sie rufen Sie Daten über eine Verbindung mit dem SQL Server mithilfe einer Client- oder Netzwerk-Bibliothek auf, die SQL-Abfragen und tabellarische Datensätze verarbeiten kann. Diese Clientanwendung kann sich unter Umständen auch auf andere Art und Weise auf die Daten auswirken.

Um zu sehen, wie dies funktioniert, führen Sie eine Abfrage, wie diese im Datawarehouse [AdventureWorksDW](https://github.com/Microsoft/sql-server-samples/releases/tag/adventureworks) durch. In dieser Ansicht werden Verkaufsdaten zurückgegeben, die zum Erstellen von Vorhersagen verwendet werden.

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

Wenn Sie einen Fehler erhalten, müssen Sie unter Umständen einige Änderungen am Abfragetext vornehmen. Beispielsweise muss das Zeichenfolgenprädikat in der WHERE-Klausel doppelt in einfache Anführungszeichen gesetzt werden.

Wenn die Abfrage funktioniert, sollten Sie sich die Ergebnisse der `str`-Funktion ansehen, um zu ermitteln, wie die Eingabedaten von R verarbeitet werden.

**Ergebnisse**

```sql
STDOUT message(s) from external script: 'data.frame':    37 obs. of  3 variables:
STDOUT message(s) from external script: $ ReportingDate: POSIXct, format: "2010-12-24 23:00:00" "2010-12-24 23:00:00"
STDOUT message(s) from external script: $ ProductSeries: Factor w/ 1 levels "M200 Europe",..: 1 1 1 1 1 1 1 1 1 1
STDOUT message(s) from external script: $ Amount       : num  3400 16925 20350 16950 16950
```

- Die Spalte für Datums-/Uhrzeitangaben wurde mit dem R-Datentyp **POSIXct** verarbeitet.
- Die Text-Spalte „ProductSeries“ wurde als ein **Faktor** erkannt, d.h. eine kategorische Variable. Zeichenfolgenwerte werden standardmäßig als Faktoren verarbeitet. Wenn Sie eine Zeichenfolge an R übergeben, wird sie in eine ganze Zahl für die interne Verwendung konvertiert und in der Ausgabe dann wieder der Zeichenfolge zugeordnet.

### <a name="summary"></a>Zusammenfassung

Aus diesen kurzen Beispielen können Sie ersehen, dass die Auswirkungen der Datenkonvertierung überprüft werden müssen, wenn SQL-Abfragen als Eingabe übergeben werden. Da einige SQL Server-Datentypen von R nicht unterstützt werden, ziehen Sie die folgenden Methoden in Betracht, um Fehler zu vermeiden:

- Testen Sie die Daten im Voraus, und überprüfen Sie Spalten oder Werte in Ihrem Schema, die ein Problem darstellen können, wenn sie dem R-Code übergeben werden.
- Geben Sie Spalten in Ihrer Eingabedatenquelle einzeln an, anstatt `SELECT *` zu verwenden, und machen Sie sich damit vertraut, wie die einzelnen Spalten verarbeitet werden.
- Führen Sie nach Bedarf explizite Umwandlungen durch, wenn Sie Ihre Eingabedaten vorbereiten, um Überraschungen zu vermeiden.
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
