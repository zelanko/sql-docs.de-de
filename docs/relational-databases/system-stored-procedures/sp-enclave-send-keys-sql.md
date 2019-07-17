---
title: Sp_enclave_send_keys (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/26/2019
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: vanto
ms.suite: sql
ms.technology: system-objects
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- sp_enclave_send_keys
- sp_enclave_send_keys_TSQL
- sys.sp_enclave_send_keys
- sys.sp_enclave_send_keys_TSQL
helpviewer_keywords:
- sp_enclave_send_keys
author: jaszymas
ms.author: jaszymas
monikerRange: '>= sql-server-ver15 || = sqlallproducts-allversions'
ms.openlocfilehash: b3d5ed50ac407beebfb54370cf91f0f3b8ba3101
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "68124692"
---
# <a name="spenclavesendkeys----transact-sql"></a>Sp_enclave_send_keys (Transact-SQL)
[!INCLUDE[tsql-appliesto-ssver15-xxxx-xxxx-xxx](../../includes/tsql-appliesto-ssver15-xxxx-xxxx-xxx.md)]

Sendet alle Enclave-aktivierten Spalte Verschlüsselungsschlüssel in der Datenbank an die Enclave von verwendeten [Always Encrypted mit sicheren Enclaves &#40;Datenbank-Engine&#41;](../../relational-databases/security/encryption/always-encrypted-enclaves.md).

## <a name="syntax"></a>Syntax  
  
```
sp_enclave_send_keys
[ ;]  
```

## <a name="arguments"></a>Argumente

Diese gespeicherte Prozedur verfügt über keine Argumente.

## <a name="return-value"></a>Rückgabewert

Diese gespeicherte Prozedur verfügt über keinen Wert zurückgibt.
  
## <a name="result-sets"></a>Resultsets

Diese gespeicherte Prozedur hat kein Resultset zurück.
  
## <a name="remarks"></a>Hinweise

**Sp_enclave_send_keys** Enclave-fähige Verschlüsselung von spaltenverschlüsselungsschlüsseln an die Enclave sendet, wenn alle der folgenden Bedingungen erfüllt sind:

- Die Enclave ist in SQL Server-Instanz aktiviert.
- **Sp_enclave_send_keys** aufgerufen wurde von einer Anwendung mit einer [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Clienttreiber, Unterstützung von Always Encrypted mit sicheren Enclaves mithilfe einer Verbindungs mit Datenbank, die Always Encrypted und Enclave-Berechnungen, die aktiviert wurde.

## <a name="permissions"></a>Berechtigungen

 Erfordert die **VIEW ANY COLUMN ENCRYPTION KEY DEFINITION** und **VIEW ANY COLUMN MASTER KEY DEFINITION** Berechtigungen in der Datenbank.  
  
## <a name="examples"></a>Beispiele  
  
```sql
EXEC sp_enclave_send_keys;  
```

## <a name="see-also"></a>Siehe auch

 [Always Encrypted mit sicheren Enclaves &#40;Datenbank-Engine&#41;](../../relational-databases/security/encryption/always-encrypted-enclaves.md)   
 [Tutorial: Erstellen und Verwenden von Indizes für Enclave-fähigen Spalten mit zufälliger Verschlüsselung](../security/tutorial-creating-using-indexes-on-enclave-enabled-columns-using-randomized-encryption.md#step-3-create-an-index-with-role-separation)   
 [Rufen Sie mithilfe von zwischengespeicherten Verschlüsselung von spaltenverschlüsselungsschlüsseln Indizierungsvorgänge](../security/encryption/configure-always-encrypted-enclaves.md#invoke-indexing-operations-using-cached-column-encryption-keys)   
 [Indizes für Enclave-fähigen Spalten mit zufälliger Verschlüsselung](../security/encryption/always-encrypted-enclaves.md#indexes-on-enclave-enabled-columns-using-randomized-encryption)   
 [Überlegungen zur AlwaysOn und Migrieren einer Datenbank](../security/encryption/always-encrypted-enclaves.md#considerations-for-alwayson-and-database-migration)
