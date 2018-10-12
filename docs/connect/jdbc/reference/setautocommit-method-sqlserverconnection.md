---
title: SetAutoCommit-Methode (SQLServerConnection) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerConnection.setAutoCommit
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: db1e22d2-e53f-474e-8c99-cb1fff7f491a
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 517ce61f011de7cf5915c88895b9795b08767b20
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MTE75
ms.contentlocale: de-DE
ms.lasthandoff: 10/01/2018
ms.locfileid: "47761565"
---
# <a name="setautocommit-method-sqlserverconnection"></a>setAutoCommit-Methode (SQLServerConnection)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Legt für dieses [SQLServerConnection](../../../connect/jdbc/reference/sqlserverconnection-class.md)-Objekt den aktuellen Modus für automatische Commits auf den angegebenen Zustand fest.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
public void setAutoCommit(boolean value)  
```  
  
#### <a name="parameters"></a>Parameter  
 *value*  
  
 **"true"** Autocommit-Modus für die Verbindung zu **"false"** zu deaktivieren.  
  
## <a name="exceptions"></a>Ausnahmen  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Remarks  
 Diese SetAutoCommit-Methode wird von der SetAutoCommit-Methode in der java.sql.Connection-Schnittstelle angegeben.  
  
 Ist für eine Verbindung der Modus für automatische Commits aktiviert, werden alle SQL-Anweisungen als einzelne Transaktionen ausgeführt, und die Commits der SQL-Anweisungen werden als einzelne Transaktionen ausgeführt. Andernfalls werden die SQL-Anweisungen in Transaktionen gruppiert, die mit einem Aufruf der [commit](../../../connect/jdbc/reference/commit-method-sqlserverconnection.md)- oder der [rollback](../../../connect/jdbc/reference/rollback-method-sqlserverconnection.md)-Methode beendet werden. Der Modus für automatische Commits ist für neue Verbindungen standardmäßig aktiviert.  
  
 Der Commit wird ausgeführt, wenn die Anweisung abgeschlossen wird oder die nächste Ausführung durchgeführt wird, je nachdem, welches Ereignis zuerst eintritt. Bei Anweisungen, von denen ein [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md)-Objekt zurückgegeben wird, wird die Anweisung abgeschlossen, wenn die letzte Zeile des Ergebnisses abgerufen oder das Resultset geschlossen wurde. In erweiterten Fällen kann eine einzelne Anweisung zusätzlich zu den Ausgabeparameterwerten mehrere Ergebnisse zurückgeben. In diesen Fällen wird der Commit ausgeführt, nachdem alle Ergebnisse und Ausgabeparameterwerte abgerufen wurden.  
  
 Ist der Modus für automatische Commits auf **false** gesetzt, startet der JDBC-Treiber nach jedem Commit implizit eine neue Transaktion.  
  
> [!NOTE]  
>  Wenn diese Methode während einer Transaktion aufgerufen wird, wird ein Commit der Transaktion ausgeführt.  
  
## <a name="see-also"></a>Weitere Informationen finden Sie unter  
 [SQLServerConnection-Elemente](../../../connect/jdbc/reference/sqlserverconnection-members.md)   
 [SQLServerConnection-Klasse](../../../connect/jdbc/reference/sqlserverconnection-class.md)  
  
  
