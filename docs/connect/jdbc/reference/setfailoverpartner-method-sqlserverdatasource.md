---
title: setFailoverPartner-Methode (SQLServerDataSource) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerDataSource.setFailoverPartner
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 5310b7c2-9d10-474f-ad3a-218fe5da694b
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 58604614f5f5025e0e0982f7d191868e3baf23e0
ms.sourcegitcommit: fe5c45a492e19a320a1a36b037704bf132dffd51
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/08/2020
ms.locfileid: "80922339"
---
# <a name="setfailoverpartner-method-sqlserverdatasource"></a>setFailoverPartner-Methode (SQLServerDataSource)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Legt den Namen des Failoverservers fest, der in einer Datenbankspiegelungskonfiguration verwendet wird.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
public void setFailoverPartner(java.lang.String serverName)  
```  
  
#### <a name="parameters"></a>Parameter  
 *serverName*  
  
 Eine **Zeichenfolge** mit dem Namen des Failoverservers.  
  
## <a name="remarks"></a>Bemerkungen  
 Der von dieser Methode festgelegte Wert wird im Falle eines Fehlers beim erstmaligen Herstellen einer Verbindung mit dem Prinzipalserver verwendet. Sobald die Verbindung hergestellt wurde, wird dieser Wert ignoriert. In Verbindung mit dieser Methode muss auch die [setDatabaseName](../../../connect/jdbc/reference/setdatabasename-method-sqlserverdatasource.md)-Methode verwendet werden, da andernfalls eine Ausnahme ausgelöst wird.  
  
 Bei festgelegtem Failoverservernamen wird das Angeben der Portnummer des Failoverservers vom Treiber nicht unterstützt. Das Aufrufen der [setServerName](../../../connect/jdbc/reference/setservername-method-sqlserverdatasource.md)-Methode und der [setInstanceName](../../../connect/jdbc/reference/setinstancename-method-sqlserverdatasource.md)-Methode mit der [setFailoverPartner](../../../connect/jdbc/reference/setfailoverpartner-method-sqlserverdatasource.md)-Methode wird jedoch unterstützt.  
  
## <a name="see-also"></a>Weitere Informationen  
 [SQLServerDataSource-Elemente](../../../connect/jdbc/reference/sqlserverdatasource-members.md)   
 [SQLServerDataSource-Klasse](../../../connect/jdbc/reference/sqlserverdatasource-class.md)  
  
  
