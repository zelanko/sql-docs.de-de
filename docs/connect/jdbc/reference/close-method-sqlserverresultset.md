---
title: close-Methode (SQLServerResultSet) | Microsoft-Dokumentation
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
ms.openlocfilehash: e78dbb981938e9af2fbe894919368da17347941a
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MTE75
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "67955586"
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
  
## <a name="remarks"></a>Bemerkungen  
 Diese close-Methode wird von der close-Methode in der java.sql.ResultSet-Schnittstelle angegeben.  
  
 Ein SQLServerResultSet-Objekt wird vom [SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-class.md)-Objekt, durch das es generiert wurde, automatisch geschlossen, wenn das SQLServerStatement-Objekt geschlossen, erneut ausgeführt oder zum Abrufen des nächsten Ergebnisses aus einer Sequenz mit mehreren Ergebnissen verwendet wird. Ein SQLServerResultSet-Objekt wird auch dann automatisch geschlossen, wenn eine automatische Speicherbereinigung stattfindet.  
  
 Beim Ausführen einer Anweisung, von der ein einzelnes, umfangreiches und schreibgeschütztes Vorwärts-Resultset erstellt wird, ist für Sie unter Umständen lediglich eine anfängliche Zeilengruppe des zurückgegebenen Resultsets von Interesse. In diesem Fall kann von der Anwendung vor dem Schließen des Resultsets die [cancel](../../../connect/jdbc/reference/cancel-method-sqlserverstatement.md)-Methode des zugeordneten Anweisungsobjekts aufgerufen werden, um die Verarbeitungszeit beim Verwerfen der übrigen, nicht benötigten Zeilen zu verringern. Wägen Sie bei der Entscheidung, ob Sie diese Methode verwenden möchten, die eingesparte Verarbeitungszeit gegen die Zeit und den Roundtrip zum Server ab, der zum Abbrechen der Ausführung erforderlich ist.  
  
## <a name="see-also"></a>Weitere Informationen  
 [SQLServerResultSet-Elemente](../../../connect/jdbc/reference/sqlserverresultset-members.md)   
 [SQLServerResultSet-Klasse](../../../connect/jdbc/reference/sqlserverresultset-class.md)  
  
  
