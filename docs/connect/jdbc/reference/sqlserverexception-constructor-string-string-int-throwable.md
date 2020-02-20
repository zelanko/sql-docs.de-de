---
title: SQLServerException-Constructor (java.lang.String, java.lang.String, int, java.lang.Throwable) | Microsoft-Dokumentation
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
ms.openlocfilehash: 18827d05bc5567b4566eaa006d88c249874132cf
ms.sourcegitcommit: b78f7ab9281f570b87f96991ebd9a095812cc546
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/31/2020
ms.locfileid: "67971073"
---
# <a name="sqlserverexception-constructor-javalangstring-javalangstring-int-javalangthrowable"></a>SQLServerException-Constructor (java.lang.String, java.lang.String, int, java.lang.Throwable)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Mit diesem Konstruktor wird eine neue Instanz der [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)-Klasse initialisiert, wenn ein **string**-, ein **string**-, ein **int**- und ein **Throwable**-Objekt vorhanden sind.

## <a name="syntax"></a>Syntax  
  
```  
public SQLServerException(java.lang.String errText,
            SQLState errState,
            int errNum,
            java.lang.Throwable cause)
            
```  
  
#### <a name="parameters"></a>Parameter  
 *errText*  
  
 Dies ist eine Zeichenfolge, die den Fehlertext enthält.
  
 *errState*  
  
 Dies ist eine Zeichenfolge, die den Status des Fehlers enthält.
 
 *errNum*  
  
 Dies ist ein int-Wert, der den Fehlercode für die Ausnahme enthält.
 
 *cause*  
  
 Dies ist ein Throwable-Objekt, das die Ursache der Ausnahme enthält.
  
## <a name="see-also"></a>Weitere Informationen  
 [SQLServerException-Konstruktoren](../../../connect/jdbc/reference/sqlserverexception-constructors.md)   
 [SQLServerException-Elemente](../../../connect/jdbc/reference/sqlserverexception-members.md)   
 [SQLServerException-Klasse](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
  
