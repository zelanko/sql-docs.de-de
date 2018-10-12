---
title: GetFailoverPartner-Methode (SQLServerDataSource) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerDataSource.getFailoverPartner
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 885f927f-9c48-42e0-a7fb-fd936d2b8130
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 39195742d8b6a2a03b0b2c835f47d0ba42735791
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MTE75
ms.contentlocale: de-DE
ms.lasthandoff: 10/01/2018
ms.locfileid: "47730458"
---
# <a name="getfailoverpartner-method-sqlserverdatasource"></a>getFailoverPartner-Methode (SQLServerDataSource)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Gibt den Namen des Failoverservers zurück, der in einer Datenbankspiegelungskonfiguration verwendet wird.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
public string getFailoverPartner()  
```  
  
## <a name="return-value"></a>Rückgabewert  
 Eine **Zeichenfolge**, die den Namen des Failoverpartners oder NULL enthält, sofern kein Name festgelegt ist.  
  
## <a name="remarks"></a>Remarks  
 Der von dieser Methode zurückgegebene Wert gibt den Failoverpartnernamen wieder, der mithilfe der [setFailoverPartner](../../../connect/jdbc/reference/setfailoverpartner-method-sqlserverdatasource.md)-Methode festgelegt wurde.  
  
## <a name="see-also"></a>Weitere Informationen finden Sie unter  
 [SQLServerDataSource-Elemente](../../../connect/jdbc/reference/sqlserverdatasource-members.md)   
 [SQLServerDataSource-Klasse](../../../connect/jdbc/reference/sqlserverdatasource-class.md)  
  
  
