---
title: sys. dm_cryptographic_provider_properties (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- dm_cryptographic_provider_properties_TSQL
- sys.dm_cryptographic_provider_properties
- sys.dm_cryptographic_provider_properties_TSQL
- dm_cryptographic_provider_properties
dev_langs:
- TSQL
helpviewer_keywords:
- sys.dm_cryptographic_provider_properties dynamic management view
ms.assetid: 024b0095-6766-4189-a39a-d316c5ec2874
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 0b08159d666fb18cc92feb88f087168b249ff523
ms.sourcegitcommit: 4d3896882c5930248a6e441937c50e8e027d29fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/05/2020
ms.locfileid: "82824695"
---
# <a name="sysdm_cryptographic_provider_properties-transact-sql"></a>sys.dm_cryptographic_provider_properties (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Gibt Informationen über registrierte Kryptografieanbieter zurück.  
  
 
|Spaltenname|Datentyp|BESCHREIBUNG|  
|-----------------|---------------|-----------------|  
|provider_id|**int**|ID des Kryptografieanbieters.|  
|guid|**uniqueidentifier**|Eindeutige Anbieter-GUID.|  
|provider_version|**nvarchar(256)**|Version des Anbieters im Format '*aa.bb.cccc.dd*'.|  
|sqlcrypt_version|**nvarchar(256)**|Hauptversionsnummer der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Cryptographic API im Format '*aa.bb.cccc.dd*'.|  
|friendly_name|**nvarchar (2048)**|Vom Anbieter bereitgestellter Name.|  
|authentication_type|**nvarchar(256)**|WINDOWS, BASIC oder OTHER.|  
|symmetric_key_support|**tinyint**|0 (nicht unterstützt)<br /><br /> 1 (unterstützt)|  
|symmetric_key_export|**tinyint**|0 (nicht unterstützt)<br /><br /> 1 (unterstützt)|  
|symmetric_key_import|**tinyint**|0 (nicht unterstützt)<br /><br /> 1 (unterstützt)|  
|symmetric_key_persistance|**tinyint**|0 (nicht unterstützt)<br /><br /> 1 (unterstützt)|  
|asymmetric_key_support|**tinyint**|0 (nicht unterstützt)<br /><br /> 1 (unterstützt)|  
|asymmetric_key_export|**tinyint**|0 (nicht unterstützt)<br /><br /> 1 (unterstützt)|  
|symmetric_key_import|**tinyint**|0 (nicht unterstützt)<br /><br /> 1 (unterstützt)|  
|symmetric_key_persistance|**tinyint**|0 (nicht unterstützt)<br /><br /> 1 (unterstützt)|  
  
## <a name="remarks"></a>Bemerkungen  
 Die sys.dm_cryptographic_provider_properties-Sicht ist öffentlich sichtbar.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Sicherheits Katalog Sichten &#40;Transact-SQL-&#41;](../../relational-databases/system-catalog-views/security-catalog-views-transact-sql.md)   
 [Verschlüsselungs Hierarchie](../../relational-databases/security/encryption/encryption-hierarchy.md)   
 [Erweiterbare Schlüsselverwaltung &#40;EKM-&#41;](../../relational-databases/security/encryption/extensible-key-management-ekm.md)   
 [Erstellen eines Kryptografieanbieters &#40;Transact-SQL-&#41;](../../t-sql/statements/create-cryptographic-provider-transact-sql.md)   
 [Sicherheitsbezogene dynamische Verwaltungssichten und -funktionen &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/security-related-dynamic-management-views-and-functions-transact-sql.md)  
  
  
