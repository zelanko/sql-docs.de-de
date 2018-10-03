---
title: Syspolicy_policy_categories (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- syspolicy_policy_categories
- syspolicy_policy_categories_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- syspolicy_policy_groups view
ms.assetid: 65f080c7-771f-4cf6-a7a0-88882c637f8d
author: VanMSFT
ms.author: vanto
manager: craigg
ms.openlocfilehash: afe9eacb2f5e42dc945505d54e420877a8f4cbca
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/01/2018
ms.locfileid: "47646498"
---
# <a name="syspolicypolicycategories-transact-sql"></a>syspolicy_policy_categories (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Zeigt eine Zeile für jede Richtlinienkategorie der richtlinienbasierten Verwaltung in der Instanz von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. In den Richtlinienkategorien können Sie Ihre Richtlinien organisieren, wenn Sie über viele Richtlinien verfügen. In der folgenden Tabelle werden die Spalten in der syspolicy_policy_groups-Sicht beschrieben.  
 
  
|Spaltenname|Datentyp|Description|  
|-----------------|---------------|-----------------|  
|policy_category_id|**int**|Bezeichner der Richtlinienkategorie.|  
|NAME|**sysname**|Name der Richtlinienkategorie.|  
|mandate_database_subscriptions|**bit**|Gibt an, ob die Richtlinienkategorie für alle Datenbanken in einer Instanz ohne ein explizites Abonnement gilt (1), oder ob die Richtlinienkategorie auf eine Datenbank unter Verwendung eines expliziten Abonnements angewendet werden muss (0).|  
  
## <a name="remarks"></a>Hinweise  
 Zeigt eine Liste der Richtliniengruppen der richtlinienbasierten Verwaltung an.  
  
## <a name="permissions"></a>Berechtigungen  
 Erfordert die Mitgliedschaft in der PolicyAdministratorRole-Rolle in der msdb-Datenbank.  
  
## <a name="see-also"></a>Siehe auch  
 [Verwalten von Servern mit der richtlinienbasierten Verwaltung](../../relational-databases/policy-based-management/administer-servers-by-using-policy-based-management.md)   
 [Sichten der richtlinienbasierten Verwaltung &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/policy-based-management-views-transact-sql.md)  
  
  
