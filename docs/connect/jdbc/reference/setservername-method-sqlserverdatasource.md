---
title: setservername-Methode (SQLServerDataSource) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerDataSource.setServerName
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 70920828-eda0-4064-be9f-c1e460db8f00
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 344ae0104f527739bf3a954ed9138252d7efb58e
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MTE75
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "67972933"
---
# <a name="setservername-method-sqlserverdatasource"></a>setServerName-Methode (SQLServerDataSource)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Legt den Namen des Computers fest, auf dem [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] ausgeführt wird.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
public void setServerName(java.lang.String serverName)  
```  
  
#### <a name="parameters"></a>Parameter  
 *serverName*  
  
 Ein **String-Objekt**, das den Servernamen enthält.  
  
## <a name="remarks"></a>Remarks  
 Der Servername ist der Hostname des Zielcomputers, auf dem [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] ausgeführt wird. Ist die serverName-Eigenschaft nicht festgelegt, wird von [getServerName](../../../connect/jdbc/reference/getservername-method-sqlserverdatasource.md) der Standardwert (NULL) zurückgegeben.  
  
## <a name="see-also"></a>Weitere Informationen  
 [SQLServerDataSource-Elemente](../../../connect/jdbc/reference/sqlserverdatasource-members.md)   
 [SQLServerDataSource-Klasse](../../../connect/jdbc/reference/sqlserverdatasource-class.md)  
  
  
