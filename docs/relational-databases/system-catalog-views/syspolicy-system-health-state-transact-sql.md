---
title: Syspolicy_system_health_state (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- syspolicy_system_health_state_TSQL
- syspolicy_system_health_state
dev_langs:
- TSQL
helpviewer_keywords:
- syspolicy_system_health_state view
ms.assetid: 00815106-9fe4-481d-a9e1-a256101887f4
author: VanMSFT
ms.author: vanto
manager: craigg
ms.openlocfilehash: 115883fa460f370f618c9286b9529e3cf221d12c
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/01/2018
ms.locfileid: "47640308"
---
# <a name="syspolicysystemhealthstate-transact-sql"></a>syspolicy_system_health_state (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Zeigt pro Richtlinie der richtlinienbasierten Verwaltung und Zielabfrageausdruck eine Zeile an. In der syspolicy_system_health_state-Sicht können Sie den Richtlinienzustand des Servers programmgesteuert überprüfen. In der folgenden Tabelle werden die Spalten in der syspolicy_system_health_state-Sicht beschrieben.  
  
|Spaltenname|Datentyp|Description|  
|-----------------|---------------|-----------------|  
|health_state_id|**bigint**|Bezeichner des Datensatzes zum Richtlinienzustand.|  
|policy_id|**int**|Bezeichner der Richtlinie.|  
|last_run_date|**datetime**|Datum und Uhrzeit der letzten Ausführung der Richtlinie.|  
|target_query_expression_with_id|**nvarchar(400)**|Der Zielausdruck, mit Identitätsvariablen zugewiesenen Werten, der das Ziel definiert, für das die Richtlinie ausgewertet wird.|  
|target_query_expression|**nvarchar(max)**|Der Ausdruck, der das Ziel definiert, für das die Richtlinie ausgewertet wird.|  
|result|**bit**|Zustand des Ziels im Bezug auf die Richtlinie:<br /><br /> 0 = Fehler<br /><br /> 1 = Erfolg|  
  
## <a name="remarks"></a>Hinweise  
 In der Sicht syspolicy_system_health_state wird der letzte Zustand des Zielabfrageausdrucks für die einzelnen aktiven (aktivierten) Richtlinien angezeigt. Auf den [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]-Seiten Objekt-Explorer und Details zum Objekt-Explorer werden die Zustände der Richtlinien aus dieser Sicht summiert, um den kritischen Zustand anzuzeigen.  
  
## <a name="permissions"></a>Berechtigungen  
 Erfordert die Mitgliedschaft in der PolicyAdministratorRole-Rolle in der msdb-Datenbank.  
  
## <a name="see-also"></a>Siehe auch  
 [Verwalten von Servern mit der richtlinienbasierten Verwaltung](../../relational-databases/policy-based-management/administer-servers-by-using-policy-based-management.md)   
 [Sichten der richtlinienbasierten Verwaltung &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/policy-based-management-views-transact-sql.md)  
  
  
