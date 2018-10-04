---
title: Sys.Certificates (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/15/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- certificates
- certificates_TSQL
- sys.certificates_TSQL
- sys.certificates
dev_langs:
- TSQL
helpviewer_keywords:
- sys.certificates catalog view
ms.assetid: e5046102-a65c-401e-b80d-05636884dec9
author: VanMSFT
ms.author: vanto
manager: craigg
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: a1336533eb3a7ffb8b3e30e252a1335012b7c373
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/01/2018
ms.locfileid: "47812978"
---
# <a name="syscertificates-transact-sql"></a>sys.certificates (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  Gibt eine Zeile für jedes Zertifikat in der Datenbank zurück.  
  
|Spaltenname|Datentyp|Description|  
|-----------------|---------------|-----------------|  
|**name**|**sysname**|Name des Zertifikats. Ist in der Datenbank eindeutig.|  
|**certificate_id**|**int**|ID des Zertifikats. Ist in der Datenbank eindeutig.|  
|**principal_id**|**int**|ID des Datenbankprinzipals, der der Besitzer dieses Zertifikats ist.|  
|**pvt_key_encryption_type**|**char(2)**|Die Verschlüsselungsart des privaten Schlüssels.<br /><br /> NA = Kein privater Schlüssel für das Zertifikat<br /><br /> MK = Privater Schlüssel wird mit dem Hauptschlüssel verschlüsselt<br /><br /> PW = Privater Schlüssel wird mit einem benutzerdefinierten Kennwort verschlüsselt<br /><br /> SK = Privater Schlüssel wird mit dem Diensthauptschlüssel verschlüsselt|  
|**pvt_key_encryption_type_desc**|**nvarchar(60)**|Die Beschreibung der Verschlüsselungsart des privaten Schlüssels.<br /><br /> NO_PRIVATE_KEY<br /><br /> ENCRYPTED_BY_MASTER_KEY<br /><br /> ENCRYPTED_BY_PASSWORD<br /><br /> ENCRYPTED_BY_SERVICE_MASTER_KEY|  
|**is_active_for_begin_dialog**|**bit**|Mit dem Wert 1 werden mit diesem Zertifikat verschlüsselte Dienstdialoge initiiert.|  
|**issuer_name**|**nvarchar(442)**|Name des Zertifikatausstellers.|  
|**cert_serial_number**|**Nvarchar(64)**|Seriennummer des Zertifikats.|  
|**SID**|**varbinary(85)**|Anmelde-SID für dieses Zertifikat.|  
|**string_sid**|**nvarchar(128)**|Zeichenfolgendarstellung der Anmelde-SID für dieses Zertifikat.|  
|**Betreff**|**nvarchar(4000)**|Betreff dieses Zertifikats.|  
|**expiry_date**|**datetime**|Das Ablaufdatum des Zertifikats.|  
|**start_date**|**datetime**|Das Datum, ab dem das Zertifikat gültig ist.|  
|**Fingerabdruck**|**varbinary(32)**|SHA-1-Hash des Zertifikats. Der SHA-1-Hash ist global eindeutig.|  
|**attested_by**|**nvarchar(260)**|Nur zur Verwendung durch das System.|  
|pvt_key_last_backup_date|**datetime**|Datum und Uhrzeit des letzten Exports des privaten Zertifikatschlüssels.|  
  
## <a name="permissions"></a>Berechtigungen  
 [!INCLUDE[ssCatViewPerm](../../includes/sscatviewperm-md.md)] Weitere Informationen finden Sie unter [Metadata Visibility Configuration](../../relational-databases/security/metadata-visibility-configuration.md).  
  
## <a name="see-also"></a>Siehe auch  
 [Sicherheitskatalogsichten &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/security-catalog-views-transact-sql.md)   
 [Katalogsichten &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/catalog-views-transact-sql.md)   
 [Verschlüsselungshierarchie](../../relational-databases/security/encryption/encryption-hierarchy.md)   
 [CREATE CERTIFICATE &#40;Transact-SQL&#41;](../../t-sql/statements/create-certificate-transact-sql.md)  
  
  
