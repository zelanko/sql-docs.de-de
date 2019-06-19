---
title: DROP ASYMMETRIC KEY (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- DROP ASYMMETRIC KEY
- DROP_ASYMMETRIC_KEY_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- asymmetric keys [SQL Server], removing
- removing asymmetric keys
- encryption [SQL Server], asymmetric keys
- DROP ASYMMETRIC KEY statement
- dropping asymmetric keys
- deleting asymmetric keys
- cryptography [SQL Server], asymmetric keys
ms.assetid: bf94ac07-9b62-4318-b55b-1eed8f3a1ac6
author: VanMSFT
ms.author: vanto
manager: craigg
ms.openlocfilehash: ed0376a9facde37d5c843e10885efaefaf225577
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "63033960"
---
# <a name="drop-asymmetric-key-transact-sql"></a>DROP ASYMMETRIC KEY (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  Entfernt einen asymmetrischen Schlüssel aus der Datenbank.  
  
 ![Themenlinksymbol](../../database-engine/configure-windows/media/topic-link.gif "Themenlinksymbol") [Transact-SQL-Syntaxkonventionen](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```  
  
DROP ASYMMETRIC KEY key_name [ REMOVE PROVIDER KEY ]  
```  
  
## <a name="arguments"></a>Argumente  
 *key_name*  
 Der Name des asymmetrischen Schlüssels, der aus der Datenbank gelöscht werden soll.  
  
 REMOVE PROVIDER KEY  
 Entfernt einen Schlüssel für erweiterte Schlüsselverwaltung (Extensible Key Management, EKM) von einem EKM-Gerät. Weitere Informationen zur erweiterbaren Schlüsselverwaltung finden Sie unter [Erweiterbare Schlüsselverwaltung &#40;EKM&#41;](../../relational-databases/security/encryption/extensible-key-management-ekm.md).  
  
## <a name="remarks"></a>Remarks  
 Ein asymmetrischer Schlüssel, mit dem ein symmetrischer Schlüssel in der Datenbank verschlüsselt wurde oder dem ein Benutzer oder Anmeldename zugeordnet wurde, kann nicht gelöscht werden. Bevor Sie einen solchen Schlüssel löschen, müssen Sie jeden Benutzer oder Anmeldenamen löschen, der dem Schlüssel zugeordnet ist. Außerdem müssen Sie jeden symmetrischen Schlüssel löschen oder ändern, der mit dem asymmetrischen Schlüssel verschlüsselt ist. Sie können die Option DROP ENCRYPTION von [ALTER SYMMETRIC KEY](../../t-sql/statements/alter-symmetric-key-transact-sql.md) verwenden, um die Verschlüsselung mit einem asymmetrischen Schlüssel zu entfernen.  
  
 Der Zugriff auf Metadaten von asymmetrischen Schlüsseln ist mithilfe der [sys.asymmetric_keys](../../relational-databases/system-catalog-views/sys-asymmetric-keys-transact-sql.md) -Katalogsicht möglich. Die Schlüssel selbst können nicht direkt in der Datenbank angezeigt werden.  
  
 Wenn der asymmetrische Schlüssel einem Schlüssel für erweiterte Schlüsselverwaltung auf einem EKM-Gerät zugeordnet und die Option REMOVE PROVIDER KEY nicht angegeben ist, wird der Schlüssel aus der Datenbank, nicht aber vom Gerät gelöscht. Eine Warnung wird ausgegeben.  
  
## <a name="permissions"></a>Berechtigungen  
 Erfordert die CONTROL-Berechtigung für den asymmetrischen Schlüssel.  
  
## <a name="examples"></a>Beispiele  
 Das folgende Beispiel entfernt den asymmetrischen Schlüssel `MirandaXAsymKey6` aus der `AdventureWorks2012` -Datenbank.  
  
```  
USE AdventureWorks2012;  
DROP ASYMMETRIC KEY MirandaXAsymKey6;  
```  
  
## <a name="see-also"></a>Weitere Informationen  
 [CREATE ASYMMETRIC KEY &#40;Transact-SQL&#41;](../../t-sql/statements/create-asymmetric-key-transact-sql.md)   
 [ALTER ASYMMETRIC KEY &#40;Transact-SQL&#41;](../../t-sql/statements/alter-asymmetric-key-transact-sql.md)   
 [Verschlüsselungshierarchie](../../relational-databases/security/encryption/encryption-hierarchy.md)   
 [ALTER SYMMETRIC KEY &#40;Transact-SQL&#41;](../../t-sql/statements/alter-symmetric-key-transact-sql.md)  
  
  
