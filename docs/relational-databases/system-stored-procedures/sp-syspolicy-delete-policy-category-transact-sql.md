---
title: sp_syspolicy_delete_policy_category (Transact-SQL) | Microsoft-Dokumentation
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
ms.openlocfilehash: 83d08b5261d6657a2bddbf494eb6f5e9ade3b065
ms.sourcegitcommit: f7ac1976d4bfa224332edd9ef2f4377a4d55a2c9
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/02/2020
ms.locfileid: "85892734"
---
# <a name="sp_syspolicy_delete_policy_category-transact-sql"></a>sp_syspolicy_delete_policy_category (Transact-SQL)
[!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

  Löscht in der richtlinienbasierten Verwaltung eine Richtlinienkategorie.  
  
 ![Symbol für Themenlink](../../database-engine/configure-windows/media/topic-link.gif "Symbol für Themenlink") [Transact-SQL-Syntaxkonventionen](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```  
  
sp_syspolicy_delete_policy_category { [ @name = ] 'name' | [ @policy_category_id = ] policy_category_id }  
```  
  
## <a name="arguments"></a>Argumente  
`[ @name = ] 'name'`Der Name der Richtlinien Kategorie. *Name ist vom Datentyp* **vom Datentyp sysname**und muss angegeben werden, wenn *policy_category_id* NULL ist.  
  
`[ @policy_category_id = ] policy_category_id`Der Bezeichner für die Richtlinien Kategorie. *policy_category_id* ist vom *Datentyp* **int**und muss angegeben werden, wenn Name NULL ist.  
  
## <a name="return-code-values"></a>Rückgabecodewerte  
 **0** (Erfolg) oder **1** (Fehler)  
  
## <a name="remarks"></a>Hinweise  
 Sie müssen sp_syspolicy_delete_policy_category im Kontext der Systemdatenbank msdb ausführen.  
  
 Sie müssen einen Wert für *Name* oder für *policy_category_id*angeben. Keiner der Werte darf NULL sein. Um diese Werte abzurufen, fragen Sie die Systemsicht msdb.dbo.syspolicy_policy_categories ab.  
  
 Um eine Richtlinienkategorie zu löschen, dürfen keine Richtlinien darauf verweisen.  
  
## <a name="permissions"></a>Berechtigungen  
 Erfordert die Mitgliedschaft in der festen Datenbankrolle PolicyAdministratorRole.  
  
> [!IMPORTANT]  
>  Mögliche Erweiterung der Anmeldeinformationen: Benutzer mit der Rolle PolicyAdministratorRole können Servertrigger erstellen und die Ausführung von Richtlinien planen. Dies kann sich auf die Arbeitsweise der [!INCLUDE[ssDE](../../includes/ssde-md.md)]-Instanz auswirken. Ein Benutzer mit der Rolle PolicyAdministratorRole kann beispielsweise eine Richtlinie erstellen, durch die das Erstellen der meisten Objekte in [!INCLUDE[ssDE](../../includes/ssde-md.md)] verhindert wird. Aufgrund dieser möglichen Erweiterung der Anmelde Informationen sollte die PolicyAdministratorRole-Rolle nur Benutzern gewährt werden, die mit dem Steuern der Konfiguration von vertraut sind [!INCLUDE[ssDE](../../includes/ssde-md.md)] .  
  
## <a name="examples"></a>Beispiele  
 Im folgenden Beispiel wird die Richtlinienkategorie "Finance" gelöscht.  
  
```  
EXEC msdb.dbo.sp_syspolicy_delete_policy_category @name = N'Finance';  
  
GO  
```  
  
## <a name="see-also"></a>Weitere Informationen  
 [Gespeicherte Prozeduren der Richtlinien basierten Verwaltung &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/policy-based-management-stored-procedures-transact-sql.md)   
 [sp_syspolicy_add_policy_category &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/sp-syspolicy-add-policy-category-transact-sql.md)   
 [sp_syspolicy_update_policy_category &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/sp-syspolicy-update-policy-category-transact-sql.md)  
  
  
