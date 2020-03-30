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
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 81d07743dfefe0b0305b1a094a9ae4632d4effd9
ms.sourcegitcommit: ff82f3260ff79ed860a7a58f54ff7f0594851e6b
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/29/2020
ms.locfileid: "67978583"
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
 Ist die trustServerCertificate-Eigenschaft auf **true** festgelegt, wird dem SSL-Zertifikat von [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] automatisch vertraut, wenn die Kommunikationsschicht mit SSL (Secure Sockets Layer) verschlüsselt ist. Anders gesagt: Das [!INCLUDE[jdbcNoVersion](../../../includes/jdbcnoversion_md.md)]-SSL-Zertifikat wird von [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] nicht überprüft. Der Standardwert ist **false**.  
  
 Ist die trustServerCertificate-Eigenschaft auf **false** festgelegt, wird das SSL-Zertifikat des Servers von [!INCLUDE[jdbcNoVersion](../../../includes/jdbcnoversion_md.md)] überprüft.  
  
## <a name="see-also"></a>Weitere Informationen  
 [SQLServerDataSource-Elemente](../../../connect/jdbc/reference/sqlserverdatasource-members.md)   
 [SQLServerDataSource-Klasse](../../../connect/jdbc/reference/sqlserverdatasource-class.md)  
  
  
