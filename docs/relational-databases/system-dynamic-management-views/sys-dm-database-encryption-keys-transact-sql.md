---
title: sys.dm_database_encryption_keys (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/27/2019
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sys.dm_database_encryption_keys
- sys.dm_database_encryption_keys_TSQL
- dm_database_encryption_keys
- dm_database_encryption_keys_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.dm_database_encryption_keys dynamic management view
ms.assetid: 56fee8f3-06eb-4fff-969e-abeaa0c4b8e4
author: stevestein
ms.author: sstein
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: 6e716c826fd366fda4505b7fcf9ec8e3b756ec25
ms.sourcegitcommit: 1124b91a3b1a3d30424ae0fec04cfaa4b1f361b6
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/01/2020
ms.locfileid: "80531052"
---
# <a name="sysdm_database_encryption_keys-transact-sql"></a>sys.dm_database_encryption_keys (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  Gibt Informationen über den Verschlüsselungsstatus einer Datenbank und die ihr zugeordneten Verschlüsselungsschlüssel für die Datenbank zurück. Weitere Informationen zur Datenbankverschlüsselung finden Sie unter [Transparent Data Encryption &#40;TDE&#41;](../../relational-databases/security/encryption/transparent-data-encryption.md).  
 
|Spaltenname|Datentyp|BESCHREIBUNG|  
|-----------------|---------------|-----------------|  
|database_id|**int**|Die ID der Datenbank.|  
|encryption_state|**int**|Gibt an, ob die Datenbank verschlüsselt oder nicht verschlüsselt ist.<br /><br /> 0 = Kein Verschlüsselungsschlüssel für die Datenbank vorhanden, keine Verschlüsselung<br /><br /> 1 = Unverschlüsselt<br /><br /> 2 = Verschlüsselung wird ausgeführt<br /><br /> 3 = Verschlüsselt.<br /><br /> 4 = Schlüsseländerung wird ausgeführt<br /><br /> 5 = Entschlüsselung wird ausgeführt<br /><br /> 6 = Schutzänderung wird ausgeführt (Das Zertifikat oder der asymmetrische Schlüssel, das bzw. der zum Verschlüsseln des Verschlüsselungsschlüssels für die Datenbank verwendet wird, wird geändert.)|  
|create_date|**Datetime**|Zeigt das Datum (in UTC) an, an dem der Verschlüsselungsschlüssel erstellt wurde.|  
|regenerate_date|**Datetime**|Zeigt das Datum (in UTC) an, an dem der Verschlüsselungsschlüssel neu generiert wurde.|  
|modify_date|**Datetime**|Zeigt das Datum (in UTC) an, an dem der Verschlüsselungsschlüssel geändert wurde.|  
|set_date|**Datetime**|Zeigt das Datum (in UTC) an, an dem der Verschlüsselungsschlüssel auf die Datenbank angewendet wurde.|  
|opened_date|**Datetime**|Zeigt an, wann (in UTC) der Datenbankschlüssel zuletzt geöffnet wurde.|  
|key_algorithm|**nvarchar(32)**|Zeigt den Algorithmus an, der für den Schlüssel verwendet wird.|  
|key_length|**int**|Zeigt die Länge des Schlüssels an.|  
|encryptor_thumbprint|**varbinary(20)**|Zeigt den Fingerabdruck der Verschlüsselung an.|  
|encryptor_type|**nvarchar(32)**|**Gilt**für [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] : ( durch [die aktuelle Version](https://go.microsoft.com/fwlink/p/?LinkId=299658)).<br /><br /> Beschreibt die Verschlüsselung.|  
|percent_complete|**real**|Prozentualer Anteil der bereits abgeschlossenen Änderung des Verschlüsselungsstatus einer Datenbank. Dieser Wert ist 0, wenn es keine Statusänderung gibt.|
|encryption_state_desc|**nvarchar(32)**|**Gilt**für [!INCLUDE[sql-server-2019](../../includes/sssqlv15-md.md)] : und höher.<br><br> Zeichenfolge, die angibt, ob die Datenbank verschlüsselt ist oder nicht.<br><br>Keine<br><br>Unverschlüsselte<br><br>Verschlüsselt<br><br>DECRYPTION_IN_PROGRESS<br><br>ENCRYPTION_IN_PROGRESS<br><br>KEY_CHANGE_IN_PROGRESS<br><br>PROTECTION_CHANGE_IN_PROGRESS|
|encryption_scan_state|**int**|**Gilt**für [!INCLUDE[sql-server-2019](../../includes/sssqlv15-md.md)] : und höher.<br><br>Gibt den aktuellen Status des Verschlüsselungsscans an. <br><br>0 = Es wurde kein Scan initiiert, TDE ist nicht aktiviert<br><br>1 = Scan wird ausgeführt.<br><br>2 = Der Scan wird ausgeführt, aber angehalten, der Benutzer kann fortgesetzt werden.<br><br>3 = Der Scan wurde aus irgendeinem Grund abgebrochen, ein manueller Eingriff ist erforderlich. Wenden Sie sich an den Microsoft-Support, um weitere Unterstützung zu erhalten.<br><br>4 = Der Scan wurde erfolgreich abgeschlossen, TDE ist aktiviert und die Verschlüsselung ist abgeschlossen.|
|encryption_scan_state_desc|**nvarchar(32)**|**Gilt**für [!INCLUDE[sql-server-2019](../../includes/sssqlv15-md.md)] : und höher.<br><br>Zeichenfolge, die den aktuellen Status des Verschlüsselungsscans angibt.<br><br> Keine<br><br>RUNNING<br><br>SUSPENDED<br><br>ABORTED<br><br>vollständig|
|encryption_scan_modify_date|**Datetime**|**Gilt**für [!INCLUDE[sql-server-2019](../../includes/sssqlv15-md.md)] : und höher.<br><br> Zeigt das Datum (in UTC) an, an dem der Verschlüsselungsscanstatus zuletzt geändert wurde.|
  
## <a name="permissions"></a>Berechtigungen

Auf [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)]erfordert `VIEW SERVER STATE` dies die Berechtigung.   
Erfordert [!INCLUDE[ssSDS_md](../../includes/sssds-md.md)] für Premium-Stufen `VIEW DATABASE STATE` die Berechtigung in der Datenbank. Erfordert [!INCLUDE[ssSDS_md](../../includes/sssds-md.md)] für Standard- und Basisstufen den **Serveradministrator** oder ein **Azure Active Directory-Administratorkonto.**   

## <a name="see-also"></a>Weitere Informationen  

 [Sicherheitsbezogene dynamische Managementansichten und Funktionen &#40;Transact-SQL-&#41;](../../relational-databases/system-dynamic-management-views/security-related-dynamic-management-views-and-functions-transact-sql.md)   
 [Transparente Datenverschlüsselung &#40;TDE-&#41;](../../relational-databases/security/encryption/transparent-data-encryption.md)   
 [SQL Server-Verschlüsselung](../../relational-databases/security/encryption/sql-server-encryption.md)   
 [SQL Server- und Datenbankverschlüsselungsschlüssel &#40;Datenbankmodul&#41;](../../relational-databases/security/encryption/sql-server-and-database-encryption-keys-database-engine.md)   
 [Verschlüsselungshierarchie](../../relational-databases/security/encryption/encryption-hierarchy.md)   
 [ALTER DATABASE SET Optionen &#40;Transact-SQL&#41;](../../t-sql/statements/alter-database-transact-sql-set-options.md)   
 [CREATE DATABASE ENCRYPTION KEY &#40;Transact-SQL&#41;](../../t-sql/statements/create-database-encryption-key-transact-sql.md)   
 [ALTER DATABASE ENCRYPTION KEY &#40;Transact-SQL&#41;](../../t-sql/statements/alter-database-encryption-key-transact-sql.md)   
 [DROP DATABASE ENCRYPTION KEY &#40;Transact-SQL&#41;](../../t-sql/statements/drop-database-encryption-key-transact-sql.md)  
  
  
