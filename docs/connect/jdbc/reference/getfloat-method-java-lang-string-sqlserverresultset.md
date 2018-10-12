---
title: getFloat-Methode (java.lang.String) (SQLServerResultSet) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerResultSet.getFloat (java.lang.String)
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 09491a8a-1931-411e-9b35-2b269c1b7f12
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 00954080561b59f12d098da300ccb9fd3917ce02
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MTE75
ms.contentlocale: de-DE
ms.lasthandoff: 10/01/2018
ms.locfileid: "47682628"
---
# <a name="getfloat-method-javalangstring-sqlserverresultset"></a>getFloat-Methode (java.lang.String) (SQLServerResultSet)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Ruft den Wert des angegebenen Spaltennamens in der aktuellen Zeile dieses [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md)-Objekts als **float**-Wert in der Programmiersprache Java ab.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
public float getFloat(java.lang.String columnName)  
```  
  
#### <a name="parameters"></a>Parameter  
 *columnName*  
  
 Eine **Zeichenfolge**, die den Spaltennamen enthält.  
  
## <a name="return-value"></a>Rückgabewert  
 Ein **"float"** Wert.  
  
## <a name="exceptions"></a>Ausnahmen  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Remarks  
 Diese GetFloat-Methode wird von der GetFloat-Methode in der java.sql.ResultSet-Schnittstelle angegeben.  
  
 Von dieser Methode werden alle zahlenbasierten Typen mit der Java-Genauigkeit vom Typ **float** zurückgegeben.  
  
## <a name="see-also"></a>Weitere Informationen finden Sie unter  
 [GetFloat-Methode &#40;SQLServerResultSet&#41;](../../../connect/jdbc/reference/getfloat-method-sqlserverresultset.md)   
 [SQLServerResultSet-Elemente](../../../connect/jdbc/reference/sqlserverresultset-members.md)   
 [SQLServerResultSet-Klasse](../../../connect/jdbc/reference/sqlserverresultset-class.md)  
  
  
