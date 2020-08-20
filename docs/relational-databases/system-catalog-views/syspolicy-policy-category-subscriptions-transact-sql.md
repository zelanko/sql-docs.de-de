---
description: syspolicy_policy_category_subscriptions (Transact-SQL)
title: syspolicy_policy_category_subscriptions (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- syspolicy_policy_category_subscriptions_TSQL
- syspolicy_policy_category_subscriptions
dev_langs:
- TSQL
helpviewer_keywords:
- syspolicy_policy_group_subscriptions view
ms.assetid: b3b3a7d7-0b78-46c0-9755-045f7a5692b9
author: VanMSFT
ms.author: vanto
ms.openlocfilehash: 99f95e323b88f6932a1f3af0ed3cf72d9bed964c
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/17/2020
ms.locfileid: "88460508"
---
# <a name="syspolicy_policy_category_subscriptions-transact-sql"></a>syspolicy_policy_category_subscriptions (Transact-SQL)
[!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

  Zeigt für jedes Abonnement der richtlinienbasierten Verwaltung in der Instanz von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]eine Zeile an. Jede Zeile beschreibt ein Paar aus Ziel und Richtlinienkategorie. In der folgenden Tabelle werden die Spalten in der syspolicy_policy_group_subscriptions-Sicht beschrieben.  
  
|Spaltenname|Datentyp|BESCHREIBUNG|  
|-----------------|---------------|-----------------|  
|policy_category_subscription_id|**int**|Bezeichner des Datensatzes.|  
|target_type|**sysname**|Typ des Datenbankobjekts, das Ziel des Abonnements ist.|  
|target_object|**sysname**|Name des Zielobjekts|  
|policy_category_id|**int**|ID der Richtlinienkategorie, die auf das Ziel angewendet wird.|  
  
## <a name="remarks"></a>Bemerkungen  
 Diese Sicht zeigt die Ziele an, die für Richtlinienkategorien abonniert werden.  
  
## <a name="permissions"></a>Berechtigungen  
 Erfordert die Mitgliedschaft in der PolicyAdministratorRole-Rolle in der msdb-Datenbank.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Verwalten von Servern mit der Richtlinien basierten Verwaltung](../../relational-databases/policy-based-management/administer-servers-by-using-policy-based-management.md)   
 [Sichten der richtlinienbasierten Verwaltung &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/policy-based-management-views-transact-sql.md)  
  
  
