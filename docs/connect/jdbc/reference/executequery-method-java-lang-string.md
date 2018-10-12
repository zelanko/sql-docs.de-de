---
title: ExecuteQuery-Methode (java.lang.String) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerPreparedStatement.executeQuery (java.lang.String)
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 610205c2-6bcd-426c-ad6f-9682551efdec
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 4d266af1e09c457db4742d6aca06df65acfd505a
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MTE75
ms.contentlocale: de-DE
ms.lasthandoff: 10/01/2018
ms.locfileid: "47774363"
---
# <a name="executequery-method-javalangstring"></a>executeQuery-Methode (java.lang.String)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Führt die angegebene SQL-Anweisung aus und gibt ein einzelnes [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md)-Objekt zurück.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
public final java.sql.ResultSet executeQuery(java.lang.String sql)  
```  
  
#### <a name="parameters"></a>Parameter  
 *sql*  
  
 Eine **Zeichenfolge** mit einer SQL-Anweisung.  
  
## <a name="return-value"></a>Rückgabewert  
 Ein SQLServerResultSet-Objekt.  
  
## <a name="exceptions"></a>Ausnahmen  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Remarks  
 Diese ExecuteQuery-Methode wird von der ExecuteQuery-Methode in der java.sql.Statement-Schnittstelle angegeben.  
  
 Die Methode überschreibt die [executeQuery](../../../connect/jdbc/reference/executequery-method-sqlserverstatement.md)-Methode, die sich in der [SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-class.md)-Klasse befindet.  
  
 Durch den Aufruf dieser Methode wird eine Ausnahme ausgelöst, da die SQL-Anweisung für das SQLServerPreparedStatement-Objekt bei der Erstellung des Objekts angegeben wird.  
  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md) wird ausgelöst, wenn die angegebene SQL-Anweisung, etwas anderes als eine einzelne erzeugt [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md) Objekt.  
  
## <a name="see-also"></a>Weitere Informationen finden Sie unter  
 [executeQuery-Methode &#40;SQLServerPreparedStatement&#41;](../../../connect/jdbc/reference/executequery-method-sqlserverpreparedstatement.md)   
 [SQLServerPreparedStatement-Elemente](../../../connect/jdbc/reference/sqlserverpreparedstatement-members.md)   
 [SQLServerPreparedStatement-Klasse](../../../connect/jdbc/reference/sqlserverpreparedstatement-class.md)  
  
  
