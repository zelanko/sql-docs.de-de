---
description: sys.dm_cryptographic_provider_sessions (Transact-SQL)
title: sys. dm_cryptographic_provider_sessions (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sys.dm_cryptographic_provider_sessions
- dm_cryptographic_provider_sessions_TSQL
- sys.dm_cryptographic_provider_sessions_TSQL
- dm_cryptographic_provider_sessions
dev_langs:
- TSQL
helpviewer_keywords:
- sys.dm_cryptographic_provider_sessions dynamic management function
ms.assetid: 9a4de02b-1a07-4850-979a-0861fddb7f9d
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 37a8854da08439c4dc3984bcdfc61a8695467c2b
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/17/2020
ms.locfileid: "88455014"
---
# <a name="sysdm_cryptographic_provider_sessions-transact-sql"></a>sys.dm_cryptographic_provider_sessions (Transact-SQL)
[!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

  Gibt Informationen über geöffnete Sitzungen für einen Kryptografieanbieter zurück.  
 
## <a name="syntax"></a>Syntax  
  
```  
  
sys.dm_cryptographic_provider_sessions(session_identifier)  
```  
  
## <a name="arguments"></a>Argumente  
 *session_identifier*  
 Eine Ganzzahl, die die zurückzugebende Sitzung angibt.  
  
 0 = Nur aktuelle Verbindung  
  
 1 = Alle kryptografischen Verbindungen  
  
## <a name="table-returned"></a>Zurückgegebene Tabelle  
  
|Spaltenname|Datentyp|BESCHREIBUNG|  
|-----------------|---------------|-----------------|  
|**provider_id**|**int**|ID des Kryptografieanbieters.|  
|**session_handle**|**varbytes (8)**|Kryptografisches Sitzungshandle.|  
|**Identität**|**nvarchar(128)**|ID, die zur Authentifizierung mit dem Kryptgrafieanbieter verwendet wird.|  
|**spid**|**short**|SPID der Sitzungs-ID für die Verbindung. Weitere Informationen finden Sie unter [@@SPID &#40;Transact-SQL&#41;](../../t-sql/functions/spid-transact-sql.md).|  
  
## <a name="remarks"></a>Bemerkungen  
 Die **sys. dm_cryptographic_provider_sessions** -Sicht ist für die öffentliche der aktuellen Verbindung sichtbar. Um alle kryptografieverbindungen anzuzeigen, müssen Sie über die **Control** Server-Berechtigung verfügen.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Sicherheitskatalogsichten &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/security-catalog-views-transact-sql.md)   
 [Erweiterbare Schlüsselverwaltung &#40;EKM&#41;](../../relational-databases/security/encryption/extensible-key-management-ekm.md)   
 [CREATE CRYPTOGRAPHIC PROVIDER &#40;Transact-SQL&#41;](../../t-sql/statements/create-cryptographic-provider-transact-sql.md)   
 [Verschlüsselungshierarchie](../../relational-databases/security/encryption/encryption-hierarchy.md)  
  
  
