---
title: GetHoldability-Methode (SQLServerResultSet) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: 4508d90f-c3c4-4eac-8001-fb0b93b66734
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 9cf27049e45c8e52c8a63a419327f377dd1f558f
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MTE75
ms.contentlocale: de-DE
ms.lasthandoff: 10/01/2018
ms.locfileid: "47841398"
---
# <a name="getholdability-method-sqlserverresultset"></a>getHoldability-Methode (SQLServerResultSet)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Ruft die Haltbarkeit dieses [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md)-Objekts ab.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
public int getHoldability()  
```  
  
## <a name="return-value"></a>Rückgabewert  
 Ein Wert vom Typ **int** mit einer der folgenden Haltbarkeitsstufen:  
  
 HOLD_CURSORS_OVER_COMMIT  
  
 CLOSE_CURSORS_AT_COMMIT  
  
## <a name="exceptions"></a>Ausnahmen  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Remarks  
 Diese GetHoldability-Methode wird von der GetHoldability-Methode in der java.sql.ResultSet-Schnittstelle angegeben.  
  
 Zum Festlegen der Holdability für Resultsets kann von Anwendungen die [setHoldability](../../../connect/jdbc/reference/setholdability-method-sqlserverconnection.md)-Methode der [SQLServerConnection](../../../connect/jdbc/reference/sqlserverconnection-class.md)-Klasse verwendet werden. Nach dem Aufrufen der [setHoldability](../../../connect/jdbc/reference/setholdability-method-sqlserverconnection.md)-Methode, dem Erstellen des Anweisungsobjekts und dessen Resultsetobjekts und dem Ausführen der Anweisung muss die Haltbarkeit von der Anwendung möglicherweise erneut geändert werden.  
  
 Wenn Servercursor mit SQL Server 2005 oder höher verbunden sind, wirkt sich das Festlegen der Haltbarkeit nur auf die Haltbarkeit neuer Resultsets aus, die erst noch für diese Verbindung erstellt werden. Bei SQL Server 2000 wirkt sich das Festlegen der Haltbarkeit jedoch sowohl auf die Haltbarkeit vorhandener als auch neuer, noch für die Verbindung zu erstellender Resultsets aus.  
  
 Wenn die Holdability zurückgesetzt und die GetHoldability-Methode wird aufgerufen, auf die zuvor erstelltes Resultsetobjekt, der von dieser Methode zurückgegebene Wert ist ggf. anders als der Holdability-Wert, der zurückgegeben werden, mithilfe der folgenden Methoden: Statement.getResultSetHoldability , Connection.getHoldability oder DatabaseMetaData.getResultSetHoldability.  
  
## <a name="see-also"></a>Weitere Informationen finden Sie unter  
 [SQLServerResultSet-Elemente](../../../connect/jdbc/reference/sqlserverresultset-members.md)   
 [SQLServerResultSet-Klasse](../../../connect/jdbc/reference/sqlserverresultset-class.md)  
  
  
