---
title: setEncrypt-Methode (SQLServerDataSource) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- setEncrypt Method (SQLServerDataSource)
apilocation:
- setEncrypt Method (SQLServerDataSource)
apitype: Assembly
ms.assetid: 0c85a9c1-f27c-457e-8461-403cc03e2d17
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 248213fed555ffc029162c44bdcccb656c311703
ms.sourcegitcommit: b78f7ab9281f570b87f96991ebd9a095812cc546
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/31/2020
ms.locfileid: "67974287"
---
# <a name="setencrypt-method-sqlserverdatasource"></a>setEncrypt-Methode (SQLServerDataSource)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Legt einen **booleschen** Wert fest, mit dem angegeben wird, ob die encrypt-Eigenschaft aktiviert ist.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
public void setEncypt(boolean encrypt)  
```  
  
#### <a name="parameters"></a>Parameter  
 *encrypt*  
  
 Der Wert lautet **TRUE**, wenn die SSL-Verschlüsselung (Secure Sockets Layer) zwischen dem Client und [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] aktiviert ist. Andernfalls lautet der Wert **false**.  
  
## <a name="remarks"></a>Bemerkungen  
 Ist die encrypt-Eigenschaft auf **TRUE** festgelegt, wird von [!INCLUDE[jdbcNoVersion](../../../includes/jdbcnoversion_md.md)] sichergestellt, dass [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] für alle zwischen Client und Server versendeten Daten die SSL-Verschlüsselung (Secure Sockets Layer) verwendet, sofern auf dem Server ein Zertifikat installiert ist. Der Standardwert ist **false**.  
  
 Bei der Initiierung eines SSL-Handshakes wird vom JDBC-Treiber die Java Virtual Machine (JVM) erkannt, auf der er ausgeführt wird.  
  
 Wenn die Eigenschaft „encrypt“auf **TRUE** festgelegt ist, verwendet [!INCLUDE[jdbcNoVersion](../../../includes/jdbcnoversion_md.md)] den JSSE-Standardsicherheitsanbieter der JVM, um die SSL-Verschlüsselung mit [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] auszuhandeln. Der Standardsicherheitsanbieter unterstützt möglicherweise nicht alle erforderlichen Funktionen zum erfolgreichen Aushandeln der SSL-Verschlüsselung. So ist es beispielsweise möglich, dass die im SSL-Zertifikat für [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] verwendete Größe des öffentlichen RSA-Schlüssels vom Standardsicherheitsanbieter nicht unterstützt wird. In diesem Fall löst der Standardsicherheitsanbieter möglicherweise einen Fehler aus, wodurch der JDBC-Treiber die Verbindung trennt. Führen Sie zum Beheben dieses Problems eine der folgenden Aktionen aus:  
  
-   Konfigurieren Sie [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] mit einem Serverzertifikat mit einem kleineren öffentlichen RSA-Schlüssel  
  
-   Konfigurieren Sie die JVM für die Verwendung eines anderen JSSE-Sicherheitsanbieters in der Sicherheitseigenschaftendatei „\<java-home/lib/security/java.security“  
  
-   Verwenden Sie eine andere JVM.  
  
 Ist die encrypt-Eigenschaft nicht angegeben oder auf **FALSE** festgelegt, wird vom Treiber die Unterstützung der SSL-Verschlüsselung durch [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] nicht erzwungen. Wenn die [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]-Instanz nicht für das Erzwingen der SSL-Verschlüsselung konfiguriert ist, wird eine Verbindung ohne jegliche Verschlüsselung hergestellt. Wenn die [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]-Instanz für das Erzwingen der SSL-Verschlüsselung konfiguriert ist, aktiviert [!INCLUDE[jdbcNoVersion](../../../includes/jdbcnoversion_md.md)] bei einer ordnungsgemäß konfigurierten Ausführung von Java Virtual Machine (JVM) automatisch die SSL-Verschlüsselung. Andernfalls wird die Verbindung getrennt, und der Treiber löst einen Fehler aus.  
  
## <a name="see-also"></a>Weitere Informationen  
 [SQLServerDataSource-Elemente](../../../connect/jdbc/reference/sqlserverdatasource-members.md)   
 [SQLServerDataSource-Klasse](../../../connect/jdbc/reference/sqlserverdatasource-class.md)  
  
  
