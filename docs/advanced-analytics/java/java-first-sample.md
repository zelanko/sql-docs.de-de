---
title: Java-spracherweiterung in SQL Server-2019 | Microsoft-Dokumentation
description: Führen Sie Java-Code, mit der Java-Sprache-Erweiterung von SQL Server 2019.
ms.prod: sql
ms.technology: machine-learning
ms.date: 09/24/2018
ms.topic: conceptual
author: HeidiSteen
ms.author: heidist
manager: cgronlun
monikerRange: '>=sql-server-ver15||=sqlallproducts-allversions'
ms.openlocfilehash: bf6fec32e28342e355b3393bb531ad1833d8af6b
ms.sourcegitcommit: b7fd118a70a5da9bff25719a3d520ce993ea9def
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/24/2018
ms.locfileid: "46715316"
---
# <a name="sql-server-java-sample-walkthrough"></a>Exemplarische Vorgehensweise zum SQL Server-Java

Dieses Beispiel zeigt eine Java-Klasse, die zwei Spalten ("ID" und "Text") von SQL Server empfängt und zwei Spalten wieder nach SQL Server ("ID" und "Ngram") zurückgegeben. Für einen angegebenen ID und die Zeichenfolgenkombination generiert den Code für Permutationen von Ngrams (Teilzeichenfolgen), die diese Permutationen zusammen mit der ursprünglichen-ID zurückgeben Die Länge der Ngram wird durch einen Parameter gesendet, um die Java-Klasse definiert.

## <a name="prerequisites"></a>Erforderliche Komponenten

