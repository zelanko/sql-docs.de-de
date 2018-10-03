---
title: cryptographic_providers (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- cryptographic_providers
- sys.cryptographic_providers
- sys.cryptographic_providers_TSQL
- cryptographic_providers_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.cryptographic_providers catalog view
ms.assetid: 9da0da95-792e-48b4-9f60-47f0729c279c
author: VanMSFT
ms.author: vanto
manager: craigg
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: 80918c74613e0fb608a9d48c1e56ad2cf206b06e
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/01/2018
ms.locfileid: "47791238"
---
# <a name="syscryptographicproviders-transact-sql"></a>sys.cryptographic_providers (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  Gibt eine Zeile für jeden registrierten Kryptografieanbieter zurück.  
    
|Spaltenname|Datentyp|Description|  
|-----------------|---------------|-----------------|  
|**provider_id**|**int**|ID des Kryptografieanbieters.|  
|**name**|**sysname**|Der Name des Kryptografieanbieters.|  
|**GUID**|**uniqueidentifier**|Eindeutige Anbieter-GUID.|  
|**version**|**nvarchar(50)**|Version des Anbieters im Format '*aa.bb.cccc.dd*'.|  
|**dll_path**|**nvarchar(512)**|Pfad zur DLL, die die API (Anwendungsprogrammierschnittstelle ) der erweiterbaren Schlüsselverwaltung (Extensible Key Management, EKM) implementiert.|  
|**is_enabled**|**bit**|Gibt an, ob der Anbieter auf dem Server aktiviert ist.<br /><br /> 0 = nicht aktiviert (Standard)<br /><br /> 1 = aktiviert|  
  
## <a name="remarks"></a>Hinweise  
 Die **sys.cryptographic_providers** -Sicht ist öffentlich sichtbar.  
  
## <a name="permissions"></a>Berechtigungen  
 [!INCLUDE[ssCatViewPerm](../../includes/sscatviewperm-md.md)] Weitere Informationen finden Sie unter [Metadata Visibility Configuration](../../relational-databases/security/metadata-visibility-configuration.md).  
  
## <a name="see-also"></a>Siehe auch  
 [Sicherheitskatalogsichten &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/security-catalog-views-transact-sql.md)   
 [Verschlüsselungshierarchie](../../relational-databases/security/encryption/encryption-hierarchy.md)   
 [Erweiterbare Schlüsselverwaltung &#40;EKM&#41;](../../relational-databases/security/encryption/extensible-key-management-ekm.md)   
 [CREATE CRYPTOGRAPHIC PROVIDER &#40;Transact-SQL&#41;](../../t-sql/statements/create-cryptographic-provider-transact-sql.md)  
  
  
