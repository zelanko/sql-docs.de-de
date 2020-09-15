---
description: Verwenden des Sql_variant-Datentyps
title: Verwenden des Sql_variant-Datentyps | Microsoft-Dokumentation
ms.custom: ''
ms.date: 08/12/2019
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: ''
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: bf29942e5d427a4a4852a6d1a856d81765690050
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 08/17/2020
ms.locfileid: "88414526"
---
# <a name="using-sql_variant-data-type"></a>Verwenden des Sql_variant-Datentyps

[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

Ab Version 6.3.0 unterstützt der JDBC-Treiber den Datentyp sql_variant. Sql_variant wird bei Verwendung von Features wie Tabellenwertparametern und BulkCopy ebenfalls unterstützt, allerdings gelten in diesem Fall einige Einschränkungen, die später in diesem Artikel erläutert werden. Nicht alle Datentypen können im sql_variant-Datentyp gespeichert werden. Eine Liste der unterstützten Datentypen, die mit sql_variant verwendet werden können, finden Sie in der SQL Server-[Dokumentation](https://docs.microsoft.com/sql/t-sql/data-types/sql-variant-transact-sql).

##  <a name="populating-and-retrieving-a-table"></a>Auffüllen und Abrufen einer Tabelle:
Angenommen, eine Tabelle enthält eine sql_variant-Spalte wie diese:

```sql
CREATE TABLE sampleTable (col1 sql_variant)  
```

Nachfolgend ist ein Beispielskript zum Einfügen von Werten mithilfe einer Anweisung gezeigt:

```java
try (Statement stmt = connection.createStatement()){
    stmt.execute("insert into sampleTable values (1)");
}
```

So fügen Sie Werte mit einer vorbereiteten Anweisung ein:

```java
try (PreparedStatement preparedStatement = con.prepareStatement("insert into sampleTable values (?)")) {
    preparedStatement.setObject(1, 1);  
    preparedStatement.execute();
}
```      

Wenn der zugrunde liegende Typ der Daten, die übergeben werden, bekannt ist, kann der entsprechende Setter verwendet werden. Beispiel: Beim Einfügen eines ganzzahligen Werts kann `preparedStatement.setInt()` verwendet werden.

```java
try (PreparedStatement preparedStatement = con.prepareStatement("insert into table values (?)")) {
    preparedStatement.setInt (1, 1);
    preparedStatement.execute();
}
```

Um Werte aus der Tabelle zu lesen, können die entsprechenden Getter verwendet werden. Wenn die vom Server empfangenen Werte bekannt sind, kann z.B. die Methode `getInt()` oder `getString()` verwendet werden:    

```java
try (SQLServerResultSet resultSet = (SQLServerResultSet) stmt.executeQuery("select * from sampleTable ")) {
    resultSet.next();          
    resultSet.getInt(1); //or rs.getString(1); or rs.getObject(1);
}
```

## <a name="using-stored-procedures-with-sql_variant"></a>Verwenden von gespeicherten Prozeduren mit sql_variant:   
Gehen wir von folgender gespeicherter Prozedur aus:     

```java
String sql = "CREATE PROCEDURE " + inputProc + " @p0 sql_variant OUTPUT AS SELECT TOP 1 @p0=col1 FROM sampleTable ";
``` 
    
Ausgabeparameter müssen registriert werden:

```java
try (CallableStatement callableStatement = con.prepareCall(" {call " + inputProc + " (?) }")) {
    callableStatement.registerOutParameter(1, microsoft.sql.Types.SQL_VARIANT);      
    callableStatement.execute();
}
```

## <a name="limitations-of-sql_variant"></a>Einschränkungen von sql_variant:
- Bei Verwendung von Tabellenwertparametern zum Auffüllen einer Tabelle mit einem Wert `datetime`/`smalldatetime`/`date`, der in einem sql_variant-Datentyp gespeichert ist, kann `getDateTime()`/`getSmallDateTime()`/`getDate()` nicht für ein Resultset aufgerufen werden. Der Vorgang wird mit folgender Ausnahme abgebrochen:
    
    `Java.lang.String cannot be cast to java.sql.Timestamp`
   
    Problemumgehung: Verwenden Sie stattdessen `getString()` oder `getObject()`. 
    
- Das Verwenden von Tabellenwertparametern und Senden eines NULL-Werts in einem sql_variant-Datentyp wird nicht unterstützt. Der Vorgang wird mit folgender Ausnahme abgebrochen:
    
    `Inserting null value with column type sql_variant in TVP is not supported.`

## <a name="see-also"></a>Weitere Informationen

[Grundlegendes zu den Datentypen des JDBC-Treibers](../../connect/jdbc/understanding-the-jdbc-driver-data-types.md)  
