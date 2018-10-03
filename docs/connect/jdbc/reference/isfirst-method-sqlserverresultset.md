---
title: IsFirst-Methode (SQLServerResultSet) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerResultSet.isFirst
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 2ff94b95-32ad-4378-8bb1-970030527bb2
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: eba9be492a28d3254b0f8826a4cdf2c566ae285f
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MTE75
ms.contentlocale: de-DE
ms.lasthandoff: 10/01/2018
ms.locfileid: "47795798"
---
# <a name="isfirst-method-sqlserverresultset"></a>isFirst-Methode (SQLServerResultSet)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Ruft ab, ob sich der Cursor in der ersten Zeile dieses [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md)-Objekts befindet.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
public boolean isFirst()  
```  
  
## <a name="return-value"></a>Rückgabewert  
 **"true"** , wenn der Cursor in der ersten Zeile befindet. **"false"** Wenn der Cursor an einer beliebigen anderen Position ist oder wenn das Resultset keine Zeilen enthält.  
  
## <a name="exceptions"></a>Ausnahmen  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Remarks  
 Diese IsFirst-Methode wird von der IsFirst-Methode in der java.sql.ResultSet-Schnittstelle angegeben.  
  
 Wird diese Methode mit Vorwärtscursors und dynamischen Cursors verwendet, wird eine Ausnahme ausgelöst.  
  
## <a name="see-also"></a>Weitere Informationen finden Sie unter  
 [SQLServerResultSet-Elemente](../../../connect/jdbc/reference/sqlserverresultset-members.md)   
 [SQLServerResultSet-Klasse](../../../connect/jdbc/reference/sqlserverresultset-class.md)  
  
  
