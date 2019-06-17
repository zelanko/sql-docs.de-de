---
title: Verwenden von Sql_variant-Datentyp | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/28/2019
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: ''
author: MightyPen
ms.author: genemi
manager: jroth
ms.openlocfilehash: c004bc40ed0c85b82612be9069e1a53041c8095c
ms.sourcegitcommit: ad2e98972a0e739c0fd2038ef4a030265f0ee788
ms.translationtype: MTE75
ms.contentlocale: de-DE
ms.lasthandoff: 06/07/2019
ms.locfileid: "66798591"
---
# <a name="using-sqlvariant-data-type"></a>Verwenden des sql_variant-Datentyps

[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

Ab Version 6.3.0 unterstützt der JDBC-Treiber für den Sql_variant-Datentyp. Sql_variant wird ebenfalls unterstützt, wenn diese Seite mithilfe von Funktionen wie Tabellenwertparameter und BulkCopy mit einigen Einschränkungen später erwähnt werden. Nicht alle Datentypen können in den Sql_variant-Datentyp gespeichert werden. Eine Liste der unterstützten Datentypen mit Sql_variant, überprüfen Sie den SQL-Server [Docs](https://docs.microsoft.com/sql/t-sql/data-types/sql-variant-transact-sql).

##  <a name="populating-and-retrieving-a-table"></a>Auffüllen und eine Tabelle abrufen:
Angenommen, eine enthält eine Tabelle mit Sql_variant-Spalte als:

```sql
CREATE TABLE sampleTable (col1 sql_variant)  
```

Ein Beispielskript zum Einfügen von Werten, die using-Anweisung:

```java
try (Statement stmt = connection.createStatement()){
    stmt.execute("insert into sampleTable values (1)");
}
```

Einfügen von Wert mit vorbereiteten Anweisung:

```java
try (PreparedStatement preparedStatement = con.prepareStatement("insert into sampleTable values (?)")) {
    preparedStatement.setObject(1, 1);  
    preparedStatement.execute();
}
```      

Wenn der zugrunde liegende Typ der übergebenen Daten bekannt ist, kann der entsprechende Setter verwendet werden. Z. B. `preparedStatement.setInt()` kann verwendet werden, wenn Sie einen ganzzahligen Wert einfügen.

```java
try (PreparedStatement preparedStatement = con.prepareStatement("insert into table values (?)")) {
    preparedStatement.setInt (1, 1);
    preparedStatement.execute();
}
```

Zum Lesen von Werten aus der Tabelle, können der jeweiligen Getter verwendet werden. Z. B. `getInt()` oder `getString()` Methoden können verwendet werden, wenn die Werte, die vom Server bekannt sind:    

```java
try (SQLServerResultSet resultSet = (SQLServerResultSet) stmt.executeQuery("select * from sampleTable ")) {
    resultSet.next();          
    resultSet.getInt(1); //or rs.getString(1); or rs.getObject(1);
}
```

## <a name="using-stored-procedures-with-sqlvariant"></a>Verwenden von gespeicherten Prozeduren mit Sql_variant:   
Wenn Sie z. B. eine gespeicherte Prozedur:     

```java
String sql = "CREATE PROCEDURE " + inputProc + " @p0 sql_variant OUTPUT AS SELECT TOP 1 @p0=col1 FROM sampleTable ";
``` 
    
Output-Parameter müssen registriert werden:

```java
try (CallableStatement callableStatement = con.prepareCall(" {call " + inputProc + " (?) }")) {
    callableStatement.registerOutParameter(1, microsoft.sql.Types.SQL_VARIANT);      
    callableStatement.execute();
}
```

## <a name="limitations-of-sqlvariant"></a>Einschränkungen von Sql_variant:
- Wenn Sie TVP zum Auffüllen einer Tabelle mit einer `datetime` / `smalldatetime` / `date` in Sql_variant, gespeicherten Wert aufrufen `getDateTime()` / `getSmallDateTime()` / `getDate()` auf eine ResultSet kann nicht verwendet werden, und es wird die folgende Ausnahme ausgelöst:
    
    `Java.lang.String cannot be cast to java.sql.Timestamp`
   
    Problemumgehung: Verwenden Sie `getString()` oder `getObject()` stattdessen. 
    
- Verwenden TVP zum Auffüllen einer Tabelle, und senden einen null-Wert in einer Sql_variant wird nicht unterstützt und löst eine Ausnahme aus:
    
    `Inserting null value with column type sql_variant in TVP is not supported.`

## <a name="see-also"></a>Weitere Informationen

[Grundlegendes zu den Datentypen in JDBC Driver](../../connect/jdbc/understanding-the-jdbc-driver-data-types.md)  
