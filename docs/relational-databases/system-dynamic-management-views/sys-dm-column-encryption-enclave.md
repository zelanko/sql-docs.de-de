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
ms.openlocfilehash: f41a5f704a50924a882e220786ac8cafc090237a
ms.sourcegitcommit: dacd9b6f90e6772a778a3235fb69412662572d02
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/11/2020
ms.locfileid: "86279561"
---
# <a name="sysdm_column_encryption_enclave-transact-sql"></a>sys.dm_column_encryption_enclave (Transact-SQL)
[!INCLUDE [sqlserver2019-windows-only](../../includes/applies-to-version/sqlserver2019-windows-only.md)]

Gibt Leistungsindikatoren für die sichere Enclave für Always Encrypted zurück. Weitere Informationen finden Sie unter [Always Encrypted mit Secure Enclaves](../security/encryption/always-encrypted-enclaves.md).

Wenn die Enclave konfiguriert ist und nach dem letzten Neustart von ordnungsgemäß initialisiert wurde [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , enthält die Sicht genau eine Zeile. Wenn die Enclave nicht konfiguriert ist oder nicht ordnungsgemäß initialisiert wurde, gibt die Sicht keine Zeilen zurück. 

|Spaltenname|Datentyp|BESCHREIBUNG|  
|-----------------|---------------|-----------------|  
|current_enclave_session_count|**int**|Die aktuelle Anzahl von Client Sitzungen, die die Enclave verwenden.|  
|current_column_encryption_key_count|**int**|Die Anzahl der Spalten Verschlüsselungsschlüssel, die die Enclave zurzeit enthält.|  
|current_memory_size_kb|**bigint**|Enclave-Speichergröße in KB|  
|total_evicted_session_count|**bigint**|Die Gesamtanzahl der Enclave-Sitzungen, die seit dem letzten Neustart des Servers entfernt wurden.|   
  
## <a name="permissions"></a>Berechtigungen  
Erfordert die `VIEW SERVER STATE`-Berechtigung.   
  
## <a name="examples"></a>Beispiele  
 
```sql  
SELECT * FROM sys.dm_column_encryption_enclave;  
GO  
```  
  
## <a name="see-also"></a>Weitere Informationen  
 [Konfigurieren des Enclave-Typs für die Always Encrypted-Serverkonfigurationsoption](../../database-engine/configure-windows/configure-column-encryption-enclave-type.md)
  
  
