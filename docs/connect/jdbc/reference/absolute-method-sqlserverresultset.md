---
title: absolute-Methode (SQLServerResultSet) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerResultSet.absolute
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 638e8148-8ca0-4e1f-9ec2-04a11bc9809b
author: MightyPen
ms.author: genemi
manager: jroth
ms.openlocfilehash: b0572ed756bd8b347c01e05168873ac543a0ea7e
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MTE75
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "66783561"
---
# <a name="absolute-method-sqlserverresultset"></a>absolute-Methode (SQLServerResultSet)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Versetzt den Cursor in die vorhandene Zeile in diesem [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md)-Objekt.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
public boolean absolute(int row)  
```  
  
#### <a name="parameters"></a>Parameter  
 *row*  
  
 Ein Wert vom Typ **int** zum Angeben der Zeilenzahl, an die verschoben werden soll. Kann positiv, negativ oder "0" sein.  
  
## <a name="return-value"></a>Rückgabewert  
 **"true"** , wenn der Cursor an die angegebene Position verschoben wird. **"false"** wenn er vor der ersten Zeile oder nach der letzten Zeile ist.  
  
## <a name="exceptions"></a>Ausnahmen  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Remarks  
 Diese absolute-Methode wird von der absolute-Methode in der java.sql.ResultSet-Schnittstelle angegeben.  
  
## <a name="see-also"></a>Weitere Informationen  
 [SQLServerResultSet-Elemente](../../../connect/jdbc/reference/sqlserverresultset-members.md)   
 [SQLServerResultSet-Klasse](../../../connect/jdbc/reference/sqlserverresultset-class.md)  
  
  
