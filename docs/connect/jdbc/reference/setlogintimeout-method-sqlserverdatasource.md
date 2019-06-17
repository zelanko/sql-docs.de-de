---
title: SetLoginTimeout-Methode (SQLServerDataSource) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerDataSource.setLoginTimeout
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: b63d1cf4-dc1b-4e35-9a56-50436642eaaf
author: MightyPen
ms.author: genemi
manager: jroth
ms.openlocfilehash: a242499204215f0d8ecdb16698bcc0fe07377db3
ms.sourcegitcommit: ad2e98972a0e739c0fd2038ef4a030265f0ee788
ms.translationtype: MTE75
ms.contentlocale: de-DE
ms.lasthandoff: 06/07/2019
ms.locfileid: "66794255"
---
# <a name="setlogintimeout-method-sqlserverdatasource"></a>setLoginTimeout-Methode (SQLServerDataSource)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Legt die Anzahl von Sekunden fest, die vom [SQLServerDataSource](../../../connect/jdbc/reference/sqlserverdatasource-class.md)-Objekt bei der Verbindungsherstellung gewartet wird.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
public void setLoginTimeout(int loginTimeout)  
```  
  
#### <a name="parameters"></a>Parameter  
 *loginTimeout*  
  
 Ein Wert vom Typ **int** zum Darstellen der Wartedauer in Sekunden. Mit dem Wert "0" wird angegeben, dass es sich bei dem Timeout um das Standardsystemtimeout (standardmäßig 15 Sekunden) handelt.  
  
## <a name="remarks"></a>Remarks  
 Diese SetLoginTimeout-Methode wird von der SetLoginTimeout-Methode in der javax.sql.DataSource-Schnittstelle angegeben.  
  
## <a name="see-also"></a>Weitere Informationen  
 [SQLServerDataSource-Elemente](../../../connect/jdbc/reference/sqlserverdatasource-members.md)   
 [SQLServerDataSource-Klasse](../../../connect/jdbc/reference/sqlserverdatasource-class.md)  
  
  
