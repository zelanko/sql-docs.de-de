---
title: getencrypt-Methode (SQLServerDataSource) | Microsoft-Dokumentation
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
author: MightyPen
ms.author: genemi
ms.openlocfilehash: d3764ff5b9308b4b370dda14e98787513c28458c
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MTE75
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "67983375"
---
# <a name="getencrypt-method-sqlserverdatasource"></a>getEncrypt-Methode (SQLServerDataSource)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Gibt einen **booleschen** Wert zurück, mit dem angegeben wird, ob die encrypt-Eigenschaft aktiviert ist.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
public boolean getEncypt()  
```  
  
## <a name="return-value"></a>Rückgabewert  
 **true** , wenn die Verschlüsselung aktiviert ist. Andernfalls lautet der Wert **false**.  
  
## <a name="remarks"></a>Remarks  
 Ist die encrypt-Eigenschaft auf **TRUE** festgelegt, wird von [!INCLUDE[jdbcNoVersion](../../../includes/jdbcnoversion_md.md)] sichergestellt, dass [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] für alle zwischen Client und Server versendeten Daten die SSL-Verschlüsselung (Secure Sockets Layer) verwendet, sofern auf dem Server ein Zertifikat installiert ist.  
  
 Ist die encrypt-Eigenschaft nicht angegeben oder auf **FALSE** festgelegt, wird vom Treiber die Unterstützung der SSL-Verschlüsselung durch [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] nicht erzwungen. Wenn die [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]-Instanz nicht für das Erzwingen der SSL-Verschlüsselung konfiguriert ist, wird eine Verbindung ohne jegliche Verschlüsselung hergestellt. Falls die [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]-Instanz für das Erzwingen der SSL-Verschlüsselung konfiguriert ist, aktiviert [!INCLUDE[jdbcNoVersion](../../../includes/jdbcnoversion_md.md)] bei Ausführung auf einer ordnungsgemäß konfigurierten Java Virtual Machine (JVM) automatisch die SSL-Verschlüsselung. Andernfalls wird die Verbindung getrennt, und der Treiber löst einen Fehler aus. Ist die encrypt-Eigenschaft nicht festgelegt, wird der Standardwert **FALSE** von der [getEncrypt](../../../connect/jdbc/reference/getencrypt-method-sqlserverdatasource.md)-Methode zurückgegeben.  
  
## <a name="see-also"></a>Weitere Informationen  
 [SQLServerDataSource-Elemente](../../../connect/jdbc/reference/sqlserverdatasource-members.md)   
 [SQLServerDataSource-Klasse](../../../connect/jdbc/reference/sqlserverdatasource-class.md)  
  
  
