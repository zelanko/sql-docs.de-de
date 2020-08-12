---
title: Aufrufen der Java Runtime
titleSuffix: SQL Server Language Extensions
description: Hier erfahren Sie, wie Sie mithilfe von SQL Server-Spracherweiterungen Java-Klassen aus gespeicherten SQL Server-Prozeduren abrufen können.
author: dphansen
ms.author: davidph
ms.date: 06/25/2020
ms.topic: conceptual
ms.prod: sql
ms.technology: language-extensions
monikerRange: '>=sql-server-ver15||>=sql-server-linux-ver15||=sqlallproducts-allversions'
ms.openlocfilehash: 5aa8659b57349efb7378209006bbada148206bcb
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/01/2020
ms.locfileid: "85735124"
---
# <a name="how-to-call-the-java-runtime-in-sql-server-language-extensions"></a>Aufrufen der Java-Runtime in SQL Server-Spracherweiterungen
 [!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

[SQL Server-Spracherweiterungen](../language-extensions-overview.md) verwenden die gespeicherte Systemprozedur [sp_execute_external_script](https://docs.microsoft.com/sql/relational-databases/system-stored-procedures/sp-execute-external-script-transact-sql) als Schnittstelle zum Aufrufen der Java-Runtime. 

In diesem Artikel werden Implementierungsdetails für Java-Klassen und -Methoden erläutert, die auf SQL Server ausgeführt werden.

## <a name="where-to-place-java-classes"></a>Platzieren von Java-Klassen

Es gibt zwei Methoden für das Aufrufen von Java-Klassen in SQL Server:

1. Fügen Sie **.class**- oder **.jar**-Dateien in Ihren [Java-Klassenpfad](#classpath) ein. 

2. Laden Sie kompilierte Klassen in eine **.jar**-Datei und andere Abhängigkeiten in die Datenbank hoch, indem Sie die DDL der [external library](#external-library) verwenden. 

> [!NOTE]
> Allgemein wird empfohlen, **.jar**-Dateien und keine einzelnen **.class**-Dateien zu verwenden. Dies ist eine gängige Vorgehensweise in Java, die den Prozess insgesamt erleichtert. Siehe auch [Erstellen einer JAR-Datei aus Klassendateien](create-a-java-jar-file-from-class-files.md).

<a name="classpath"></a>

## <a name="use-classpath"></a>Verwenden von CLASSPATH

### <a name="basic-principles"></a>Grundlegende Prinzipien

Im Folgenden finden Sie einige grundlegende Prinzipien für das Ausführen von Java auf SQL Server.

* In Ihrem Java-Klassenpfad müssen kompilierte benutzerdefinierte Java-Klassen in **.class**- oder **.jar**-Dateien vorhanden sein. Der [Parameter CLASSPATH](#set-classpath) stellt den Pfad zu den kompilierten Java-Dateien bereit. 

* Die von Ihnen aufgerufene Java-Methode muss im **script**-Parameter für die gespeicherte Prozedur bereitgestellt werden.

* Wenn die Klasse zu einem Paket gehört, muss der **packageName** bereitgestellt werden.

* **params** wird verwendet, um Parameter an eine Java-Klasse zu übergeben. Das Aufrufen einer Methode, die Argumente erfordert, wird nicht unterstützt. Daher stellen Parameter die einzige Möglichkeit dar, um Argumentwerte an Ihre Methode zu übergeben. 

> [!NOTE]
> Dieser Hinweis behandelt nochmals unterstützte und nicht unterstützte Vorgänge, die spezifisch für Java in SQL Server 2019 Release Candidate 1 sind.
> * In der gespeicherten Prozedur werden Eingabeparameter unterstützt. Ausgabeparameter werden nicht unterstützt.

### <a name="call-java-class"></a>Aufrufen der Java-Klasse

Die gespeicherte Systemprozedur [sp_execute_external_script](https://docs.microsoft.com/sql/relational-databases/system-stored-procedures/sp-execute-external-script-transact-sql) dient als Schnittstelle für das Aufrufen der Java-Runtime. Das folgende Beispiel zeigt ein `sp_execute_external_script` unter Verwendung der Java-Erweiterung sowie Parameter für das Angeben von Pfad, Skript und benutzerdefiniertem Code.

> [!NOTE]
> Beachten Sie, dass Sie nicht definieren müssen, welche Methode aufgerufen werden soll. Standardmäßig wird eine Methode namens **execute** aufgerufen. Dies bedeutet, dass Sie das [SDK für die Java-Erweiterung in SQL Server](extensibility-sdk-java-sql-server.md) befolgen und eine Ausführmethode in Ihrer Java-Klasse implementieren müssen.

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

### <a name="set-classpath"></a>Festlegen von CLASSPATH

Nachdem Sie Ihre Java-Klasse bzw. -Klassen kompiliert und eine JAR-Datei in Ihrem Java-Klassenpfad erstellt haben, stehen Ihnen zwei Optionen zur Verfügung, um den Klassenpfad für die SQL Server Java-Erweiterung bereitzustellen:

1. Externe Bibliotheken verwenden

    Die einfachste Möglichkeit besteht darin, SQL Server automatisch nach Ihren Klassen suchen zu lassen, indem Sie externe Bibliotheken erstellen und mit der Bibliothek auf eine JAR-Datei verweisen. [Verwenden externer Bibliotheken für Java](#external-library)

2. Systemumgebungsvariable registrieren

    Sie können eine Systemumgebungsvariable erstellen und die Pfade zu Ihrer JAR-Datei bereitstellen, die die Klassen enthält. Erstellen Sie eine Systemumgebungsvariable namens **CLASSPATH**.

<a name="external-library"></a>

## <a name="use-external-library"></a>Verwenden externer Bibliotheken

In SQL Server 2019 Release Candidate 1 können Sie externe Bibliotheken für die Java-Sprache unter Windows und Linux verwenden. Sie können Ihre Klassen in einer JAR-Datei kompilieren und die JAR-Datei und andere Abhängigkeiten mit der DDL [CREATE EXTERNAL LIBRARY](https://docs.microsoft.com/sql/t-sql/statements/create-external-library-transact-sql) in die Datenbank hochladen.

Beispiel für das Hochladen einer JAR-Datei mit externer Bibliothek:

```sql 
CREATE EXTERNAL LIBRARY myJar
FROM (CONTENT = '<local path to .jar file>') 
WITH (LANGUAGE = 'Java'); 
GO
```

Durch das Erstellen einer externen Bibliothek hat SQL Server automatisch Zugriff auf die Java-Klassen, und Sie müssen keine speziellen Berechtigungen für den Klassenpfad festlegen.

Beispiel für das Aufrufen einer Methode in einer Klasse aus einem Paket, das als externe Bibliothek hochgeladen wurde:

```sql
EXEC sp_execute_external_script
  @language = N'Java'
, @script = N'MyPackage.MyCLass'
, @input_data_1 = N'SELECT * FROM MYTABLE'
with result sets ((column1 int))
```

Weitere Informationen finden Sie unter [CREATE EXTERNAL LANGUAGE](https://docs.microsoft.com/sql/t-sql/statements/create-external-library-transact-sql).

## <a name="loopback-connection-to-sql-server"></a>Loopbackverbindung mit SQL Server

Verwenden Sie eine Loopbackverbindung, um über JDBC eine Verbindung mit SQL Server herzustellen und Daten aus Java zu lesen oder zu schreiben, die über `sp_execute_external_script`ausgeführt werden. Sie können diese Methode verwenden, wenn nicht die Möglichkeit besteht, die Argumente **InputDataSet** und **OutputDataSet** von `sp_execute_external_script` zu verwenden.
Verwenden Sie das folgende Beispiel, um unter Windows eine Loopbackverbindung herzustellen:

```
jdbc:sqlserver://localhost:1433;databaseName=Adventureworks;integratedSecurity=true;
``` 

Zum Erstellen einer Loopbackverbindung unter Linux benötigt der JDBC-Treiber drei Verbindungseigenschaften, die im folgenden Zertifikat definiert sind:

[Client-Certificate-Authentication](https://github.com/microsoft/mssql-jdbc/wiki/Client-Certificate-Authentication-for-Loopback-Scenarios)


## <a name="next-steps"></a>Nächste Schritte

+ [Tutorial: Suchen nach einer Zeichenfolge mithilfe regulärer Ausdrücke in Java](../tutorials/search-for-string-using-regular-expressions-in-java.md)
