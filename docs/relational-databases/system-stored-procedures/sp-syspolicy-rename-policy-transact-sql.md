---
title: sp_syspolicy_rename_policy (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 08/09/2016
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_syspolicy_rename_policy_TSQL
- sp_syspolicy_rename_policy
dev_langs:
- TSQL
helpviewer_keywords:
- sp_syspolicy_rename_policy
ms.assetid: ce2b07f5-23b1-4f49-8e7b-c18cf3f3d45b
author: VanMSFT
ms.author: vanto
ms.openlocfilehash: e157090ba5fb9b6c3c9da7fb88d0aa0612d2f727
ms.sourcegitcommit: f7ac1976d4bfa224332edd9ef2f4377a4d55a2c9
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/02/2020
ms.locfileid: "85892694"
---
# <a name="sp_syspolicy_rename_policy-transact-sql"></a>sp_syspolicy_rename_policy (Transact-SQL)
[!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

  Benennt in der richtlinienbasierten Verwaltung eine vorhandene Richtlinie um.  
  
  
 ![Symbol für Themenlink](../../database-engine/configure-windows/media/topic-link.gif "Symbol für Themenlink") [Transact-SQL-Syntaxkonventionen](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```  
  
sp_syspolicy_rename_policy { [ @name = ] 'name' | [ @policy_id = ] policy_id }  
    , [ @new_name = ] 'new_name'  
```  
  
## <a name="arguments"></a>Argumente  
`[ @name = ] 'name'`Der Name der Richtlinie, die Sie umbenennen möchten. *Name ist vom Datentyp* **vom Datentyp sysname**und muss angegeben werden, wenn *policy_id* NULL ist.  
  
`[ @policy_id = ] policy_id`Der Bezeichner für die Richtlinie, die Sie umbenennen möchten. *policy_id* ist vom *Datentyp* **int**und muss angegeben werden, wenn Name NULL ist.  
  
`[ @new_name = ] 'new_name'`Der neue Name für die Richtlinie. *new_name* ist vom **Datentyp vom Datentyp sysname**und ist erforderlich. Darf nicht NULL und keine leere Zeichenfolge sein.  
  
## <a name="return-code-values"></a>Rückgabecodewerte  
 **0** (Erfolg) oder **1** (Fehler)  
  
## <a name="remarks"></a>Hinweise  
 Sie müssen sp_syspolicy_rename_policy im Kontext der Systemdatenbank msdb ausführen.  
  
 Sie müssen einen Wert für " *Name* " oder " *policy_id*" angeben. Keiner der Werte darf NULL sein. Um diese Werte abzurufen, fragen Sie die Systemsicht msdb.dbo.syspolicy_policies ab.  
  
## <a name="permissions"></a>Berechtigungen  
 Erfordert die Mitgliedschaft in der festen Datenbankrolle PolicyAdministratorRole.  
  
> [!IMPORTANT]  
>  Mögliche Erweiterung der Anmeldeinformationen: Benutzer mit der Rolle PolicyAdministratorRole können Servertrigger erstellen und die Ausführung von Richtlinien planen. Dies kann sich auf die Arbeitsweise der [!INCLUDE[ssDE](../../includes/ssde-md.md)]-Instanz auswirken. Ein Benutzer mit der Rolle PolicyAdministratorRole kann beispielsweise eine Richtlinie erstellen, durch die das Erstellen der meisten Objekte in [!INCLUDE[ssDE](../../includes/ssde-md.md)] verhindert wird. Aufgrund dieser möglichen Erweiterung der Anmelde Informationen sollte die PolicyAdministratorRole-Rolle nur Benutzern gewährt werden, die mit dem Steuern der Konfiguration von vertraut sind [!INCLUDE[ssDE](../../includes/ssde-md.md)] .  
  
## <a name="examples"></a>Beispiele  
 Im folgenden Beispiel wird die Richtlinie "Test Policy 1" in "Test Policy 2" umbenannt.  
  
```  
EXEC msdb.dbo.sp_syspolicy_rename_policy @name = N'Test Policy 1'  
, @new_name = N'Test Policy 2';  
  
GO  
```  
  
## <a name="see-also"></a>Weitere Informationen  
 [Gespeicherte Prozeduren der Richtlinien basierten Verwaltung &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/policy-based-management-stored-procedures-transact-sql.md)  
  
  
