---
title: 'Tutorial: Suchen nach RegEx-Zeichenfolgen in Java'
description: In diesem Tutorial erfahren Sie, wie Sie SQL Server-Spracherweiterungen verwenden und Java-Code ausführen, der eine Zeichenfolge mit regulären Ausdrücken (RegEx) durchsucht.
author: dphansen
ms.author: davidph
ms.date: 11/05/2019
ms.topic: conceptual
ms.prod: sql
ms.technology: language-extensions
monikerRange: '>=sql-server-ver15||>=sql-server-linux-ver15||=sqlallproducts-allversions'
ms.openlocfilehash: dab5079ab3c0447b0895bbc3642f23884317f3c4
ms.sourcegitcommit: 9b41725d6db9957dd7928a3620fe4db41eb51c6e
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 08/13/2020
ms.locfileid: "88180500"
---
# <a name="tutorial-search-for-a-string-using-regular-expressions-regex-in-java"></a>Tutorial: Suchen nach einer Zeichenfolge mithilfe regulärer Ausdrücke (RegEx) in Java
[!INCLUDE [SQL Server 2019 and later](../../includes/applies-to-version/sqlserver2019.md)]

In diesem Tutorial wird gezeigt, wie Sie [SQL Server-Spracherweiterungen](../language-extensions-overview.md) verwenden, um eine Java-Klasse zu erstellen, die zwei Spalten (ID und Text) aus SQL Server und einen RegEx als Eingabeparameter empfängt. Die Klasse gibt an SQL Server zwei Spalten (ID und Text) zurück.

Für einen bestimmten Text in der Textspalte, der an die Java-Klasse gesendet wird, prüft der Code, ob der angegebene reguläre Ausdruck erfüllt ist, und gibt diesen Text zusammen mit der ursprünglichen ID zurück.

In diesem Beispielcode wird ein RegEx verwendet, der prüft, ob ein Text das Wort „Java“ bzw. „java“ enthält.

## <a name="prerequisites"></a>Voraussetzungen

