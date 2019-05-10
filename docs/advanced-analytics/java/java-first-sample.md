---
title: Java-Beispiel und Tutorials für SQL Server-2019 – SQL Server Machine Learning Services
description: Führen Sie Java-Beispielcode für SQL Server-2019 zu Schritten für SQL Server-Daten mit der Erweiterung der Java-Sprache vertraut zu machen.
ms.prod: sql
ms.technology: machine-learning
ms.date: 04/23/2019
ms.topic: conceptual
author: nelgson
ms.author: negust
ms.reviewer: dphansen
manager: cgronlun
monikerRange: '>=sql-server-ver15||=sqlallproducts-allversions'
ms.openlocfilehash: 000318716b07f58e94bd5c482d9c349e5d4e5481
ms.sourcegitcommit: d5cd4a5271df96804e9b1a27e440fb6fbfac1220
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/28/2019
ms.locfileid: "64775123"
---
# <a name="sql-server-regex-java-sample"></a>SQL Server-Regex-Java-Beispiel

Dieses Beispiel zeigt eine Java-Klasse, die zwei Spalten ("ID" und "Text") von SQL Server empfängt, und nimmt auch einen regulären Ausdruck als Eingabeparameter. Die Klasse gibt zwei Spalten an SQL Server ("ID" und "Text") zurück.

Für einen angegebenen Text in der Textspalte gesendet, um die Java-Klasse überprüft der Code, wenn der angegebene reguläre Ausdruck erfüllt ist, und diesen Text zusammen mit der ursprünglichen-ID. gibt 

Dieses spezielle Beispiel verwendet einen regulären Ausdruck, der überprüft, ob ein Text das Wort "Java" oder "Java" enthält.

## <a name="microsoft-extensibility-sdk-for-java-for-microsoft-sql-server"></a>Erweiterungen für Microsoft-SDK für Java für Microsoft SQL Server

 In der CTP-Version 2.5 ändern wir die Methode, die Sie Java-Code, die Java-Sprache-Erweiterung implementieren für die Kommunikation mit dem SQL Server verwendet. Dies bietet ein besseres Benutzererlebnis für Entwickler, bei der Interaktion mit SQL Server aus Java.

Sie sollten über das SDK als eine Hilfsschnittstelle vorstellen, die es erleichtern, zur Implementierung von Java-Code für SQL Server ausgeführt wird.

> [!NOTE]
> Die Einführung des SDK ist eine große Änderung gegenüber früheren CTPs. Alle vorherigen Beispiele, mussten Sie arbeiten müssen aktualisiert werden, um das SDK verwenden.

Weitere Informationen finden Sie unter den [SDK-Dokumentation](java-sdk.md).

## <a name="prerequisites"></a>Erforderliche Komponenten

