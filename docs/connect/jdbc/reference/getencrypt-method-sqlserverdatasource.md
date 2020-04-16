---
title: Methode „getEncrypt“ (SQLServerDataSource) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- getEncrypt Method (SQLServerDataSource)
apilocation:
- getEncrypt Method (SQLServerDataSource)
apitype: Assembly
ms.assetid: 1cdb12dd-6e6f-4bbd-8f5f-9e630f3ee2c9
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 7edee23f7111b55a6d34ac6ae10bf3720879fc01
ms.sourcegitcommit: 54cfeb36c9caa51ec68fa8f4a1918e305db5e00a
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/11/2020
ms.locfileid: "81219296"
---
# <a name="getencrypt-method-sqlserverdatasource"></a>getEncrypt-Methode (SQLServerDataSource)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Gibt einen **booleschen** Wert zurück, mit dem angegeben wird, ob die encrypt-Eigenschaft aktiviert ist.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
public boolean getEncypt()  
```  
  
## <a name="return-value"></a>Rückgabewert  
 **TRUE**, wenn die Verschlüsselung aktiviert ist. Andernfalls lautet der Wert **false**.  
  
## <a name="remarks"></a>Bemerkungen  
 Ist die encrypt-Eigenschaft auf **TRUE** festgelegt, wird von [!INCLUDE[jdbcNoVersion](../../../includes/jdbcnoversion_md.md)] sichergestellt, dass [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] für alle zwischen Client und Server versendeten Daten die TLS-Verschlüsselung verwendet, sofern auf dem Server ein Zertifikat installiert ist.  
  
 Ist die encrypt-Eigenschaft nicht angegeben oder auf **FALSE** festgelegt, wird vom Treiber die Unterstützung der TLS-Verschlüsselung durch [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] nicht erzwungen. Wenn die [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]-Instanz nicht für das Erzwingen der TLS-Verschlüsselung konfiguriert ist, wird eine Verbindung ohne jegliche Verschlüsselung hergestellt. Ist die Instanz [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] für das Erzwingen der TSL-Verschlüsselung konfiguriert, aktiviert [!INCLUDE[jdbcNoVersion](../../../includes/jdbcnoversion_md.md)] automatisch die TSL-Verschlüsselung, wenn er auf einer ordnungsgemäß konfigurierten Java Virtual Machine-Instanz (JVM) ausgeführt wird. Andernfalls wird die Verbindung beendet, und der Treiber löst einen Fehler aus. Ist die encrypt-Eigenschaft nicht festgelegt, wird der Standardwert **FALSE** von der [getEncrypt](../../../connect/jdbc/reference/getencrypt-method-sqlserverdatasource.md)-Methode zurückgegeben.  
  
## <a name="see-also"></a>Weitere Informationen  
 [SQLServerDataSource-Elemente](../../../connect/jdbc/reference/sqlserverdatasource-members.md)   
 [SQLServerDataSource-Klasse](../../../connect/jdbc/reference/sqlserverdatasource-class.md)  
  
  
