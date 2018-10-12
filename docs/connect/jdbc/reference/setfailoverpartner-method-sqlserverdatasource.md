---
title: SetFailoverPartner-Methode (SQLServerDataSource) | Microsoft-Dokumentation
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
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 0b737bee1f97e11a1acf0adf039603125b15609c
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MTE75
ms.contentlocale: de-DE
ms.lasthandoff: 10/01/2018
ms.locfileid: "47621998"
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
  
## <a name="remarks"></a>Remarks  
 Der von dieser Methode festgelegte Wert wird im Falle eines Fehlers beim erstmaligen Herstellen einer Verbindung mit dem Prinzipalserver verwendet. Sobald die Verbindung hergestellt wurde, wird dieser Wert ignoriert. In Verbindung mit dieser Methode muss auch die [setDatabaseName](../../../connect/jdbc/reference/setdatabasename-method-sqlserverdatasource.md)-Methode verwendet werden, da andernfalls eine Ausnahme ausgelöst wird.  
  
 Bei festgelegtem Failoverservernamen wird das Angeben der Portnummer des Failoverservers vom Treiber nicht unterstützt. Das Aufrufen der [setServerName](../../../connect/jdbc/reference/setservername-method-sqlserverdatasource.md)-Methode und der [setInstanceName](../../../connect/jdbc/reference/setinstancename-method-sqlserverdatasource.md)-Methode mit der [setFailoverPartner](../../../connect/jdbc/reference/setfailoverpartner-method-sqlserverdatasource.md)-Methode wird jedoch unterstützt.  
  
## <a name="see-also"></a>Weitere Informationen finden Sie unter  
 [SQLServerDataSource-Elemente](../../../connect/jdbc/reference/sqlserverdatasource-members.md)   
 [SQLServerDataSource-Klasse](../../../connect/jdbc/reference/sqlserverdatasource-class.md)  
  
  
