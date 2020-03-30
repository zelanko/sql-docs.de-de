---
title: SQLServerException Constructor (java.lang.Object, java.lang.String, java.lang.String, int, boolean) | Microsoft-Dokumentation
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
ms.openlocfilehash: 72ae0e8ed3c65a795723326d7ca49e2f5a909f18
ms.sourcegitcommit: ff82f3260ff79ed860a7a58f54ff7f0594851e6b
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/29/2020
ms.locfileid: "67971146"
---
# <a name="sqlserverexception-constructor-javalangobject-javalangstring-javalangstring-int-boolean"></a>SQLServerException Constructor (java.lang.Object, java.lang.String, java.lang.String, int, boolean)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Initialisiert eine neue Instanz der [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)-Klasse, wenn ein **Objekt**, ein **string**-Objekt, ein **string**-Objekt, ein **int**-Wert und ein **boolescher** Wert vorhanden sind.

## <a name="syntax"></a>Syntax  
  
```  

public SQLServerException(java.lang.Object obj,
            java.lang.String errText,
            java.lang.String errState,
            int errNum,
            boolean bStack)

            
```  
  
#### <a name="parameters"></a>Parameter  
 *obj*  
  
 Der E/A-Puffer, der die Ausnahme generiert hat

 *errText*  
  
 Eine Zeichenfolge, die den Fehlercode enthält
  
 *sqlState*  
  
 Ein Enumerationsobjekt, das den SQL-Zustand enthält
 
 *errNum*  
  
 Ein int-Wert, der den Fehlercode für die Ausnahme enthält
 
 *bStack*  
  
 Ein boolescher Wert, der angibt, ob die Stapelüberwachung generiert werden soll
  
## <a name="see-also"></a>Weitere Informationen  
 [SQLServerException-Konstruktoren](../../../connect/jdbc/reference/sqlserverexception-constructors.md)   
 [SQLServerException-Elemente](../../../connect/jdbc/reference/sqlserverexception-members.md)   
 [SQLServerException-Klasse](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
  
