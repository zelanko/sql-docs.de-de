---
title: SetUser-Methode (SQLServerDataSource) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: conceptual
apiname:
- SQLServerDataSource.setUser
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: d2ea7906-2d10-438d-aa51-f576eea923c7
caps.latest.revision: 9
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 8b6bf6d311e318dd9f233de2f698ad1d7892714e
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/03/2018
---
# <a name="setuser-method-sqlserverdatasource"></a>setUser-Methode (SQLServerDataSource)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Legt den Benutzernamen fest, der zum Herstellen einer Verbindung mit der Datenquelle verwendet wird.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
public void setUser(java.lang.String user)  
```  
  
#### <a name="parameters"></a>Parameter  
 *user*  
  
 Ein **Zeichenfolge** , die den Benutzernamen enthält.  
  
## <a name="remarks"></a>Hinweise  
 SetUser-Methode wird der Benutzername, der verwendet wird, für die Verbindung [!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)]. Wenn der Wert für den Benutzernamen nicht festgelegt ist, die [GetUser](../../../connect/jdbc/reference/getuser-method-sqlserverdatasource.md) -Methode den Standardwert NULL zurück.  
  
## <a name="see-also"></a>Siehe auch  
 [SQLServerDataSource-Elemente](../../../connect/jdbc/reference/sqlserverdatasource-members.md)   
 [SQLServerDataSource-Klasse](../../../connect/jdbc/reference/sqlserverdatasource-class.md)  
  
  
