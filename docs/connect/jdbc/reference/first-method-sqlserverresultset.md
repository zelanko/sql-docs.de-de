---
title: first-Methode (SQLServerResultSet) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerResultSet.first
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 67ed9447-7b10-4c87-98e7-f4c2e2470b3a
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: ac09ce40ecd70b4bde4bf2a01017775a7b90863f
ms.sourcegitcommit: fe5c45a492e19a320a1a36b037704bf132dffd51
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/08/2020
ms.locfileid: "80924219"
---
# <a name="first-method-sqlserverresultset"></a>first-Methode (SQLServerResultSet)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Versetzt den Cursor in die erste Zeile dieses [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md)-Objekts.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
public boolean first()  
```  
  
## <a name="return-value"></a>Rückgabewert  
 **TRUE**, wenn der Cursor in die erste Zeile bewegt wird. Andernfalls lautet der Wert **false**.  
  
## <a name="exceptions"></a>Ausnahmen  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Bemerkungen  
 Diese first-Methode wird von der first-Methode in der java.sql.ResultSet-Schnittstelle angegeben.  
  
## <a name="see-also"></a>Weitere Informationen  
 [SQLServerResultSet-Elemente](../../../connect/jdbc/reference/sqlserverresultset-members.md)   
 [SQLServerResultSet-Klasse](../../../connect/jdbc/reference/sqlserverresultset-class.md)  
  
  
