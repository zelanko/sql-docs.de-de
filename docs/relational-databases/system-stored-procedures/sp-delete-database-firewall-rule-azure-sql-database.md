---
title: Sp_delete_database_firewall_rule (Azure SQL-Datenbank) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 08/04/2017
ms.prod: ''
ms.prod_service: sql-database
ms.reviewer: ''
ms.service: sql-database
ms.component: system-stored-procedures
ms.suite: sql
ms.technology: system-objects
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- sp_delete_database_firewall_rule
- sp_delete_database_firewall_rule_TSQL
- sys.sp_delete_database_firewall_rule
- sys.sp_delete_database_firewall_rule_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sp_delete_database_firewall_rule procedure
ms.assetid: ed295312-e586-4fc2-9e80-806b490ee7bd
author: VanMSFT
ms.author: vanto
manager: craigg
monikerRange: = azuresqldb-current || = sqlallproducts-allversions
ms.openlocfilehash: 225d5d7571e213308de337240ec8a0897f074a6a
ms.sourcegitcommit: 182b8f68bfb345e9e69547b6d507840ec8ddfd8b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/27/2018
ms.locfileid: "43037484"
---
# <a name="spdeletedatabasefirewallrule-azure-sql-database"></a>sp_delete_database_firewall_rule (Azure SQL-Datenbank)
[!INCLUDE[tsql-appliesto-xxxxxx-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-xxxxxx-asdb-xxxx-xxx-md.md)]

  Entfernt die firewalleinstellung auf Datenbankebene von Ihrer [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)]. Datenbank-Firewall-Regeln konfiguriert und für die master-Datenbank und für Benutzerdatenbanken auf gelöscht werden können, [!INCLUDE[ssSDS_md](../../includes/sssds-md.md)].   
  
 
## <a name="syntax"></a>Syntax  
  
```  
  
sp_delete_database_firewall_rule [@name =] [N]'name'
[ ; ]  
```  
  
## <a name="arguments"></a>Argumente  
 [ **@name =**] **"***Namen***"**  
 Der Name der Firewalleinstellung auf Datenbankebene, die entfernt wird. *Namen* ist **vom Datentyp nvarchar(128)** hat keinen Standardwert. Der Unicode-Bezeichner `N` ist optional für [!INCLUDE[ssSDS_md](../../includes/sssds-md.md)]. 
  
## <a name="permissions"></a>Berechtigungen  
 Nur die Server serverebenenprinzipal-Anmeldung erstellt, die im Rahmen des Bereitstellungsprozesses oder ein Azure Active Directory-Dienstprinzipal zugewiesen, wie Firewallregeln auf Datenbankebene Admin löschen zu kann.  
  
## <a name="example"></a>Beispiel  
 Im folgenden Beispiel wird die Firewall auf Datenbankebene, die Einstellung mit dem Namen `Example DB Setting 1`.
  
```  
-- Remove database-level firewall setting  
EXECUTE sp_delete_database_firewall_rule N'Example DB Setting 1';  
  
```  
  
## <a name="see-also"></a>Siehe auch  
 [Azure SQL-Datenbankfirewall](https://azure.microsoft.com/documentation/articles/sql-database-firewall-configure/)   
 [Vorgehensweise: Konfigurieren der Firewalleinstellungen (Azure SQL-Datenbank)](https://azure.microsoft.com/documentation/articles/sql-database-configure-firewall-settings/)   
 [Sp_set_firewall_rule &#40;Azure SQL-Datenbank&#41;](../../relational-databases/system-stored-procedures/sp-set-firewall-rule-azure-sql-database.md)   
 [Sp_set_database_firewall_rule &#40;Azure SQL-Datenbank&#41;](../../relational-databases/system-stored-procedures/sp-set-database-firewall-rule-azure-sql-database.md)   
 [Sys. database_firewall_rules &#40;Azure SQL-Datenbank&#41;](../../relational-databases/system-catalog-views/sys-database-firewall-rules-azure-sql-database.md)  
  
  


