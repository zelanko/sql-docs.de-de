---
title: setHostNameInCertificate-Methode (SQLServerDataSource) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- setHostNameInCertificate Method (SQLServerDataSource)
apilocation:
- setHostNameInCertificate Method (SQLServerDataSource)
apitype: Assembly
ms.assetid: 2bcf4f2e-a103-4374-abc4-ffad4ce8e3c0
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 418e9aea8d44d3be23bc21c5a8950c5788e7c07a
ms.sourcegitcommit: 54cfeb36c9caa51ec68fa8f4a1918e305db5e00a
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/11/2020
ms.locfileid: "81219290"
---
# <a name="sethostnameincertificate-method-sqlserverdatasource"></a>setHostNameInCertificate-Methode (SQLServerDataSource)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Legt den Hostnamen fest, der bei der Überprüfung des TLS-Zertifikats (Transport Layer Security) von [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], zuvor bekannt als Secure Sockets Layer (SSL), verwendet werden soll.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
public void setHostNameInCertificate(java.lang.String hostNameInCertificate)  
```  
  
#### <a name="parameters"></a>Parameter  
 *hostNameInCertificate*  
  
 Ein **String-Objekt**, das den Hostnamen enthält.  
  
## <a name="remarks"></a>Bemerkungen  
 Der hostNameInCertificate-Wert wird zur Überprüfung des TLS-/SSL-Zertifikats von [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] verwendet, wenn die Kommunikationsebene über TLS verschlüsselt wird. Der Standardwert ist "null".  
  
 Ist die hostNameInCertificate-Eigenschaft auf NULL festgelegt oder nicht angegeben, überprüft [!INCLUDE[jdbcNoVersion](../../../includes/jdbcnoversion_md.md)] das TLS-/SSL-Zertifikat von [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] anhand des serverName-Eigenschaftswerts. Ist die hostNameInCertificate-Eigenschaft auf eine Zeichenfolge oder eine leere Zeichenfolge ("") festgelegt, überprüft der Treiber das TLS-/SSL-Serverzertifikat anhand dieses Werts.  
  
## <a name="see-also"></a>Weitere Informationen  
 [SQLServerDataSource-Elemente](../../../connect/jdbc/reference/sqlserverdatasource-members.md)   
 [SQLServerDataSource-Klasse](../../../connect/jdbc/reference/sqlserverdatasource-class.md)  
  
  
