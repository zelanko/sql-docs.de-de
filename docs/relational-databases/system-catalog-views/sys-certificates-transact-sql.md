---
title: sys. Zertifikate (Transact-SQL) | Microsoft-Dokumentation
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
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 08193bd8f9b6dfd3aace80315c75bbb88e076f3a
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/27/2020
ms.locfileid: "75255842"
---
# <a name="syscertificates-transact-sql"></a>sys.certificates (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  Gibt eine Zeile für jedes Zertifikat in der Datenbank zurück.  
  
|Spaltenname|Datentyp|BESCHREIBUNG|  
|-----------------|---------------|-----------------|  
|**name**|**sysname**|Name des Zertifikats. Ist in der Datenbank eindeutig.|  
|**certificate_id**|**int**|ID des Zertifikats. Ist in der Datenbank eindeutig.|  
|**principal_id**|**int**|ID des Datenbankprinzipals, der der Besitzer dieses Zertifikats ist.|  
|**pvt_key_encryption_type**|**char (2)**|Die Verschlüsselungsart des privaten Schlüssels.<br /><br /> NA = Kein privater Schlüssel für das Zertifikat<br /><br /> MK = Privater Schlüssel wird mit dem Hauptschlüssel verschlüsselt<br /><br /> PW = Privater Schlüssel wird mit einem benutzerdefinierten Kennwort verschlüsselt<br /><br /> SK = Privater Schlüssel wird mit dem Diensthauptschlüssel verschlüsselt|  
|**pvt_key_encryption_type_desc**|**nvarchar(60)**|Die Beschreibung der Verschlüsselungsart des privaten Schlüssels.<br /><br /> NO_PRIVATE_KEY<br /><br /> ENCRYPTED_BY_MASTER_KEY<br /><br /> ENCRYPTED_BY_PASSWORD<br /><br /> ENCRYPTED_BY_SERVICE_MASTER_KEY|  
|**is_active_for_begin_dialog**|**bit**|Mit dem Wert 1 werden mit diesem Zertifikat verschlüsselte Dienstdialoge initiiert.|  
|**issuer_name**|**nvarchar (442)**|Name des Zertifikatausstellers.|  
|**cert_serial_number**|**nvarchar (64)**|Seriennummer des Zertifikats.|  
|**sid**|**varbinary(85)**|Anmelde-SID für dieses Zertifikat.|  
|**string_sid**|**nvarchar(128)**|Zeichenfolgendarstellung der Anmelde-SID für dieses Zertifikat.|  
|**Betreff**|**nvarchar(4000)**|Betreff dieses Zertifikats.|  
|**expiry_date**|**datetime**|Das Ablaufdatum des Zertifikats.|  
|**start_date**|**datetime**|Das Datum, ab dem das Zertifikat gültig ist.|  
|**Fingerabdruck**|**varbinary(32)**|SHA-1-Hash des Zertifikats. Der SHA-1-Hash ist global eindeutig.|  
|**attested_by**|**nvarchar(260)**|Nur zur Verwendung durch das System.|  
|**pvt_key_last_backup_date**|**datetime**|Das Datum und die Uhrzeit, zu denen der private Schlüssel des Zertifikats zuletzt exportiert wurde.|  
  
## <a name="permissions"></a>Berechtigungen  
 [!INCLUDE[ssCatViewPerm](../../includes/sscatviewperm-md.md)] Weitere Informationen finden Sie unter [Metadata Visibility Configuration](../../relational-databases/security/metadata-visibility-configuration.md).  
  
## <a name="see-also"></a>Weitere Informationen  
 [Sicherheits Katalog Sichten &#40;Transact-SQL-&#41;](../../relational-databases/system-catalog-views/security-catalog-views-transact-sql.md)   
 [Katalog Sichten &#40;Transact-SQL-&#41;](../../relational-databases/system-catalog-views/catalog-views-transact-sql.md)   
 [Verschlüsselungs Hierarchie](../../relational-databases/security/encryption/encryption-hierarchy.md)   
 [CREATE CERTIFICATE &#40;Transact-SQL&#41;](../../t-sql/statements/create-certificate-transact-sql.md)  
  
  
