---
title: GetFetchDirection-Methode (SQLServerResultSet) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerResultSet.getFetchDirection
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 5ab385c2-e18c-4b75-ac2d-2402af5c52a5
author: MightyPen
ms.author: genemi
manager: jroth
ms.openlocfilehash: efd432f446efaef2c8d3d391c98ea1ba72a3f662
ms.sourcegitcommit: ad2e98972a0e739c0fd2038ef4a030265f0ee788
ms.translationtype: MTE75
ms.contentlocale: de-DE
ms.lasthandoff: 06/07/2019
ms.locfileid: "66803042"
---
# <a name="getfetchdirection-method-sqlserverresultset"></a>getFetchDirection-Methode (SQLServerResultSet)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Ruft die Abrufrichtung für dieses [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md)-Objekt ab.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
public int getFetchDirection()  
```  
  
## <a name="return-value"></a>Rückgabewert  
 Ein Wert vom Typ **int** zum Angeben der aktuellen Abrufrichtung.  
  
## <a name="exceptions"></a>Ausnahmen  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Remarks  
 Diese GetFetchDirection-Methode wird von der GetFetchDirection-Methode in der java.sql.ResultSet-Schnittstelle angegeben.  
  
 Von dieser Methode wird FETCH_FORWARD für schreibgeschützte Vorwärtscursor zurückgegeben, die letzte Einstellung, die durch einen Aufruf der [setFetchDirection](../../../connect/jdbc/reference/setfetchdirection-method-sqlserverresultset.md)-Methode für andere Cursortypen vorgenommen wurde. Wenn die setFetchDirection-Methode niemals aufgerufen wurde, wird für diese Cursortypen FETCH_UNKNOWN zurückgegeben.  
  
## <a name="see-also"></a>Weitere Informationen  
 [SQLServerResultSet-Elemente](../../../connect/jdbc/reference/sqlserverresultset-members.md)   
 [SQLServerResultSet-Klasse](../../../connect/jdbc/reference/sqlserverresultset-class.md)  
  
  
