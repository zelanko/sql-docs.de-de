---
title: Verwenden von gespeicherten Prozeduren mit Eingabeparametern | Microsoft-Dokumentation
ms.custom: ''
ms.date: 07/11/2018
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: 8f491b70-7d1b-42bd-964f-9a8b86af5eaa
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: a2b85c7ff9943f2c83109b18000adf7c2456b7a7
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MTE75
ms.contentlocale: de-DE
ms.lasthandoff: 10/01/2018
ms.locfileid: "47635048"
---
# <a name="using-a-stored-procedure-with-input-parameters"></a>Verwenden von gespeicherten Prozeduren mit Eingabeparametern

[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

Eine aufrufbare gespeicherte [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Prozedur enthält mindestens einen IN-Parameter, über den Daten an die gespeicherte Prozedur übergeben werden können. Die [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)] bietet die [SQLServerPreparedStatement](../../connect/jdbc/reference/sqlserverpreparedstatement-class.md) -Klasse, die Sie verwenden können, um diese Art von gespeicherter Prozedur aufzurufen und zum Verarbeiten der Daten, die zurückgegeben.

Wenn Sie eine gespeicherte Prozedur mit IN-Parametern mit dem JDBC-Treiber aufrufen, müssen Sie die `call`-SQL-Escapesequenz zusammen mit der [prepareCall](../../connect/jdbc/reference/preparecall-method-sqlserverconnection.md)-Methode der [SQLServerConnection](../../connect/jdbc/reference/sqlserverconnection-class.md)-Klasse verwenden. Die Syntax für die `call`-Escapesequenz mit IN-Parameter lautet wie folgt:

`{call procedure-name[([parameter][,[parameter]]...)]}`

> [!NOTE]  
> Weitere Informationen zu SQL-Escapesequenzen, finden Sie unter [mithilfe von SQL-Escapesequenzen](../../connect/jdbc/using-sql-escape-sequences.md).

Geben Sie die IN-Parameter beim Erstellen der `call`-Escapesequenz mit dem Fragezeichen (?) an. das als Platzhalter für die Parameterwerte fungiert, die an die gespeicherte Prozedur übergeben werden. Um einen Wert für einen Parameter angeben, können Sie eine der Setter-Methoden der SQLServerPreparedStatement-Klasse. Die verwendbare Festlegungsmethode hängt vom Datentyp des IN-Parameters ab.

Wenn Sie einen Wert an die Festlegungsmethode übergeben, müssen Sie nicht nur den Wert angeben, der im Parameter verwendet wird, sondern auch die ordinale Position des Parameters in der gespeicherten Prozedur. Wenn die gespeicherte Prozedur beispielsweise einen einzigen IN-Parameter enthält, ist der Ordinalwert "1". Wenn die gespeicherte Prozedur zwei Parameter enthält, ist der erste Ordinalwert "1" und der zweite Ordinalwert "2".

Ein Beispiel für den Aufruf einer gespeicherten Prozedur mit einem IN-Parameter enthält die gespeicherte Prozedur „uspGetEmployeeManagers“ in der [!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal_md.md)]-Beispieldatenbank. Diese gespeicherte Prozedur übernimmt einen einzelnen Eingabeparameter mit dem Namen "EmployeeID" (integer-Wert) und gibt abhängig von der angegebenen "EmployeeID" eine rekursive Liste der Mitarbeiter und deren Vorgesetzten zurück. Der Java-Code für den Aufruf dieser gespeicherten Prozedur sieht folgendermaßen aus:

```java
public static void executeSprocInParams(Connection con) throws SQLException {  
    try(PreparedStatement pstmt = con.prepareStatement("{call dbo.uspGetEmployeeManagers(?)}"); ) {  

        pstmt.setInt(1, 50);  
        ResultSet rs = pstmt.executeQuery();  

        while (rs.next()) {  
            System.out.println("EMPLOYEE:");  
            System.out.println(rs.getString("LastName") + ", " + rs.getString("FirstName"));  
            System.out.println("MANAGER:");  
            System.out.println(rs.getString("ManagerLastName") + ", " + rs.getString("ManagerFirstName"));  
            System.out.println();  
        }  
    }
}
```

## <a name="see-also"></a>Weitere Informationen finden Sie unter

[Verwenden von Anweisungen mit gespeicherten Prozeduren](../../connect/jdbc/using-statements-with-stored-procedures.md)
