---
title: GetQueryTimeout-Methode (SQLServerStatement) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerStatement.getQueryTimeout
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 8dff954f-b458-4fa6-abe6-be62ff75e2b9
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: b19809f549fa252f18964f2c3b9e63de1c8cf5e3
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MTE75
ms.contentlocale: de-DE
ms.lasthandoff: 10/01/2018
ms.locfileid: "47841468"
---
# <a name="getquerytimeout-method-sqlserverstatement"></a>getQueryTimeout-Methode (SQLServerStatement)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Ruft die Anzahl von Sekunden ab, die von [!INCLUDE[jdbcNoVersion](../../../includes/jdbcnoversion_md.md)] auf die Ausführung dieses [SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-class.md)-Objekts gewartet wird.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
public final int getQueryTimeout()  
```  
  
## <a name="return-value"></a>Rückgabewert  
 Ein Wert vom Typ **int**, der die Wartezeit des JDBC-Treibers in Sekunden angibt, oder „0“, wenn kein Limit vorhanden ist.  
  
## <a name="exceptions"></a>Ausnahmen  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Remarks  
 Diese GetQueryTimeout-Methode wird von der GetQueryTimeout-Methode in der java.sql.Statement-Schnittstelle angegeben.  
  
## <a name="see-also"></a>Weitere Informationen finden Sie unter  
 [SQLServerStatement-Elemente](../../../connect/jdbc/reference/sqlserverstatement-members.md)   
 [SQLServerStatement-Klasse](../../../connect/jdbc/reference/sqlserverstatement-class.md)  
  
  
