---
title: isStatementPoolingEnabled-Methode (SQLServerConnection) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2018
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerConnection.isStatementPoolingEnabled
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: ''
author: MightyPen
ms.author: genemi
ms.openlocfilehash: d2f5178c8a2ce5b527ce70e6a3d8fc139ccc9c72
ms.sourcegitcommit: b78f7ab9281f570b87f96991ebd9a095812cc546
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/31/2020
ms.locfileid: "67977200"
---
# <a name="isstatementpoolingenabled-method-sqlserverconnection"></a>isStatementPoolingEnabled-Methode (SQLServerConnection)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

 Diese Methode gibt zurück, ob für diese Verbindung Anweisungspooling aktiviert ist.

## <a name="syntax"></a>Syntax  
  
```  
  
public boolean isStatementPoolingEnabled()  
```  

## <a name="return-value"></a>Rückgabewert
 Der Rückgabewert ist ein **Boolescher Wert**, der das Flag enthält, das angibt, ob Anweisungspooling aktiviert ist.

## <a name="exceptions"></a>Ausnahmen  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
 
## <a name="remarks"></a>Bemerkungen  
 Diese Methode ist über den JDCB-Treiber, Version 6.4 und höher, verfügbar.
 
## <a name="see-also"></a>Weitere Informationen  
 [SQLServerConnection-Elemente](../../../connect/jdbc/reference/sqlserverconnection-members.md)   
 [SQLServerConnection-Klasse](../../../connect/jdbc/reference/sqlserverconnection-class.md)  
  
  