+ SQL Server-2019-Datenbank-Engine-Instanz mit dem Extensibility Framework und Java-Erweiterung [auf Windows](../install/sql-machine-learning-services-windows-install.md) oder [unter Linux](https://docs.microsoft.com/sql/linux/sql-server-linux-setup). Weitere Informationen zur Systemkonfiguration von finden Sie unter [Java-spracherweiterung in SQL Server-2019](extension-java.md). Weitere Informationen zum Schreiben von Code Anforderungen finden Sie unter [das Aufrufen von Java in SQL Server](howto-call-java-from-sql.md).

+ SQL Server Management Studio oder ein anderes Tool für die Ausführung von T-SQL.

+ Java SE Development Kit (JDK) 1.10 auf Windows oder JDK 1.8 unter Linux.

Befehlszeilencompiler verwenden **Javac** ist für dieses Tutorial ausreichend. 

## <a name="1---load-sample-data"></a>1: Laden von Beispieldaten

Zuerst erstellen und Auffüllen einer *überprüft* -Tabelle mit **ID** und **Text** Spalten. Verbinden mit SQL Server, und führen Sie das folgende Skript zum Erstellen einer Tabelle:

```sql
DROP TABLE IF exists reviews;
GO
CREATE TABLE reviews(
    id int NOT NULL,
    "text" nvarchar(30) NOT NULL)

INSERT INTO reviews(id, "text") VALUES (1, 'AAA BBB CCC DDD EEE FFF')
INSERT INTO reviews(id, "text") VALUES (2, 'GGG HHH III JJJ KKK LLL')
INSERT INTO reviews(id, "text") VALUES (3, 'MMM NNN OOO PPP QQQ RRR')
GO
```

## <a name="2---class-ngramjava"></a>2 - Class-Ngram.java

Zunächst erstellen die Hauptklasse. Dies ist die erste von drei Klassen.

In diesem Schritt erstellen Sie eine Klasse namens **Ngram.java** , und kopieren Sie die folgenden Java-Code in diese Datei. 


```java
//We will package our classes in a package called pkg
//Packages are option in Java-SQL, but required for this sample.
package pkg;

import java.util.List;
import java.util.stream.Collectors;
import java.util.stream.IntStream;

public class Ngram {

    //Required: This is only required if you are passing data in @input_data_1
    //from SQL Server in sp_execute_external_script
    public static int[] inputDataCol1 = new int[1];
    public static String[] inputDataCol2 = new String[1];

    //Required: Input null map. Size just needs to be set to "1"
    public static boolean[][] inputNullMap = new boolean[1][1];

    //Required: Output data columns returned back to SQL Server
    public static int[] outputDataCol1;
    public static String[] outputDataCol2;

    //Required: Output null map. Is populated with true or false values 
    //to indicate nulls
    public static boolean[][] outputNullMap;

    //Optional: This is only required if parameters are passed with @params
    // from SQL Server in sp_execute_external_script
    // n is giving us the size of ngram substrings
    public static int param1;

    //Optional: The number of rows we will be returning
    public static int numberOfRows;

    //Required: Number of output columns returned
    public static short numberOfOutputCols;

    /*Java main method - Only for testing purposes outside of SQL Server
    public static void main(String... args) {
        //getNGrams();
    }*/

    //This is the method we will be calling from SQL Server
    public static void getNGrams() {

        System.out.println("inputDataCol1.length= "+ inputDataCol1.length);
        if (inputDataCol1.length == 0 ) {
            // TODO: Set empty return
            return;
        }
        //Using a stream to "loop" over the input data inputDataCol1.length. You can also use a for loop for this.
        final List<InputRow> inputDataSet = IntStream.range(0, inputDataCol1.length)
                .mapToObj(i -> new InputRow(inputDataCol1[i], inputDataCol2[i]))
                .collect(Collectors.toList());


        //Again, we are using a stream to loop over data
        final List<OutputRow> outputDataSet = inputDataSet.stream()
                // Generate ngrams of size n for each incoming string
                // Each invocation of ngrams returns a list. flatMap flattens
                // the resulting list-of-lists to a flat list.
                .flatMap(inputRow -> ngrams(param1, inputRow.text).stream().map(s -> new OutputRow(inputRow.id, s)))
                .collect(Collectors.toList());

        //Print the outputDataSet
        System.out.println(outputDataSet);

        //Set the number of rows and columns we will be returning
        numberOfOutputCols = 2;
        numberOfRows = outputDataSet.size();
        outputDataCol1 = new int[numberOfRows]; // ID column
        outputDataCol2 = new String[numberOfRows]; //The ngram column
        outputNullMap = new boolean[2][numberOfRows];// output null map

        //Since we don't have any null values, we will populate all values in the outputNullMap to false
        IntStream.range(0, numberOfRows).forEach(i -> {
            final OutputRow outputRow = outputDataSet.get(i);
            outputDataCol1[i] = outputRow.id;
            outputDataCol2[i] = outputRow.ngram;
            outputNullMap[0][i] = false;
            outputNullMap[1][i] = false;
        });
    }

    // Example: ngrams(3, "abcde") = ["abc", "bcd", "cde"].
    private static List<String> ngrams(int n, String text) {
        return IntStream.range(0, text.length() - n + 1)
                .mapToObj(i -> text.substring(i, i + n))
                .collect(Collectors.toList());
    }
}
```

## <a name="3---class-inputrowjava"></a>3 - Klasse InputRow.java

Erstellen Sie eine zweite Klasse namens **InputRow.java**, bestehend aus den folgenden Code, und am gleichen Speicherort wie gespeichert **Ngram.java**.

```java
package pkg;

//This object represents one input row
public class InputRow {
    public final int id;
    public final String text;

    public InputRow(final int id, final String text) {
        this.id = id;
        this.text = text;
    }
}
```

## <a name="4---class-outputrowjava"></a>4 - Klasse OutputRow.java

Die dritte und letzte Klasse heißt **OutputRow.java**. Kopieren Sie den Code, und speichern Sie als OutputRow.java am gleichen Speicherort wie die anderen.

```java
package pkg;

//This object represents one output row
public class OutputRow {
    public final int id;
    public final String ngram;

    public OutputRow(final int id, final String ngram) {
        this.id = id;
        this.ngram = ngram;
    }

    @Override
    public String toString() { return id + ":" + ngram; }
}
```

## <a name="5---compile"></a>5 - Kompilierung

Sobald Sie fertig sind, Klassen haben Javac zur Kompilierung in "Class"-Dateien ausführen (`javac Ngram.java InputRow.java OutputRow.java`). Sie sollten drei class-Dateien für dieses Beispiel (Ngram.class InputRow.class und OutputRow.class) erhalten.

Platzieren Sie den kompilierten Code in einem Unterordner namens "Pkg" in den Klassenpfad-Speicherort. Wenn Sie auf einer entwicklungsworkstation arbeiten, ist dieser Schritt, in dem Sie die Dateien auf den SQL Server-Computer kopieren.

Der Klassenpfad ist der Speicherort des kompilierten Codes. Zum Beispiel unter Linux, wenn im Klassenpfad ist "/ home/Myclasspath /", und klicken Sie dann die class-Dateien in "/ Home/Myclasspath/Pkg" werden soll. Im Beispielskript in Schritt 7, der KLASSENPFAD in der Sp_execute_external_script bereitgestellt wird "/ home/Myclasspath /" (bei Linux). 

Auf Windows, es wird empfohlen, einen relativ flachen Ordner-Struktur, ein oder zwei Ebenen, um Berechtigungen zu vereinfachen. Beispielsweise könnte Classpath "C:\myJavaCode" mit einem Unterordner namens "\pkg" mit den kompilierten Klassen ähneln. 

Weitere Informationen zu den Klassenpfad, finden Sie unter [legen Sie CLASSPATH](howto-call-java-from-sql.md#set-classpath). 

### <a name="using-jar-files"></a>Verwenden die JAR-Dateien

Wenn Sie Ihre Klassen und Abhängigkeiten in JAR-Dateien packen möchten, geben Sie den vollständigen Pfad zu der JAR-Datei im Sp_execute_external_script CLASSPATH-Parameter. Z. B. wenn die JAR-Datei "ngram.jar" aufgerufen wird, der KLASSENPFAD wird "/ home/myclasspath/ngram.jar" unter Linux.

## <a name="6---set-permissions"></a>6: Festlegen von Berechtigungen

Ausführung des Skripts ist nur erfolgreich, wenn die Prozess-Identitäten Zugriff auf Ihren Code haben. 

### <a name="on-linux"></a>Unter Linux

Erteilen von Lese-/Schreibberechtigungen für den Klassenpfad so die **Mssql_satellite** Benutzer.

### <a name="on-windows"></a>Für Windows

Erteilen von Berechtigungen "Lesen und Ausführen" für **SQLRUserGroup** und **alle Anwendungspakete** SID für den Ordner, die kompilierten Java-Code enthält. 

Die gesamte Struktur muss über Berechtigungen verfügen, die vom Stamm bis zum letzten Unterordner übergeordnete. 
 
1. Mit der rechten Maustaste in des Ordners (z. B. "C:\myJavaCode"), wählen Sie **Eigenschaften** > **Sicherheit**.
2. Klicken Sie auf **Bearbeiten**.
3. Klicken Sie auf **Hinzufügen**.
4. In **wählen Benutzer, Computer, Dienstkonten oder Gruppen**:
   + Klicken Sie auf **Objekttypen** , und stellen Sie sicher, dass *integrierte Sicherheitsprinzipien* und *Gruppen* ausgewählt sind.
   + Klicken Sie auf **Speicherorte** den Namen des lokalen Computers am oberen Rand der Liste auswählen.
5. Geben Sie **SQLRUserGroup**, überprüfen Sie den Namen ein, und klicken Sie dann auf OK, um die Gruppe hinzuzufügen.
6. Geben Sie **alle Application Pakete**, überprüfen Sie den Namen, und klicken Sie dann auf OK, um Sie hinzuzufügen. Wenn der Name nicht behoben wird, rufen Sie die Speicherorte Schritt. Die SID ist lokal auf Ihrem Computer.

Stellen Sie sicher, dass beide Sicherheitsidentitäten "Lese-und Ausführungsberechtigungen" auf den Ordner und Unterordner von "Pkg" verfügen.

<a name="call-method"></a>

## <a name="7---call-getngrams"></a>7 - Aufruf *getNgrams()*

Geben Sie die Java-Methode, um den Code von SQL Server aufzurufen, **getNgrams()** im "Script"-Parameter von Sp_execute_external_script. Diese Methode gehört zu einem Paket namens "Pkg" und eine neue Klassendatei namens **Ngram.java**.

Dieses Beispiel übergibt die CLASSPATH-Parameter, um den Pfad für die Java-Dateien anzugeben. Er verwendet auch "Params" einen Parameter an die Java-Klasse übergeben. Stellen Sie sicher, dass diese Classpath 30 Zeichen nicht überschreitet. Wenn dies der Fall ist, erhöhen Sie den Wert in das folgende Skript ein.

+ Führen Sie unter Linux den folgenden Code in SQL Server Management Studio oder ein anderes Tool zum Ausführen von Transact-SQL verwendet. 

+ Ändern Sie auf Windows, **@myClassPath** zu N'C:\myJavaCode\' (vorausgesetzt, es ist der übergeordnete Ordner des \pkg) vor dem Ausführen der Abfrage in SQL Server Management Studio oder ein anderes Tool.

```sql
DECLARE @myClassPath nvarchar(50)
DECLARE @n int 
--This is where you store your classes or jars.
--Update this to your own classpath
SET @myClassPath = N'/home/myclasspath/'
--This is the size of the ngram
SET @n = 3
EXEC sp_execute_external_script
  @language = N'Java'
, @script = N'pkg.Ngram.getNGrams'
, @input_data_1 = N'SELECT id, text FROM reviews'
, @parallel = 0
, @params = N'@CLASSPATH nvarchar(30), @param1 INT'
, @CLASSPATH = @myClassPath
, @param1 = @n
with result sets ((ID int, ngram varchar(20)))
GO
```

### <a name="results"></a>Ergebnisse

Nach dem Ausführen des Aufrufs, erhalten Sie ein Resultset mit zwei Spalten:

![Ergebnisse aus Java-Beispiel](../media/java/java-sample-results.png "Beispielergebnisse")

### <a name="if-you-get-an-error"></a>Wenn Sie eine Fehlermeldung erhalten

Regel, die Sie alle Probleme im Zusammenhang mit den Klassenpfad. 

+ CLASSPATH muss den übergeordneten Ordner und Unterordner, aber nicht auf den Unterordner "Pkg" bestehen. Während der Pkg-Unterordner vorhanden sein muss, sollte es nicht in Classpath-Wert in der gespeicherten Prozedur angegeben werden.

+ Der Unterordner "Pkg" sollte den kompilierten Code für alle drei Klassen enthalten.

+ Classpath darf nicht länger als die deklarierten Wert (`DECLARE @myClassPath nvarchar(50)`). Wenn dies der Fall ist, der Pfad auf die ersten 50 Zeichen abgeschnitten, und der kompilierte Code wird nicht geladen werden. Sie erreichen eine `SELECT @myClassPath` um den Wert überprüfen. Erhöhen Sie die Länge, wenn es sich bei 50 Zeichen ist nicht ausreichend. 

+ Überprüfen Sie abschließend die Berechtigungen auf *jedes* Ordner vom Stamm zum Unterordner "Pkg", um sicherzustellen, dass die Sicherheitsidentitäten, die der externe Prozess ausgeführt über die Berechtigung zum Lesen und Ausführen von Code.

## <a name="see-also"></a>Siehe auch

+ [Gewusst wie: Aufrufen von Java in SQL Server](howto-call-java-from-sql.md)
+ [Java-Erweiterungen in SQL Server](extension-java.md)
+ [Java und SQL Server-Datentypen](java-sql-datatypes.md)