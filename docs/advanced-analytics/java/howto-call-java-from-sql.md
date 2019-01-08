---
title: 'Gewusst wie: Aufrufen von Java aus SQL – SQL Server Machine Learning Services'
description: Erfahren Sie, wie Sie Java-Klassen von SQL Server gespeicherte Prozeduren, die mit der Programmiersprache Java programming Language-Erweiterung in SQL Server-2019 aufrufen.
ms.prod: sql
ms.technology: machine-learning
ms.date: 12/07/2018
ms.topic: conceptual
author: HeidiSteen
ms.author: heidist
manager: cgronlun
monikerRange: '>=sql-server-ver15||=sqlallproducts-allversions'
ms.openlocfilehash: 438c1096a933932e08c5cbf21722ba75874bb1dc
ms.sourcegitcommit: ee76332b6119ef89549ee9d641d002b9cabf20d2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/20/2018
ms.locfileid: "53644759"
---
# <a name="how-to-call-java-from-sql-server-2019-preview"></a>Gewusst wie: Aufrufen von Java aus SQL Server-2019 (Vorschau)

Bei Verwendung der [Java-spracherweiterung](extension-java.md), [Sp_execute_external_script](https://docs.microsoft.com/sql/relational-databases/system-stored-procedures/sp-execute-external-script-transact-sql) System gespeicherte Prozedur ist die Schnittstelle zum Aufrufen von Java Runtime verwendet. Berechtigungen für die Datenbank gelten für Ausführung von Java-Code.

Dieser Artikel beschreibt die Implementierungsdetails für Java-Klassen und Methoden, die auf SQL Server ausführen. Sobald Sie mit diesen Einzelheiten vertraut sind, überprüfen Sie die [Java-Beispiel](java-first-sample.md) im nächsten Schritt.

## <a name="basic-principles"></a>Grundlegende Prinzipien

* Kompilierte benutzerdefinierte Java-Klassen müssen in der class-Dateien oder JAR-Dateien in Ihren Java-Klassenpfad vorhanden sein. Die [CLASSPATH Parameter](#set-classpath) enthält den Pfad zu der kompilierten Java-Dateien. 

* Die Java-Methode, die Sie aufrufen, muss in der "Script"-Parameter für die gespeicherte Prozedur angegeben werden.

* Wenn die Klasse zu einem Paket gehört, muss der "Paketname" bereitgestellt werden.

* "Params" wird zum Übergeben von Parametern an eine Java-Klasse. Aufrufen einer Methode, die Argumente erfordert wird nicht unterstützt Parameter, die einzige Möglichkeit, Argumentwerte an die Methode übergeben werden. 

> [!Note]
> In diesem Hinweis restates unterstützten und nicht unterstützten Vorgänge, die spezifisch für Java in CTP-Version 2.x.
> * Bei der gespeicherten Prozedur werden die Eingabeparameter unterstützt. Output-Parameter sind nicht auf.
> * Streaming mit dem Parameter Sp_execute_external_script **@r_rowsPerRead** wird nicht unterstützt.
> * Partitionierung mit **@input_data_1_partition_by_columns** wird nicht unterstützt.
> * Parallele Verarbeitung mit  **@parallel= 1** wird unterstützt.

## <a name="call-spexecuteexternalscript"></a>Aufrufen von sp_execute_external_script

Sowohl Windows und Linux, die für die [Sp_execute_external_script](https://docs.microsoft.com/sql/relational-databases/system-stored-procedures/sp-execute-external-script-transact-sql) System gespeicherte Prozedur ist die Schnittstelle zum Aufrufen von Java Runtime verwendet. Das folgende Beispiel zeigt eine Sp_execute_external_script mit Java-Erweiterung, und denselben Parametern für die Angabe von Pfad, Skripts und Ihren benutzerdefinierten Code.

```sql
DECLARE @myClassPath nvarchar(30)
DECLARE @param1 int

SET @myClassPath = N'/<my path>/program.jar'
SET @param1 = 3

EXEC sp_execute_external_script
  @language = N'Java'
, @script = N'<packageName>.<ClassName>.<methodName>'
, @input_data_1 = N'<Input Query>
, @params = N'@CLASSPATH nvarchar(30), @param1 INT'
, @CLASSPATH = @myClassPath
, @param1 = @param1
```

<a name="set-classpath"></a>

## <a name="set-classpath"></a>Legen Sie CLASSPATH

Sobald Sie Ihre Java-Klasse oder Klassen kompiliert und die .class Dateien oder den JAR-Dateien in Ihre Java-Classpath platziert haben, haben Sie zwei Optionen für die Bereitstellung der SQL Server-Java-Erweiterung in des Klassenpfads:

**Option 1: Als Parameter übergeben**

Ein Ansatz für die Angabe eines Pfads in kompiliertem Code ist durch Festlegen des KLASSENPFADS als Eingabeparameter an die Prozedur Sp_execute_external_script. Die [Java-Beispiel](java-first-sample.md#call-method) wird diese Technik veranschaulicht. Wenn Sie diesen Ansatz wählen und mehrere Pfade umfassen, achten Sie darauf, dass Sie das Pfadtrennzeichen zu verwenden, das für das zugrunde liegende Betriebssystem gültig ist:

* Trennen Sie die Pfade in den KLASSENPFAD unter Linux mit Doppelpunkt ":".
* Auf Windows, trennen Sie die Pfade in CLASSPATH mit einem Semikolon ";"

**Option 2: Registrieren Sie eine Systemvariable**

Ebenso, wie Sie eine Systemvariable für das JDK ausführbare Dateien erstellt haben, können Sie eine Systemvariable für Codepfade erstellen. Erstellt eine Systemumgebungsvariable "CLASSPATH" dazu

## <a name="class-requirements"></a>Klasse von Anforderungen

In der Reihenfolge für die SQL Server mit der Java Runtime kommunizieren müssen Sie bestimmte statische Variablen in Ihrer Klasse implementieren. SQL Server kann dann eine Methode in den Java-Klasse und Exchange Daten mithilfe der Java-Sprache-Erweiterung ausgeführt werden.

> [!Note]
> Erwarten Sie die Details der Implementierung in zukünftigen CTPs zu ändern, wie wir arbeiten an um die Oberfläche für Entwickler zu verbessern.

## <a name="method-requirements"></a>Anforderungen an die Methode
Um Argumente zu übergeben, verwenden die **@param** Parameter in Sp_execute_external_script. Die Methode selbst keine Argumente. Der Rückgabetyp muss "void" sein.  

```java
public static void test()  {}
```

## <a name="data-inputs"></a>Verweisdateneingaben 

In diesem Abschnitt wird erläutert, wie Daten aus einer SQL Server-Abfrage mit Java übertragen **"inputdataset"** in Sp_execute_external_script.

Für jede Eingabespalte, die Ihre SQL-Abfrage in Java pusht, müssen Sie ein Array zu deklarieren.

### <a name="inputdatacol"></a>inputDataCol

In der aktuellen Version der Java-Erweiterung die **InputDataColN** Variable ist erforderlich, wobei *N* ist die Nummer der Spalte. 

```java
public static <type>[] inputDataColN = new <type>[1]
```

Diese Arrays müssen initialisiert werden (die Größe des Arrays muss größer als 0 sein und muss nicht die tatsächliche Länge der Spalte entsprechen).

Beispiel: `public static int[] inputDataCol1 = new int[1];`

Mit den Daten aus einer SQL Server-Abfrage vor der Ausführung von Java-Programm, dass Sie aufrufen, werden diese Arrayvariablen aufgefüllt werden.

### <a name="inputnullmap"></a>inputNullMap

NULL-Zuordnung wird von der Erweiterung verwendet, Sie wissen, welche Werte null sind. Diese Variable wird mit Informationen zu null-Werte von SQL Server vor der Ausführung der Benutzerfunktion aufgefüllt.

Der Benutzer muss nur zum Initialisieren dieser Variablen (und die Größe des Arrays muss größer als 0 sein).

```java
public static boolean[][] inputNullMap = new boolean[1][1];
```

## <a name="data-outputs"></a>-Ausgaben 

In diesem Abschnitt wird beschrieben, **"outputdataset"**, die Ausgabe-Datasets, die von Java, die Sie zum Senden und beibehalten, die in SQL Server zurückgegeben.

> [!Note]
> Ausgabeparameter in [Sp_execute_external_script](https://docs.microsoft.com/sql/relational-databases/system-stored-procedures/sp-execute-external-script-transact-sql) werden in dieser Version nicht unterstützt.

### <a name="outputdatacoln"></a>outputDataColN

Ähnlich wie **"inputdataset"**, für jede Ausgabespalte, die Ihre Java-Programm wieder nach SQL Server sendet, müssen Sie deklarieren eine Arrayvariable. Alle **OutputDataCol** Arrays sollte die gleiche Länge aufweisen. Sie müssen sicherstellen, dass dies mit der Zeit, die die Klasse Ausführung abgeschlossen ist, initialisiert wird.

```java
public static <type>[] outputDataColN = new <type>[]
```

### <a name="numberofoutputcols"></a>numberofOutputCols

Legen Sie diese Variable, um die Anzahl der Spalten der Ausgabe-Daten, die Sie erwarten, wenn die Funktion die Ausführung beendet.

```java
public static short numberofOutputCols = <expected number of output columns>;
```

### <a name="outputnullmap"></a>outputNullMap

NULL-Zuordnung wird von der Erweiterung verwendet, um anzugeben, welche Werte null sind. Wir werden dies erfordert, da primitive Typen null nicht unterstützt. Derzeit muss auch die Zuordnung null für Zeichenfolgen-Datentypen, auch wenn Zeichenfolgen als null sein können. NULL-Werte werden durch "True" gekennzeichnet.

Diese NullMap muss aktualisiert werden, mit der erwarteten Anzahl von Spalten und Zeilen, die Sie an SQL Server zurückgeben.

```java
public static boolean[][] outputNullMap
```
<a name="create-external-library"></a>


## <a name="next-steps"></a>Nächste Schritte

+ [Java-Beispiel in SQL Server](java-first-sample.md)
+ [Java und SQL Server-Datentypen](java-sql-datatypes.md)
+ [Java-spracherweiterung in SQL Server](extension-java.md)
