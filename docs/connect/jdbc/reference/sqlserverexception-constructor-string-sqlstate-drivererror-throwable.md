---
title: SQLServerException-Konstruktor (Java. lang. String, SQLSTATE, drivererror, Java. lang. Throwable) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2018
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: ''
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 13b0e3aea694b0cedb3594cb76650ca7c938eb55
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MTE75
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "67971093"
---
# <a name="sqlserverexception-constructor-javalangstring-sqlstate-drivererror-javalangthrowable"></a>SQLServerException-Konstruktor (Java. lang. String, SQLSTATE, drivererror, Java. lang. Throwable)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Initialisiert eine neue Instanz der [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md) -Klasse, wenn ein **Zeichen** folgen Objekt, ein **SQLSTATE** -Objekt, ein **drivererror** -Objekt **und ein** einschränktes Objekt angegeben werden.

## <a name="syntax"></a>Syntax  
  
```  
public SQLServerException(java.lang.String errText,
            SQLState sqlState,
            DriverError driverError,
            java.lang.Throwable cause)
            
```  
  
#### <a name="parameters"></a>Parameter  
 *errText*  
  
 Eine Zeichenfolge, die den Fehlertext enthält.
  
 *sqlState*  
  
 Ein Enumeration-Objekt, das den SQL-Zustand enthält.
 
 *driverError*  
  
 Ein Enumeration-Objekt, das den Treiber Fehler enthält.
 
 *cause*  
  
 Ein drobbares Objekt, das die Ursache der Ausnahme enthält.
  
## <a name="see-also"></a>Weitere Informationen  
 [SQLServerException-Konstruktoren](../../../connect/jdbc/reference/sqlserverexception-constructors.md)   
 [SQLServerException-Elemente](../../../connect/jdbc/reference/sqlserverexception-members.md)   
 [SQLServerException-Klasse](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
  
