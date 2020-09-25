---
title: setAutoCommit-Methode (SQLServerConnection)
description: Lernen Sie die öffentlichen API-Details für die setAutoCommit-Methode in der SQLServerConnection-Klasse des JDBC-Treibers für SQL Server kennen.
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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 117fa85e5ec6bdd7d0d37de9fc057dd8127cf42a
ms.sourcegitcommit: 129f8574eba201eb6ade1f1620c6b80dfe63b331
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/30/2020
ms.locfileid: "87435375"
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
  
 Mit dem Wert **TRUE** wird der Modus für automatische Commits für die Verbindung aktiviert, und mit dem Wert **FALSE** wird er deaktiviert.  
  
## <a name="exceptions"></a>Ausnahmen  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Bemerkungen  
 Diese setAutoCommit-Methode wird von der setAutoCommit-Methode in der java.sql.Connection-Schnittstelle angegeben.  
  
 Ist für eine Verbindung der Modus für automatische Commits aktiviert, werden alle SQL-Anweisungen als einzelne Transaktionen ausgeführt, und die Commits der SQL-Anweisungen werden als einzelne Transaktionen ausgeführt. Andernfalls werden die SQL-Anweisungen in Transaktionen gruppiert, die mit einem Aufruf der [commit](../../../connect/jdbc/reference/commit-method-sqlserverconnection.md)- oder der [rollback](../../../connect/jdbc/reference/rollback-method-sqlserverconnection.md)-Methode beendet werden. Der Modus für automatische Commits ist für neue Verbindungen standardmäßig aktiviert.  
  
 Der Commit wird ausgeführt, wenn die Anweisung abgeschlossen wird oder die nächste Ausführung durchgeführt wird, je nachdem, welches Ereignis zuerst eintritt. Wenn Anweisungen ein [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md)-Objekt zurückgeben, wird die Anweisung abgeschlossen, wenn die letzte Zeile des Ergebnisses abgerufen oder das Resultset geschlossen wurde. In erweiterten Fällen kann eine einzelne Anweisung zusätzlich zu den Ausgabeparameterwerten mehrere Ergebnisse zurückgeben. In diesen Fällen wird der Commit ausgeführt, nachdem alle Ergebnisse und Ausgabeparameterwerte abgerufen wurden.  
  
 Ist der Modus für automatische Commits auf **false** gesetzt, startet der JDBC-Treiber nach jedem Commit implizit eine neue Transaktion.  
  
> [!NOTE]  
> Wenn diese Methode während einer Transaktion aufgerufen wird, wird ein Commit der Transaktion ausgeführt.  
  
## <a name="see-also"></a>Weitere Informationen  
 [SQLServerConnection-Elemente](../../../connect/jdbc/reference/sqlserverconnection-members.md)  
 [SQLServerConnection-Klasse](../../../connect/jdbc/reference/sqlserverconnection-class.md)  
