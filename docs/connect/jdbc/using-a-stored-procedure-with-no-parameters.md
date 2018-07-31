---
title: Verwenden von gespeicherten Prozeduren ohne Parameter
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: e9470a6d-a758-4c56-96ec-7b37139e36a7
caps.latest.revision: 18
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 7db021b9d3fdf875c2c6074159b56d8e6cb0fd14
ms.sourcegitcommit: e77197ec6935e15e2260a7a44587e8054745d5c2
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/11/2018
ms.locfileid: "37992922"
---
# <a name="using-a-stored-procedure-with-no-parameters"></a>Verwenden von gespeicherten Prozeduren ohne Parameter
[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

  Die einfachste Art einer gespeicherten [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]-Prozedur, die aufgerufen werden kann, enthält keine Parameter und gibt ein einziges Resultset zurück. Die [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)] bietet die [SQLServerStatement](../../connect/jdbc/reference/sqlserverstatement-class.md) -Klasse, die Sie verwenden können, um diese Art von gespeicherter Prozedur aufrufen und Verarbeiten der Daten, die zurückgegeben.  
  
 Wenn Sie mit dem JDBC-Treiber eine gespeicherte Prozedur ohne Parameter aufrufen möchten, müssen Sie die `call`-SQL-Escapesequenz verwenden. Die Syntax für die `call`-Escapesequenz ohne Parameter lautet folgendermaßen:  
  
 `{call procedure-name}`  
  
> [!NOTE]  
>  Weitere Informationen zu SQL-Escapesequenzen, finden Sie unter [mithilfe von SQL-Escapesequenzen](../../connect/jdbc/using-sql-escape-sequences.md).  
  
 Erstellen Sie als Beispiel die folgende Prozedur in der [!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal_md.md)]-Beispieldatenbank:  
  
```  
CREATE PROCEDURE GetContactFormalNames   
AS  
BEGIN  
   SELECT TOP 10 Title + ' ' + FirstName + ' ' + LastName AS FormalName   
   FROM Person.Contact  
END  
```  
  
 Diese gespeicherte Prozedur gibt ein einzelnes Resultset zurück, das eine Datenspalte enthält, bei der es sich um eine Kombination aus Titel, Vorname und Nachname der ersten zehn Kontakte in der Tabelle "Person.Contact" handelt.  
  
 Im folgenden Beispiel wird eine offene Verbindung zur [!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal_md.md)]-Beispieldatenbank an die Funktion übergeben, und die gespeicherte Prozedur „GetContactFormalNames“ wird mit der [executeQuery](../../connect/jdbc/reference/executequery-method-sqlserverstatement.md)-Methode aufgerufen.  
  
```  
public static void executeSprocNoParams(Connection con) {  
   try {  
      Statement stmt = con.createStatement();  
      ResultSet rs = stmt.executeQuery("{call dbo.GetContactFormalNames}");  
  
      while (rs.next()) {  
         System.out.println(rs.getString("FormalName"));  
      }  
      rs.close();  
      stmt.close();  
   }  
   catch (Exception e) {  
      e.printStackTrace();  
   }  
}  
```  
  
## <a name="see-also"></a>Weitere Informationen finden Sie unter  
 [Verwenden von Anweisungen mit gespeicherten Prozeduren](../../connect/jdbc/using-statements-with-stored-procedures.md)  
  
  
