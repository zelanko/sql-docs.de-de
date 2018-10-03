---
title: GetDisableStatementPooling-Methode (SQLServerDataSource) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2018
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: ''
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: f7da0c0139af73e207a4aa28ae6e99fc291039da
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MTE75
ms.contentlocale: de-DE
ms.lasthandoff: 10/01/2018
ms.locfileid: "47634598"
---
# <a name="getdisablestatementpooling-method-sqlserverdatasource"></a>getDisableStatementPooling-Methode (SQLServerDataSource)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Gibt den Wert der **DisableStatementPooling** Connection-Eigenschaft. Diese Einstellung steuert, ob die Anweisung Verbindungspooling aktiviert ist oder nicht für diese Verbindung.

  
## <a name="syntax"></a>Syntax  
  
```
public boolean getDisableStatementPooling();  
```  
  
## <a name="return-value"></a>Rückgabewert  
 Ein **booleschen** mit dem Wert des **DisableStatementPooling** Connection-Eigenschaft.
  
## <a name="exceptions"></a>Ausnahmen  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
 
## <a name="remarks"></a>Remarks  
 Diese Methode wird von JDBC Driver, Version 6.4 verfügbar und auf dem Weg.
 
## <a name="see-also"></a>Weitere Informationen finden Sie unter  
 [SQLServerDataSource-Elemente](../../../connect/jdbc/reference/sqlserverdatasource-members.md)   
 [SQLServerDataSource-Klasse](../../../connect/jdbc/reference/sqlserverdatasource-class.md)  
  
  
