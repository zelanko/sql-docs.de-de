---
title: Close-Methode (SQLServerResultSet) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerResultSet.close
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 8f3adf5b-874e-4cf2-b4ef-672dda42d77a
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: ec9b51d08e10df0f829308d163b573c0670c78e7
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MTE75
ms.contentlocale: de-DE
ms.lasthandoff: 10/01/2018
ms.locfileid: "47637258"
---
# <a name="close-method-sqlserverresultset"></a>close-Methode (SQLServerResultSet)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Gibt die Datenbank- und JDBC-Ressourcen dieses [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md)-Objekts umgehend frei, sodass nicht darauf gewartet werden muss, bis dieser Vorgang beim automatischen Schließen ausgeführt wird.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
public void close()  
```  
  
## <a name="exceptions"></a>Ausnahmen  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Remarks  
 Diese close-Methode wird von der close-Methode in der java.sql.ResultSet-Schnittstelle angegeben.  
  
 Ein SQLServerResultSet-Objekt wird vom [SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-class.md)-Objekt, durch das es generiert wurde, automatisch geschlossen, wenn das SQLServerStatement-Objekt geschlossen, erneut ausgeführt oder zum Abrufen des nächsten Ergebnisses aus einer Sequenz mit mehreren Ergebnissen verwendet wird. Ein SQLServerResultSet-Objekt wird auch dann automatisch geschlossen, wenn eine automatische Speicherbereinigung stattfindet.  
  
 Beim Ausführen einer Anweisung, von der ein einzelnes, umfangreiches und schreibgeschütztes Vorwärts-Resultset erstellt wird, ist für Sie unter Umständen lediglich eine anfängliche Zeilengruppe des zurückgegebenen Resultsets von Interesse. In diesem Fall kann von der Anwendung vor dem Schließen des Resultsets die [cancel](../../../connect/jdbc/reference/cancel-method-sqlserverstatement.md)-Methode des zugeordneten Anweisungsobjekts aufgerufen werden, um die Verarbeitungszeit beim Verwerfen der übrigen, nicht benötigten Zeilen zu verringern. Wägen Sie bei der Entscheidung, ob Sie diese Methode verwenden möchten, die eingesparte Verarbeitungszeit gegen die Zeit und den Roundtrip zum Server ab, der zum Abbrechen der Ausführung erforderlich ist.  
  
## <a name="see-also"></a>Weitere Informationen finden Sie unter  
 [SQLServerResultSet-Elemente](../../../connect/jdbc/reference/sqlserverresultset-members.md)   
 [SQLServerResultSet-Klasse](../../../connect/jdbc/reference/sqlserverresultset-class.md)  
  
  
