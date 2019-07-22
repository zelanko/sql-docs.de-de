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
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MTE75
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "67971146"
---
# <a name="sqlserverexception-constructor-javalangobject-javalangstring-javalangstring-int-boolean"></a>SQLServerException Constructor (java.lang.Object, java.lang.String, java.lang.String, int, boolean)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Initialisiert eine neue Instanz der [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md) -Klasse, wenn ein **Objekt**, ein **Zeichen** folgen Objekt, ein **Zeichen** folgen Objekt, ein **int**-Wert und ein **boolescher**Wert angegeben werden.

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
  
 Der IO-Puffer, der die Ausnahme generiert hat.

 *errText*  
  
 Eine Zeichenfolge, die den Fehlertext enthält.
  
 *sqlState*  
  
 Ein Enumeration-Objekt, das den SQL-Zustand enthält.
 
 *errNum*  
  
 Ein int-Wert, der den Fehlercode für die Ausnahme enthält.
 
 *bStack*  
  
 Ein boolescher Wert, der angibt, ob die Stapel Überwachung generiert werden soll.
  
## <a name="see-also"></a>Weitere Informationen  
 [SQLServerException-Konstruktoren](../../../connect/jdbc/reference/sqlserverexception-constructors.md)   
 [SQLServerException-Elemente](../../../connect/jdbc/reference/sqlserverexception-members.md)   
 [SQLServerException-Klasse](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
  
