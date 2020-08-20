---
description: syspolicy_policy_execution_history (Transact-SQL)
title: syspolicy_policy_execution_history (Transact-SQL) | Microsoft-Dokumentation
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
ms.openlocfilehash: 499f67e29a9d6a4205dd04acc325bf10bc917fc2
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/17/2020
ms.locfileid: "88493814"
---
# <a name="syspolicy_policy_execution_history-transact-sql"></a>syspolicy_policy_execution_history (Transact-SQL)
[!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

  Zeigt die folgenden Informationen an: Zeit der Ausführung der Richtlinien, Ergebnis der einzelnen Ausführungen, Details zu eventuell aufgetretenen Fehlern. In der folgenden Tabelle werden die Spalten in der syspolicy_policy_execution_history-Sicht beschrieben.  
  
|Spaltenname|Datentyp|BESCHREIBUNG|  
|-----------------|---------------|-----------------|  
|history_id|**bigint**|Bezeichner des Datensatzes. Jeder Datensatz gibt eine Richtlinie und den Zeitpunkt der Initiierung an.|  
|policy_id|**int**|Bezeichner der Richtlinie.|  
|start_date|**datetime**|Datum und Uhrzeit der Ausführung der Richtlinie.|  
|end_date|**datetime**|Zeitpunkt, zu dem die Ausführung der Richtlinie beendet wurde.|  
|result|**bit**|Gibt an, ob die Richtlinie erfolgreich oder fehlerhaft ausgeführt wurde. 0 = Fehler, 1 = Erfolgreich.|  
|exception_message|**nvarchar(max)**|Von der Ausnahme (falls aufgetreten) generierte Meldung.|  
|exception|**nvarchar(max)**|Beschreibung der Ausnahme, falls aufgetreten.|  
  
## <a name="remarks"></a>Bemerkungen  
 Die [syspolicy_policy_execution_history_details](../../relational-databases/system-catalog-views/syspolicy-policy-execution-history-details-transact-sql.md) -Sicht enthält zugehörige Details zu den Zielen der Richtlinie und den getesteten Bedingungsausdrücken.  
  
## <a name="permissions"></a>Berechtigungen  
 Erfordert die Mitgliedschaft in der PolicyAdministratorRole-Rolle in der msdb-Datenbank.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Verwalten von Servern mit der Richtlinien basierten Verwaltung](../../relational-databases/policy-based-management/administer-servers-by-using-policy-based-management.md)   
 [Sichten der richtlinienbasierten Verwaltung &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/policy-based-management-views-transact-sql.md)  
  
  
