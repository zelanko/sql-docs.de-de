---
description: SQLServerException Constructor (java.lang.Object, java.lang.String, java.lang.String, int, boolean)
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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: f66bd8759733c2574438ba12ce9f12b00cf88842
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 08/17/2020
ms.locfileid: "88450496"
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
  
 Dies ist eine Zeichenfolge, die den Fehlertext enthält.
  
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
  
  
