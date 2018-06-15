---
title: SQLServerException-Konstruktor (java.lang.String, SQLState, DriverError, "java.lang.Throwable") | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2018
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: conceptual
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: ''
caps.latest.revision: 1
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 33f7b15a2f4dd8e83c7e703e96812f29691e6bd6
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/03/2018
ms.locfileid: "32846195"
---
# <a name="sqlserverexception-constructor-javalangstring-sqlstate-drivererror-javalangthrowable"></a>SQLServerException-Konstruktor (java.lang.String, SQLState, DriverError, "java.lang.Throwable")
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Initialisiert eine neue Instanz der der [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md) Klasse, sofern eine **Zeichenfolge** -Objekt, eine **Sqlstate** -Objekt, eine **Drivererror** das Objekt, und ein **auslösbares** Objekt.

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
  
 Ein Enum-Objekt, das die SQL-Zustand enthält.
 
 *driverError*  
  
 Ein Enum-Objekt, das den Treiberfehler enthält.
 
 *Ursache*  
  
 Ein auslösbares-Objekt, das die Ursache der Ausnahme enthält.
  
## <a name="see-also"></a>Siehe auch  
 [SQLServerException-Konstruktoren](../../../connect/jdbc/reference/sqlserverexception-constructors.md)   
 [SQLServerException-Elemente](../../../connect/jdbc/reference/sqlserverexception-members.md)   
 [SQLServerException-Klasse](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
  
