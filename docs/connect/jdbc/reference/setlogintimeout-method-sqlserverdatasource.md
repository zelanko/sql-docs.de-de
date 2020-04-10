---
title: setLoginTimeout-Methode (SQLServerDataSource) | Microsoft-Dokumentation
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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 83d6869075e296465ee9c60b0c5032407d4fe2da
ms.sourcegitcommit: fe5c45a492e19a320a1a36b037704bf132dffd51
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/08/2020
ms.locfileid: "80925757"
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
  
## <a name="remarks"></a>Bemerkungen  
 Diese setLoginTimeout-Methode wird von der setLoginTimeout-Methode in der javax.sql.DataSource-Schnittstelle angegeben.  
  
## <a name="see-also"></a>Weitere Informationen  
 [SQLServerDataSource-Elemente](../../../connect/jdbc/reference/sqlserverdatasource-members.md)   
 [SQLServerDataSource-Klasse](../../../connect/jdbc/reference/sqlserverdatasource-class.md)  
  
  
