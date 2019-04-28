---
title: Sp_syspolicy_delete_policy_category (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_syspolicy_delete_policy_category_TSQL
- sp_syspolicy_delete_policy_category
dev_langs:
- TSQL
helpviewer_keywords:
- sp_syspolicy_delete_policy_category
ms.assetid: e09d0d50-94d5-48fd-b284-445ddea6dfcd
author: VanMSFT
ms.author: vanto
manager: craigg
ms.openlocfilehash: dd98f116bfa471797d2e9b340561c4eef121e0a7
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "63002632"
---
# <a name="spsyspolicydeletepolicycategory-transact-sql"></a>sp_syspolicy_delete_policy_category (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Löscht in der richtlinienbasierten Verwaltung eine Richtlinienkategorie.  
  
 ![Themenlinksymbol](../../database-engine/configure-windows/media/topic-link.gif "Topic link icon") [Transact-SQL Syntax Conventions (Transact-SQL-Syntaxkonventionen)](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```  
  
sp_syspolicy_delete_policy_category { [ @name = ] 'name' | [ @policy_category_id = ] policy_category_id }  
```  
  
## <a name="arguments"></a>Argumente  
`[ @name = ] 'name'` Ist der Name der Richtlinienkategorie. *Namen* ist **Sysname**, und muss angegeben werden, wenn *Policy_category_id* ist NULL.  
  
`[ @policy_category_id = ] policy_category_id` Ist der Bezeichner für die Richtlinienkategorie. *Policy_category_id* ist **Int**, und muss angegeben werden, wenn *Namen* ist NULL.  
  
## <a name="return-code-values"></a>Rückgabecodewerte  
 **0** (Erfolg) oder **1** (Fehler)  
  
## <a name="remarks"></a>Hinweise  
 Sie müssen sp_syspolicy_delete_policy_category im Kontext der Systemdatenbank msdb ausführen.  
  
 Geben Sie einen Wert für *Namen* oder *Policy_category_id*. Keiner der Werte darf NULL sein. Um diese Werte abzurufen, fragen Sie die Systemsicht msdb.dbo.syspolicy_policy_categories ab.  
  
 Um eine Richtlinienkategorie zu löschen, dürfen keine Richtlinien darauf verweisen.  
  
## <a name="permissions"></a>Berechtigungen  
 Erfordert die Mitgliedschaft in der festen Datenbankrolle PolicyAdministratorRole.  
  
> [!IMPORTANT]  
>  Mögliche Erweiterung der Anmeldeinformationen: Benutzer der Rolle PolicyAdministratorRole können Servertrigger erstellen und Ausführung von Richtlinien planen, die den Betrieb der Instanz von beeinflussen, können die [!INCLUDE[ssDE](../../includes/ssde-md.md)]. Ein Benutzer mit der Rolle PolicyAdministratorRole kann beispielsweise eine Richtlinie erstellen, durch die das Erstellen der meisten Objekte in [!INCLUDE[ssDE](../../includes/ssde-md.md)] verhindert wird. Aufgrund dieser möglichen Erweiterung der Anmeldeinformationen, sollte die PolicyAdministratorRole-Rolle gewährt werden nur für Benutzer, die mit der Kontrolle der Konfiguration von vertrauenswürdigen sind die [!INCLUDE[ssDE](../../includes/ssde-md.md)].  
  
## <a name="examples"></a>Beispiele  
 Im folgenden Beispiel wird die Richtlinienkategorie "Finance" gelöscht.  
  
```  
EXEC msdb.dbo.sp_syspolicy_delete_policy_category @name = N'Finance';  
  
GO  
```  
  
## <a name="see-also"></a>Siehe auch  
 [Gespeicherte Prozeduren für Richtlinie der richtlinienbasierten Verwaltung &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/policy-based-management-stored-procedures-transact-sql.md)   
 [sp_syspolicy_add_policy_category &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-syspolicy-add-policy-category-transact-sql.md)   
 [sp_syspolicy_update_policy_category &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-syspolicy-update-policy-category-transact-sql.md)  
  
  
