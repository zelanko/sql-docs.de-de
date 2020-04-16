---
title: getTrustServerCertificate-Methode (SQLServerDataSource) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- getTrustServerCertificate Method (SQLServerDataSource)
apilocation:
- getTrustServerCertificate Method (SQLServerDataSource)
apitype: Assembly
ms.assetid: e4f443cc-b5d7-4859-81df-836a8642ed07
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: f43719fc585a4d1a2fda23fa1111a3918365572b
ms.sourcegitcommit: 54cfeb36c9caa51ec68fa8f4a1918e305db5e00a
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/11/2020
ms.locfileid: "81219306"
---
# <a name="gettrustservercertificate-method-sqlserverdatasource"></a>getTrustServerCertificate-Methode (SQLServerDataSource)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Gibt einen **booleschen** Wert zurück, der angibt, ob die trustServerCertificate-Eigenschaft aktiviert ist.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
public boolean getTrustServerCertificate()  
```  
  
## <a name="return-value"></a>Rückgabewert  
 Der Wert ist **TRUE**, wenn trustServerCertificate aktiviert ist. Andernfalls lautet der Wert **false**.  
  
## <a name="remarks"></a>Bemerkungen  
 Ist die trustServerCertificate-Eigenschaft auf **TRUE** festgelegt, wird dem TLS-Zertifikat (Transport Layer Security) von [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], früher als Secure Sockets Layer (SSL) bezeichnet, automatisch vertraut, wenn die Kommunikationsebene über TLS verschlüsselt ist. Das heißt, dass das TLS-/SSL-Zertifikat von [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] von [!INCLUDE[jdbcNoVersion](../../../includes/jdbcnoversion_md.md)] nicht überprüft wird. Der Standardwert ist **false**.  
  
 Wird die trustServerCertificate-Eigenschaft auf **FALSE** festgelegt, wird das TLS-/SSL-Serverzertifikat von [!INCLUDE[jdbcNoVersion](../../../includes/jdbcnoversion_md.md)] überprüft.  
  
## <a name="see-also"></a>Weitere Informationen  
 [SQLServerDataSource-Elemente](../../../connect/jdbc/reference/sqlserverdatasource-members.md)   
 [SQLServerDataSource-Klasse](../../../connect/jdbc/reference/sqlserverdatasource-class.md)  
  
  
