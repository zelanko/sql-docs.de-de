---
title: GetWorkstationID-Methode (SQLServerDataSource) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerDataSource.getWorkstationID
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: f6a701de-a8fa-4668-9310-99a8c6e32c88
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: ece266f25a57c2a99e8acb0b308f7bd918189057
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MTE75
ms.contentlocale: de-DE
ms.lasthandoff: 10/01/2018
ms.locfileid: "47673628"
---
# <a name="getworkstationid-method-sqlserverdatasource"></a>getWorkstationID-Methode (SQLServerDataSource)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Gibt den Namen des Clientcomputers zurück, der zum Herstellen einer Verbindung mit der Datenquelle verwendet wird.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
public java.lang.String getWorkstationID()  
```  
  
## <a name="return-value"></a>Rückgabewert  
 Eine **Zeichenfolge** mit dem Computernamen des Clients.  
  
## <a name="remarks"></a>Remarks  
 Die workstationID ist der Name des Clientcomputers oder der Workstation. Wenn die WorkstationID-Eigenschaft nicht festgelegt ist, wird der Standardwert erstellt InetAddress.getLocalHost().getHostName()-Methode aufrufen. Wenn GetHostName einen leeren Wert zurückgibt, wird die getHostAddress().toString()-Methode aufgerufen.  
  
## <a name="see-also"></a>Weitere Informationen finden Sie unter  
 [SQLServerDataSource-Elemente](../../../connect/jdbc/reference/sqlserverdatasource-members.md)   
 [SQLServerDataSource-Klasse](../../../connect/jdbc/reference/sqlserverdatasource-class.md)  
  
  
