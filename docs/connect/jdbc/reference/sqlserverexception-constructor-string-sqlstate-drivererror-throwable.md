---
title: SQLServerException(java.lang.String, SQLState, DriverError, java.lang.Throwable)-Konstruktor | Microsoft-Dokumentation
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
ms.openlocfilehash: 7a9e235417b1a682156d775b8a3458d73eba9e95
ms.sourcegitcommit: fe5c45a492e19a320a1a36b037704bf132dffd51
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/08/2020
ms.locfileid: "80902606"
---
# <a name="sqlserverexception-constructor-javalangstring-sqlstate-drivererror-javalangthrowable"></a>SQLServerException(java.lang.String, SQLState, DriverError, java.lang.Throwable)-Konstruktor
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Mit diesem Konstruktor wird eine neue Instanz der [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)-Klasse initialisiert, wenn ein **string**-, ein **sqlstate**-, ein **drivererror**- sowie ein **Throwable**-Objekt vorhanden sind.

## <a name="syntax"></a>Syntax  
  
```  
public SQLServerException(java.lang.String errText,
            SQLState sqlState,
            DriverError driverError,
            java.lang.Throwable cause)
            
```  
  
#### <a name="parameters"></a>Parameter  
 *errText*  
  
 Dies ist eine Zeichenfolge, die den Fehlertext enthält.
  
 *sqlState*  
  
 Dies ist ein Enumerationsobjekt, das den SQL-Zustand enthält.
 
 *driverError*  
  
 Dies ist ein Enumerationsobjekt, das den Treiberfehler enthält.
 
 *cause*  
  
 Dies ist ein Throwable-Objekt, das die Ursache der Ausnahme enthält.
  
## <a name="see-also"></a>Weitere Informationen  
 [SQLServerException-Konstruktoren](../../../connect/jdbc/reference/sqlserverexception-constructors.md)   
 [SQLServerException-Elemente](../../../connect/jdbc/reference/sqlserverexception-members.md)   
 [SQLServerException-Klasse](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
  
