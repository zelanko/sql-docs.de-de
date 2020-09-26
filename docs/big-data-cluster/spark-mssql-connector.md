---
title: Verwenden des Apache Spark-Connectors für SQL Server und Azure SQL
titleSuffix: SQL Server big data clusters
description: Hier erfahren Sie, wie Sie den Apache Spark-Connector für SQL Server und Azure SQL verwenden, um in SQL Server zu lesen und zu schreiben.
author: MikeRayMSFT
ms.author: mikeray
ms.reviewer: mikeray
ms.date: 11/04/2019
ms.topic: conceptual
ms.prod: sql
ms.technology: machine-learning-bdc
ms.openlocfilehash: 454d5fadaa88d645e9d1c2feec2c9d87c2af29c9
ms.sourcegitcommit: 331b8495e4ab37266945c81ff5b93d250bdaa6da
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 08/20/2020
ms.locfileid: "88645501"
---
# <a name="use-the-apache-spark-connector-for-sql-server-and-azure-sql"></a>Verwenden des Apache Spark-Connectors für SQL Server und Azure SQL

Der [Apache Spark-Connector für SQL Server und Azure SQL](https://github.com/microsoft/sql-spark-connector) ist ein Hochleistungsconnector, der es Ihnen ermöglicht, Transaktionsdaten in Big Data-Analysen zu verwenden und Ergebnisse für Ad-hoc-Abfragen oder Berichte zu speichern. Der Connector ermöglicht Ihnen die Verwendung einer beliebigen SQL-Datenbank (lokal oder in der Cloud) als Eingabedatenquelle oder als Ausgabedatensenke für Spark-Aufträge. Der Connector verwendet SQL Server-APIs für Massenschreibvorgänge. Alle Parameter für Massenschreibvorgänge können vom Benutzer als optionale Parameter übergeben werden und werden vom Connector unverändert an die zugrunde liegende API übergeben. Weitere Informationen zu Massenschreibvorgängen finden Sie unter [Verwenden von Massenkopieren mit dem JDBC Driver]( ../connect/jdbc/using-bulk-copy-with-the-jdbc-driver.md#sqlserverbulkcopyoptions).

Der Connector ist standardmäßig in Big Data-Clustern in SQL Server enthalten.

Weitere Informationen zum Connector finden Sie im [Open-Source-Repository](https://github.com/microsoft/sql-spark-connector). Beispiele finden Sie unter [Beispiele](https://github.com/microsoft/sql-spark-connector/tree/master/samples).

## <a name="write-to-a-new-sql-table"></a>Schreiben in eine neue SQL-Tabelle

>[!CAUTION]
> Im Modus `overwrite` löscht der Connector zuerst die Tabelle, wenn sie standardmäßig bereits in der Datenbank vorhanden ist. Verwenden Sie diese Option mit der gebotenen Sorgfalt, um unerwartete Datenverluste zu vermeiden.
> 
> Wenn Sie bei Verwendung des Modus `overwrite` nicht die Option `truncate` verwenden, gehen bei der erneuten Erstellung der Tabelle Indizes verloren. Beispielsweise wird eine Columnstore-Tabelle zu einem Heap. Wenn Sie die vorhandene Indizierung beibehalten möchten, müssen Sie auch die Option `truncate` mit dem Wert `true` angeben. Beispiel: `.option("truncate",true)`

```python
server_name = "jdbc:sqlserver://{SERVER_ADDR}"
database_name = "database_name"
url = server_name + ";" + "databaseName=" + database_name + ";"

table_name = "table_name"
username = "username"
password = "password123!#" # Please specify password here

try:
  df.write \
    .format("com.microsoft.sqlserver.jdbc.spark") \
    .mode("overwrite") \
    .option("url", url) \
    .option("dbtable", table_name) \
    .option("user", username) \
    .option("password", password) \
    .save()
except ValueError as error :
    print("Connector write failed", error)
```

## <a name="append-to-sql-table"></a>Anfügen an eine SQL-Tabelle
```python
try:
  df.write \
    .format("com.microsoft.sqlserver.jdbc.spark") \
    .mode("append") \
    .option("url", url) \
    .option("dbtable", table_name) \
    .option("user", username) \
    .option("password", password) \
    .save()
except ValueError as error :
    print("Connector write failed", error)
```

## <a name="specify-the-isolation-level"></a>Angeben der Isolationsstufe

Beim Durchführen der Masseneinfügung in die Datenbank verwendet dieser Connector standardmäßig die Isolationsstufe READ_COMMITTED. Wenn Sie diese in eine andere Isolationsstufe ändern möchten, verwenden Sie die Option `mssqlIsolationLevel` wie unten gezeigt.
```python
    .option("mssqlIsolationLevel", "READ_UNCOMMITTED") \
```

## <a name="read-from-sql-table"></a>Lesen aus einer SQL-Tabelle

```python
jdbcDF = spark.read \
        .format("com.microsoft.sqlserver.jdbc.spark") \
        .option("url", url) \
        .option("dbtable", table_name) \
        .option("user", username) \
        .option("password", password).load()
```

## <a name="non-active-directory-mode"></a>Nicht-Active Directory-Modus

Im Nicht-Active Directory-Sicherheitsmodus verfügt jeder Benutzer über einen Benutzernamen und ein Kennwort. Diese Angaben müssen bei der Instanziierung des Connectors als Parameter angegeben werden, um Lese- und/oder Schreibvorgänge ausführen zu können.

Nachfolgend finden Sie ein Beispiel für die Connectorinstanziierung im Nicht-Active Directory-Modus. Ersetzen Sie vor dem Ausführen des Skripts die `?` durch die jeweiligen Werte für Ihr Konto.

```python
# Note: '?' is a placeholder for a necessary user-specified value
connector_type = "com.microsoft.sqlserver.jdbc.spark" 

url = "jdbc:sqlserver://master-p-svc;databaseName=?;"
writer = df.write \ 
   .format(connector_type)\ 
   .mode("overwrite") 
   .option("url", url) \ 
   .option("user", ?) \ 
   .option("password",?) 
writer.save() 
```

## <a name="active-directory-mode"></a>Active Directory-Modus

Im Active Directory-Sicherheitsmodus muss der Benutzer nach dem Generieren einer Schlüsseltabellendatei die Parameter `principal` und `keytab` bei der Containerinstanziierung angeben.

In diesem Modus lädt der Treiber die Schlüsseltabellendatei in die entsprechenden Executor-Container. Dann verwenden die Executor-Container den Prinzipalnamen und die Schlüsseltabelle, um ein Token zu generieren, das zum Erstellen eines JDBC-Connectors für Lese-/Schreibvorgänge verwendet wird.

Nachfolgend finden Sie ein Beispiel für die Connectorinstanziierung im Active Directory-Modus. Ersetzen Sie vor dem Ausführen des Skripts die `?` durch die jeweiligen Werte für Ihr Konto.

```python
# Note: '?' is a placeholder for a necessary user-specified value
connector_type = "com.microsoft.sqlserver.jdbc.spark"

url = "jdbc:sqlserver://master-p-svc;databaseName=?;integratedSecurity=true;authenticationScheme=JavaKerberos;" 
writer = df.write \ 
   .format(connector_type)\ 
   .mode("overwrite") 
   .option("url", url) \ 
   .option("principal", ?) \ 
   .option("keytab", ?)   

writer.save() 
```

## <a name="next-steps"></a>Nächste Schritte

Weitere Informationen zu Big Data-Cluster finden Sie unter [Vorgehensweise: Bereitstellen von [!INCLUDE[big-data-clusters-2019](../includes/ssbigdataclusters-ss-nover.md)] auf Kubernetes](deployment-guidance.md).

Haben Sie Feedback oder Featurevorschläge für SQL Server-Big Data-Cluster? [Senden Sie uns eine Nachricht über Feedback zu Big Data-Cluster für SQL Server.](https://aka.ms/sql-server-bdc-feedback)
