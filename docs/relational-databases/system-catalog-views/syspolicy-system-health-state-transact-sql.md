---
title: syspolicy_system_health_state (Transact-SQL) | Microsoft-Dokumentation
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
ms.openlocfilehash: 47701075fd3c650870f2ce81b021fe7c8910b26e
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "68110904"
---
# <a name="syspolicy_system_health_state-transact-sql"></a>syspolicy_system_health_state (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Zeigt pro Richtlinie der richtlinienbasierten Verwaltung und Zielabfrageausdruck eine Zeile an. In der syspolicy_system_health_state-Sicht können Sie den Richtlinienzustand des Servers programmgesteuert überprüfen. In der folgenden Tabelle werden die Spalten in der syspolicy_system_health_state-Sicht beschrieben.  
  
|Spaltenname|Datentyp|BESCHREIBUNG|  
|-----------------|---------------|-----------------|  
|health_state_id|**BIGINT**|Bezeichner des Datensatzes zum Richtlinienzustand.|  
|policy_id|**int**|Bezeichner der Richtlinie.|  
|last_run_date|**datetime**|Datum und Uhrzeit der letzten Ausführung der Richtlinie.|  
|target_query_expression_with_id|**nvarchar (400)**|Der Zielausdruck, mit Identitätsvariablen zugewiesenen Werten, der das Ziel definiert, für das die Richtlinie ausgewertet wird.|  
|target_query_expression|**nvarchar(max)**|Der Ausdruck, der das Ziel definiert, für das die Richtlinie ausgewertet wird.|  
|result|**bit**|Zustand des Ziels im Bezug auf die Richtlinie:<br /><br /> 0 = Fehler<br /><br /> 1 = Erfolg|  
  
## <a name="remarks"></a>Bemerkungen  
 In der Sicht syspolicy_system_health_state wird der letzte Zustand des Zielabfrageausdrucks für die einzelnen aktiven (aktivierten) Richtlinien angezeigt. Auf den [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] -Seiten Objekt-Explorer und Details zum Objekt-Explorer werden die Zustände der Richtlinien aus dieser Sicht summiert, um den kritischen Zustand anzuzeigen.  
  
## <a name="permissions"></a>Berechtigungen  
 Erfordert die Mitgliedschaft in der PolicyAdministratorRole-Rolle in der msdb-Datenbank.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Verwalten von Servern mit der richtlinienbasierten Verwaltung](../../relational-databases/policy-based-management/administer-servers-by-using-policy-based-management.md)   
 [Sichten der Richtlinien basierten Verwaltung &#40;Transact-SQL-&#41;](../../relational-databases/system-catalog-views/policy-based-management-views-transact-sql.md)  
  
  
