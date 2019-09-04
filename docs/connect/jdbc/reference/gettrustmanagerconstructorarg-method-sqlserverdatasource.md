---
title: gettrustmanagerconstructorarg-Methode (SQLServerDataSource) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2018
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerDataSource.getTrustManagerConstructorArg
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: ''
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 8f3af347e41f3ba90b283b56d8cb2c1550b69006
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MTE75
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "67978594"
---
# <a name="gettrustmanagerconstructorarg-method-sqlserverdatasource"></a>getTrustManagerConstructorArg-Methode (SQLServerDataSource)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Gibt den Zeichen folgen Wert der Trust managerconstructor arg-Verbindungs Eigenschaft zurück.
  
## <a name="syntax"></a>Syntax  
  
```  
  
public java.lang.String getTrustManagerConstructorArg()  
```  
  
## <a name="return-value"></a>Rückgabewert  
 Eine **Zeichenfolge** , die den Wert der Trust managerconstructor arg-Verbindungs Eigenschaft enthält, oder NULL, wenn kein Wert festgelegt ist.  
  
## <a name="remarks"></a>Bemerkungen  
 Wenn die trustmanagerclass-Eigenschaft nicht festgelegt ist, gibt die [gettrustmanagerconstructorarg](../../../connect/jdbc/reference/gettrustmanagerconstructorarg-method-sqlserverdatasource.md) -Methode NULL zurück.  
  
## <a name="see-also"></a>Weitere Informationen  
 [SQLServerDataSource-Elemente](../../../connect/jdbc/reference/sqlserverdatasource-members.md)   
 [SQLServerDataSource-Klasse](../../../connect/jdbc/reference/sqlserverdatasource-class.md)  
  
  
