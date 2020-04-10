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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 06a6a95838ef4ee1c605fa54fce9ef2d81f4573e
ms.sourcegitcommit: fe5c45a492e19a320a1a36b037704bf132dffd51
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/08/2020
ms.locfileid: "80923724"
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
 **TRUE**, wenn der Cursor an die gegebene Position bewegt wird. **FALSE**, wenn sich der Cursor vor der ersten oder nach der letzten Zeile befindet.  
  
## <a name="exceptions"></a>Ausnahmen  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Bemerkungen  
 Diese absolute-Methode wird von der absolute-Methode in der java.sql.ResultSet-Schnittstelle angegeben.  
  
## <a name="see-also"></a>Weitere Informationen  
 [SQLServerResultSet-Elemente](../../../connect/jdbc/reference/sqlserverresultset-members.md)   
 [SQLServerResultSet-Klasse](../../../connect/jdbc/reference/sqlserverresultset-class.md)  
  
  
