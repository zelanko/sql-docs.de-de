---
description: sys.dm_cryptographic_provider_properties (Transact-SQL)
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
ms.openlocfilehash: 562c2884b0eda3488b436c1007c188ec7c64425b
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/17/2020
ms.locfileid: "88493788"
---
# <a name="sysdm_cryptographic_provider_properties-transact-sql"></a>sys.dm_cryptographic_provider_properties (Transact-SQL)
[!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

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
  
## <a name="see-also"></a>Siehe auch  
 [Sicherheitskatalogsichten &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/security-catalog-views-transact-sql.md)   
 [Verschlüsselungshierarchie](../../relational-databases/security/encryption/encryption-hierarchy.md)   
 [Erweiterbare Schlüsselverwaltung &#40;EKM&#41;](../../relational-databases/security/encryption/extensible-key-management-ekm.md)   
 [CREATE CRYPTOGRAPHIC PROVIDER &#40;Transact-SQL&#41;](../../t-sql/statements/create-cryptographic-provider-transact-sql.md)   
 [Sicherheitsbezogene dynamische Verwaltungssichten und -funktionen &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/security-related-dynamic-management-views-and-functions-transact-sql.md)  
  
  
