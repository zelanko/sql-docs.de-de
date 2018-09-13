---
title: GetTrustServerCertificate-Methode (SQLServerDataSource) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: conceptual
apiname:
- getTrustServerCertificate Method (SQLServerDataSource)
apilocation:
- getTrustServerCertificate Method (SQLServerDataSource)
apitype: Assembly
ms.assetid: e4f443cc-b5d7-4859-81df-836a8642ed07
caps.latest.revision: 15
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 08540cf4f154af29902f7d855af740ee930f2505
ms.sourcegitcommit: 603d2e588ac7b36060fa0cc9c8621ff2a6c0fcc7
ms.translationtype: MTE75
ms.contentlocale: de-DE
ms.lasthandoff: 08/14/2018
ms.locfileid: "42784763"
---
# <a name="gettrustservercertificate-method-sqlserverdatasource"></a>getTrustServerCertificate-Methode (SQLServerDataSource)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Gibt eine **booleschen** -Wert, der angibt, ob die TrustServerCertificate-Eigenschaft aktiviert ist.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
public boolean getTrustServerCertificate()  
```  
  
## <a name="return-value"></a>Rückgabewert  
 **"true"** Wenn TrustServerCertificate aktiviert ist. Andernfalls lautet der Wert **false**.  
  
## <a name="remarks"></a>Remarks  
 Ist die trustServerCertificate-Eigenschaft auf **true** festgelegt, wird dem SSL-Zertifikat von [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] automatisch vertraut, wenn die Kommunikationsschicht mit SSL (Secure Sockets Layer) verschlüsselt ist. Anders gesagt: Das [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]-SSL-Zertifikat wird von [!INCLUDE[jdbcNoVersion](../../../includes/jdbcnoversion_md.md)] nicht überprüft. Der Standardwert ist **false**.  
  
 Ist die trustServerCertificate-Eigenschaft auf **false** festgelegt, wird das SSL-Zertifikat des Servers von [!INCLUDE[jdbcNoVersion](../../../includes/jdbcnoversion_md.md)] überprüft.  
  
## <a name="see-also"></a>Weitere Informationen finden Sie unter  
 [SQLServerDataSource-Elemente](../../../connect/jdbc/reference/sqlserverdatasource-members.md)   
 [SQLServerDataSource-Klasse](../../../connect/jdbc/reference/sqlserverdatasource-class.md)  
  
  
