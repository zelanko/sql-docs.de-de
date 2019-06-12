---
title: SetWorkstationID-Methode (SQLServerDataSource) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerDataSource.setWorkstationID
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: c1093615-90bf-4918-9f05-8abd765ffb03
author: MightyPen
ms.author: genemi
manager: jroth
ms.openlocfilehash: 3b9b4dd4ce34dcc39148a2346fd729a8dfb6b87f
ms.sourcegitcommit: ad2e98972a0e739c0fd2038ef4a030265f0ee788
ms.translationtype: MTE75
ms.contentlocale: de-DE
ms.lasthandoff: 06/07/2019
ms.locfileid: "66773233"
---
# <a name="setworkstationid-method-sqlserverdatasource"></a>setWorkstationID-Methode (SQLServerDataSource)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Legt den Namen des Clientcomputers fest, der zum Herstellen einer Verbindung mit der Datenquelle verwendet wird.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
public void setWorkstationID(java.lang.String workstationID)  
```  
  
#### <a name="parameters"></a>Parameter  
 *workstationID*  
  
 Eine **Zeichenfolge** mit dem Computernamen des Clients.  
  
## <a name="remarks"></a>Remarks  
 Die workstationID ist der Name des Clientcomputers oder der Workstation. Wenn die WorkstationID-Eigenschaft nicht festgelegt ist, wird der Standardwert erstellt InetAddress.getLocalHost().getHostName()-Methode aufrufen. Wenn GetHostName einen leeren Wert zurückgibt, wird die getHostAddress().toString()-Methode aufgerufen.  
  
## <a name="see-also"></a>Weitere Informationen  
 [SQLServerDataSource-Elemente](../../../connect/jdbc/reference/sqlserverdatasource-members.md)   
 [SQLServerDataSource-Klasse](../../../connect/jdbc/reference/sqlserverdatasource-class.md)  
  
  
