---
title: GetUpdateCount-Methode (SQLServerStatement) | Microsoft-Dokumentation
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
manager: jroth
ms.openlocfilehash: 6f05796220e305a0d6e06e15a58f780048d49a53
ms.sourcegitcommit: ad2e98972a0e739c0fd2038ef4a030265f0ee788
ms.translationtype: MTE75
ms.contentlocale: de-DE
ms.lasthandoff: 06/07/2019
ms.locfileid: "66790529"
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
  
## <a name="remarks"></a>Remarks  
 Diese GetUpdateCount-Methode wird von der GetUpdateCount-Methode in der java.sql.Statement-Schnittstelle angegeben.  
  
## <a name="see-also"></a>Weitere Informationen  
 [SQLServerStatement-Elemente](../../../connect/jdbc/reference/sqlserverstatement-members.md)   
 [SQLServerStatement-Klasse](../../../connect/jdbc/reference/sqlserverstatement-class.md)  
  
  
