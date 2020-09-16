---
description: getUpdateCount-Methode (SQLServerStatement)
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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 19a4cfc7b9957d8ba4392477e6dcd3732f10bd7c
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 08/17/2020
ms.locfileid: "88433902"
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
  
  