+ SQL Server-2019-Datenbank-Engine-Instanz mit dem Extensibility Framework und Java-Erweiterung [auf Windows](../install/sql-machine-learning-services-windows-install.md) oder [unter Linux](https://docs.microsoft.com/sql/linux/sql-server-linux-setup). Weitere Informationen zur Systemkonfiguration von finden Sie unter [Java-spracherweiterung in SQL Server-2019](extension-java.md). Weitere Informationen zum Schreiben von Code Anforderungen finden Sie unter [das Aufrufen von Java in SQL Server](howto-call-java-from-sql.md).

+ SQL Server Management Studio oder Azure Data Studio für die Ausführung von T-SQL.

+ Java SE Development Kit (JDK) 8 oder JRE 8 unter Windows oder Linux.

+ [Microsoft Java-SDK für Microsoft SQL Server, die sich in Erweiterbarkeit](http://aka.ms/mssql-java-lang-extension) Mssql-Java-Sprache-extension.jar.

Befehlszeilencompiler verwenden **Javac** ist für dieses Tutorial ausreichend.

## <a name="1---create-sample-data-in-a-sql-server-table"></a>1: Erstellen von Beispieldaten in einer SQL Server-Tabelle

Zuerst erstellen und Auffüllen einer *Testdata* -Tabelle mit **ID** und **Text** Spalten. Verbinden mit SQL Server, und führen Sie das folgende Skript zum Erstellen einer Tabelle:

```sql
CREATE DATABASE javatest
GO
USE javatest
GO

-- Create table for test data
DROP TABLE IF exists testdata;
GO

CREATE TABLE testdata(
id int NOT NULL,
"text" nvarchar(100) NOT NULL)
GO

TRUNCATE TABLE testdata
GO

-- Insert data into test table
INSERT INTO testdata(id, "text") VALUES (1, 'This sentence contains java')
INSERT INTO testdata(id, "text") VALUES (2, 'This sentence does not')
INSERT INTO testdata(id, "text") VALUES (3, 'I love Java!')
GO
Select * FROM testdata
```

## <a name="2---class-regexsamplejava"></a>2 - Class-RegexSample.java

Zunächst erstellen die Hauptklasse.

In diesem Schritt erstellen Sie eine Klasse namens **RegexSample.java** , und kopieren Sie die folgenden Java-Code in diese Datei.

Main-Klasse ist das SDK, importieren, die von dieser Klasse erkannt werden, d. h., das die JAR-Datei in Schritt 1 heruntergeladen haben muss.

> [!NOTE]
> Beachten Sie, dass diese Klasse das Java SDK-Erweiterungspaket importiert.
Finden Sie im Artikel über die [Microsoft Extensibility-SDK für Java für Microsoft SQL Server](java-sdk.md) Weitere Details.

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

## <a name="3-compile-and-create-jar-file"></a>3 kompilieren und erstellen die JAR-Datei

Es wird empfohlen, dass Sie Ihre Klassen und Abhängigkeiten in JAR-Dateien verpacken. Die meisten Java-IDEs wie Eclipse oder IntelliJ generieren die Unterstützung von JAR-Dateien aus, wenn Sie Build/das Projekt kompilieren. In diesem Beispiel haben wir die JAR-Datei namens **regex.jar**.

Wenn Sie eine JAR-Datei manuell erstellen, Sie können die Schritte, finden Sie unter [Vorgehensweise: Erstellen Sie eine JAR-Datei](extension-java.md#create-jar).

> [!NOTE]
> In diesem Beispiel wird verwendet, Pakete, was bedeutet, dass das Paket "Pkg" am Anfang der Klasse wird sichergestellt, dass es sich bei der kompilierte Code in einen Unterordner namens "Pkg" gespeichert wird. Dies automatisch übernommen, wenn Sie eine IDE verwenden, aber wenn Sie mithilfe von Klassen manuell kompilieren **Javac**, Sie müssen den kompilierten Code manuell in den Unterordner "Pkg" zu platzieren.

## <a name="4---create-external-libraries"></a>4: Erstellen von externen Bibliotheken

Erstellen Sie eine externe Bibliothek, SQL Server haben automatisch Zugriff auf die JAR-Dateien, und Sie müssen nicht den Klassenpfad keine besonderen Berechtigungen fest.

In diesem Beispiel müssen Sie zwei externe Bibliotheken erstellen. Eine für das SDK, und eine für das Regex-Java-Beispiel.

1.  Herunterladen [Microsoft Extensibility-SDK für Java für Microsoft SQL Server](http://aka.ms/mssql-java-lang-extension) Mssql-Java-Sprache-extension.jar.

1. Erstellen Sie die externe Bibliothek für das sdk

```sql
-- Create external library for the SDK
CREATE EXTERNAL LIBRARY sdk
FROM (CONTENT = '<path>/mssql-java-lang-extension.jar')
WITH (LANGUAGE = 'Java');
GO
```

3. Erstellen Sie die externe Bibliothek für das Regex-Beispiel

```sql
-- Create external library for the regex sample
CREATE EXTERNAL LIBRARY regex
FROM (CONTENT = '<path>/regex.jar')
WITH (LANGUAGE = 'Java');
GO
```

## <a name="5---set-permissions-skip-if-you-performed-step-4"></a>5: Festlegen von Berechtigungen (überspringen Sie diese Option, wenn Sie Schritt 4 ausgeführt)

Dieser Schritt ist nicht erforderlich, wenn Sie externe Bibliotheken verwenden. Als empfohlene Vorgehensweise ist, um eine externe Bibliothek aus der Sie JAR-Datei zu erstellen.

Wenn Sie keine externe Bibliotheken verwenden möchten, müssen Sie die erforderlichen Berechtigungen festgelegt haben. Ausführung des Skripts ist nur erfolgreich, wenn die Prozess-Identitäten Zugriff auf Ihren Code haben. Weitere Informationen zum Festlegen von Berechtigungen finden Sie [hier](extension-java.md).

### <a name="on-linux"></a>On Linux

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
6. Geben Sie **alle ANWENDUNGSPAKETE**, überprüfen Sie den Namen, und klicken Sie dann auf OK, um Sie hinzuzufügen. Wenn der Name nicht behoben wird, rufen Sie die Speicherorte Schritt. Die SID ist lokal auf Ihrem Computer.

Stellen Sie sicher, dass beide Sicherheitsidentitäten "Lese-und Ausführungsberechtigungen" auf den Ordner und Unterordner "Pkg" verfügen.

<a name="call-method"></a>

## <a name="2---call-the-java-class"></a>2: Rufen Sie die Java-Klasse

Zum Aufrufen von des Java-Codes aus SQL Server erstellen wir eine gespeicherte Prozedur, die Sp_execute_external_script aufruft. In der "Script"-Parameter wird die [Paket] definiert. [Class] wir aufrufen möchten. In diesem Beispiel wird die Klasse gehört, um ein Paket namens **Pkg** und eine Datei namens **RegexSample.java**.

> [!NOTE]
>Wir definieren die aufzurufende Methode nicht. In der Standardeinstellung die **ausführen** aufgerufene Methode. Dies bedeutet, dass Sie führen die SDK-Schnittstelle und eine Execute-Methode in Ihre Java-Klasse implementieren müssen, sollten Sie die Klasse von SQL Server aufrufen kann.

```sql
/*
This stored procedure takes an input query (input dataset) and a regular expression and returns the rows that fulfilled the given regular expression. This sample uses a regular expression that checks if a text contains the word "Java" or "java" ([Jj]ava) 
*/

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

Nach dem Ausführen des Aufrufs, erhalten Sie ein Resultset mit zwei Zeilen.

![Ergebnisse aus Java-Beispiel](../media/java/java-sample-results.png "Beispielergebnisse")

### <a name="if-you-get-an-error"></a>Wenn Sie eine Fehlermeldung erhalten

+ Beim Kompilieren Ihrer Klassen sollten die Unterordner "Pkg" den kompilierten Code für alle drei Klassen enthalten.

+ Wenn Sie keine externe Bibliotheken verwenden, aktivieren Sie zum Schluss Berechtigungen auf *jedes* Ordner vom Stamm zum Unterordner "Pkg", um sicherzustellen, dass die Sicherheitsidentitäten, die der externe Prozess ausgeführt über die Berechtigung zum Lesen und Ausführen von Code.

## <a name="next-steps"></a>Nächste Schritte

+ [Erweiterungen für Microsoft-SDK für Java für Microsoft SQL Server](java-sdk.md)
+ [Gewusst wie: Aufrufen von Java in SQL Server](howto-call-java-from-sql.md)
+ [Java-Erweiterungen in SQL Server](extension-java.md)
+ [Java und SQL Server-Datentypen](java-sql-datatypes.md)
