---
description: sp_syspolicy_rename_condition (Transact-SQL)
title: sp_syspolicy_rename_condition (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_syspolicy_rename_condition
- sp_syspolicy_rename_condition_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sp_syspolicy_rename_condition
ms.assetid: d9f3f9b1-701b-4fce-9b42-c282656caf84
author: VanMSFT
ms.author: vanto
ms.openlocfilehash: 1df9ab11c50340b75d51481822f4a8925df34a51
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/17/2020
ms.locfileid: "88485627"
---
# <a name="sp_syspolicy_rename_condition-transact-sql"></a>sp_syspolicy_rename_condition (Transact-SQL)
[!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

  Benennt in der richtlinienbasierten Verwaltung eine vorhandene Bedingung um.  
  
 ![Symbol für Themenlink](../../database-engine/configure-windows/media/topic-link.gif "Symbol für Themenlink") [Transact-SQL-Syntaxkonventionen](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```  
  
sp_syspolicy_rename_condition { [ @name = ] 'name' | [ @condition_id = ] condition_id }  
    , [ @new_name = ] 'new_name'  
```  
  
## <a name="arguments"></a>Argumente  
`[ @name = ] 'name'` Der Name der Bedingung, die Sie umbenennen möchten. *Name ist vom Datentyp* **vom Datentyp sysname**und muss angegeben werden, wenn *condition_id* NULL ist.  
  
`[ @condition_id = ] condition_id` Der Bezeichner für die Bedingung, die Sie umbenennen möchten. *condition_id* ist vom *Datentyp* **int**und muss angegeben werden, wenn Name NULL ist.  
  
`[ @new_name = ] 'new_name'` Der neue Name der Bedingung. *new_name* ist vom **Datentyp vom Datentyp sysname**und ist erforderlich. Darf nicht NULL und keine leere Zeichenfolge sein.  
  
## <a name="return-code-values"></a>Rückgabecodewerte  
 **0** (Erfolg) oder **1** (Fehler)  
  
## <a name="remarks"></a>Bemerkungen  
 Sie müssen sp_syspolicy_rename_condition im Kontext der Systemdatenbank msdb ausführen.  
  
 Sie müssen einen Wert für " *Name* " oder " *condition_id*" angeben. Keiner der Werte darf NULL sein. Um diese Werte abzurufen, fragen Sie die Systemsicht msdb.dbo.syspolicy_conditions ab.  
  
## <a name="permissions"></a>Berechtigungen  
 Erfordert die Mitgliedschaft in der festen Datenbankrolle PolicyAdministratorRole.  
  
> [!IMPORTANT]  
>  Mögliche Erweiterung der Anmeldeinformationen: Benutzer mit der Rolle PolicyAdministratorRole können Servertrigger erstellen und die Ausführung von Richtlinien planen. Dies kann sich auf die Arbeitsweise der [!INCLUDE[ssDE](../../includes/ssde-md.md)]-Instanz auswirken. Ein Benutzer mit der Rolle PolicyAdministratorRole kann beispielsweise eine Richtlinie erstellen, durch die das Erstellen der meisten Objekte in [!INCLUDE[ssDE](../../includes/ssde-md.md)] verhindert wird. Aufgrund dieser möglichen Erweiterung der Anmelde Informationen sollte die PolicyAdministratorRole-Rolle nur Benutzern gewährt werden, die mit dem Steuern der Konfiguration von vertraut sind [!INCLUDE[ssDE](../../includes/ssde-md.md)] .  
  
## <a name="examples"></a>Beispiele  
 Im folgenden Beispiel wird die Bedingung "Change Tracking Enabled" umbenannt.  
  
```  
EXEC msdb.dbo.sp_syspolicy_rename_condition @name = N'Change Tracking Enabled'  
, @new_name = N'Verify Change Tracking Enabled';  
  
GO  
```  
  
## <a name="see-also"></a>Siehe auch  
 [Gespeicherte Prozeduren der Richtlinien basierten Verwaltung &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/policy-based-management-stored-procedures-transact-sql.md)  
  
  
