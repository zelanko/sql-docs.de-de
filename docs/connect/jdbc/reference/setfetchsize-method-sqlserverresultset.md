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
manager: jroth
ms.openlocfilehash: c5d0bd8714714a479f9370ed2c60b626006e1964
ms.sourcegitcommit: ad2e98972a0e739c0fd2038ef4a030265f0ee788
ms.translationtype: MTE75
ms.contentlocale: de-DE
ms.lasthandoff: 06/07/2019
ms.locfileid: "66803377"
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
  
## <a name="see-also"></a>Weitere Informationen  
 [SQLServerResultSet-Elemente](../../../connect/jdbc/reference/sqlserverresultset-members.md)   
 [SQLServerResultSet-Klasse](../../../connect/jdbc/reference/sqlserverresultset-class.md)  
  
  
