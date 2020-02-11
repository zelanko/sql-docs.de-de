---
title: sys. dm_column_encryption_enclave (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 10/11/2019
ms.prod: sql
ms.reviewer: vanto
ms.technology: system-objects
ms.topic: language-reference
author: jaszymas
ms.author: jaszymas
monikerRange: '>= sql-server-ver15 || = sqlallproducts-allversions'
ms.openlocfilehash: d10bef0df04501c177086b6c89b3f67dec3bab10
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "73599243"
---
# <a name="sysdm_column_encryption_enclave-transact-sql"></a>sys.dm_column_encryption_enclave (Transact-SQL)
[!INCLUDE [tsql-appliesto-ssver15-xxxx-xxxx-xxx-winonly](../../includes/tsql-appliesto-ssver15-xxxx-xxxx-xxx-winonly.md)]

Gibt Leistungsindikatoren für die sichere Enclave für Always Encrypted zurück. Weitere Informationen finden Sie unter [Always Encrypted mit Secure Enclaves](../security/encryption/always-encrypted-enclaves.md).

Wenn die Enclave konfiguriert ist und nach dem letzten Neustart von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]ordnungsgemäß initialisiert wurde, enthält die Sicht genau eine Zeile. Wenn die Enclave nicht konfiguriert ist oder nicht ordnungsgemäß initialisiert wurde, gibt die Sicht keine Zeilen zurück. 

|Spaltenname|Datentyp|BESCHREIBUNG|  
|-----------------|---------------|-----------------|  
|current_enclave_session_count|**int**|Die aktuelle Anzahl von Client Sitzungen, die die Enclave verwenden.|  
|current_column_encryption_key_count|**int**|Die Anzahl der Spalten Verschlüsselungsschlüssel, die die Enclave zurzeit enthält.|  
|current_memory_size_kb|**BIGINT**|Enclave-Speichergröße in KB|  
|total_evicted_session_count|**BIGINT**|Die Gesamtanzahl der Enclave-Sitzungen, die seit dem letzten Neustart des Servers entfernt wurden.|   
  
## <a name="permissions"></a>Berechtigungen  
Erfordert die `VIEW SERVER STATE`-Berechtigung.   
  
## <a name="examples"></a>Beispiele  
 
```sql  
SELECT * FROM sys.dm_column_encryption_enclave;  
GO  
```  
  
## <a name="see-also"></a>Weitere Informationen  
 [Konfigurieren des Enclave-Typs für die Always Encrypted-Serverkonfigurationsoption](../../database-engine/configure-windows/configure-column-encryption-enclave-type.md)
  
  
