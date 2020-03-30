---
title: Methode „getUpdateCount“ (SQLServerStatement) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerStatement.getUpdateCount
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: e9570228-4500-44b6-b2f1-84ac050b5112
author: MightyPen
ms.author: genemi
ms.openlocfilehash: e319f5f924fc82b3b7dfac31d5d64d8ea15ee3ab
ms.sourcegitcommit: ff82f3260ff79ed860a7a58f54ff7f0594851e6b
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/29/2020
ms.locfileid: "67978397"
---
# <a name="getupdatecount-method-sqlserverstatement"></a>getUpdateCount-Methode (SQLServerStatement)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Ruft das aktuelle Ergebnis als Updatezählung ab.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
public final int getUpdateCount()  
```  
  
## <a name="return-value"></a>Rückgabewert  
 Ein Element vom Typ **int** mit der Updatezählung. Ist das zurückgegebene Ergebnis ein Resultsetobjekt oder sind mehrere Ergebnisse vorhanden, wird -1 zurückgegeben.  
  
## <a name="exceptions"></a>Ausnahmen  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Bemerkungen  
 Diese getUpdateCount-Methode wird von der getUpdateCount-Methode in der java.sql.Statement-Schnittstelle angegeben.  
  
## <a name="see-also"></a>Weitere Informationen  
 [SQLServerStatement-Elemente](../../../connect/jdbc/reference/sqlserverstatement-members.md)   
 [SQLServerStatement-Klasse](../../../connect/jdbc/reference/sqlserverstatement-class.md)  
  
  
