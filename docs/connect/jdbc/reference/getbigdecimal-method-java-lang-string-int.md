---
title: getBigDecimal Method (java.lang.String, int) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerCallableStatement.getBigDecimal (java.lang.String, int)
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 6967ba55-9c9a-4f6f-a4d2-8ee9c9a82c14
author: MightyPen
ms.author: genemi
ms.openlocfilehash: fd2d46569386637b5082288b83268a80dac013e5
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MTE75
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "67953893"
---
# <a name="getbigdecimal-method-javalangstring-int"></a>getBigDecimal-Methode (java.lang.String, int)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Ruft den Wert des angegebenen Parameters unter Berücksichtigung des Parameternamens und der Dezimalstellen als java.math.BigDecimal-Objekt ab.  
  
> [!NOTE]  
>  Diese Methode gilt in der JDBC-Spezifikation als veraltet. Verwenden Sie stattdessen die [getBigDecimal (java.lang.String)](../../../connect/jdbc/reference/getbigdecimal-method-java-lang-string.md)-Methode.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
public java.math.BigDecimal getBigDecimal(java.lang.String sCol,  
                                          int scale)  
```  
  
#### <a name="parameters"></a>Parameter  
 *sCol*  
  
 Ein **String-Objekt**, das den Parameternamen enthält.  
  
 *scale*  
  
 Ein Wert vom Typ **int**, der die Anzahl von Stellen rechts des Dezimalzeichens anzeigt.  
  
## <a name="return-value"></a>Rückgabewert  
 Ein BigDecimal-Objekt.  
  
## <a name="exceptions"></a>Ausnahmen  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Bemerkungen  
 Diese getBigDecimal-Methode wird von der getBigDecimal-Methode in der Java. SQL. CallableStatement-Schnittstelle angegeben.  
  
## <a name="see-also"></a>Weitere Informationen  
 [getBigDecimal-Methode &#40;SQLServerCallableStatement&#41;](../../../connect/jdbc/reference/getbigdecimal-method-sqlservercallablestatement.md)   
 [SQLServerCallableStatement-Elemente](../../../connect/jdbc/reference/sqlservercallablestatement-members.md)   
 [SQLServerCallableStatement-Klasse](../../../connect/jdbc/reference/sqlservercallablestatement-class.md)  
  
  
