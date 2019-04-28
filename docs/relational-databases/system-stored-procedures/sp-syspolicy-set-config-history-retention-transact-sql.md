---
title: Sp_syspolicy_set_config_history_retention (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 08/09/2016
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_syspolicy_set_config_history_retention_TSQL
- sp_syspolicy_set_config_history_retention
dev_langs:
- TSQL
helpviewer_keywords:
- sp_syspolicy_set_config_history_retention
ms.assetid: 2574898a-e724-4447-b96c-ff778471339d
author: VanMSFT
ms.author: vanto
manager: craigg
ms.openlocfilehash: 4f810cc775e79da6d01a2856afb04f80756be68a
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "63000799"
---
# <a name="spsyspolicysetconfighistoryretention-transact-sql"></a>sp_syspolicy_set_config_history_retention (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Gibt die Anzahl der Tage an, wie lange der Richtlinienauswertungsverlauf für die richtlinienbasierte Verwaltung beibehalten wird.  
  
 ![Themenlinksymbol](../../database-engine/configure-windows/media/topic-link.gif "Topic link icon") [Transact-SQL Syntax Conventions (Transact-SQL-Syntaxkonventionen)](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```  
  
sp_syspolicy_set_config_history_retention [ @value = ] value  
```  
  
## <a name="arguments"></a>Argumente  
`[ @value = ] value` Ist die Anzahl der Tage, die Richtlinie der richtlinienbasierten Verwaltung Verlauf erhalten bleibt. *Wert* ist **Sqlvariant**.  
  
## <a name="return-code-values"></a>Rückgabecodewerte  
 **0** (Erfolg) oder **1** (Fehler)  
  
## <a name="remarks"></a>Hinweise  
 Sie müssen sp_syspolicy_set_config_history_retention im Kontext der Systemdatenbank msdb ausführen.  
  
 Wenn *Wert* festgelegt ist, 0 (null) der Verlauf nicht automatisch entfernt.  
  
 Um den aktuellen Wert für die Verlaufsbeibehaltung anzuzeigen, führen Sie die folgende Abfrage aus:  
  
```  
SELECT current_value FROM msdb.dbo.syspolicy_configuration  
WHERE name = 'HistoryRetentionInDays'  
```  
  
## <a name="permissions"></a>Berechtigungen  
 Erfordert die Mitgliedschaft in der festen Datenbankrolle PolicyAdministratorRole.  
  
> [!IMPORTANT]  
>  Mögliche Erweiterung der Anmeldeinformationen: Benutzer der Rolle PolicyAdministratorRole können Servertrigger erstellen und Ausführung von Richtlinien planen, die den Betrieb der Instanz von beeinflussen, können die [!INCLUDE[ssDE](../../includes/ssde-md.md)]. Ein Benutzer mit der Rolle PolicyAdministratorRole kann beispielsweise eine Richtlinie erstellen, durch die das Erstellen der meisten Objekte in [!INCLUDE[ssDE](../../includes/ssde-md.md)] verhindert wird. Aufgrund dieser möglichen Erweiterung der Anmeldeinformationen, sollte die PolicyAdministratorRole-Rolle gewährt werden nur für Benutzer, die mit der Kontrolle der Konfiguration von vertrauenswürdigen sind die [!INCLUDE[ssDE](../../includes/ssde-md.md)].  
  
## <a name="examples"></a>Beispiele  
 Im folgenden Beispiel wird die Beibehaltungsdauer für den Richtlinienauswertungsverlauf auf 28 Tage festgelegt.  
  
```  
EXEC msdb.dbo.sp_syspolicy_set_config_history_retention @value = 28;  
  
GO  
```  
  
## <a name="see-also"></a>Siehe auch  
 [Gespeicherte Prozeduren für Richtlinie der richtlinienbasierten Verwaltung &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/policy-based-management-stored-procedures-transact-sql.md)   
 [sp_syspolicy_configure &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-syspolicy-configure-transact-sql.md)  
  
  
