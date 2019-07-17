---
title: Sys. dm_database_encryption_keys (Transact-SQL) | Microsoft-Dokumentation
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
ms.openlocfilehash: 2c66fbc1cdf98d45a7440d2def9cb3fd1be5635a
ms.sourcegitcommit: e7d921828e9eeac78e7ab96eb90996990c2405e9
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/16/2019
ms.locfileid: "68255755"
---
# <a name="sysdmdatabaseencryptionkeys-transact-sql"></a>sys.dm_database_encryption_keys (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  Gibt Informationen über den Verschlüsselungsstatus einer Datenbank und die ihr zugeordneten Verschlüsselungsschlüssel für die Datenbank zurück. Weitere Informationen zur Datenbankverschlüsselung finden Sie unter [Transparent Data Encryption &#40;TDE&#41;](../../relational-databases/security/encryption/transparent-data-encryption.md).  
 
|Spaltenname|Datentyp|Beschreibung|  
|-----------------|---------------|-----------------|  
|database_id|**int**|Die ID der Datenbank.|  
|encryption_state|**int**|Gibt an, ob die Datenbank verschlüsselt oder nicht verschlüsselt ist.<br /><br /> 0 = Kein Verschlüsselungsschlüssel für die Datenbank vorhanden, keine Verschlüsselung<br /><br /> 1 = Unverschlüsselt<br /><br /> 2 = Verschlüsselung wird ausgeführt<br /><br /> 3 = Verschlüsselt.<br /><br /> 4 = Schlüsseländerung wird ausgeführt<br /><br /> 5 = Entschlüsselung wird ausgeführt<br /><br /> 6 = Schutzänderung wird ausgeführt (Das Zertifikat oder der asymmetrische Schlüssel, das bzw. der zum Verschlüsseln des Verschlüsselungsschlüssels für die Datenbank verwendet wird, wird geändert.)|  
|create_date|**datetime**|Zeigt das Datum an (in UTC) des Verschlüsselungsschlüssels erstellt wurde.|  
|regenerate_date|**datetime**|Zeigt das Datum an (in UTC) wurde der Verschlüsselungsschlüssel erneut generiert.|  
|modify_date|**datetime**|Zeigt das Datum an (in UTC) des Verschlüsselungsschlüssels geändert wurde.|  
|set_date|**datetime**|Zeigt das Datum an (in UTC) des Verschlüsselungsschlüssels auf die Datenbank angewendet wurde.|  
|opened_date|**datetime**|Zeigt, wann (in UTC) der Datenbankschlüssel zuletzt geöffnet wurde.|  
|key_algorithm|**nvarchar(32)**|Zeigt den Algorithmus an, der für den Schlüssel verwendet wird.|  
|key_length|**int**|Zeigt die Länge des Schlüssels an.|  
|encryptor_thumbprint|**varbinary(20)**|Zeigt den Fingerabdruck der Verschlüsselung an.|  
|encryptor_type|**nvarchar(32)**|**Gilt für**: [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ([!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] bis [aktuelle Version](https://go.microsoft.com/fwlink/p/?LinkId=299658)).<br /><br /> Beschreibt die Verschlüsselung.|  
|percent_complete|**real**|Prozentualer Anteil der bereits abgeschlossenen Änderung des Verschlüsselungsstatus einer Datenbank. Dieser Wert ist 0, wenn es keine Statusänderung gibt.|
|encryption_state_desc|**nvarchar(32)**|**Gilt für**: [!INCLUDE[sql-server-2019](../../includes/sssqlv15-md.md)] und höher.<br><br> Eine Zeichenfolge, die angibt, ob die Datenbank verschlüsselt oder nicht verschlüsselt.<br><br>Keine<br><br>UNVERSCHLÜSSELTE<br><br>VERSCHLÜSSELT<br><br>DECRYPTION_IN_PROGRESS<br><br>ENCRYPTION_IN_PROGRESS<br><br>KEY_CHANGE_IN_PROGRESS<br><br>PROTECTION_CHANGE_IN_PROGRESS|
|encryption_scan_state|**int**|**Gilt für**: [!INCLUDE[sql-server-2019](../../includes/sssqlv15-md.md)] und höher.<br><br>Gibt den aktuellen Zustand der der verschlüsselungsscan an. <br><br>0 = keine Überprüfung wurde initiiert, TDE nicht aktiviert ist<br><br>1 = Überprüfung wird ausgeführt.<br><br>2 = Überprüfung wird ausgeführt, aber wurde angehalten, der Benutzer kann fortgesetzt werden.<br><br>3 = Überprüfung erfolgreich abgeschlossen wurde, TDE aktiviert ist und die Verschlüsselung abgeschlossen ist.<br><br>4 = Überprüfung wurde aus irgendeinem Grund abgebrochen, manueller Eingriff erforderlich ist. Wenden Sie sich an Microsoft Support, um weitere Unterstützung zu erhalten.|
|encryption_scan_state_desc|**nvarchar(32)**|**Gilt für**: [!INCLUDE[sql-server-2019](../../includes/sssqlv15-md.md)] und höher.<br><br>Eine Zeichenfolge, die den aktuellen Zustand des verschlüsselungsscans angibt.<br><br> Keine<br><br>RUNNING<br><br>SUSPENDED<br><br>VOLLSTÄNDIG<br><br>ABORTED|
|encryption_scan_modify_date|**datetime**|**Gilt für**: [!INCLUDE[sql-server-2019](../../includes/sssqlv15-md.md)] und höher.<br><br> Zeigt das Datum an (in UTC) des Verschlüsselungsstatus für die Überprüfung zuletzt geändert wurde.|
  
## <a name="permissions"></a>Berechtigungen

Auf [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)], erfordert `VIEW SERVER STATE` Berechtigung.   
Auf [!INCLUDE[ssSDS_md](../../includes/sssds-md.md)] Premium-Tarife, erfordert die `VIEW DATABASE STATE` Berechtigung in der Datenbank. Auf [!INCLUDE[ssSDS_md](../../includes/sssds-md.md)] Standard und Basic-Version, erfordert die **Serveradministrator** oder **Azure Active Directory-Administrator** Konto.   

## <a name="see-also"></a>Siehe auch  

 [Sicherheitsbezogene dynamische Verwaltungssichten und -funktionen &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/security-related-dynamic-management-views-and-functions-transact-sql.md)   
 [Transparente Datenverschlüsselung &#40;TDE&#41;](../../relational-databases/security/encryption/transparent-data-encryption.md)   
 [SQL Server-Verschlüsselung](../../relational-databases/security/encryption/sql-server-encryption.md)   
 [Verschlüsselungsschlüssel für SQL Server und Datenbank &#40;Datenbank-Engine&#41;](../../relational-databases/security/encryption/sql-server-and-database-encryption-keys-database-engine.md)   
 [Verschlüsselungshierarchie](../../relational-databases/security/encryption/encryption-hierarchy.md)   
 [ALTER DATABASE SET-Optionen &#40;Transact-SQL&#41;](../../t-sql/statements/alter-database-transact-sql-set-options.md)   
 [CREATE DATABASE ENCRYPTION KEY &#40;Transact-SQL&#41;](../../t-sql/statements/create-database-encryption-key-transact-sql.md)   
 [ALTER DATABASE ENCRYPTION KEY &#40;Transact-SQL&#41;](../../t-sql/statements/alter-database-encryption-key-transact-sql.md)   
 [DROP DATABASE ENCRYPTION KEY &#40;Transact-SQL&#41;](../../t-sql/statements/drop-database-encryption-key-transact-sql.md)  
  
  
