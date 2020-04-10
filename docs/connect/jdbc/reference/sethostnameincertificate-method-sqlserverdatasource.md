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
ms.openlocfilehash: 19e31723533c7e26e3afcbca4f8298141747fe82
ms.sourcegitcommit: fe5c45a492e19a320a1a36b037704bf132dffd51
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/08/2020
ms.locfileid: "80922309"
---
# <a name="sethostnameincertificate-method-sqlserverdatasource"></a>setHostNameInCertificate-Methode (SQLServerDataSource)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Legt den Hostnamen fest, der bei der Überprüfung des Secure Sockets Layer-Zertifikats (SSL) von [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] verwendet werden soll.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
public void setHostNameInCertificate(java.lang.String hostNameInCertificate)  
```  
  
#### <a name="parameters"></a>Parameter  
 *hostNameInCertificate*  
  
 Ein **String-Objekt**, das den Hostnamen enthält.  
  
## <a name="remarks"></a>Bemerkungen  
 Der hostNameInCertificate-Wert dient zum Überprüfen des SSL-Zertifikats von [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], wenn die Kommunikationsschicht mithilfe von SSL verschlüsselt wird. Der Standardwert ist "null".  
  
 Ist die hostNameInCertificate-Eigenschaft auf NULL festgelegt oder nicht angegeben, wird das SSL-Zertifikat von [!INCLUDE[jdbcNoVersion](../../../includes/jdbcnoversion_md.md)] durch [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] anhand der serverName-Eigenschaft überprüft. Ist die hostNameInCertificate-Eigenschaft auf eine Zeichenfolge oder auf eine leere Zeichenfolge festgelegt, wird das SSL-Zertifikat des Servers anhand dieses Werts überprüft.  
  
## <a name="see-also"></a>Weitere Informationen  
 [SQLServerDataSource-Elemente](../../../connect/jdbc/reference/sqlserverdatasource-members.md)   
 [SQLServerDataSource-Klasse](../../../connect/jdbc/reference/sqlserverdatasource-class.md)  
  
  
