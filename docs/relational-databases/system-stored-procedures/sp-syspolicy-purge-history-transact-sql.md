---
title: Sp_syspolicy_purge_history (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_syspolicy_purge_history_TSQL
- sp_syspolicy_purge_history
dev_langs:
- TSQL
helpviewer_keywords:
- sp_syspolicy_purge_history
ms.assetid: 6db414e7-4946-4bd2-8264-6b490810b306
author: VanMSFT
ms.author: vanto
ms.openlocfilehash: 946ffe13439bcaf86ade71e0333d59249b1101b6
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "67997332"
---
# <a name="spsyspolicypurgehistory-transact-sql"></a>sp_syspolicy_purge_history (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Entfernt den Richtlinienauswertungsverlauf gemäß der Einstellung für das Verlaufsbeibehaltungsintervall.  
  
 ![Themenlinksymbol](../../database-engine/configure-windows/media/topic-link.gif "Topic link icon") [Transact-SQL Syntax Conventions (Transact-SQL-Syntaxkonventionen)](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```  
  
sp_syspolicy_purge_history  
```  
  
## <a name="arguments"></a>Argumente  
 Diese gespeicherte Prozedur weist keine Parameter auf.  
  
## <a name="return-code-values"></a>Rückgabecodewerte  
 **0** (Erfolg) oder **1** (Fehler)  
  
## <a name="remarks"></a>Hinweise  
 Sie müssen sp_syspolicy_purge_history im Kontext der Systemdatenbank msdb ausführen.  
  
 Sie können das Verlaufsbeibehaltungsintervall mithilfe der folgenden Abfrage anzeigen:  
  
```  
SELECT current_value  
FROM msdb.dbo.syspolicy_configuration  
WHERE name = N'HistoryRetentionInDays';  
GO  
```  
  
> [!NOTE]  
>  Wenn das Verlaufsbeibehaltungsintervall auf 0 gesetzt ist, wird der Richtlinienauswertungsverlauf nicht entfernt.  
  
## <a name="permissions"></a>Berechtigungen  
 Erfordert die Mitgliedschaft in der festen Datenbankrolle PolicyAdministratorRole.  
  
> [!IMPORTANT]  
>  Mögliche Erweiterung der Anmeldeinformationen: Benutzer der Rolle PolicyAdministratorRole können Servertrigger erstellen und Ausführung von Richtlinien planen, die den Betrieb der Instanz von beeinflussen, können die [!INCLUDE[ssDE](../../includes/ssde-md.md)]. Ein Benutzer mit der Rolle PolicyAdministratorRole kann beispielsweise eine Richtlinie erstellen, durch die das Erstellen der meisten Objekte in [!INCLUDE[ssDE](../../includes/ssde-md.md)] verhindert wird. Aufgrund dieser möglichen Erweiterung der Anmeldeinformationen, sollte die PolicyAdministratorRole-Rolle gewährt werden nur für Benutzer, die mit der Kontrolle der Konfiguration von vertrauenswürdigen sind die [!INCLUDE[ssDE](../../includes/ssde-md.md)].  
  
## <a name="examples"></a>Beispiele  
 Im folgenden Beispiel wird der Richtlinienauswertungsverlauf entfernt.  
  
```  
EXEC msdb.dbo.sp_syspolicy_purge_history;  
  
GO  
```  
  
## <a name="see-also"></a>Siehe auch  
 [Gespeicherte Prozeduren für Richtlinie der richtlinienbasierten Verwaltung &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/policy-based-management-stored-procedures-transact-sql.md)   
 [sp_syspolicy_set_config_history_retention &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-syspolicy-set-config-history-retention-transact-sql.md)   
 [sp_syspolicy_delete_policy_execution_history &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-syspolicy-delete-policy-execution-history-transact-sql.md)  
  
  
