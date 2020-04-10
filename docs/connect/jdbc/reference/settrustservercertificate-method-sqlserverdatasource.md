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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 0a5c2ea95878abc101032eb662a601a65047c1e1
ms.sourcegitcommit: fe5c45a492e19a320a1a36b037704bf132dffd51
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/08/2020
ms.locfileid: "80901998"
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
  
  
