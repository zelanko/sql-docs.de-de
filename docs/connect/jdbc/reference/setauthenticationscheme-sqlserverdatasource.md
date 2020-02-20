---
title: setAuthenticationScheme (SQLServerDataSource) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: b942f78e-7ce1-44ef-923d-a7c3d7c76b83
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 3c728bd32a0aff2549d9e572955c8fb6d889e127
ms.sourcegitcommit: b78f7ab9281f570b87f96991ebd9a095812cc546
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/31/2020
ms.locfileid: "67975284"
---
# <a name="setauthenticationscheme-sqlserverdatasource"></a>setAuthenticationScheme (SQLServerDataSource)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Gibt die Art der integrierten Sicherheit an, die für die Anwendung verwendet werden soll.  
  
## <a name="syntax"></a>Syntax  
  
```vb  
public void setAuthenticationScheme(String authenticationScheme);  
```  
  
#### <a name="parameters"></a>Parameter  
 *authenticationScheme*  
  
 Mögliche Werte sind **"JavaKerberos"** und der Standardwert **"NativeAuthentication"** . Weitere Informationen finden Sie unter [Verwenden der integrierten Kerberos-Authentifizierung für Verbindungen mit SQL Server](../../../connect/jdbc/using-kerberos-integrated-authentication-to-connect-to-sql-server.md).  
  
## <a name="see-also"></a>Weitere Informationen  
 [SQLServerDataSource-Elemente](../../../connect/jdbc/reference/sqlserverdatasource-members.md)   
 [SQLServerDataSource-Klasse](../../../connect/jdbc/reference/sqlserverdatasource-class.md)  
  
  
