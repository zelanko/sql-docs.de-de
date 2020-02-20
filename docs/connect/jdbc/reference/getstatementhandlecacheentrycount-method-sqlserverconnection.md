---
title: getStatementHandleCacheEntryCount-Methode (SQLServerConnection) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2018
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerConnection.getStatementHandleCacheEntryCount
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: ''
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 6a5d87ab4f78a5f006e87c34fa774fd9f430aaae
ms.sourcegitcommit: b78f7ab9281f570b87f96991ebd9a095812cc546
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/31/2020
ms.locfileid: "67979537"
---
# <a name="getstatementhandlecacheentrycount-method-sqlserverconnection"></a>getStatementHandleCacheEntryCount-Methode (SQLServerConnection)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

 Gibt die aktuelle Anzahl von Handles für Prepared Statements zurück, die in einem Pool zusammengefasst sind

## <a name="syntax"></a>Syntax  
  
```  
  
public int getStatementHandleCacheEntryCount()  
```  

## <a name="return-value"></a>Rückgabewert
 Ein **int**-Wert, der die aktuelle Anzahl der Handles für Prepared Statements enthält, die in einem Pool zusammengefasst sind

## <a name="exceptions"></a>Ausnahmen  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
 
## <a name="remarks"></a>Bemerkungen  
 Diese Methode ist über den JDCB-Treiber, Version 6.4 und höher, verfügbar.
 
## <a name="see-also"></a>Weitere Informationen  
 [SQLServerConnection-Elemente](../../../connect/jdbc/reference/sqlserverconnection-members.md)   
 [SQLServerConnection-Klasse](../../../connect/jdbc/reference/sqlserverconnection-class.md)  
  
  
