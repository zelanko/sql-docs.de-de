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
manager: craigg
ms.openlocfilehash: 298e169fe2b67b16b55d607f504446c48893fc1b
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MTE75
ms.contentlocale: de-DE
ms.lasthandoff: 10/01/2018
ms.locfileid: "47616938"
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
 Dieser absolute-Methode wird von der absolute-Methode in der java.sql.ResultSet-Schnittstelle angegeben.  
  
## <a name="see-also"></a>Weitere Informationen finden Sie unter  
 [SQLServerResultSet-Elemente](../../../connect/jdbc/reference/sqlserverresultset-members.md)   
 [SQLServerResultSet-Klasse](../../../connect/jdbc/reference/sqlserverresultset-class.md)  
  
  
