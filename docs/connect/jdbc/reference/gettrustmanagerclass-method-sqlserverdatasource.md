---
title: gettrustmanagerclass-Methode (SQLServerDataSource) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2018
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerDataSource.getTrustManagerClass
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: ''
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 567f5e7e3aca87b875e4f93c26d7caa5535a8c75
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MTE75
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "67978598"
---
# <a name="gettrustmanagerclass-method-sqlserverdatasource"></a>getTrustManagerClass-Methode (SQLServerDataSource)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Gibt den Zeichen folgen Wert der Trust ManagerClass-Verbindungs Eigenschaft zurück.
  
## <a name="syntax"></a>Syntax  
  
```  
  
public java.lang.String getTrustManagerClass()  
```  
  
## <a name="return-value"></a>Rückgabewert  
 Eine **Zeichenfolge** , die den Wert der Trust ManagerClass-Verbindungs Eigenschaft enthält, oder NULL, wenn kein Wert festgelegt ist.  
  
## <a name="remarks"></a>Remarks  
 Wenn die trustmanagerclass-Eigenschaft nicht festgelegt ist, gibt die [gettrustmanagerclass](../../../connect/jdbc/reference/gettrustmanagerclass-method-sqlserverdatasource.md) -Methode NULL zurück.  
  
## <a name="see-also"></a>Weitere Informationen  
 [SQLServerDataSource-Elemente](../../../connect/jdbc/reference/sqlserverdatasource-members.md)   
 [SQLServerDataSource-Klasse](../../../connect/jdbc/reference/sqlserverdatasource-class.md)  
  
  
