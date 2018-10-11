---
title: SQLServerException-Konstruktor (java.lang.Object, java.lang.String, java.lang.String, Int, Boolean) | Microsoft-Dokumentation
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
manager: craigg
ms.openlocfilehash: 5b8c39021b8afac5631e44cddd8874cbf22975a3
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MTE75
ms.contentlocale: de-DE
ms.lasthandoff: 10/01/2018
ms.locfileid: "47670028"
---
# <a name="sqlserverexception-constructor-javalangobject-javalangstring-javalangstring-int-boolean"></a>SQLServerException-Konstruktor (java.lang.Object, java.lang.String, java.lang.String, Int, Boolean)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Initialisiert eine neue Instanz der der [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md) Klasse, sofern eine **Objekt**, **Zeichenfolge** Objekt eine **Zeichenfolge** -Objekt, das eine **Int**, und ein **booleschen**.

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
  
 Der e/a-Puffer, der die Ausnahme generiert hat.

 *errText*  
  
 Eine Zeichenfolge, die den Fehlertext enthält.
  
 *sqlState*  
  
 Ein Enumerationsobjekt, das den SQL-Status enthält.
 
 *errNum*  
  
 Eine ganze Zahl, die den Fehlercode für die ausgelöste Ausnahme enthalten.
 
 *bStack*  
  
 Ein boolescher Wert, der angibt, ob die stapelüberwachung generiert werden soll.
  
## <a name="see-also"></a>Weitere Informationen finden Sie unter  
 [SQLServerException-Konstruktoren](../../../connect/jdbc/reference/sqlserverexception-constructors.md)   
 [SQLServerException-Elemente](../../../connect/jdbc/reference/sqlserverexception-members.md)   
 [SQLServerException-Klasse](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
  
