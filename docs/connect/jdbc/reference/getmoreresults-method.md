---
title: getMoreResults()-Methode | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerStatement.getMoreResults ()
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: df89db50-0b2f-4094-820a-30be25ad72fe
author: MightyPen
ms.author: genemi
ms.openlocfilehash: dcbce9783641376ae142e94ab5e45dc47fe16fef
ms.sourcegitcommit: b78f7ab9281f570b87f96991ebd9a095812cc546
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/31/2020
ms.locfileid: "67981733"
---
# <a name="getmoreresults-method-"></a>getMoreResults-Methode ()
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Wechselt zum nächsten Ergebnis dieses [SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-class.md)-Objekts.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
public final boolean getMoreResults()  
```  
  
## <a name="return-value"></a>Rückgabewert  
 Der Wert ist **TRUE**, wenn das zurückgegebene Ergebnis ein Resultset ist. Andernfalls lautet der Wert **false**.  
  
## <a name="exceptions"></a>Ausnahmen  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Bemerkungen  
 Diese getMoreResults-Methode wird von der getMoreResults-Methode in der java.sql.Statement-Schnittstelle angegeben.  
  
 Durch den Aufruf der getMoreResults-Methode werden alle momentan geöffneten Resultsetobjekte geschlossen, die mit der [getResultSet](../../../connect/jdbc/reference/getresultset-method-sqlserverstatement.md)-Methode abgerufen werden.  
  
## <a name="see-also"></a>Weitere Informationen  
 [getMoreResults-Methode &#40;SQLServerStatement&#41;](../../../connect/jdbc/reference/getmoreresults-method-sqlserverstatement.md)   
 [SQLServerStatement-Elemente](../../../connect/jdbc/reference/sqlserverstatement-members.md)   
 [SQLServerStatement-Klasse](../../../connect/jdbc/reference/sqlserverstatement-class.md)  
  
  
