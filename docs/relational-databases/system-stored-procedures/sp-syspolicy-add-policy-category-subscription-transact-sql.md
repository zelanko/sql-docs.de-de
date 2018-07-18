---
title: Sp_syspolicy_add_policy_category_subscription (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.component: system-stored-procedures
ms.reviewer: ''
ms.suite: sql
ms.technology: system-objects
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- sp_syspolicy_add_policy_category_subscription
- sp_syspolicy_add_policy_category_subscription_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sp_syspolicy_add_policy_category_subscription
ms.assetid: 4284f550-9a3f-4726-8181-15e407fbf08f
caps.latest.revision: 8
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 5c3e5f4079a75fca4112da1185a941b3a77e6b85
ms.sourcegitcommit: f1caaa156db2b16e817e0a3884394e7b30fb642f
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/04/2018
ms.locfileid: "33253119"
---
# <a name="spsyspolicyaddpolicycategorysubscription-transact-sql"></a>sp_syspolicy_add_policy_category_subscription (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Fügt der angegebenen Datenbank ein Richtlinienkategorieabonnement hinzu.  
  
 ![Themenlinksymbol](../../database-engine/configure-windows/media/topic-link.gif "Topic link icon") [Transact-SQL Syntax Conventions (Transact-SQL-Syntaxkonventionen)](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```  
  
sp_syspolicy_add_policy_category_subscription [ @target_type = ] 'target_type'  
    , [ @target_object = ] 'target_object'  
    , [ @policy_category = ] 'policy_category'  
    [ , [ @policy_category_subscription_id = ] policy_category_subscription_id OUTPUT ]  
```  
  
## <a name="arguments"></a>Argumente  
 [ **@target_type=** ] **'***target_type***'**  
 Der Zieltyp des Kategorieabonnements. *Target_type* ist **Sysname**ist erforderlich und muss auf 'DATABASE' festgelegt werden.  
  
 [  **@target_object=** ] **"***Target_object***"**  
 Ist der Name der Datenbank, die die Kategorie abonniert. *Target_object* ist **Sysname**, und es ist erforderlich.  
  
 [ **@policy_category=** ] **'***policy_category***'**  
 Ist der Name der Richtlinienkategorie zu abonnieren. *Policy_category* ist **Sysname**, und es ist erforderlich.  
  
 Zum Abrufen von Werten für *Policy_category*, Fragen Sie die Systemsicht syspolicy_policy_categories ab.  
  
 [ **@policy_category_subscription_id=** ] *policy_category_subscription_id*  
 Der Bezeichner für das Kategorieabonnement. *Policy_category_subscription_id* ist **Int**, und wird als OUTPUT zurückgegeben.  
  
## <a name="return-code-values"></a>Rückgabecodewerte  
 **0** (Erfolg) oder **1** (Fehler)  
  
## <a name="remarks"></a>Hinweise  
 Sie müssen sp_syspolicy_add_policy_category_subscription im Kontext der Systemdatenbank msdb ausführen.  
  
 Wenn Sie eine Richtlinienkategorie angeben, die nicht vorhanden ist, wird eine neue Richtlinienkategorie erstellt. Das Abonnement wird für alle Datenbanken beauftragt, wenn Sie die gespeicherte Prozedur ausführen. Wenn Sie dann das beauftragte Abonnement für die neue Kategorie löschen, ist das Abonnement nur für die Datenbank gültig, die Sie als *target_object* angegeben haben. Weitere Informationen zum Ändern der Einstellung eines beauftragten Abonnements finden Sie unter [sp_syspolicy_update_policy_category &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-syspolicy-update-policy-category-transact-sql.md).  
  
## <a name="permissions"></a>Berechtigungen  
 Diese gespeicherte Prozedur wird im Kontext des aktuellen Besitzers der gespeicherten Prozedur ausgeführt.  
  
## <a name="examples"></a>Beispiele  
 Im folgenden Beispiel wird angegebene Datenbank konfiguriert, um eine Richtlinienkategorie zu abonnieren, die den Namen "Table Naming Policies" hat.  
  
```  
EXEC msdb.dbo.sp_syspolicy_add_policy_category_subscription @target_type = N'DATABASE'  
, @target_object = N'AdventureWorks2012'  
, @policy_category = N'Table Naming Policies';  
  
GO  
```  
  
## <a name="see-also"></a>Siehe auch  
 [Gespeicherte Prozeduren Richtlinie der richtlinienbasierten Verwaltung &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/policy-based-management-stored-procedures-transact-sql.md)   
 [Sp_syspolicy_update_policy_category_subscription &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-syspolicy-update-policy-category-subscription-transact-sql.md)   
 [Sp_syspolicy_unsubscribe_from_policy_category &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-syspolicy-unsubscribe-from-policy-category-transact-sql.md)  
  
  
