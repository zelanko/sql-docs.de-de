---
title: sys. column_master_keys (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 10/15/2019
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- column_master_key_definitions_TSQL
- column_master_key_definitions
- sys.column_master_key_definitions_TSQL
- sys.column_master_key_definitions
- column_master_keys_TSQL
- column_master_keys
- sys.column_master_keys_TSQL
- sys.column_master_keys
dev_langs:
- TSQL
helpviewer_keywords:
- sys.column_master_key_definitions catalog view
- sys.column_master_keys catalog view
ms.assetid: fbec2efa-5fe9-4121-9b34-60497b0b2aca
author: jaszymas
ms.author: jaszymas
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: e28fae709bc81a10c6ad23228d12532172841488
ms.sourcegitcommit: f3321ed29d6d8725ba6378d207277a57cb5fe8c2
ms.contentlocale: de-DE
ms.lasthandoff: 07/06/2020
ms.locfileid: "86003077"
---
# <a name="syscolumn_master_keys-transact-sql"></a>sys.column_master_keys (Transact-SQL)
[!INCLUDE [sqlserver2016-asdb-asdbmi-asa](../../includes/applies-to-version/sqlserver2016-asdb-asdbmi-asa.md)]

  Gibt eine Zeile für jeden Datenbank-Hauptschlüssel zurück, der mit der [Create Master Key](../../t-sql/statements/create-column-master-key-transact-sql.md) -Anweisung hinzugefügt wurde. Jede Zeile stellt einen einzelnen Spalten Hauptschlüssel (Column Master Key, CMK) dar.  
    
|Spaltenname|Datentyp|BESCHREIBUNG|  
|-----------------|---------------|-----------------|  
|**name**|**sysname**|Der Name des CMK.|  
|**column_master_key_id**|**int**|ID des Spalten Hauptschlüssels.|  
|**create_date**|**datetime**|Datum, an dem der Spalten Hauptschlüssel erstellt wurde.|  
|**modify_date**|**datetime**|Datum, an dem der Spalten Hauptschlüssel zuletzt geändert wurde.|  
|**key_store_provider_name**|**sysname**|Der Name des Anbieters für den Spalten Hauptschlüssel-Speicher, der den CMK enthält. Zulässige Werte sind:<br /><br /> MSSQL_CERTIFICATE_STORE: Wenn der Spalten Hauptschlüssel-Speicher ein Zertifikat Speicher ist.<br /><br /> Ein benutzerdefinierter Wert, wenn der Spalten Hauptschlüssel-Speicher einen benutzerdefinierten Typ hat.|  
|**key_path**|**nvarchar(4000)**|Ein Speicher spezifischer Pfad des Spalten Hauptschlüssels für den Schlüssel. Das Format des Pfads hängt vom Speicher Typ des Spalten Hauptschlüssels ab. Beispiel:<br /><br /> `'CurrentUser/Personal/'<thumbprint>`<br /><br /> Für einen benutzerdefinierten Spalten Hauptschlüssel-Speicher ist der Entwickler dafür verantwortlich, den Schlüssel Pfad für den benutzerdefinierten Spalten Hauptschlüssel-Speicher zu definieren.|  
|**allow_enclave_computations**|**bit**|Gibt an, ob der Spalten Hauptschlüssel Enclave-fähig ist, (wenn Spalten Verschlüsselungsschlüssel, die mit diesem Hauptschlüssel verschlüsselt sind, für Berechnungen in serverseitigen sicheren Enklaven verwendet werden können). Weitere Informationen finden Sie unter [Always Encrypted mit Secure Enclaves](../../relational-databases/security/encryption/always-encrypted-enclaves.md).|  
|**Signatur**|**varbinary(max)**|Eine digitale Signatur von **key_path** und **allow_enclave_computations**, die mit dem Spalten Hauptschlüssel erstellt wurden, auf die von **key_path**verwiesen wird.|


  
## <a name="permissions"></a>Berechtigungen  
 Erfordert die **View any Column Master Key** -Berechtigung.  
  
 [!INCLUDE[ssCatViewPerm](../../includes/sscatviewperm-md.md)] Weitere Informationen finden Sie unter [Metadata Visibility Configuration](../../relational-databases/security/metadata-visibility-configuration.md).  
  
## <a name="see-also"></a>Weitere Informationen  
 [Erstellen eines Spalten Hauptschlüssels &#40;Transact-SQL-&#41;](../../t-sql/statements/create-column-master-key-transact-sql.md)   
 [Sicherheits Katalog Sichten &#40;Transact-SQL-&#41;](../../relational-databases/system-catalog-views/security-catalog-views-transact-sql.md)   
 [sys.column_encryption_key_values &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-column-encryption-key-values-transact-sql.md)  
 [Always Encrypted](../../relational-databases/security/encryption/always-encrypted-database-engine.md)   
 [Übersicht über die Schlüsselverwaltung für Always Encrypted](../../relational-databases/security/encryption/overview-of-key-management-for-always-encrypted.md)   
 [Verwalten von Schlüsseln für Always Encrypted mit Secure Enclaves](../../relational-databases/security/encryption/always-encrypted-enclaves-manage-keys.md)   
 
  
  
