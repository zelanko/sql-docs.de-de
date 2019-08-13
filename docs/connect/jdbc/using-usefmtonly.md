---
title: Abrufen von parametermetadata über USEF | Microsoft-Dokumentation
ms.custom: ''
ms.date: 07/31/2019
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: ''
caps.latest.revision: ''
author: rene-ye
ms.author: v-reye
manager: kenvh
ms.openlocfilehash: 29ee2c5c22baf77b6994a440f1d9d442ba2b812a
ms.sourcegitcommit: a1adc6906ccc0a57d187e1ce35ab7a7a951ebff8
ms.translationtype: MTE75
ms.contentlocale: de-DE
ms.lasthandoff: 08/09/2019
ms.locfileid: "68894092"
---
# <a name="retrieving-parametermetadata-via-usefmtonly"></a>Abrufen von parametermetadata über USEF
[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

  Der Microsoft JDBC-Treiber für SQL Server bietet eine alternative Möglichkeit, Parameter Metadaten vom Server, **usefmtonly**, abzufragen. Diese Funktion wurde erstmals in Version 7,4 des Treibers eingeführt und ist als Problem Umgehung für bekannte Probleme in `sp_describe_undeclared_parameters`erforderlich.
  
  Der Treiber verwendet die gespeicherte Prozedur `sp_describe_undeclared_parameters` primär zum Abfragen von Parameter Metadaten, da dies die empfohlene Vorgehensweise für das Abrufen von Parameter Metadaten in den meisten Fällen ist. Das Ausführen der gespeicherten Prozedur schlägt jedoch in den folgenden Anwendungsfällen fehl:
  
-   Für Always Encrypted Spalten
  
-   Für temporäre Tabellen und Tabellenvariablen
  
-   Gegen Sichten 
  
  Die vorgeschlagene Lösung für diese Anwendungsfälle besteht darin, die SQL-Abfrage des Benutzers für Parameter und Tabellen Ziele zu analysieren und dann `SELECT` eine Abfrage `FMTONLY` mit aktiviertem auszuführen. Mit dem folgenden Code Ausschnitt können Sie die Funktion visualisieren.
  
```sql
--create a normal table 'Foo' and a temporary table 'Bar'
CREATE TABLE Foo(c1 int);
CREATE TABLE #Bar(c1 int);

EXEC sp_describe_undeclared_parameters N'SELECT * FROM Foo WHERE c1 = @p0' --works fine
EXEC sp_describe_undeclared_parameters N'SELECT * FROM #Bar WHERE c1 = @p0' --fails with "Invalid object name '#Bar'"

SET FMTONLY ON;
SELECT c1 FROM Foo; --works
SET FMTONLY OFF;
SET FMTONLY ON;
SELECT c1 FROM #Bar; --works
SET FMTONLY OFF;
```
 
## <a name="turning-the-feature-onoff"></a>Aktivieren/Deaktivieren des Features 
 Die Funktion **usefmtonly** ist standardmäßig deaktiviert. Benutzer können diese Funktion über die Verbindungs Zeichenfolge aktivieren `useFmtOnly=true`, indem Sie angeben. Beispiel: `jdbc:sqlserver://<server>:<port>;databaseName=<databaseName>;user=<user>;password=<password>;useFmtOnly=true;`.
 
 Alternativ ist die Funktion über `SQLServerDataSource`verfügbar.
 ```java
SQLServerDataSource ds = new SQLServerDataSource();
ds.setServerName(<server>);
ds.setPortNumber(<port>);
ds.setDatabaseName("<databaseName>");
ds.setUser("<user>");
ds.setPassword("<password>");
ds.setUseFmtOnly(true);
try (Connection c = ds.getConnection()) {
    // do work with connection
}
 ```
 
 Die Funktion ist auch auf der Anweisungs Ebene verfügbar. Benutzer können das Feature durch `PreparedStatement.setUseFmtOnly(boolean)`aktivieren/deaktivieren.
> [!NOTE]  
>  Der Treiber priorisiert die Eigenschaft auf Anweisungs Ebene über die Eigenschaft der Verbindungs Ebene.

## <a name="using-the-feature"></a>Verwenden des Features
  Sobald die Funktion aktiviert ist, verwendet der Treiber intern das neue Feature anstelle `sp_describe_undeclared_parameters` von, wenn Parameter Metadaten abgefragt werden. Für den Endbenutzer sind keine weiteren Aktionen erforderlich.
```java
final String sql = "INSERT INTO #Bar VALUES (?)";
try (Connection c = DriverManager.getConnection(URL, USERNAME, PASSWORD)) {
    try (Statement s = c.createStatement()) {
        s.execute("CREATE TABLE #Bar(c1 int)");
    }
    try (PreparedStatement p1 = c.prepareStatement(sql); PreparedStatement p2 = c.prepareStatement(sql)) {
        ((SQLServerPreparedStatement) p1).setUseFmtOnly(true);
        ParameterMetaData pmd1 = p1.getParameterMetaData();
        System.out.println(pmd1.getParameterTypeName(1)); // prints int
        ParameterMetaData pmd2 = p2.getParameterMetaData(); // throws exception, Invalid object name '#Bar'
    }
}
```
> [!NOTE]  
>  Die Funktion unterstützt `SELECT/INSERT/UPDATE/DELETE` nur Abfragen. Abfragen sollten mit einem der vier unterstützten Schlüsselwörter oder einem [allgemeinen Tabellen Ausdruck](https://docs.microsoft.com/sql/t-sql/queries/with-common-table-expression-transact-sql?view=sql-server-2017) beginnen, gefolgt von einer der unterstützten Abfragen. Parameter in allgemeinen Tabellen Ausdrücken werden nicht unterstützt.

## <a name="known-issues"></a>Bekannte Probleme
  Es gibt derzeit einige Probleme mit diesem Feature, die auf Mängel in der SQL-Analyselogik zurückzuführen sind. Diese Probleme können in einem zukünftigen Update für das Feature behoben werden und sind im folgenden zusammen mit Vorschlägen zur Problem Umgehung dokumentiert.
  
A. Verwenden eines "Vorwärts deklarierten" Alias
```sql
CREATE TABLE Foo(c1 int)

DELETE fooAlias FROM Foo fooAlias WHERE c1 > ?; --Invalid object name 'fooAlias'

--Workaround #1: Specify AS keyword
DELETE fooAlias FROM Foo AS fooAlias WHERE c1 > ?;
--Workaround #2: Use the table name
DELETE Foo FROM Foo fooAlias WHERE c1 > ?;
```

B. Mehrdeutiger Spalten Name, wenn Tabellen Spaltennamen aufweisen
```sql
CREATE TABLE Foo(c1 int, c2 int, c3 int)
CREATE TABLE Bar(c1 int, c2 int, c3 int)

SELECT c1,c2 FROM Foo WHERE c3 IN (SELECT c3 FROM Bar WHERE c1 > ? and c2 < ? and c3 = ?); --Ambiguous Column Name

--Workaround: Use aliases
SELECT c1,c2 FROM Foo WHERE c3 IN (SELECT c3 FROM Bar b WHERE b.c1 = ? and b.c2 = ? and b.c3 = ?);
```

C. Aus einer Unterabfrage mit Parametern auswählen
```sql

CREATE TABLE Foo(c1 int)

SELECT * FROM (SELECT * FROM Foo WHERE c1 = ?) WHERE c1 = ?; --Incorrect syntax near '?'

--Workaround: N/A
```

D. Unterabfragen in einer SET-Klausel
```sql
CREATE TABLE Foo(c1 int)

UPDATE Foo SET c1 = (SELECT c1 FROM Foo) WHERE c1 = ?; --Incorrect syntax near ')'

--Workaround: Add a 'delimiting' condition
UPDATE Foo SET c1 = (SELECT c1 FROM Foo HAVING (HASH JOIN)) WHERE c1 = ?;
```

## <a name="see-also"></a>Siehe auch  
 [Festlegen von Verbindungseigenschaften](../../connect/jdbc/setting-the-connection-properties.md)  
  
  
