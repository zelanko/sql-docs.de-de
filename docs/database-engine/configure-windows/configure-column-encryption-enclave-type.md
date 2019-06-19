---
title: Serverkonfigurationsoption „column encryption enclave type“ | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/24/2018
ms.prod: sql
ms.prod_service: security
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
author: jaszymas
ms.author: jaszymas
manager: jroth
monikerRange: '>= sql-server-ver15 || = sqlallproducts-allversions'
ms.openlocfilehash: 1031bdfa3aa6c728d3e33b500fe942d5e52c5fdc
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "66799466"
---
# <a name="column-encryption-enclave-type-server-configuration-option"></a>Serverkonfigurationsoption „column encryption enclave type“
[!INCLUDE[tsql-appliesto-ssver15-xxxx-xxxx-xxx](../../includes/tsql-appliesto-ssver15-xxxx-xxxx-xxx.md)]

  Verwenden Sie die Option **column encryption enclave type**, um Secure Enclaves für Always Encrypted zu aktivieren oder zu deaktivieren.  Weitere Informationen finden Sie unter [Always Encrypted mit Secure Enclaves](../../relational-databases/security/encryption/always-encrypted-enclaves.md).

 In der folgenden Tabelle werden die möglichen Werte für **column encryption enclave type** aufgeführt:  
  
|value|und Beschreibung|  
|-------------------|-----------------|  
|0|**Keine Secure Enclave**. Die [!INCLUDE[ssDE](../../includes/ssde-md.md)] kann die Secure Enclave für Always Encrypted nicht initialisieren. Aus diesem Grund ist die Funktionalität von Always Encrypted mit Secure Enclaves nicht verfügbar.|  
|1|**Virtualisierungsbasierte Sicherheit (VBS)** . Die [!INCLUDE[ssDE](../../includes/ssde-md.md)] initialisiert die Secure Enclave (als über VBS gesicherte Arbeitsspeicher-Enclave) für Always Encrypted.|    

> [!IMPORTANT]
> Änderungen an **column encryption enclave type** treten erst in Kraft, nachdem Sie die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Instanz neu gestartet haben.
  
   
## <a name="examples"></a>Beispiele  
 Das folgende Beispiel aktiviert die Secure Enclave:  

```sql  
sp_configure 'column encryption enclave type', 1;  
GO  
RECONFIGURE;  
GO  
```  

Das folgende Beispiel deaktiviert die Secure Enclave:  

```sql  
sp_configure 'column encryption enclave type', 0;  
GO  
RECONFIGURE;  
GO  
```  

## <a name="see-also"></a>Weitere Informationen  
 [sp_configure &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-configure-transact-sql.md)   
 [RECONFIGURE &#40;Transact-SQL&#41;](../../t-sql/language-elements/reconfigure-transact-sql.md)   
 [Serverkonfigurationsoptionen &#40;SQL Server&#41;](../../database-engine/configure-windows/server-configuration-options-sql-server.md)  
  
  
