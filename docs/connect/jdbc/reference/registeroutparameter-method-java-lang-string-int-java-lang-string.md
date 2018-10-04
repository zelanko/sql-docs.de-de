---
title: RegisterOutParameter-Methode zum Typ und Name | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerCallableStatement.registerOutParameter
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: f962c912-2475-4e1f-a384-579be2d17f37
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 68bbdc4fec692a3f7830c25213ea4900b6ed6f52
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MTE75
ms.contentlocale: de-DE
ms.lasthandoff: 10/01/2018
ms.locfileid: "47731698"
---
# <a name="registeroutparameter-method-javalangstring-int-javalangstring"></a>registerOutParameter-Methode (java.lang.String, int, java.lang.String)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Registriert den OUT-Parameter mit dem angegebenen Namen für den angegebenen JDBC-Typ und den Typnamen.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
public void registerOutParameter(java.lang.String s,  
                                 int n,  
                                 java.lang.String s1)  
```  
  
#### <a name="parameters"></a>Parameter  
 *s*  
  
 Ein **String-Objekt**, das den Parameternamen enthält.  
  
 *n*  
  
 Ein JDBC-Typcode gemäß der Definition in "java.sql.Types".  
  
 *s1*  
  
 Ein **String-Objekt**, das den vollqualifizierten SQL-Typnamen enthält.  
  
## <a name="exceptions"></a>Ausnahmen  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Remarks  
 Diese RegisterOutParameter-Methode wird von der RegisterOutParameter-Methode in der java.sql.CallableStatement-Schnittstelle angegeben.  
  
## <a name="see-also"></a>Weitere Informationen finden Sie unter  
 [registerOutParameter-Methode &#40;SQLServerCallableStatement&#41;](../../../connect/jdbc/reference/registeroutparameter-method-sqlservercallablestatement.md)   
 [SQLServerCallableStatement-Elemente](../../../connect/jdbc/reference/sqlservercallablestatement-members.md)   
 [SQLServerCallableStatement-Klasse](../../../connect/jdbc/reference/sqlservercallablestatement-class.md)  
  
  
