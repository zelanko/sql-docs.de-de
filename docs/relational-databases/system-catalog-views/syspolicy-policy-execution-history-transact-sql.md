---
title: Syspolicy_policy_execution_history (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- syspolicy_policy_execution_history_TSQL
- syspolicy_policy_execution_history
dev_langs:
- TSQL
helpviewer_keywords:
- syspolicy_policy_execution_history view
ms.assetid: b13c44a7-6d49-4d50-abe1-e657fc52bb05
author: VanMSFT
ms.author: vanto
manager: craigg
ms.openlocfilehash: 155c88f9e23a706fe7124893a8dd0c5ac5f03173
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62671791"
---
# <a name="syspolicypolicyexecutionhistory-transact-sql"></a>syspolicy_policy_execution_history (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Zeigt die folgenden Informationen an: Zeit der Ausführung der Richtlinien, Ergebnis der einzelnen Ausführungen, Details zu eventuell aufgetretenen Fehlern. In der folgenden Tabelle werden die Spalten in der syspolicy_policy_execution_history-Sicht beschrieben.  
  
|Spaltenname|Datentyp|Description|  
|-----------------|---------------|-----------------|  
|history_id|**bigint**|Bezeichner des Datensatzes. Jeder Datensatz gibt eine Richtlinie und den Zeitpunkt der Initiierung an.|  
|policy_id|**int**|Bezeichner der Richtlinie.|  
|start_date|**datetime**|Datum und Uhrzeit der Ausführung der Richtlinie.|  
|end_date|**datetime**|Zeitpunkt, zu dem die Ausführung der Richtlinie beendet wurde.|  
|result|**bit**|Gibt an, ob die Richtlinie erfolgreich oder fehlerhaft ausgeführt wurde. 0 = Fehler, 1 = Erfolgreich.|  
|exception_message|**nvarchar(max)**|Von der Ausnahme (falls aufgetreten) generierte Meldung.|  
|exception|**nvarchar(max)**|Beschreibung der Ausnahme, falls aufgetreten.|  
  
## <a name="remarks"></a>Hinweise  
 Die [syspolicy_policy_execution_history_details](../../relational-databases/system-catalog-views/syspolicy-policy-execution-history-details-transact-sql.md) -Sicht enthält zugehörige Details zu den Zielen der Richtlinie und den getesteten Bedingungsausdrücken.  
  
## <a name="permissions"></a>Berechtigungen  
 Erfordert die Mitgliedschaft in der PolicyAdministratorRole-Rolle in der msdb-Datenbank.  
  
## <a name="see-also"></a>Siehe auch  
 [Verwalten von Servern mit der richtlinienbasierten Verwaltung](../../relational-databases/policy-based-management/administer-servers-by-using-policy-based-management.md)   
 [Sichten der richtlinienbasierten Verwaltung &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/policy-based-management-views-transact-sql.md)  
  
  
