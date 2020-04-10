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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: c8c90b5fcf9fd58bf4c6468603a91242fa1f935c
ms.sourcegitcommit: fe5c45a492e19a320a1a36b037704bf132dffd51
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/08/2020
ms.locfileid: "80902556"
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
  
 Eine Zeichenfolge, die den Fehlercode enthält
  
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
  
  
