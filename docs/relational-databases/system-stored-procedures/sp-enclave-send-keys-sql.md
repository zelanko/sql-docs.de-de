---
title: sp_enclave_send_keys (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 10/19/2019
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
ms.openlocfilehash: ca6e7485e85665f06c2410438b902fa0647418ae
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/27/2020
ms.locfileid: "73593750"
---
# <a name="sp_enclave_send_keys-transact-sql"></a>sp_enclave_send_keys (Transact-SQL)
[!INCLUDE [tsql-appliesto-ssver15-xxxx-xxxx-xxx-winonly](../../includes/tsql-appliesto-ssver15-xxxx-xxxx-xxx-winonly.md)]

Sendet Spalten Verschlüsselungsschlüssel, die in der Datenbank definiert sind, an den serverseitigen sicheren Enclave, der mit [Always Encrypted mit sicheren Enklaven](../security/encryption/always-encrypted-enclaves.md)verwendet wird.

`sp_enclave_send_keys`sendet nur die Schlüssel, die Enclave-fähig sind, und verschlüsselt Spalten, die die zufällige Verschlüsselung verwenden und über Indizes verfügen. Bei einer regulären Benutzer Abfrage stellt ein Client Treiber dem Enclave die Schlüssel zur Verfügung, die für Berechnungen in der Abfrage erforderlich sind. `sp_enclave_send_keys`sendet alle in der Datenbank definierten Spalten Verschlüsselungsschlüssel und wird für verschlüsselte Spalten von Indizes verwendet. 

`sp_enclave_send_keys`bietet eine einfache Möglichkeit, Schlüssel an die Enclave zu senden und den Cache für die Spalten Verschlüsselungsschlüssel für nachfolgende Indizierungs Vorgänge aufzufüllen. Verwenden `sp_enclave_send_keys` Sie zum Aktivieren von:
- Ein DBA zum erneuten Erstellen oder Ändern von Indizes oder Statistiken für verschlüsselte Daten Bank Spalten, wenn der DBA keinen Zugriff auf den Spalten Hauptschlüssel hat. Siehe [Aufrufen von Indizierungs Vorgängen mit zwischengespeicherten Spalten Verschlüsselungsschlüsseln](../security/encryption/always-encrypted-enclaves-create-use-indexes.md#invoke-indexing-operations-using-cached-column-encryption-keys).
- [!INCLUDE [ssnoversion-md](../../includes/ssnoversion-md.md)]um die Wiederherstellung von Indizes für verschlüsselte Spalten abzuschließen. Siehe [Daten Bank Wiederherstellung](../security/encryption/always-encrypted-enclaves.md#database-recovery).
- Eine Anwendung, die .NET Framework Datenanbieter für die SQL Server zum Massen Laden von Daten in verschlüsselte Spalten verwendet.

Um erfolgreich aufrufen `sp_enclave_send_keys`zu können, müssen Sie eine Verbindung mit der Datenbank herstellen, wobei Always Encrypted und Enclave-Berechnungen für die Datenbankverbindung aktiviert sind. Außerdem benötigen Sie Zugriff auf Spalten Hauptschlüssel, um die Spalten Verschlüsselungsschlüssel zu schützen, die Sie senden werden, und Sie benötigen Berechtigungen für den Zugriff auf Always Encrypted Schlüssel Metadaten in der Datenbank. 

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
  
## <a name="permissions"></a>Berechtigungen

 Erfordert die `VIEW ANY COLUMN ENCRYPTION KEY DEFINITION` - `VIEW ANY COLUMN MASTER KEY DEFINITION` Berechtigung und die-Berechtigung in der Datenbank.  
  
## <a name="examples"></a>Beispiele  
  
```sql
EXEC sp_enclave_send_keys;  
```

## <a name="see-also"></a>Weitere Informationen:
- [Always Encrypted mit Secure Enclaves](../security/encryption/always-encrypted-enclaves.md) 
 
- [Erstellen und Verwenden von Indizes in Spalten mithilfe von Always Encrypted mit Secure Enclaves](../security/encryption/always-encrypted-enclaves-create-use-indexes.md)

- [Tutorial: Erstellen und Verwenden von Indizes für Enclave-aktivierte Spalten mithilfe der zufälligen Verschlüsselung](../security/tutorial-creating-using-indexes-on-enclave-enabled-columns-using-randomized-encryption.md)
