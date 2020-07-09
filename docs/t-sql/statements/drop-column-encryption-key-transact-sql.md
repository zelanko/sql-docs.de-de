---
title: DROP COLUMN ENCRYPTION KEY (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 10/15/2019
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- DROP COLUMN ENCRYPTION
- DROP COLUMN ENCRYPTION KEY
- DROP_COLUMN_ENCRYPTION_TSQL
- DROP_COLUMN_ENCRYPTION_KEY_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- DROP COLUMN ENCRYPTION KEY statement
- column encryption key, drop
ms.assetid: 86415302-1383-4d36-9fc7-f780831a2d37
author: jaszymas
ms.author: jaszymas
ms.openlocfilehash: 72b5760614c009836ada1922598e438095615935
ms.sourcegitcommit: f3321ed29d6d8725ba6378d207277a57cb5fe8c2
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/06/2020
ms.locfileid: "86003176"
---
# <a name="drop-column-encryption-key-transact-sql"></a>DROP COLUMN ENCRYPTION KEY (Transact-SQL)
[!INCLUDE [sqlserver2016-asdb-asdbmi-asa](../../includes/applies-to-version/sqlserver2016-asdb-asdbmi-asa.md)]

  Entfernt einen Spaltenverschlüsselungsschlüssel (Column Encryption Key, CEK) aus der Datenbank.  
  
 ![Symbol für Themenlink](../../database-engine/configure-windows/media/topic-link.gif "Symbol für Themenlink") [Transact-SQL-Syntaxkonventionen](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```syntaxsql
  
DROP COLUMN ENCRYPTION KEY key_name [;]  
```  
  
## <a name="arguments"></a>Argumente  
 *key_name*  
 Der Name des CEK, der aus der Datenbank entfernt werden soll.  
  
## <a name="remarks"></a>Bemerkungen  
 CEKs können nicht entfernt werden, wenn sie verwendet werden, um eine Spalte in der Datenbank zu verschlüsseln. Alle Spalten, die den CEK verwenden, müssen zunächst entfernt werden.  
  
## <a name="permissions"></a>Berechtigungen  
 Erfordert die **ALTER ANY COLUMN ENCRYPTION KEY**-Berechtigung in der Datenbank.  
  
## <a name="examples"></a>Beispiele  
  
### <a name="a-dropping-a-column-encryption-key"></a>A. Entfernen eines CEK  
 Im folgenden Beispiel wird ein CEK mit der Bezeichnung `MyCEK` entfernt.  
  
```  
DROP COLUMN ENCRYPTION KEY MyCEK;  
GO  
```  
  
## <a name="see-also"></a>Weitere Informationen  
 [CREATE COLUMN ENCRYPTION KEY &#40;Transact-SQL&#41;](../../t-sql/statements/create-column-encryption-key-transact-sql.md)   
 [ALTER COLUMN ENCRYPTION KEY &#40;Transact-SQL&#41;](../../t-sql/statements/alter-column-encryption-key-transact-sql.md)   
 [CREATE COLUMN MASTER KEY &#40;Transact-SQL&#41;](../../t-sql/statements/create-column-master-key-transact-sql.md)  
 [Always Encrypted](../../relational-databases/security/encryption/always-encrypted-database-engine.md)   
 [Always Encrypted mit Secure Enclaves](../../relational-databases/security/encryption/always-encrypted-enclaves.md)   
 [Übersicht über die Schlüsselverwaltung für Always Encrypted](../../relational-databases/security/encryption/overview-of-key-management-for-always-encrypted.md)   
 [Verwalten von Schlüsseln für Always Encrypted mit Secure Enclaves](../../relational-databases/security/encryption/always-encrypted-enclaves-manage-keys.md)   
  
  
