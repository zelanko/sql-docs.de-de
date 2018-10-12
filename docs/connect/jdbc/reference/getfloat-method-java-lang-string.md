---
title: GetFloat-Methode (java.lang.String) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerCallableStatement.getFloat (java.lang.String)
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: b6492341-fdc2-449c-9d03-95a5dadf1bb0
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 471fc44de47f89438cff96ac6d3189f6224664eb
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MTE75
ms.contentlocale: de-DE
ms.lasthandoff: 10/01/2018
ms.locfileid: "47711868"
---
# <a name="getfloat-method-javalangstring"></a>getFloat-Methode (java.lang.String)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Ruft den Wert des angegebenen Parameters unter Berücksichtigung des Parameternamens als **float**-Wert in der Programmiersprache Java ab.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
public float getFloat(java.lang.String sCol)  
```  
  
#### <a name="parameters"></a>Parameter  
 *sCol*  
  
 Ein **String-Objekt**, das den Parameternamen enthält.  
  
## <a name="return-value"></a>Rückgabewert  
 Ein **"float"** Wert.  
  
## <a name="exceptions"></a>Ausnahmen  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Remarks  
 Diese getFloat-Methode wird von der getFloat-Methode in der java.sql.CallableStatement-Schnittstelle angegeben.  
  
 Von dieser Methode werden alle zahlenbasierten Typen mit der Java-Genauigkeit vom Typ **float** zurückgegeben.  
  
## <a name="see-also"></a>Weitere Informationen finden Sie unter  
 [getFloat-Methode &#40;SQLServerCallableStatement&#41;](../../../connect/jdbc/reference/getfloat-method-sqlservercallablestatement.md)   
 [SQLServerCallableStatement-Elemente](../../../connect/jdbc/reference/sqlservercallablestatement-members.md)   
 [SQLServerCallableStatement-Klasse](../../../connect/jdbc/reference/sqlservercallablestatement-class.md)  
  
  
