---
title: 'Gewusst wie: Aufrufen von Java aus SQL – SQL Server Machine Learning Services'
description: Erfahren Sie, wie Sie Java-Klassen von SQL Server gespeicherte Prozeduren, die mit der Programmiersprache Java programming Language-Erweiterung in SQL Server-2019 aufrufen.
ms.prod: sql
ms.technology: machine-learning
ms.date: 04/23/2019
ms.topic: conceptual
author: dphansen
ms.author: davidph
manager: cgronlun
monikerRange: '>=sql-server-ver15||=sqlallproducts-allversions'
ms.openlocfilehash: a75878ccc4f14d03f84102dd48bfd43a6e04daea
ms.sourcegitcommit: bd5f23f2f6b9074c317c88fc51567412f08142bb
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/24/2019
ms.locfileid: "63473554"
---
# <a name="how-to-call-java-from-sql-server-2019-preview"></a>Gewusst wie: Aufrufen von Java aus SQL Server-2019 (Vorschau)

Bei Verwendung der [Java-spracherweiterung](extension-java.md), [Sp_execute_external_script](https://docs.microsoft.com/sql/relational-databases/system-stored-procedures/sp-execute-external-script-transact-sql) System gespeicherte Prozedur ist die Schnittstelle zum Aufrufen von Java Runtime verwendet. Berechtigungen für die Datenbank gelten für Ausführung von Java-Code.

Dieser Artikel beschreibt die Implementierungsdetails für Java-Klassen und Methoden, die auf SQL Server ausführen. Sobald Sie mit diesen Einzelheiten vertraut sind, überprüfen Sie die [Java-Beispiel](java-first-sample.md) im nächsten Schritt.

Es gibt zwei Methoden zum Aufrufen von Java-Klassen in SQL Server:

1. Platzieren Sie .class oder JAR-Dateien in Ihrem [Java-Classpath](#classpath). Dies ist für Windows und Linux verfügbar.

2. Hochladen der kompilierte Klassen in eine JAR-Datei und andere Abhängigkeiten in der Datenbank mithilfe der [externe Bibliothek](#external-library) DDL. Diese Option ist verfügbar für Windows und Linux von CTP-Version 2.4.

> [!NOTE]
> Als allgemeine Empfehlung verwenden Sie die JAR-Dateien und nicht für die einzelnen class-Dateien. Dies ist in Java üblich und erleichtert die allgemeine Erfahrung. Siehe auch: [Vorgehensweise: Erstellen Sie eine JAR-Datei aus Klassendateien](extension-java.md#create-jar).

<a name="classpath"></a>

## <a name="classpath"></a>CLASSPATH

### <a name="basic-principles"></a>Grundlegende Prinzipien

* Kompilierte benutzerdefinierte Java-Klassen müssen in der class-Dateien oder JAR-Dateien in Ihren Java-Klassenpfad vorhanden sein. Die [CLASSPATH Parameter](#set-classpath) enthält den Pfad zu der kompilierten Java-Dateien. 

* Die Java-Methode, die Sie aufrufen, muss in der "Script"-Parameter für die gespeicherte Prozedur angegeben werden.

* Wenn die Klasse zu einem Paket gehört, muss der "Paketname" bereitgestellt werden.

* "Params" wird zum Übergeben von Parametern an eine Java-Klasse. Aufrufen einer Methode, die Argumente erfordert wird nicht unterstützt Parameter, die einzige Möglichkeit, Argumentwerte an die Methode übergeben werden. 

> [!Note]
> In diesem Hinweis restates unterstützten und nicht unterstützten Vorgänge, die spezifisch für Java in CTP-Version 2.x.
> * Bei der gespeicherten Prozedur werden die Eingabeparameter unterstützt. Output-Parameter sind nicht auf.
> * Streaming mit dem Parameter Sp_execute_external_script @r_rowsPerRead wird nicht unterstützt.
> * Partitionierung mit @input_data_1_partition_by_columns wird nicht unterstützt.
> * Parallele Verarbeitung mit @parallel= 1 wird unterstützt.

### <a name="call-java-class"></a>Rufen Sie Java-Klasse

Sowohl Windows und Linux, die für die [Sp_execute_external_script](https://docs.microsoft.com/sql/relational-databases/system-stored-procedures/sp-execute-external-script-transact-sql) System gespeicherte Prozedur ist die Schnittstelle zum Aufrufen von Java Runtime verwendet. Das folgende Beispiel zeigt eine Sp_execute_external_script mit Java-Erweiterung, und denselben Parametern für die Angabe von Pfad, Skripts und Ihren benutzerdefinierten Code.

> [!NOTE]
> Beachten Sie, dass Sie nicht definieren, welche Methode Sie aufrufen müssen. Standardmäßig, eine Methode namens **ausführen** aufgerufen wird. Dies bedeutet, dass Sie verwenden möchten, führen das SDK, und implementieren eine Execute-Methode in Ihrer Java-Klasse.

```sql
DECLARE @param1 int
SET @param1 = 3

EXEC sp_execute_external_script
  @language = N'Java'
, @script = N'<packageName>.<ClassName>'
, @input_data_1 = N'<Input Query>'
, @param1 = @param1
```

<a name="set-classpath"></a>

### <a name="set-classpath"></a>Legen Sie CLASSPATH

Nachdem Sie Ihre Java-Klasse oder Klassen kompiliert haben, und erstellt eine JAR-Datei in Ihren Java-Klassenpfad, Sie haben zwei Optionen für die Bereitstellung der SQL Server-Java-Erweiterung in des Klassenpfads:

**Option 1: Verwenden von externen Bibliotheken** die einfachste Möglichkeit besteht, stellen SQL Server, die automatisch Ihre Klassen zu ermitteln, von externen Bibliotheken erstellen und in der Bibliothek eine JAR-Datei verweisen. [Verwenden von externen Bibliotheken für Java](howto-call-java-from-sql.md#external-library)

**Option 2: Registrieren Sie eine Systemumgebungsvariable**

Ebenso, wie Sie eine System-Umgebungsvariable für die Java-Laufzeit erstellt haben, können Sie erstellen eine Systemumgebungsvariable und geben Sie die Pfade zu Ihrer JAR-Datei, die Klassen enthält. Zu diesem Zweck müssen Sie eine Systemumgebungsvariable "CLASSPATH" zu erstellen.

<a name="external-library"></a>

## <a name="external-library"></a>Externe Bibliothek

In SQL Server 2019 CTP 2.4 können Sie externe Bibliotheken für Java-Sprache unter Windows und Linux. Sie können die Klassen in eine JAR-Datei zu kompilieren und Hochladen der JAR-Datei und andere Abhängigkeiten in der Datenbank mithilfe der [CREATE EXTERNAL LIBRARY](https://docs.microsoft.com/sql/t-sql/statements/create-external-library-transact-sql) DDL.

Beispiel für eine JAR-Datei mit externen Bibliothek hochladen:

```sql 
CREATE EXTERNAL LIBRARY myJar
FROM (CONTENT = '<local path to .jar file>') 
WITH (LANGUAGE = 'Java'); 
GO
```

Erstellen Sie eine externe Bibliothek, SQL Server haben automatisch Zugriff auf die Java-Klassen aus, und Sie müssen nicht den Klassenpfad keine besonderen Berechtigungen fest.

Beispiel für das Aufrufen einer Methode in einer Klasse aus einem Paket, die als eine externe Bibliothek hochgeladen werden:

```sql
EXEC sp_execute_external_script
  @language = N'Java'
, @script = N'MyPackage.MyCLass'
, @input_data_1 = N'SELECT * FROM MYTABLE'
with result sets ((column1 int))
```

Weitere Informationen finden Sie unter [CREATE EXTERNAL LIBRARY](https://docs.microsoft.com/sql/t-sql/statements/create-external-library-transact-sql).

## <a name="next-steps"></a>Nächste Schritte

+ [Java-Beispiel in SQL Server](java-first-sample.md)
+ [Java und SQL Server-Datentypen](java-sql-datatypes.md)
+ [Java-spracherweiterung in SQL Server](extension-java.md)
