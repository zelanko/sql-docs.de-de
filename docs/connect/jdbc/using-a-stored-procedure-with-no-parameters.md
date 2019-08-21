---
title: Verwenden von gespeicherten Prozeduren ohne Parameter | Microsoft-Dokumentation
ms.custom: ''
ms.date: 08/12/2019
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: e9470a6d-a758-4c56-96ec-7b37139e36a7
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 01f59f44d42af1d0880df48b043080525d9821ee
ms.sourcegitcommit: 9348f79efbff8a6e88209bb5720bd016b2806346
ms.translationtype: MTE75
ms.contentlocale: de-DE
ms.lasthandoff: 08/14/2019
ms.locfileid: "69027024"
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

## <a name="see-also"></a>Siehe auch

[Verwenden von Anweisungen mit gespeicherten Prozeduren](../../connect/jdbc/using-statements-with-stored-procedures.md)
