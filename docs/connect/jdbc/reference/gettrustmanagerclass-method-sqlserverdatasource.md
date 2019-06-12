---
title: GetTrustManagerClass-Methode (SQLServerDataSource) | Microsoft-Dokumentation
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
manager: jroth
ms.openlocfilehash: 327dcad497c934c787d509a41f0068691bf5588a
ms.sourcegitcommit: ad2e98972a0e739c0fd2038ef4a030265f0ee788
ms.translationtype: MTE75
ms.contentlocale: de-DE
ms.lasthandoff: 06/07/2019
ms.locfileid: "66786214"
---
# <a name="gettrustmanagerclass-method-sqlserverdatasource"></a>getTrustManagerClass-Methode (SQLServerDataSource)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Gibt den Zeichenfolgenwert der TrustManagerClass Verbindungseigenschaft zurück.
  
## <a name="syntax"></a>Syntax  
  
```  
  
public java.lang.String getTrustManagerClass()  
```  
  
## <a name="return-value"></a>Rückgabewert  
 Ein **Zeichenfolge** , enthält den Wert der-Verbindungseigenschaft TrustManagerClass oder Null, wenn kein Wert festgelegt ist.  
  
## <a name="remarks"></a>Remarks  
 Wenn die TrustManagerClass-Eigenschaft nicht festgelegt ist, die [GetTrustManagerClass](../../../connect/jdbc/reference/gettrustmanagerclass-method-sqlserverdatasource.md) Methode gibt null zurück.  
  
## <a name="see-also"></a>Weitere Informationen  
 [SQLServerDataSource-Elemente](../../../connect/jdbc/reference/sqlserverdatasource-members.md)   
 [SQLServerDataSource-Klasse](../../../connect/jdbc/reference/sqlserverdatasource-class.md)  
  
  
