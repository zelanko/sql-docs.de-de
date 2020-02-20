---
title: closeUnreferencedPreparedStatementHandles-Methode (SQLServerConnection) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2018
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerConnection.closeUnreferencedPreparedStatementHandles
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: ''
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 7256475421b8666e28eaaf03f3ff4cb9768aa289
ms.sourcegitcommit: b78f7ab9281f570b87f96991ebd9a095812cc546
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/31/2020
ms.locfileid: "67955600"
---
# <a name="closeunreferencedpreparedstatementhandles-method-sqlserverconnection"></a>closeUnreferencedPreparedStatementHandles-Methode (SQLServerConnection)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

 Erzwingt, dass unprepare-Anforderungen für ausstehende verworfene Prepared Statements ausgeführt werden.

## <a name="syntax"></a>Syntax  
  
```  
  
public void closeUnreferencedPreparedStatementHandles()  
```  


## <a name="exceptions"></a>Ausnahmen  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  

## <a name="remarks"></a>Bemerkungen  
 Diese Methode ist im JDCB-Treiber, Version 6.4 und höher, verfügbar.
 
## <a name="see-also"></a>Weitere Informationen  
 [SQLServerConnection-Elemente](../../../connect/jdbc/reference/sqlserverconnection-members.md)   
 [SQLServerConnection-Klasse](../../../connect/jdbc/reference/sqlserverconnection-class.md)  
  
  
