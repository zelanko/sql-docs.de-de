---
title: DROP CRYPTOGRAPHIC PROVIDER (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: sql-database
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- DROP CRYPTOGRAPHIC PROVIDER
- DROP_CRYPTOGRAPHIC_PROVIDER_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- DROP CRYPTOGRAPHIC PROVIDER statement
ms.assetid: 71c55c20-439e-4897-aef5-f20e556d668f
author: VanMSFT
ms.author: vanto
ms.openlocfilehash: 54ac21a2303da83323fb1f28ff78d8c3bbe275fa
ms.sourcegitcommit: f7ac1976d4bfa224332edd9ef2f4377a4d55a2c9
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/02/2020
ms.locfileid: "85897829"
---
# <a name="drop-cryptographic-provider-transact-sql"></a>DROP CRYPTOGRAPHIC PROVIDER (Transact-SQL)
[!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

  Löscht einen Kryptographieanbieter in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
 ![Symbol für Themenlink](../../database-engine/configure-windows/media/topic-link.gif "Symbol für Themenlink") [Transact-SQL-Syntaxkonventionen](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```  
  
DROP CRYPTOGRAPHIC PROVIDER provider_name   
```  
  
## <a name="arguments"></a>Argumente  
 *provider_name*  
 Der Name des EKM-Anbieters (Extensible Key Management).  
  
## <a name="remarks"></a>Bemerkungen  
 Um einen Anbieter von erweiterbarer Schlüsselverwaltung (Extensible Key Management, EKM) löschen zu können, müssen alle Sitzungen, die den Anbieter verwenden, beendet werden.  
  
 Ein EKM-Anbieter kann nur gelöscht werden, wenn ihm keine Anmeldeinformationen zugeordnet sind.  
  
 Wenn dem EKM-Anbieter beim Löschen Schlüssel zugeordnet sind, bleiben die GUIDs für die Schlüssel weiterhin in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] gespeichert. Wenn ein Anbieter später mit den gleichen Schlüssel-GUIDs erstellt wird, werden die Schlüssel wiederverwendet.  
  
## <a name="permissions"></a>Berechtigungen  
 Erfordert die CONTROL-Berechtigung für den symmetrischen Schlüssel.  
  
## <a name="examples"></a>Beispiele  
 Im folgenden Beispiel wird ein Kryptografieanbieter mit dem Namen `SecurityProvider`gelöscht.  
  
```  
/* First, disable provider to perform the upgrade.  
This will terminate all open cryptographic sessions. */  
ALTER CRYPTOGRAPHIC PROVIDER SecurityProvider   
SET ENABLED = OFF;  
GO  
/* Drop the provider. */  
DROP CRYPTOGRAPHIC PROVIDER SecurityProvider;  
GO  
```  
  
## <a name="see-also"></a>Weitere Informationen  
 [Erweiterbare Schlüsselverwaltung &#40;EKM&#41;](../../relational-databases/security/encryption/extensible-key-management-ekm.md)   
 [CREATE CRYPTOGRAPHIC PROVIDER &#40;Transact-SQL&#41;](../../t-sql/statements/create-cryptographic-provider-transact-sql.md)   
 [ALTER CRYPTOGRAPHIC PROVIDER &#40;Transact-SQL&#41;](../../t-sql/statements/alter-cryptographic-provider-transact-sql.md)   
 [CREATE SYMMETRIC KEY &#40;Transact-SQL&#41;](../../t-sql/statements/create-symmetric-key-transact-sql.md)  
  
  
