---
title: setWorkstationID-Methode (SQLServerDataSource) | Microsoft-Dokumentation
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
ms.openlocfilehash: 08b09958276a5cc7f7cc3de6e56f7d7336ca9e64
ms.sourcegitcommit: b78f7ab9281f570b87f96991ebd9a095812cc546
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/31/2020
ms.locfileid: "67972033"
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
  
## <a name="remarks"></a>Bemerkungen  
 Die workstationID ist der Name des Clientcomputers oder der Workstation. Ist die workstationID-Eigenschaft nicht festgelegt, wird der Standardwert durch Aufruf der InetAddress.getLocalHost().getHostName()-Methode erstellt. Wenn getHostName einen leeren Wert zurückgibt, wird die Methode „getHostAddress().toString()“ aufgerufen.  
  
## <a name="see-also"></a>Weitere Informationen  
 [SQLServerDataSource-Elemente](../../../connect/jdbc/reference/sqlserverdatasource-members.md)   
 [SQLServerDataSource-Klasse](../../../connect/jdbc/reference/sqlserverdatasource-class.md)  
  
  
