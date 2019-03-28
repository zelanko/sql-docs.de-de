---
title: Sp_getmergedeletetype (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/04/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- sp_getmergedeletetype
- sp_getmergedeletetype_TSQL
helpviewer_keywords:
- sp_getmergedeletetype
ms.assetid: 64450e4d-844d-4176-874e-f3845536f7d2
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 3056c5c298fc1987e7c6f25e4a28220d3e033115
ms.sourcegitcommit: c44014af4d3f821e5d7923c69e8b9fb27aeb1afd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/27/2019
ms.locfileid: "58535202"
---
# <a name="spgetmergedeletetype-transact-sql"></a>sp_getmergedeletetype (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Gibt den Typ des Mergelöschvorgangs zurück. Diese gespeicherte Prozedur wird auf dem Verleger für die Veröffentlichungsdatenbank oder auf dem Abonnenten für die Abonnementdatenbank ausgeführt.  
  
 ![Themenlinksymbol](../../database-engine/configure-windows/media/topic-link.gif "Topic link icon") [Transact-SQL Syntax Conventions (Transact-SQL-Syntaxkonventionen)](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```  
  
sp_getmergedeletetype [ @source_object = ] 'source_object', [ @rowguid =] 'rowguid', [ @delete_type=] delete_type OUTPUT  
```  
  
## <a name="arguments"></a>Argumente  
`[ @source_object = ] 'source_object'` Ist der Name des Quellobjekts. *Source_object* ist **nvarchar(386)**, hat keinen Standardwert.  
  
`[ @rowguid = ] 'rowguid'` Ist der Zeilenbezeichner für den Typ der Löschung. *ROWGUID* ist **Uniqueidentifier**, hat keinen Standardwert.  
  
`[ @delete_type = ] delete_type OUTPUT` Ist der Code den Typ der Löschung angibt. *Delete_type* ist **Int**, hat keinen Standardwert. *Delete_type* ist auch ein OUTPUT-Parameter und kann einen der folgenden Werte sein.  
  
|Wert|Description|  
|-----------|-----------------|  
|**1**|Löschvorgang durch Benutzer|  
|**5**|Teilweiser Löschvorgang|  
|**6**|Löschvorgang durch System|  
  
## <a name="remarks"></a>Hinweise  
 **Sp_getmergedeletetype** wird bei der Mergereplikation verwendet.  
  
## <a name="permissions"></a>Berechtigungen  
 Nur Mitglieder der der **Sysadmin** -Serverrolle sein oder die **Db_owner** feste Datenbankrolle können ausführen **Sp_getmergedeletetype**.  
  
## <a name="see-also"></a>Siehe auch  
 [Gespeicherte Systemprozeduren &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
