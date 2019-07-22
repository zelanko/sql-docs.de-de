---
title: getHoldability-Methode (SQLServerResultSet) | Microsoft-Dokumentation
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
ms.openlocfilehash: 57bf0cfc206319bf6afcb09435e8787499266c0c
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MTE75
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "67982927"
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
 Diese getHoldability-Methode wird von der getHoldability-Methode in der Java. SQL. Resultset-Schnittstelle angegeben.  
  
 Zum Festlegen der Holdability für Resultsets kann von Anwendungen die [setHoldability](../../../connect/jdbc/reference/setholdability-method-sqlserverconnection.md)-Methode der [SQLServerConnection](../../../connect/jdbc/reference/sqlserverconnection-class.md)-Klasse verwendet werden. Nach dem Aufrufen der [setHoldability](../../../connect/jdbc/reference/setholdability-method-sqlserverconnection.md)-Methode, dem Erstellen des Anweisungsobjekts und dessen Resultsetobjekts und dem Ausführen der Anweisung muss die Haltbarkeit von der Anwendung möglicherweise erneut geändert werden.  
  
 Wenn Servercursor mit SQL Server 2005 oder höher verbunden sind, wirkt sich das Festlegen der Haltbarkeit nur auf die Haltbarkeit neuer Resultsets aus, die erst noch für diese Verbindung erstellt werden. Bei SQL Server 2000 wirkt sich das Festlegen der Haltbarkeit jedoch sowohl auf die Haltbarkeit vorhandener als auch neuer, noch für die Verbindung zu erstellender Resultsets aus.  
  
 Wenn die Haltbarkeit zurückgesetzt wird und die getHoldability-Methode für das zuvor erstellte Resultsetobjekt aufgerufen wird, unterscheidet sich der von dieser Methode zurückgegebene Wert möglicherweise von dem von den folgenden Methoden zurückgegebenen Wert der Haltbarkeit: Statement. getresultsetholdability , Connection. getHoldability oder DatabaseMetaData. getresultsertholdability.  
  
## <a name="see-also"></a>Weitere Informationen  
 [SQLServerResultSet-Elemente](../../../connect/jdbc/reference/sqlserverresultset-members.md)   
 [SQLServerResultSet-Klasse](../../../connect/jdbc/reference/sqlserverresultset-class.md)  
  
  
