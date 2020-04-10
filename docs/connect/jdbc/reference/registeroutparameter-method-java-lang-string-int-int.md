---
title: registerOutParameter-Methode für den Typ und Skalierung | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerCallableStatement.registerOutParameter (java.lang.String, int, int)
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 8bddc557-4526-4843-9804-05dc83c8832d
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: cb0a97e0b9ee1ef33897d98580a67794fbc8e2bb
ms.sourcegitcommit: fe5c45a492e19a320a1a36b037704bf132dffd51
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/08/2020
ms.locfileid: "80904276"
---
# <a name="registeroutparameter-method-javalangstring-int-int"></a>registerOutParameter-Methode (java.lang.String, int, int)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Registriert den OUT-Parameter mit dem angegebenen Namen für den angegebenen JDBC-Typ und die Dezimalstellen.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
public void registerOutParameter(java.lang.String s,  
                                 int n,  
                                 int n1)  
```  
  
#### <a name="parameters"></a>Parameter  
 *s*  
  
 Ein **String-Objekt**, das den Parameternamen enthält.  
  
 *sqlType*  
  
 Ein JDBC-Typcode gemäß der Definition in "java.sql.Types".  
  
 *scale*  
  
 Ein **int**-Element, das die Anzahl der rechts des Dezimalzeichens anzuzeigenden Stellen angibt.  
  
## <a name="exceptions"></a>Ausnahmen  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Bemerkungen  
 Diese registerOutParameter-Methode wird von der registerOutParameter-Methode in der java.sql.CallableStatement-Schnittstelle angegeben.  
  
## <a name="see-also"></a>Weitere Informationen  
 [registerOutParameter-Methode &#40;SQLServerCallableStatement&#41;](../../../connect/jdbc/reference/registeroutparameter-method-sqlservercallablestatement.md)   
 [SQLServerCallableStatement-Elemente](../../../connect/jdbc/reference/sqlservercallablestatement-members.md)   
 [SQLServerCallableStatement-Klasse](../../../connect/jdbc/reference/sqlservercallablestatement-class.md)  
  
  
