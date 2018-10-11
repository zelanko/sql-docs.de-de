---
title: SetFetchSize-Methode (SQLServerResultSet) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerResultSet.setFetchSize
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 233bf4f8-4758-42d0-a80b-33e34fa78027
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 4ab8221e52cc5e3510a70a0e9affa290374330a8
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MTE75
ms.contentlocale: de-DE
ms.lasthandoff: 10/01/2018
ms.locfileid: "47814348"
---
# <a name="setfetchsize-method-sqlserverresultset"></a>setFetchSize-Methode (SQLServerResultSet)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Gibt für den JDBC-Treiber an, wie viele Zeilen aus der Datenbank abgerufen werden sollen, wenn für dieses [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md)-Objekt weitere Zeilen benötigt werden.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
public void setFetchSize(int rows)  
```  
  
#### <a name="parameters"></a>Parameter  
 *rows*  
  
 Ein **Int** , der angibt, der Anzahl der abzurufenden Zeilen.  
  
## <a name="exceptions"></a>Ausnahmen  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Remarks  
 Diese SetFetchSize-Methode wird von der SetFetchSize-Methode in der java.sql.ResultSet-Schnittstelle angegeben.  
  
 Ist die angegebene Abrufgröße NULL, wird der Wert vom JDBC-Treiber ignoriert und die korrekte Abrufgröße geschätzt. Der Standardwert wird von dem [SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-class.md)-Objekt festgelegt, von dem das Resultset erstellt wurde. Die Abrufgröße kann jedoch jederzeit geändert werden.  
  
 Mit dieser Methode wird die Blockabrufgröße für Servercursor geändert. Die Änderungen treten beim nächsten Aufruf von "sp_cursorfetch" durch den JDB-Treiber in Kraft. Durch das Festlegen der Abrufgröße auf NULL wird die Standardabrufgröße für den momentan verwendeten Cursortyp wiederhergestellt.  
  
## <a name="see-also"></a>Weitere Informationen finden Sie unter  
 [SQLServerResultSet-Elemente](../../../connect/jdbc/reference/sqlserverresultset-members.md)   
 [SQLServerResultSet-Klasse](../../../connect/jdbc/reference/sqlserverresultset-class.md)  
  
  
