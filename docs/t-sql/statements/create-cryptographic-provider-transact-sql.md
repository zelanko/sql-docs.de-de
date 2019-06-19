---
title: CREATE CRYPTOGRAPHIC PROVIDER (Transact-SQL) | Microsoft-Dokumentation
ms.date: 03/14/2017
ms.prod: sql
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- CREATE_CRYPTOGRAPHIC_TSQL
- CRYPTOGRAPHIC PROVIDER
- PROVIDER_TSQL
- CREATE CRYPTOGRAPHIC
- CREATE CRYPTOGRAPHIC PROVIDER
- CRYPTOGRAPHIC_PROVIDER_TSQL
- CREATE_CRYPTOGRAPHIC_PROVIDER_TSQL
- PROVIDER
dev_langs:
- TSQL
helpviewer_keywords:
- 33085 (Database Engine error)
- CREATE CRYPTOGRAPHIC PROVIDER statement
- 33032 (Database Engine error)
ms.assetid: 059a39a6-9d32-4d3f-965b-0a1ce75229c7
author: VanMSFT
ms.author: vanto
manager: craigg
ms.openlocfilehash: 8ec316925fcd21a80561750665386a72f096060d
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "62993780"
---
# <a name="create-cryptographic-provider-transact-sql"></a>CREATE CRYPTOGRAPHIC PROVIDER (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Erstellt einen Kryptografieanbieter innerhalb [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] von einem EKM-Anbieter (Extensible Key Management) aus.  
  
 ![Themenlinksymbol](../../database-engine/configure-windows/media/topic-link.gif "Themenlinksymbol") [Transact-SQL-Syntaxkonventionen](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```  
  
CREATE CRYPTOGRAPHIC PROVIDER provider_name   
    FROM FILE = path_of_DLL  
```  
  
## <a name="arguments"></a>Argumente  
 *provider_name*  
 Der Name des EKM-Anbieters (Extensible Key Management).  
  
 *path_of_DLL*  
 Der Pfad der DLL-Datei, die die erweiterbare Schlüsselverwaltungsschnittstelle von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] implementiert. Wenn der **SQL Server-Connector für Microsoft Azure Key Vault** verwendet wird, lautet der Standardspeicherort: **C:\Program Files\Microsoft SQL Server Connector for Microsoft Azure Key Vault\Microsoft.AzureKeyVaultService.EKM.dll**.  
  
## <a name="remarks"></a>Remarks  
 Alle von einem Anbieter erstellten Schlüssel verweisen über den GUID auf den Anbieter. Der GUID bleibt in allen Versionen der DLL erhalten.  
  
 Die DLL, die die SQLEKM-Schnittstelle implementiert, muss mit einem beliebigen Zertifikat digital signiert werden. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] überprüft die Signatur. Diese Prüfung umfasst auch die Zertifikatskette, deren Stamm im Speicherort **Trusted Root Cert Authorities** auf einem Windows-System installiert sein muss. Wenn sich die Signatur bei der Überprüfung ihrer Gültigkeit als nicht ordnungsgemäß erweist, schlägt die Anweisung CREATE CRYPTOGRAPHIC PROVIDER fehl. Weitere Informationen zu Zertifikaten finden Sie unter [SQL Server-Zertifikate und asymmetrische Schlüssel](../../relational-databases/security/sql-server-certificates-and-asymmetric-keys.md).  
  
 Wenn von einer DLL des EKM-Anbieters nicht alle erforderlichen Methoden implementiert werden, kann CREATE CRYPTOGRAPHIC PROVIDER den Fehler 33085 zurückgeben:  
  
 `One or more methods cannot be found in cryptographic provider library '%.*ls'.`  
  
 Wenn die Headerdatei, mit der die DLL des EKM-Anbieters erstellt wurde, veraltet ist, kann CREATE CRYPTOGRAPHIC PROVIDER den Fehler 33032 zurückgeben:  
  
 `SQL Crypto API version '%02d.%02d' implemented by provider is not supported. Supported version is '%02d.%02d'.`  
  
## <a name="permissions"></a>Berechtigungen  
 Erfordert die CONTROL SERVER-Berechtigung oder die Mitgliedschaft in der festen Serverrolle **sysadmin**.  
  
## <a name="examples"></a>Beispiele  
 Im folgenden Beispiel wird ein Kryptografieanbieter mit dem Namen `SecurityProvider` in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] aus einer DLL-Datei erstellt. Die DLL-Datei bekommt den Namen `c:\SecurityProvider\SecurityProvider_v1.dll` und wird auf dem Server installiert. Das Zertifikat des Anbieters muss zuerst auf dem Server installiert werden.  
  
```  
-- Install the provider  
CREATE CRYPTOGRAPHIC PROVIDER SecurityProvider  
    FROM FILE = 'C:\SecurityProvider\SecurityProvider_v1.dll';  
```  
  
## <a name="see-also"></a>Weitere Informationen  
 [Erweiterbare Schlüsselverwaltung &#40;EKM&#41;](../../relational-databases/security/encryption/extensible-key-management-ekm.md)   
 [ALTER CRYPTOGRAPHIC PROVIDER &#40;Transact-SQL&#41;](../../t-sql/statements/alter-cryptographic-provider-transact-sql.md)   
 [DROP CRYPTOGRAPHIC PROVIDER &#40;Transact-SQL&#41;](../../t-sql/statements/drop-cryptographic-provider-transact-sql.md)   
 [CREATE SYMMETRIC KEY &#40;Transact-SQL&#41;](../../t-sql/statements/create-symmetric-key-transact-sql.md)   
 [Erweiterbare Schlüsselverwaltung mit Azure Key Vault &#40;SQL Server&#41;](../../relational-databases/security/encryption/extensible-key-management-using-azure-key-vault-sql-server.md)  
  
  
