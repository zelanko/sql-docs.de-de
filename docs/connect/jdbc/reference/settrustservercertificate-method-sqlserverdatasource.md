---
description: setTrustServerCertificate-Methode (SQLServerDataSource)
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
ms.openlocfilehash: 1fb76148ae8c63dd30bd1532ec74d545bcc3388d
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 08/17/2020
ms.locfileid: "88355096"
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
  
 **TRUE**, wenn das TLS-Serverzertifikat (Transport Layer Security), früher SSL-Serverzertifikat (Secure Sockets Layer), bei der Verschlüsselung der Kommunikationsebene über TLS automatisch als vertrauenswürdig eingestuft werden soll. Andernfalls lautet der Wert **false**.  
  
## <a name="remarks"></a>Bemerkungen  
 Wenn die trustServerCertificate-Eigenschaft auf **TRUE** festgelegt ist, wird dem TLS-/SSL-Zertifikat von [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] bei einer Verschlüsselung der Kommunikationsebene über TLS automatisch vertraut. Das heißt, dass das TLS-/SSL-Zertifikat von [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] von [!INCLUDE[jdbcNoVersion](../../../includes/jdbcnoversion_md.md)] nicht überprüft wird. Der Standardwert ist **false**.  
  
 Wird die trustServerCertificate-Eigenschaft auf **FALSE** festgelegt, wird das TLS-/SSL-Serverzertifikat von [!INCLUDE[jdbcNoVersion](../../../includes/jdbcnoversion_md.md)] überprüft.  
  
## <a name="see-also"></a>Weitere Informationen  
 [SQLServerDataSource-Elemente](../../../connect/jdbc/reference/sqlserverdatasource-members.md)   
 [SQLServerDataSource-Klasse](../../../connect/jdbc/reference/sqlserverdatasource-class.md)  
  
  
