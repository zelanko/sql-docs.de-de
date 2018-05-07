---
title: SQLServerException-Konstruktor (java.lang.String, java.lang.String, Int, "java.lang.Throwable") | Microsoft Docs
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
ms.openlocfilehash: 94b45ed912fbf61a0f15b23ca5393ed31746c90b
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/03/2018
---
# <a name="sqlserverexception-constructor-javalangstring-javalangstring-int-javalangthrowable"></a>SQLServerException-Konstruktor (java.lang.String, java.lang.String, Int, "java.lang.Throwable")
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Initialisiert eine neue Instanz der der [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md) Klasse, sofern eine **Zeichenfolge** -Objekt, eine **Zeichenfolge** -Objekt, ein **Int**, und eine **auslösbares** Objekt.

## <a name="syntax"></a>Syntax  
  
```  
public SQLServerException(java.lang.String errText,
            SQLState errState,
            int errNum,
            java.lang.Throwable cause)
            
```  
  
#### <a name="parameters"></a>Parameter  
 *errText*  
  
 Eine Zeichenfolge mit dem Fehlertext.
  
 *errState*  
  
 Eine Zeichenfolge, die den Status des Fehlers enthält.
 
 *errNum*  
  
 Einen int-Wert, der den Fehlercode für die ausgelöste Ausnahme enthält.
 
 *Ursache*  
  
 Ein auslösbares-Objekt, das die Ursache der Ausnahme enthält.
  
## <a name="see-also"></a>Siehe auch  
 [SQLServerException-Konstruktoren](../../../connect/jdbc/reference/sqlserverexception-constructors.md)   
 [SQLServerException-Elemente](../../../connect/jdbc/reference/sqlserverexception-members.md)   
 [SQLServerException-Klasse](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
  
