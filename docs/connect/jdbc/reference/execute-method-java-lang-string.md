---
title: Execute-Methode (java.lang.String) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerPreparedStatement.execute (java.lang.String)
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: a871917e-d286-46c3-96cf-2e8e8b22111c
author: MightyPen
ms.author: genemi
manager: jroth
ms.openlocfilehash: d3ffb7c175c21d56467899bba9de7c110e324d1d
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MTE75
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "66802346"
---
# <a name="execute-method-javalangstring"></a>execute-Methode (java.lang.String)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Führt die angegebene SQL-Anweisung aus. Hierbei können mehrere Ergebnisse zurückgegeben werden.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
public final boolean execute(java.lang.String sql)  
```  
  
#### <a name="parameters"></a>Parameter  
 *sql*  
  
 Eine **Zeichenfolge** mit einer SQL-Anweisung.  
  
## <a name="return-value"></a>Rückgabewert  
 **"true"** Wenn die Anweisung ein Resultset zurückgibt. **"false"** Wenn updatezählung oder kein Ergebnis zurückgegeben wird.  
  
## <a name="exceptions"></a>Ausnahmen  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Remarks  
 Diese execute-Methode wird von der execute-Methode in der java.sql.Statement-Schnittstelle angegeben.  
  
 Die Methode überschreibt die [execute](../../../connect/jdbc/reference/execute-method-sqlserverstatement.md)-Methode, die sich in der [SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-class.md)-Klasse befindet.  
  
 Durch den Aufruf dieser Methode wird eine Ausnahme ausgelöst, da die SQL-Anweisung für das SQLServerPreparedStatement-Objekt bei der Erstellung des Objekts angegeben wird.  
  
## <a name="see-also"></a>Weitere Informationen  
 [execute-Methode &#40;SQLServerPreparedStatement&#41;](../../../connect/jdbc/reference/execute-method-sqlserverpreparedstatement.md)   
 [SQLServerPreparedStatement-Elemente](../../../connect/jdbc/reference/sqlserverpreparedstatement-members.md)   
 [SQLServerPreparedStatement-Klasse](../../../connect/jdbc/reference/sqlserverpreparedstatement-class.md)  
  
  
