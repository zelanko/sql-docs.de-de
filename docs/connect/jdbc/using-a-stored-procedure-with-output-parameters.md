---
title: Verwenden von gespeicherten Prozeduren mit Ausgabeparametern | Microsoft-Dokumentation
ms.custom: ''
ms.date: 08/12/2019
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: 1c006f27-7e99-43d5-974c-7b782659290c
author: MightyPen
ms.author: genemi
ms.openlocfilehash: efafaa709666620e7237f2481c392aba25dfd5f8
ms.sourcegitcommit: b78f7ab9281f570b87f96991ebd9a095812cc546
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/31/2020
ms.locfileid: "69026831"
---
# <a name="using-a-stored-procedure-with-output-parameters"></a>Verwenden von gespeicherten Prozeduren mit Ausgabeparametern

[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

Eine aufrufbare gespeicherte [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Prozedur gibt mindestens einen OUT-Parameter zurück, mit dem die gespeicherte Prozedur Daten an die aufrufende Anwendung zurückgibt. [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)] stellt die Klasse [SQLServerCallableStatement](../../connect/jdbc/reference/sqlservercallablestatement-class.md) bereit, die Sie verwenden können, um diese Art gespeicherte Prozedur aufzurufen und die zurückgegebenen Daten zu verarbeiten.

Wenn Sie diese Art von gespeicherter Prozedur mit dem JDBC-Treiber aufrufen, müssen Sie die SQL-Escapesequenz `call` zusammen mit der [prepareCall](../../connect/jdbc/reference/preparecall-method-sqlserverconnection.md)-Methode der [SQLServerConnection](../../connect/jdbc/reference/sqlserverconnection-class.md)-Klasse verwenden. Die Syntax für die Escapesequenz `call` mit OUT-Parameter lautet wie folgt:

`{call procedure-name[([parameter][,[parameter]]...)]}`

> [!NOTE]  
> Weitere Informationen zu SQL-Escapesequenzen finden Sie unter [Verwenden von SQL-Escapesequenzen](../../connect/jdbc/using-sql-escape-sequences.md).

Geben Sie die OUT-Parameter beim Erstellen der Escapesequenz `call` mit dem Fragezeichen (?) an. das als Platzhalter für die Parameterwerte fungiert, die von der gespeicherten Prozedur zurückgegeben werden. Sie müssen den Datentyp für jeden Parameter angeben, um einen Wert für einen OUT-Parameter festzulegen, indem Sie die Methode [registerOutParameter](../../connect/jdbc/reference/registeroutparameter-method-sqlservercallablestatement.md) der Klasse „SQLServerCallableStatement“ verwenden, bevor Sie die gespeicherte Prozedur ausführen.

Bei dem Wert, den Sie für den OUT-Parameter in der Methode „registerOutParameter“ angeben, muss es sich um einen der in java.sql.Types enthaltenen JDBC-Datentypen handeln, der wiederum einem der nativen [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Datentypen zugeordnet wird. Weitere Informationen zum JDBC-Treiber und [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Datentypen finden Sie unter [Grundlegendes zu den Datentypen des JDBC-Treibers](../../connect/jdbc/understanding-the-jdbc-driver-data-types.md).

Wenn Sie einen Wert an die Methode „registerOutParameter“ für einen OUT-Parameter übergeben, müssen Sie nicht nur den für den Parameter zu verwendenden Datentyp angeben, sondern auch die ordinale Position des Parameters oder den Namen des Parameters der gespeicherten Prozedur. Wenn die gespeicherte Prozedur beispielsweise einen einzigen OUT-Parameter enthält, ist der Ordinalwert 1. Wenn die gespeicherte Prozedur zwei Parameter enthält, ist der erste Ordinalwert 1 und der zweite Ordinalwert 2.

> [!NOTE]  
> Die Verwendung der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Datentypen CURSOR, SQLVARIANT, TABLE und TIMESTAMP für OUT-Parameter wird vom JDBC-Treiber nicht unterstützt.

Erstellen Sie als Beispiel die folgende Prozedur in der [!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal_md.md)]-Beispieldatenbank:

```sql
CREATE PROCEDURE GetImmediateManager  
   @employeeID INT,  
   @managerID INT OUTPUT  
AS  
BEGIN  
   SELECT @managerID = ManagerID
   FROM HumanResources.Employee
   WHERE EmployeeID = @employeeID  
END
```

Diese gespeicherte Prozedur gibt abhängig vom angegebenen IN-Parameter "employeeID" (ein integer-Wert) einen einzigen OUT-Parameter "managerID" zurück (ebenfalls ein integer-Wert). Bei dem im OUT-Parameter zurückgegebenen Wert handelt es sich um die auf "EmployeeID" basierende "ManagerID", die in der Tabelle "HumanResources.Employee" enthalten ist.

Im folgenden Beispiel werden eine offene Verbindung zur [!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal_md.md)]-Beispieldatenbank an die Funktion übergeben und die gespeicherte Prozedur „GetImmediateManager“ mit der [execute](../../connect/jdbc/reference/execute-method-sqlserverstatement.md)-Methode aufgerufen:

```java
public static void executeStoredProcedure(Connection con) throws SQLException {  
    try(CallableStatement cstmt = con.prepareCall("{call dbo.GetImmediateManager(?, ?)}");) {  
        cstmt.setInt(1, 5);  
        cstmt.registerOutParameter(2, java.sql.Types.INTEGER);  
        cstmt.execute();  
        System.out.println("MANAGER ID: " + cstmt.getInt(2));  
    }  
}
```

In diesem Beispiel werden die Ordnungspositionen verwendet, um die Parameter zu identifizieren. Alternativ können Sie einen Parameter mit seinem Namen anstelle der Ordnungsposition identifizieren. Im folgenden Codebeispiel wird das vorhergehende Beispiel geändert, um die Verwendung von benannten Parametern in einer Java-Anwendung zu veranschaulichen. Beachten Sie, dass die Parameternamen den Parameternamen in der Definition der gespeicherten Prozedur entsprechen:

```java
public static void executeStoredProcedure(Connection con) throws SQLException {  
    try(CallableStatement cstmt = con.prepareCall("{call dbo.GetImmediateManager(?, ?)}"); ) {  
        cstmt.setInt("employeeID", 5);  
        cstmt.registerOutParameter("managerID", java.sql.Types.INTEGER);  
        cstmt.execute();  
        System.out.println("MANAGER ID: " + cstmt.getInt("managerID"));  
    }  
}
```

> [!NOTE]  
> In diesen Beispielen wird die execute-Methode der SQLServerCallableStatement-Klasse zum Ausführen der gespeicherten Prozedur verwendet. da von der gespeicherten Prozedur nicht auch ein Resultset zurückgegeben wurde. Andernfalls müsste die [executeQuery](../../connect/jdbc/reference/executequery-method-sqlserverstatement.md)-Methode verwendet werden.

Gespeicherte Prozeduren können Updatezählungen und mehrere Resultsets zurückgeben. Der [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)] folgt der JDBC 3.0-Spezifikation, die angibt, dass mehrere Resultsets und Updatezählungen vor dem Abrufen der OUT-Parameter abgerufen werden sollten. Dies bedeutet, dass die Anwendung alle ResultSet-Objekte und Updatezählungen abrufen sollte, bevor die OUT-Parameter mit den CallableStatement.getter-Methoden abgerufen werden. Andernfalls gehen die noch nicht abgerufenen ResultSet-Objekte und Updatezählungen verloren, wenn die OUT-Parameter abgerufen werden. Weitere Informationen zu Updatezählungen und mehreren Resultsets finden Sie unter [Verwenden einer gespeicherten Prozedur mit aktualisierten Zählerwerten](../../connect/jdbc/using-a-stored-procedure-with-an-update-count.md) und [Verwenden mehrerer Resultsets](../../connect/jdbc/using-multiple-result-sets.md).

## <a name="see-also"></a>Weitere Informationen

[Verwenden von Anweisungen mit gespeicherten Prozeduren](../../connect/jdbc/using-statements-with-stored-procedures.md)
