---
title: syspolicy_policies (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- syspolicy_policies_TSQL
- syspolicy_policies
dev_langs:
- TSQL
helpviewer_keywords:
- syspolicy_policies view
ms.assetid: aecf35bb-187e-4f80-870f-48081b88974e
author: VanMSFT
ms.author: vanto
ms.openlocfilehash: 49ef90e030c2899e49adcb69e8765a57f623ace7
ms.sourcegitcommit: f7ac1976d4bfa224332edd9ef2f4377a4d55a2c9
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/02/2020
ms.locfileid: "85900580"
---
# <a name="syspolicy_policies-transact-sql"></a>syspolicy_policies (Transact-SQL)
[!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

  Zeigt eine Zeile für jede Richtlinie der Richtlinien basierten Verwaltung in der Instanz von an [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . syspolicy_policies gehört zum dbo-Schema in der msdb-Datenbank. In der folgenden Tabelle werden die Spalten in der syspolicy_policies-Sicht beschrieben.  
  
|Spaltenname|Datentyp|BESCHREIBUNG|  
|-----------------|---------------|-----------------|  
|policy_id|**int**|Bezeichner der Richtlinie.|  
|name|**sysname**|Name der Richtlinie.|  
|condition_id|**int**|ID der Bedingung, die durch diese Richtlinie erzwungen oder getestet wird.|  
|root_condition_id|**int**|Nur zur internen Verwendung.|  
|date_created|**datetime**|Datum und Uhrzeit der Erstellung der Richtlinie.|  
|execution_mode|**int**|Auswertungsmodus für die Richtlinie. Es sind folgende Werte möglich:<br /><br /> 0 = Bedarfsgesteuert<br /><br /> Dieser Modus wertet die Richtlinie aus, wenn sie vom Benutzer direkt angegeben wird.<br /><br /> 1 = Bei Änderung: Verhindern<br /><br /> Dieser automatisierte Modus verwendet DDL-Trigger, um Richtlinienverstöße zu verhindern.<br /><br /> 2 = Bei Änderung: Nur protokollieren<br /><br /> Dieser automatisierte Modus verwendet die Ereignisbenachrichtigung, um eine Richtlinie dann auszuwerten, wenn eine relevante Änderung auftritt. Die Richtlinienverstöße werden protokolliert.<br /><br /> 4 = Nach Zeitplan<br /><br /> Dieser automatisierte Modus verwendet einen [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Agentauftrag, um eine Richtlinie in regelmäßigen Abständen auszuwerten. In diesem Modus werden Richtlinienverstöße protokolliert.<br /><br /> Hinweis: der Wert 3 ist nicht möglich.|  
|policy_category|**int**|ID der Richtlinienkategorie der richtlinienbasierten Verwaltung, zu der diese Richtlinie gehört. Ist NULL, wenn sie sich in der Standardrichtliniengruppe befindet.|  
|schedule_uid|**uniqueidentifier**|Enthält die ID des Zeitplans, wenn execution_mode den Wert Nach Zeitplan aufweist. Ist andernfalls NULL.|  
|description|**nvarchar(max)**|Beschreibung der Richtlinie. Die Beschreibungsspalte ist optional und kann NULL sein.|  
|help_text|**nvarchar(4000)**|Der Linktext, der zu help_link gehört.|  
|help_link|**nvarchar (2083)**|Der zusätzliche Hilfelink, der der Richtlinie vom Richtlinienersteller zugewiesen wird.|  
|object_set_id|**int**|ID des Objektsatzes, den die Richtlinie auswertet.|  
|is_enabled|**bit**|Gibt an, ob die Richtlinie zurzeit aktiviert (1) oder deaktiviert (0) ist.|  
|job_id|**uniqueidentifier**|Enthält die ID des [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Agent-Auftrags, der die Richtlinie ausführt, wenn execution_mode den Wert Nach Zeitplan aufweist.|  
|created_by|**sysname**|Anmeldung, die die Richtlinie erstellt hat.|  
|modified_by|**sysname**|Anmeldung, die die Richtlinie zuletzt geändert hat. Ist NULL, wenn nie geändert.|  
|date_modified|**datetime**|Datum und Uhrzeit der Erstellung der Richtlinie. Ist NULL, wenn nie geändert.|  
  
## <a name="remarks"></a>Hinweise  
 Wenn Sie Probleme mit der Richtlinien basierten Verwaltung beheben, Fragen Sie die [syspolicy_conditions](../../relational-databases/system-catalog-views/syspolicy-conditions-transact-sql.md) Sicht ab, um zu bestimmen, ob die Richtlinie aktiviert ist. Diese Sicht zeigt darüber hinaus an, wer die Richtlinie erstellt oder zuletzt geändert hat.  
  
## <a name="permissions"></a>Berechtigungen  
 Erfordert die Mitgliedschaft in der PolicyAdministratorRole-Rolle in der msdb-Datenbank.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Verwalten von Servern mit der Richtlinien basierten Verwaltung](../../relational-databases/policy-based-management/administer-servers-by-using-policy-based-management.md)   
 [Sichten der richtlinienbasierten Verwaltung &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/policy-based-management-views-transact-sql.md)  
  
  
