---
title: getMoreResults-Methode (int) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerStatement.getMoreResults (int)
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 6419e5a8-8b3a-4d5b-8226-95865c52c723
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 08760680774b2e760b66d9e210c4ef939872444e
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MTE75
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "67981776"
---
# <a name="getmoreresults-method-int"></a>getMoreResults-Methode (int)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Wechselt zum nächsten Schritt des [SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-class.md)-Objekts und behandelt alle derzeit geöffneten Resultsetobjekte gemäß den Anweisungen, die durch den angegebenen Modus vorgegeben werden.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
public final boolean getMoreResults(int mode)  
```  
  
#### <a name="parameters"></a>Parameter  
 *mode*  
  
 Ein Wert vom Typ **int** zur Angabe der Behandlung von derzeit geöffneten Resultsetobjekten. Dabei muss es sich um eine der folgenden Konstanten handeln:  
  
 CLOSE_CURRENT_RESULT  
  
 KEEP_CURRENT_RESULT (vom JDBC-Treiber nicht unterstützt)  
  
 CLOSE_ALL_RESULTS  
  
## <a name="return-value"></a>Rückgabewert  
 **true** , wenn das zurückgegebene Ergebnis ein Resultset ist. Andernfalls lautet der Wert **false**.  
  
## <a name="exceptions"></a>Ausnahmen  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Remarks  
 Diese getMoreResults-Methode wird von der getMoreResults-Methode in der Java. SQL. Statement-Schnittstelle angegeben.  
  
 Falls die getMoreResults-Methode aufgerufen wird, bevor die Ergebnisse abgerufen werden, entspricht das Verhalten dem *mode*-Argument, und das nächste Ergebnis wird aufgerufen.  
  
> [!NOTE]  
>  Die Verwendung der Konstante KEEP_CURRENT_RESULT wird vom JDBC-Treiber nicht unterstützt. Bei ihrer Verwendung wird eine Ausnahme ausgelöst.  
  
## <a name="see-also"></a>Weitere Informationen  
 [getMoreResults-Methode &#40;SQLServerStatement&#41;](../../../connect/jdbc/reference/getmoreresults-method-sqlserverstatement.md)   
 [SQLServerStatement-Elemente](../../../connect/jdbc/reference/sqlserverstatement-members.md)   
 [SQLServerStatement-Klasse](../../../connect/jdbc/reference/sqlserverstatement-class.md)  
  
  
