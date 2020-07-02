---
title: sp_syspolicy_unsubscribe_from_policy_category (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_syspolicy_unsubscribe_from_policy_category_TSQL
- sp_syspolicy_unsubscribe_from_policy_category
dev_langs:
- TSQL
helpviewer_keywords:
- sp_syspolicy_unsubscribe_from_policy_category
ms.assetid: 47abab63-e605-40e8-a54e-2241e2e01afd
author: VanMSFT
ms.author: vanto
ms.openlocfilehash: d606cbca53810eaa9e19153e5de8b821391b2659
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/01/2020
ms.locfileid: "85752775"
---
# <a name="sp_syspolicy_unsubscribe_from_policy_category-transact-sql"></a>sp_syspolicy_unsubscribe_from_policy_category (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/applies-to-version/sqlserver.md)]

  Löscht ein Richtlinienkategorieabonnement für die aktuelle Datenbank.  
  
 ![Symbol für Themenlink](../../database-engine/configure-windows/media/topic-link.gif "Symbol für Themenlink") [Transact-SQL-Syntaxkonventionen](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```  
  
sp_syspolicy_unsubscribe_from_policy_category [ @policy_category = ] 'policy_category'  
```  
  
## <a name="arguments"></a>Argumente  
`[ @policy_category = ] 'policy_category'`Der Name des Richtlinienkategorieabonnements, das Sie löschen möchten. *policy_category* ist vom **Datentyp vom Datentyp sysname**und ist erforderlich.  
  
 Wenn Sie Werte für *policy_category*abrufen möchten, Fragen Sie die msdb.dbo.syspolicy_policy_categories-Systemsicht ab.  
  
## <a name="return-code-values"></a>Rückgabecodewerte  
 **0** (Erfolg) oder **1** (Fehler)  
  
## <a name="remarks"></a>Hinweise  
 Sie müssen sp_syspolicy_unsubscribe_from_policy_category im Kontext der Datenbank ausführen, in der Sie ein Richtlinienkategorieabonnement entfernen möchten.  
  
## <a name="permissions"></a>Berechtigungen  
 Erfordert die Mitgliedschaft in der festen Datenbankrolle "db_owner".  
  
## <a name="examples"></a>Beispiele  
 Im folgenden Beispiel wird ein Abonnement für die Richtlinienkategorie "Finance" für die angegebene Datenbank gelöscht.  
  
```  
USE <database_name>;  
  
EXEC sys.sp_syspolicy_unsubscribe_from_policy_category @policy_category = N'Finance';  
  
GO  
```  
  
## <a name="see-also"></a>Weitere Informationen  
 [Gespeicherte Prozeduren der Richtlinien basierten Verwaltung &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/policy-based-management-stored-procedures-transact-sql.md)   
 [sp_syspolicy_subscribe_to_policy_category &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/sp-syspolicy-subscribe-to-policy-category-transact-sql.md)  
  
  
