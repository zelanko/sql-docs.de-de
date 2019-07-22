---
title: netthostnameincertificate-Methode (SQLServerDataSource) | Microsoft-Dokumentation
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
author: MightyPen
ms.author: genemi
ms.openlocfilehash: deeab57c573311db36eabdbad60c3cb2fbda9a47
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MTE75
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "67974215"
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
  
## <a name="remarks"></a>Remarks  
 Der hostNameInCertificate-Wert dient zum Überprüfen des SSL-Zertifikats von [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], wenn die Kommunikationsschicht mithilfe von SSL verschlüsselt wird. Der Standardwert ist "null".  
  
 Ist die hostNameInCertificate-Eigenschaft auf NULL festgelegt oder nicht angegeben, wird das SSL-Zertifikat von [!INCLUDE[jdbcNoVersion](../../../includes/jdbcnoversion_md.md)] durch [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] anhand der serverName-Eigenschaft überprüft. Ist die hostNameInCertificate-Eigenschaft auf eine Zeichenfolge oder auf eine leere Zeichenfolge festgelegt, wird das SSL-Zertifikat des Servers anhand dieses Werts überprüft.  
  
## <a name="see-also"></a>Weitere Informationen  
 [SQLServerDataSource-Elemente](../../../connect/jdbc/reference/sqlserverdatasource-members.md)   
 [SQLServerDataSource-Klasse](../../../connect/jdbc/reference/sqlserverdatasource-class.md)  
  
  
