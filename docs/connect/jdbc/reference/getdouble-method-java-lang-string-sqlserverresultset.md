---
title: getDouble-Methode (java.lang.String) (SQLServerResultSet) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerResultSet.getDouble (java.lang.String)
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 3ee26412-43d2-404b-bc05-ffd0fc75805c
author: MightyPen
ms.author: genemi
ms.openlocfilehash: e82f85941899fc05fc8fdf35cd7ae65870100ef3
ms.sourcegitcommit: b78f7ab9281f570b87f96991ebd9a095812cc546
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/31/2020
ms.locfileid: "67983579"
---
# <a name="getdouble-method-javalangstring-sqlserverresultset"></a>getDouble-Methode (java.lang.String) (SQLServerResultSet)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Ruft den Wert des angegebenen Spaltennamens in der aktuellen Zeile dieses [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md)-Objekts als Wert vom Typ **double** in der Programmiersprache Java ab.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
public double getDouble(java.lang.String columnName)  
```  
  
#### <a name="parameters"></a>Parameter  
 *columnName*  
  
 Eine **Zeichenfolge**, die den Spaltennamen enthält.  
  
## <a name="return-value"></a>Rückgabewert  
 Ein **double**-Wert  
  
## <a name="exceptions"></a>Ausnahmen  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Bemerkungen  
 Diese getDouble-Methode wird von der getDouble-Methode in der java.sql.ResultSet-Schnittstelle angegeben.  
  
 Von dieser Methode werden alle zahlenbasierten Datentypen mit der Java-Genauigkeit vom Typ **double** zurückgegeben.  
  
## <a name="see-also"></a>Weitere Informationen  
 [getDouble-Methode &#40;SQLServerResultSet&#41;](../../../connect/jdbc/reference/getdouble-method-sqlserverresultset.md)   
 [SQLServerResultSet-Elemente](../../../connect/jdbc/reference/sqlserverresultset-members.md)   
 [SQLServerResultSet-Klasse](../../../connect/jdbc/reference/sqlserverresultset-class.md)  
  
  
