---
title: column_master_keys (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/24/2018
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.component: system-catalog-views
ms.reviewer: ''
ms.suite: sql
ms.technology: system-objects
ms.tgt_pltfrm: ''
ms.topic: language-reference
applies_to:
- Azure SQL Database
- SQL Server 2016 Preview
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
manager: craigg
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: e683a88fb9490a7041ac02edc02a8ba2f63b1382
ms.sourcegitcommit: b7fd118a70a5da9bff25719a3d520ce993ea9def
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/24/2018
ms.locfileid: "46713542"
---
# <a name="syscolumnmasterkeys-transact-sql"></a>sys.column_master_keys (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2016-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2016-asdb-xxxx-xxx-md.md)]

  Gibt eine Zeile für jede Datenbank-Hauptschlüssel, der hinzugefügt werden, mithilfe der [CREATE MASTER KEY](../../t-sql/statements/create-column-master-key-transact-sql.md) Anweisung. Jede Zeile stellt einen einzelnen spaltenhauptschlüssel (CMK).  
    
|Spaltenname|Datentyp|Description|  
|-----------------|---------------|-----------------|  
|**name**|**sysname**|Der Name des CMK.|  
|**column_master_key_id**|**int**|ID des spaltenhauptschlüssels.|  
|**create_date**|**datetime**|Datum, an den spaltenhauptschlüssel erstellt wurde.|  
|**modify_date**|**datetime**|Datum, an den spaltenhauptschlüssel, den zuletzt geändert wurde.|  
|**key_store_provider_name**|**sysname**|Der Name des Anbieters für den Speicher des spaltenhauptschlüssels, der den CMK enthält. Zulässige Werte sind:<br /><br /> "Mssql_certificate_store" – Wenn der Speicher des spaltenhauptschlüssels eine Zertifikat-Store ist.<br /><br /> Ein benutzerdefinierte Wert, wenn der Speicher des spaltenhauptschlüssels eines benutzerdefinierten Typs ist.|  
|**key_path**|**nvarchar(4000)**|Eine unternehmensspezifische Pfad des spaltenhauptschlüssels des Schlüssels. Das Format des Pfads, hängt von den Spalte Hauptschlüssel Speichertyp ab. Beispiel:<br /><br /> `'CurrentUser/Personal/'<thumbprint>`<br /><br /> Für einen benutzerdefinierten Speicher des spaltenhauptschlüssels, der Entwickler ist dafür verantwortlich zu definieren ein Schlüsselpfad für den Speicher des benutzerdefinierten spaltenhauptschlüssels ist.|  
|**allow_enclave_computations**|**bit**|Gibt an, ob der spaltenhauptschlüssel Enclave-fähig ist, (wenn der spaltenverschlüsselungsschlüssel, die mit dieser Hauptschlüssel verschlüsselt, die für Berechnungen in serverseitigen sichere Enclaves verwendet werden können). Weitere Informationen finden Sie unter [Always Encrypted mit sicheren Enclaves](../../relational-databases/security/encryption/always-encrypted-enclaves.md).|  
|**signature**|**varbinary(max)**|Eine digitale Signatur der **Key_path** und **Allow_enclave_computations**, erstellt mit dem spaltenhauptschlüssel, auf die **Key_path**.|


  
## <a name="permissions"></a>Berechtigungen  
 Erfordert die **VIEW ANY COLUMN MASTER KEY** Berechtigung.  
  
 [!INCLUDE[ssCatViewPerm](../../includes/sscatviewperm-md.md)] Weitere Informationen finden Sie unter [Metadata Visibility Configuration](../../relational-databases/security/metadata-visibility-configuration.md).  
  
## <a name="see-also"></a>Siehe auch  
 [CREATE COLUMN MASTER KEY &#40;Transact-SQL&#41;](../../t-sql/statements/create-column-master-key-transact-sql.md)   
 [Sicherheitskatalogsichten &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/security-catalog-views-transact-sql.md)   
 [Always Encrypted &amp;amp;#40;Datenbank-Engine&amp;amp;#41;](../../relational-databases/security/encryption/always-encrypted-database-engine.md)   
 [sys.column_encryption_key_values &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-column-encryption-key-values-transact-sql.md)  
  
  
