---
title: setTrustServerCertificate-Methode (SQLServerDataSource) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- setTrustServerCertificate Method (SQLServerDataSource)
apilocation:
- setTrustServerCertificate Method (SQLServerDataSource)
apitype: Assembly
ms.assetid: 6c37b518-147e-4cd9-9eff-b48a3f5888c6
author: MightyPen
ms.author: genemi
ms.openlocfilehash: bd4059c3562d679e4f5f8bfdd133ca69a62c1fd2
ms.sourcegitcommit: ff82f3260ff79ed860a7a58f54ff7f0594851e6b
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/29/2020
ms.locfileid: "67972209"
---
# <a name="settrustservercertificate-method-sqlserverdatasource"></a>setTrustServerCertificate-Methode (SQLServerDataSource)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Legt einen **booleschen** Wert fest, der angibt, ob die trustServerCertificate-Eigenschaft aktiviert ist.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
public void setTrustServerCertificate(boolean trustServerCertificate)  
```  
  
#### <a name="parameters"></a>Parameter  
 *trustServerCertificate*  
  
 **TRUE**, wenn das SSL-Serverzertifikat (Secure Sockets Layer) bei der Verschlüsselung der Kommunikationsebene über SSL automatisch als vertrauenswürdig eingestuft werden soll. Andernfalls lautet der Wert **false**.  
  
## <a name="remarks"></a>Bemerkungen  
 Wenn die trustServerCertificate-Eigenschaft auf **true** festgelegt ist, wird dem SSL-Zertifikat von [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] automatisch vertraut, wenn die Kommunikationsschicht mit SSL verschlüsselt ist. Anders gesagt: Das [!INCLUDE[jdbcNoVersion](../../../includes/jdbcnoversion_md.md)]-SSL-Zertifikat wird von [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] nicht überprüft. Der Standardwert ist **false**.  
  
 Ist die trustServerCertificate-Eigenschaft auf **false** festgelegt, wird das SSL-Zertifikat des Servers von [!INCLUDE[jdbcNoVersion](../../../includes/jdbcnoversion_md.md)] überprüft.  
  
## <a name="see-also"></a>Weitere Informationen  
 [SQLServerDataSource-Elemente](../../../connect/jdbc/reference/sqlserverdatasource-members.md)   
 [SQLServerDataSource-Klasse](../../../connect/jdbc/reference/sqlserverdatasource-class.md)  
  
  
