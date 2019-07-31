---
title: sp_enclave_send_keys (Transact-SQL) | Microsoft-Dokumentation
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
ms.openlocfilehash: b4ced2feee2227ba1db492f721f57907069c5d99
ms.sourcegitcommit: 97e94b76f9f48d161798afcf89a8c2ac0f09c584
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/30/2019
ms.locfileid: "68661351"
---
# <a name="spenclavesendkeys----transact-sql"></a>sp_enclave_send_keys (Transact-SQL)
[!INCLUDE[tsql-appliesto-ssver15-xxxx-xxxx-xxx](../../includes/tsql-appliesto-ssver15-xxxx-xxxx-xxx.md)]

Sendet alle Enclave-aktivierten Spalten Verschlüsselungsschlüssel in der Datenbank an die Enclave, die von [Always Encrypted mit sicheren &#40;Enklaven Datenbank-Engine&#41;](../../relational-databases/security/encryption/always-encrypted-enclaves.md)verwendet wird.

## <a name="syntax"></a>Syntax  
  
```
sp_enclave_send_keys
[ ;]  
```

## <a name="arguments"></a>Argumente

Diese gespeicherte Prozedur weist keine Argumente auf.

## <a name="return-value"></a>Rückgabewert

Diese gespeicherte Prozedur weist keinen Rückgabewert auf.
  
## <a name="result-sets"></a>Resultsets

Diese gespeicherte Prozedur hat keine Resultsets.
  
## <a name="remarks"></a>Hinweise

**sp_enclave_send_keys** sendet Enclave-aktivierte Spalten Verschlüsselungsschlüssel an die Enclave, wenn alle der folgenden Bedingungen erfüllt sind:

- Die Enclave ist in der SQL Server Instanz aktiviert.
- **sp_enclave_send_keys** wurde von einer Anwendung mithilfe eines [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Client Treibers aufgerufen und unterstützt Always Encrypted mit sicheren Enklaven mithilfe einer Datenbankverbindung, bei der sowohl Always Encrypted als auch Enclave-Berechnungen aktiviert sind.

## <a name="permissions"></a>Berechtigungen

 Erfordert die Berechtigungen **View any Column Encryption Key Definition** und **View any Column Master Key Definition** in der Datenbank.  
  
## <a name="examples"></a>Beispiele  
  
```sql
EXEC sp_enclave_send_keys;  
```

## <a name="see-also"></a>Siehe auch

 [Always Encrypted mit sicheren Enklaven &#40;Datenbank-Engine&#41;](../../relational-databases/security/encryption/always-encrypted-enclaves.md)   
 [Tutorial: Erstellen und Verwenden von Indizes für Enclave-aktivierte Spalten mithilfe der zufälligen Verschlüsselung](../security/tutorial-creating-using-indexes-on-enclave-enabled-columns-using-randomized-encryption.md#step-3-create-an-index-with-role-separation)   
 [Aufrufen von Indizierungs Vorgängen mit zwischengespeicherten Spalten Verschlüsselungsschlüsseln](../security/encryption/configure-always-encrypted-enclaves.md#invoke-indexing-operations-using-cached-column-encryption-keys)   
 [Indizes in Enclave-aktivierten Spalten mithilfe der zufälligen Verschlüsselung](../security/encryption/always-encrypted-enclaves.md#indexes-on-enclave-enabled-columns-using-randomized-encryption)   
 [Überlegungen zu AlwaysOn und Daten Bank Migration](../security/encryption/always-encrypted-enclaves.md#anchorname-1-considerations-availability-groups-db-migration)
