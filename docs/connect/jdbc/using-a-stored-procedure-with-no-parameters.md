---
title: Verwenden von gespeicherten Prozeduren ohne Parameter | Microsoft-Dokumentation
ms.custom: ''
ms.date: 07/11/2018
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: e9470a6d-a758-4c56-96ec-7b37139e36a7
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 3dade70a033ddf2a9e20ffc09930a27e26d9a579
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MTE75
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "67916498"
---
# <a name="using-a-stored-procedure-with-no-parameters"></a>Verwenden von gespeicherten Prozeduren ohne Parameter

[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

Die einfachste Art einer gespeicherten [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Prozedur, die aufgerufen werden kann, enthält keine Parameter und gibt ein einziges Resultset zurück. Der [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)] stellt die [SQLServerStatement](../../connect/jdbc/reference/sqlserverstatement-class.md) -Klasse bereit, die Sie verwenden können, um diese Art von gespeicherter Prozedur aufzurufen und die zurückgegebenen Daten zu verarbeiten.

Wenn Sie mit dem JDBC-Treiber eine gespeicherte Prozedur ohne Parameter aufrufen möchten, müssen Sie die `call`-SQL-Escapesequenz verwenden. Die Syntax für die `call`-Escapesequenz ohne Parameter lautet folgendermaßen:

`{call procedure-name}`

> [!NOTE]  
> Weitere Informationen zu den SQL-Escapesequenzen finden [Sie unter Verwenden von SQL](../../connect/jdbc/using-sql-escape-sequences.md)-Escapesequenzen.

Erstellen Sie als Beispiel die folgende Prozedur in der [!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal_md.md)]-Beispieldatenbank:

```sql
CREATE PROCEDURE GetContactFormalNames
AS  
BEGIN  
   SELECT TOP 10 Title + ' ' + FirstName + ' ' + LastName AS FormalName
   FROM Person.Contact  
END  
```

Diese gespeicherte Prozedur gibt ein einzelnes Resultset zurück, das eine Datenspalte enthält, bei der es sich um eine Kombination aus Titel, Vorname und Nachname der ersten zehn Kontakte in der Tabelle „Person.Contact“ handelt.

Im folgenden Beispiel wird eine offene Verbindung zur [!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal_md.md)]-Beispieldatenbank an die Funktion übergeben, und die gespeicherte Prozedur „GetContactFormalNames“ wird mit der [executeQuery](../../connect/jdbc/reference/executequery-method-sqlserverstatement.md)-Methode aufgerufen.

```java
public static void executeSprocNoParams(Connection con) throws SQLException {  
    try(Statement stmt = con.createStatement();) {  

        ResultSet rs = stmt.executeQuery("{call dbo.GetContactFormalNames}");  
        while (rs.next()) {  
            System.out.println(rs.getString("FormalName"));  
        }  
    }  
}
```

## <a name="see-also"></a>Weitere Informationen

[Verwenden von Anweisungen mit gespeicherten Prozeduren](../../connect/jdbc/using-statements-with-stored-procedures.md)
