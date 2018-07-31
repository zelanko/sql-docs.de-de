---
title: Verwenden von gespeicherten Prozeduren mit einer Updatezählung | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: 64cf4877-5995-4bfc-8865-b7618a5c8d01
caps.latest.revision: 26
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: d858b255d5bdd6ce74509d36f4d0497220350694
ms.sourcegitcommit: e77197ec6935e15e2260a7a44587e8054745d5c2
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/11/2018
ms.locfileid: "38040818"
---
# <a name="using-a-stored-procedure-with-an-update-count"></a>Verwenden von gespeicherten Prozeduren mit einer Updatezählung
[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

  Zum Ändern von Daten in einer [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]-Datenbank mit einer gespeicherten Prozedur stellt [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)] die Klasse [SQLServerCallableStatement](../../connect/jdbc/reference/sqlservercallablestatement-class.md) bereit. Mithilfe der Klasse „SQLServerCallableStatement“ können Sie gespeicherte Prozeduren aufrufen, die Daten in der Datenbank ändern und die Anzahl der betroffenen Zeilen zurückgeben (die so genannte Updatezählung).  
  
 Nachdem der Aufruf der gespeicherten Prozedur mit der Klasse „SQLServerCallableStatement“ eingerichtet wurde, können Sie die gespeicherte Prozedur mit der Methode [execute](../../connect/jdbc/reference/execute-method-sqlserverstatement.md) oder der Methode [executeUpdate](../../connect/jdbc/reference/executeupdate-method-sqlserverstatement.md) aufrufen. Anders als die Methode „execute“ gibt die Methode „executeUpdate“ einen **int**-Wert zurück, der die von der gespeicherten Prozedur betroffene Anzahl von Zeilen enthält. Wenn Sie die Methode „execute“ verwenden und die Anzahl der betroffenen Zeilen ermitteln möchten, können Sie nach dem Ausführen der gespeicherten Prozedur die Methode [getUpdateCount](../../connect/jdbc/reference/getupdatecount-method-sqlserverstatement.md) aufrufen.  
  
> [!NOTE]  
>  Wenn der JDBC-Treiber alle Updatezählungen zurückgeben soll, einschließlich der Updatezählungen, die von eventuell ausgelösten Triggern zurückgegeben werden, müssen Sie die lastUpdateCount-Verbindungseigenschaft auf "false" setzen. Weitere Informationen zur LastUpdateCount-Eigenschaft finden Sie unter [Festlegen der Verbindungseigenschaften](../../connect/jdbc/setting-the-connection-properties.md).  
  
 Erstellen Sie als Beispiel die folgende Tabelle und gespeicherte Prozedur, und fügen Sie Beispieldaten in der [!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal_md.md)]-Beispieldatenbank ein:  
  
```  
CREATE TABLE TestTable   
   (Col1 int IDENTITY,   
    Col2 varchar(50),   
    Col3 int);  
  
CREATE PROCEDURE UpdateTestTable  
   @Col2 varchar(50),  
   @Col3 int  
AS  
BEGIN  
   UPDATE TestTable  
   SET Col2 = @Col2, Col3 = @Col3  
END;  
INSERT INTO dbo.TestTable (Col2, Col3) VALUES ('b', 10);  
```  
  
 Im folgenden Beispiel wird eine offene Verbindung mit der [!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal_md.md)]-Beispieldatenbank an die Funktion übergeben, mit der Methode „execute“ wird die gespeicherte Prozedur „UpdateTestTable“ aufgerufen, und anschließend wird mit der Methode „getUpdateCount“ die Anzahl der von der gespeicherten Prozedur betroffenen Zeilen zurückgegeben.  
  
 [!code[JDBC#UsingSprocWithUpdateCount1](../../connect/jdbc/codesnippet/Java/using-a-stored-procedure_0_1.java)]  
  
## <a name="see-also"></a>Weitere Informationen finden Sie unter  
 [Verwenden von Anweisungen mit gespeicherten Prozeduren](../../connect/jdbc/using-statements-with-stored-procedures.md)  
  
  
