---
title: Using sql_variant Data Type | Microsoft-Dokumentation
ms.custom: ''
ms.date: 08/12/2019
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: ''
author: MightyPen
ms.author: genemi
ms.openlocfilehash: cdede5d41d5ad7fc22cfed3f1efa9f95612032ca
ms.sourcegitcommit: 9348f79efbff8a6e88209bb5720bd016b2806346
ms.translationtype: MTE75
ms.contentlocale: de-DE
ms.lasthandoff: 08/14/2019
ms.locfileid: "69025841"
---
# <a name="using-sql_variant-data-type"></a>Verwenden des Sql_variant-Datentyps

[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

Ab Version 6.3.0 unterstützt der JDBC-Treiber den sql_variant-Datentyp. Sql_variant wird auch unterstützt, wenn Features wie Tabellenwert Parameter und bulkcopy mit einigen Einschränkungen weiter unten auf dieser Seite verwendet werden. Nicht alle Datentypen können im sql_variant-Datentyp gespeichert werden. Eine Liste der unterstützten Datentypen mit sql_variant finden Sie in den [SQL Server](https://docs.microsoft.com/sql/t-sql/data-types/sql-variant-transact-sql)-Dokumentation.

##  <a name="populating-and-retrieving-a-table"></a>Auffüllen und Abrufen einer Tabelle:
Angenommen, eine Tabelle enthält eine Tabelle mit einer sql_variant-Spalte wie:

```sql
CREATE TABLE sampleTable (col1 sql_variant)  
```

Ein Beispielskript zum Einfügen von Werten mithilfe der-Anweisung:

```java
try (Statement stmt = connection.createStatement()){
    stmt.execute("insert into sampleTable values (1)");
}
```

Einfügen von Werten mithilfe der vorbereiteten Anweisung:

```java
try (PreparedStatement preparedStatement = con.prepareStatement("insert into sampleTable values (?)")) {
    preparedStatement.setObject(1, 1);  
    preparedStatement.execute();
}
```      

Wenn der zugrunde liegende Typ der zu über gebenden Daten bekannt ist, kann der entsprechende Setter verwendet werden. Kann beispielsweise `preparedStatement.setInt()` verwendet werden, wenn ein ganzzahliger Wert eingefügt wird.

```java
try (PreparedStatement preparedStatement = con.prepareStatement("insert into table values (?)")) {
    preparedStatement.setInt (1, 1);
    preparedStatement.execute();
}
```

Zum Lesen von Werten aus der Tabelle können die entsprechenden Getter verwendet werden. Beispielsweise können `getInt()` - `getString()` oder-Methoden verwendet werden, wenn die vom Server kommenden Werte bekannt sind:    

```java
try (SQLServerResultSet resultSet = (SQLServerResultSet) stmt.executeQuery("select * from sampleTable ")) {
    resultSet.next();          
    resultSet.getInt(1); //or rs.getString(1); or rs.getObject(1);
}
```

## <a name="using-stored-procedures-with-sql_variant"></a>Verwenden von gespeicherten Prozeduren mit sql_variant:   
Eine gespeicherte Prozedur wie z. b.:     

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
- Bei Verwendung von TVP zum Auffüllen einer Tabelle mit einem `datetime` `smalldatetime` `getSmallDateTime()` / `getDateTime()` / `date` / Wert, der in einem sql_variant gespeichert ist, wird beim Aufrufen / `getDate()` von für einen Resultset funktioniert nicht und löst die folgende Ausnahme aus:
    
    `Java.lang.String cannot be cast to java.sql.Timestamp`
   
    Problem Umgehung: `getString()` verwenden `getObject()` Sie stattdessen oder. 
    
- Die Verwendung von TVP zum Auffüllen einer Tabelle und das Senden eines NULL-Werts in einem sql_variant-Objekt wird nicht unterstützt und löst eine Ausnahme aus:
    
    `Inserting null value with column type sql_variant in TVP is not supported.`

## <a name="see-also"></a>Siehe auch

[Grundlegendes zu den Datentypen des JDBC-Treibers](../../connect/jdbc/understanding-the-jdbc-driver-data-types.md)  
