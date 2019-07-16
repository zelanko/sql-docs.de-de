---
title: column_master_keys (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/24/2018
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
author: VanMSFT
ms.author: vanto
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: 8ae8a4077c0fe4e3f6b7754b4fc53a401d03e355
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "68140058"
---
# <a name="syscolumnmasterkeys-transact-sql"></a>sys.column_master_keys (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2016-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2016-asdb-xxxx-xxx-md.md)]

  Gibt eine Zeile für jede Datenbank-Hauptschlüssel, der hinzugefügt werden, mithilfe der [CREATE MASTER KEY](../../t-sql/statements/create-column-master-key-transact-sql.md) Anweisung. Jede Zeile stellt einen einzelnen spaltenhauptschlüssel (CMK).  
    
|Spaltenname|Datentyp|Beschreibung|  
|-----------------|---------------|-----------------|  
|**name**|**sysname**|Der Name des CMK.|  
|**column_master_key_id**|**int**|ID des spaltenhauptschlüssels.|  
|**create_date**|**datetime**|Datum, an den spaltenhauptschlüssel erstellt wurde.|  
|**modify_date**|**datetime**|Datum, an den spaltenhauptschlüssel, den zuletzt geändert wurde.|  
|**key_store_provider_name**|**sysname**|Der Name des Anbieters für den Speicher des spaltenhauptschlüssels, der den CMK enthält. Zulässige Werte sind:<br /><br /> "Mssql_certificate_store" - ist der Speicher des spaltenhauptschlüssels eine Zertifikat-Store.<br /><br /> Ein benutzerdefinierte Wert, wenn der Speicher des spaltenhauptschlüssels eines benutzerdefinierten Typs ist.|  
|**key_path**|**nvarchar(4000)**|Eine unternehmensspezifische Pfad des spaltenhauptschlüssels des Schlüssels. Das Format des Pfads, hängt von den Spalte Hauptschlüssel Speichertyp ab. Beispiel:<br /><br /> `'CurrentUser/Personal/'<thumbprint>`<br /><br /> Für einen benutzerdefinierten Speicher des spaltenhauptschlüssels, der Entwickler ist dafür verantwortlich zu definieren ein Schlüsselpfad für den Speicher des benutzerdefinierten spaltenhauptschlüssels ist.|  
|**allow_enclave_computations**|**bit**|Gibt an, ob der spaltenhauptschlüssel Enclave-fähig ist, (wenn der spaltenverschlüsselungsschlüssel, die mit dieser Hauptschlüssel verschlüsselt, die für Berechnungen in serverseitigen sichere Enclaves verwendet werden können). Weitere Informationen finden Sie unter [Always Encrypted mit Secure Enclaves](../../relational-databases/security/encryption/always-encrypted-enclaves.md).|  
|**signature**|**varbinary(max)**|Eine digitale Signatur der **Key_path** und **Allow_enclave_computations**, erstellt mit dem spaltenhauptschlüssel, auf die **Key_path**.|


  
## <a name="permissions"></a>Berechtigungen  
 Erfordert die **VIEW ANY COLUMN MASTER KEY** Berechtigung.  
  
 [!INCLUDE[ssCatViewPerm](../../includes/sscatviewperm-md.md)] Weitere Informationen finden Sie unter [Metadata Visibility Configuration](../../relational-databases/security/metadata-visibility-configuration.md).  
  
## <a name="see-also"></a>Siehe auch  
 [CREATE COLUMN MASTER KEY &#40;Transact-SQL&#41;](../../t-sql/statements/create-column-master-key-transact-sql.md)   
 [Sicherheitskatalogsichten &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/security-catalog-views-transact-sql.md)   
 [Always Encrypted &#40;Datenbank-Engine&#41;](../../relational-databases/security/encryption/always-encrypted-database-engine.md)   
 [sys.column_encryption_key_values &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-column-encryption-key-values-transact-sql.md)  
  
  