+ Eine Instanz der SQL Server 2019-Datenbank-Engine mit dem Erweiterungsframework und der Java-Programmiererweiterung [unter Windows](../install/install-sql-server-language-extensions-on-windows.md) oder [unter Linux](https://docs.microsoft.com/sql/linux/sql-server-linux-setup-language-extensions). Weitere Informationen finden Sie unter [Spracherweiterung in SQL Server 2019](../language-extensions-overview.md). Weitere Informationen zu Codierungsanforderungen finden Sie unter [Aufrufen von Java in SQL Server](../how-to/call-java-from-sql.md).

+ SQL Server Management Studio oder Azure Data Studio für die Ausführung von T-SQL.

+ Java SE Development Kit (JDK) 8 oder JRE 8 unter Windows oder Linux.

+ Die Datei **mssql-java-lang-extension.jar** aus dem [Microsoft Java Extensibility SDK für Microsoft SQL Server](../how-to/extensibility-sdk-java-sql-server.md).

Die Befehlszeilenkompilierung mit **javac** ist für dieses Tutorial ausreichend.

## <a name="create-sample-data"></a>Erstellen von Beispieldaten

Erstellen Sie zunächst eine neue Datenbank, und füllen Sie eine Tabelle **testdata** mit den Spalten **ID** und **Text**.

```sql
CREATE DATABASE javatest
GO

USE javatest
GO

CREATE TABLE testdata (
    id int NOT NULL,
    "text" nvarchar(100) NOT NULL
)
GO

-- Insert data into test table
INSERT INTO testdata(id, "text") VALUES (1, 'This sentence contains java')
INSERT INTO testdata(id, "text") VALUES (2, 'This sentence does not')
INSERT INTO testdata(id, "text") VALUES (3, 'I love Java!')
GO
```

## <a name="create-the-main-class"></a>Erstellen der Hauptklasse

In diesem Schritt erstellen Sie eine Klassendatei namens **RegexSample.java** und kopieren den folgenden Java-Code in diese Datei.

Diese Hauptklasse importiert das SDK, was bedeutet, dass die in Schritt 1 heruntergeladene JAR-Datei aus dieser Klasse erkennbar sein muss.

```java
package pkg;

import com.microsoft.sqlserver.javalangextension.PrimitiveDataset;
import com.microsoft.sqlserver.javalangextension.AbstractSqlServerExtensionExecutor;
import java.util.LinkedHashMap;
import java.util.LinkedList;
import java.util.ListIterator;
import java.util.regex.*;

public class RegexSample extends AbstractSqlServerExtensionExecutor {
    private Pattern expr;

    public RegexSample() {
        // Setup the expected extension version, and class to use for input and output dataset
        executorExtensionVersion = SQLSERVER_JAVA_LANG_EXTENSION_V1;
        executorInputDatasetClassName = PrimitiveDataset.class.getName();
        executorOutputDatasetClassName = PrimitiveDataset.class.getName();
    }
    
    public PrimitiveDataset execute(PrimitiveDataset input, LinkedHashMap<String, Object> params) {
        // Validate the input parameters and input column schema
        validateInput(input, params);

        int[] inIds = input.getIntColumn(0);
        String[] inValues = input.getStringColumn(1);
        int rowCount = inValues.length;

        String regexExpr = (String)params.get("regexExpr");
        expr = Pattern.compile(regexExpr);

        System.out.println("regex expression: " + regexExpr);

        // Lists to store the output data
        LinkedList<Integer> outIds = new LinkedList<Integer>();
        LinkedList<String> outValues = new LinkedList<String>();

        // Evaluate each row
        for(int i = 0; i < rowCount; i++) {
            if (check(inValues[i])) {
                outIds.add(inIds[i]);
                outValues.add(inValues[i]);
            }
        }

        int outputRowCount = outValues.size();

        int[] idOutputCol = new int[outputRowCount];
        String[] valueOutputCol = new String[outputRowCount];

        // Convert the list of output columns to arrays
        outValues.toArray(valueOutputCol);

        ListIterator<Integer> it = outIds.listIterator(0);
        int rowId = 0;

        System.out.println("Output data:");
        while (it.hasNext()) {
            idOutputCol[rowId] = it.next().intValue();

            System.out.println("ID: " + idOutputCol[rowId] + " Value: " + valueOutputCol[rowId]);
            rowId++;
        }

        // Construct the output dataset
        PrimitiveDataset output = new PrimitiveDataset();

        output.addColumnMetadata(0, "ID", java.sql.Types.INTEGER, 0, 0);
        output.addColumnMetadata(1, "Text", java.sql.Types.NVARCHAR, 0, 0);

        output.addIntColumn(0, idOutputCol, null);
        output.addStringColumn(1, valueOutputCol);

        return output;
    }

    private void validateInput(PrimitiveDataset input, LinkedHashMap<String, Object> params) {
        // Check for the regex expression input parameter
        if (params.get("regexExpr") == null) {
            throw new IllegalArgumentException("Input parameter 'regexExpr' is not found");
        }

        // The expected input schema should be at least 2 columns, (INTEGER, STRING)
        if (input.getColumnCount() < 2) {
            throw new IllegalArgumentException("Unexpected input schema, schema should be an (INTEGER, NVARCHAR or VARCHAR)");
        }

        // Check that the input column types are expected
        if (input.getColumnType(0) != java.sql.Types.INTEGER &&
                (input.getColumnType(1) != java.sql.Types.VARCHAR && input.getColumnType(1) == java.sql.Types.NVARCHAR )) {
            throw new IllegalArgumentException("Unexpected input schema, schema should be an (INTEGER, NVARCHAR or VARCHAR)");
        }
    }

    private boolean check(String text) {
        Matcher m = expr.matcher(text);

        return m.find();
    }
}
```

## <a name="compile-and-create-a-jar-file"></a>Kompilieren und Erstellen einer JAR-Datei

Packen Sie Ihre Klassen und Abhängigkeiten in `.jar`-Dateien. Die meisten Java-IDEs (z. B. Eclipse oder IntelliJ) unterstützen das Erstellen von `.jar`-Dateien, wenn Sie das Projekt erstellen oder kompilieren. Geben Sie der `.jar`-Datei den Namen **regex.jar**.

Wenn Sie keine Java-IDE verwenden, können Sie eine `.jar`-Datei auch manuell erstellen. Weitere Informationen finden Sie unter [Erstellen einer JAR-Java-Datei aus Klassendateien](../how-to/create-a-java-jar-file-from-class-files.md).

> [!NOTE]
> In diesem Tutorial werden Pakete verwendet. Die Zeile `package pkg;` am Anfang der Klasse stellt sicher, dass der kompilierte Code in einem Unterordner mit dem Namen **pkg** gespeichert wird. Wenn Sie eine IDE verwenden, wird der kompilierte Code automatisch in diesem Ordner gespeichert. Wenn Sie **javac** verwenden, um die Klassen manuell zu kompilieren, müssen Sie den kompilierten Code selbst im Ordner **pkg** platzieren.

## <a name="create-external-language"></a>Erstellen einer externen Sprache

Sie müssen eine externe Sprache in der Datenbank erstellen. Die externe Sprache ist ein datenbankweites Objekt, was bedeutet, dass externe Sprachen wie Java für jede Datenbank, in der Sie sie verwenden möchten, erstellt werden müssen.

### <a name="create-external-language-on-windows"></a>Erstellen einer externen Sprache unter Windows

Wenn Sie Windows verwenden, führen Sie die folgenden Schritte aus, um eine externe Sprache für Java zu erstellen.

1. Erstellen Sie eine ZIP-Datei mit der Erweiterung.

    Im Rahmen des SQL Server-Setups unter Windows wird die **ZIP**-Datei mit der Java-Erweiterung an diesem Speicherort installiert: `[SQL Server install path]\MSSQL\Binn\java-lang-extension.zip`. Die ZIP-Datei enthält die Datei **javaextension.dll**.

2. Erstellen Sie eine externe Sprache „Java“ aus der ZIP-Datei:

    ```sql
    CREATE EXTERNAL LANGUAGE Java
    FROM
    (CONTENT = N'[SQL Server install path]\MSSQL\Binn\java-lang-extension.zip', FILE_NAME = 'javaextension.dll',
    ENVIRONMENT_VARIABLES = N'{"JRE_HOME":"<path to JRE>"}' );
    GO
    ```

### <a name="create-external-language-on-linux"></a>Erstellen einer externen Sprache unter Linux

Im Rahmen des Setups wird die Datei mit der Erweiterung **.tar.gz** unter folgendem Pfad gespeichert: `/opt/mssql-extensibility/lib/java-lang-extension.tar.gz`.

Führen Sie die folgende T-SQL-Anweisung aus, um eine externe Sprache „Java“ zu erstellen:

```sql
CREATE EXTERNAL LANGUAGE Java
FROM (CONTENT = N'/opt/mssql-extensibility/lib/java-lang-extension.tar.gz', file_name = 'javaextension.so',
ENVIRONMENT_VARIABLES = N'{"JRE_HOME":"<path to JRE>"}' );
GO
```

### <a name="permissions-to-execute-external-language"></a>Berechtigungen zum Ausführen einer externen Sprache

Damit ein Benutzer Java-Code ausführen kann, benötigt dieser die Berechtigung zum Ausführen externer Skripts für diese bestimmte Sprache.

Weitere Informationen finden Sie unter [CREATE EXTERNAL LANGUAGE](https://docs.microsoft.com/sql/t-sql/statements/create-external-language-transact-sql).

## <a name="create-external-libraries"></a>Erstellen von externen Bibliotheken

Verwenden Sie [CREATE EXTERNAL LIBRARY](https://docs.microsoft.com/sql/t-sql/statements/create-external-library-transact-sql), um eine externe Bibliothek für Ihre `.jar`-Dateien zu erstellen. SQL Server wird auf die `.jar`-Dateien zugreifen können, sodass Sie keine speziellen Berechtigungen für den **classpath** (Klassenpfad) festlegen müssen.

In diesem Beispiel erstellen Sie zwei externe Bibliotheken. Eine für das SDK und eine für den RegEx-Java-Code.

1. Die SDK-JAR-Datei **mssql-java-lang-extension.jar** wird als Teil von SQL Server 2019 sowohl unter Windows als auch unter Linux installiert.

    + Standardinstallationspfad unter Windows: **[Basisverzeichnis der Instanzinstallation]\MSSQL\Binn\mssql-java-lang-extension.jar**

    + Standardinstallationspfad unter Linux: **/opt/mssql/lib/mssql-java-lang-extension.jar**

    Da es sich um einen Open-Source-Code handelt, ist dieser auch im [GitHub-Repository für SQL Server-Spracherweiterungen](https://github.com/microsoft/sql-server-language-extensions) verfügbar. Weitere Informationen finden Sie unter [Microsoft Extensibility SDK für Java für Microsoft SQL Server](../how-to/extensibility-sdk-java-sql-server.md).

2. Erstellen Sie eine externe Bibliothek für das SDK.

    ```sql
    CREATE EXTERNAL LIBRARY sdk
    FROM (CONTENT = '<OS specific path from above>/mssql-java-lang-extension.jar')
    WITH (LANGUAGE = 'Java');
    GO
    ```

3. Erstellen Sie eine externe Bibliothek für den RegEx-Code.

    ```sql
    CREATE EXTERNAL LIBRARY regex
    FROM (CONTENT = '<path>/regex.jar')
    WITH (LANGUAGE = 'Java');
    GO
    ```

## <a name="set-permissions"></a>Festlegen von Berechtigungen

> [!NOTE]
> Überspringen Sie diesen Schritt, wenn Sie im vorherigen Schritt externe Bibliotheken verwendet haben. Es wird empfohlen, eine externe Bibliothek aus der `.jar`-Datei zu erstellen.

Wenn Sie keine externen Bibliotheken verwenden möchten, müssen Sie die erforderlichen Berechtigungen festlegen. Die Skriptausführung ist nur erfolgreich, wenn die Prozess-IDs auf Ihren Code zugreifen können. Weitere Informationen zum Festlegen von Berechtigungen finden Sie im [Installationshandbuch](../install/install-sql-server-language-extensions-on-windows.md).

### <a name="on-linux"></a>Unter Linux

Gewähren Sie dem Benutzer **mssql_satellite** Berechtigungen zum Lesen/Ausführen für den Klassenpfad.

### <a name="on-windows"></a>Unter Windows

Gewähren Sie **SQLRUserGroup** und der SID **Alle Anwendungspakete** Berechtigungen zum Lesen/Ausführen für den Ordner, in dem sich der kompilierte Java-Code befindet.

Die gesamte Struktur muss über Berechtigungen verfügen, vom übergeordneten Stammverzeichnis bis hin zum letzten Unterordner.

1. Klicken Sie mit der rechten Maustaste auf den Ordner (z. B. `C:\myJavaCode`), und wählen Sie **Eigenschaften** > **Sicherheit** aus.
2. Klicken Sie auf **Bearbeiten**.
3. Klicken Sie auf **Hinzufügen**.
4. Unter **Benutzer, Computer, Dienstkonten oder Gruppen auswählen**:
   1. Klicken Sie auf **Objekttypen**, und stellen Sie sicher, dass *Integrierte Sicherheitsprinzipien* und *Gruppen* ausgewählt sind.
   2. Klicken Sie auf **Speicherorte**, um den Namen des lokalen Computers oben in der Liste auszuwählen.
5. Geben Sie **SQLRUserGroup** ein, überprüfen Sie den Namen, und klicken Sie auf „OK“, um die Gruppe hinzuzufügen.
6. Geben Sie **ALL APPLICATION PACKAGES** (Alle Anwendungspakete) ein, überprüfen Sie den Namen, und klicken Sie zum Hinzufügen auf „OK“. 
    Wenn der Name nicht aufgelöst wird, gehen Sie zurück zum Schritt „Speicherorte“. Die SID wird lokal auf Ihrem Computer gespeichert.

Stellen Sie sicher, dass beide Sicherheits-IDs über Berechtigungen zum **Lesen und Ausführen** für den Ordner und den Unterordner **pkg** verfügen.

<a name="call-method"></a>

## <a name="call-the-java-class"></a>Aufrufen der Java-Klasse

Erstellen Sie eine gespeicherte Prozedur, die `sp_execute_external_script` aufruft, um den Java-Code von SQL Server aufzurufen. Legen Sie im Parameter **script** fest, welche `package.class`-Klasse Sie aufrufen möchten. Im folgenden Code gehört die Klasse zu dem Paket **pkg** und der Klassendatei **RegexSample.java**.

> [!NOTE]
> Der Code definiert nicht, welche Methode aufgerufen werden soll. Standardmäßig wird die **execute**-Methode aufgerufen. Das bedeutet, dass Sie der SDK-Schnittstelle folgen und eine „execute“-Methode in der Java-Klasse implementieren müssen, wenn Sie die Klasse aus SQL Server abrufen möchten.

Die gespeicherte Prozedur übernimmt eine Eingabeabfrage (Eingabedataset) und einen regulären Ausdruck und gibt die Zeilen zurück, die den angegebenen regulären Ausdruck erfüllen. Es wird ein regulärer Ausdruck `[Jj]ava` verwendet, der prüft, ob ein Text das Wort **Java** oder **java** enthält.

```sql
CREATE OR ALTER PROCEDURE [dbo].[java_regex] @expr nvarchar(200), @query nvarchar(400)
AS
BEGIN
--Call the Java program by giving the package.className in @script
--The method invoked in the Java code is always the "execute" method
EXEC sp_execute_external_script
  @language = N'Java'
, @script = N'pkg.RegexSample'
, @input_data_1 = @query
, @params = N'@regexExpr nvarchar(200)'
, @regexExpr = @expr
with result sets ((ID int, text nvarchar(100)));
END
GO

--Now execute the above stored procedure and provide the regular expression and an input query
EXECUTE [dbo].[java_regex] N'[Jj]ava', N'SELECT id, text FROM testdata'
GO
```

### <a name="results"></a>Ergebnisse

Nach der Ausführung des Aufrufs sollten Sie ein Resultset mit zwei der Zeilen erhalten.

![Ergebnisse aus dem Java-Beispiel](../media/java/java-sample-results.png "Bespielergebnisse")

### <a name="if-you-get-an-error"></a>Wenn Sie eine Fehlermeldung erhalten:

+ Wenn Sie Ihre Klassen kompilieren, sollte der Unterordner **pkg** den kompilierten Code für alle drei Klassen erhalten.

+ Wenn Sie keine externen Bibliotheken verwenden, überprüfen Sie die Berechtigungen für *jeden einzelnen* Ordner, vom **Stammordner** bis zum Unterordner **pkg**. So können Sie sicherstellen, dass die Sicherheits-IDs, die den externen Prozess ausführen, über Berechtigungen zum Lesen und Ausführen des Codes verfügen.

## <a name="next-steps"></a>Nächste Schritte

+ [Aufrufen von Java in SQL Server](../how-to/call-java-from-sql.md)
+ [Java-Erweiterungen in SQL Server](../language-extensions-overview.md)
+ [Java- und SQL Server-Datentypen](../how-to/java-to-sql-data-types.md)
