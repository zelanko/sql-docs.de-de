---
title: sp_delete_database_firewall_rule (Azure SQL-Datenbank) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 08/04/2017
ms.service: sql-database
ms.reviewer: ''
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
monikerRange: = azuresqldb-current || = sqlallproducts-allversions
ms.openlocfilehash: 660405e7e7592557422e43655c35ec27c194aad3
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/27/2020
ms.locfileid: "68130682"
---
# <a name="sp_delete_database_firewall_rule-azure-sql-database"></a>sp_delete_database_firewall_rule (Azure SQL-Datenbank)
[!INCLUDE[tsql-appliesto-xxxxxx-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-xxxxxx-asdb-xxxx-xxx-md.md)]

  Entfernt die Firewalleinstellung auf Daten Bank [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)]Ebene aus dem. Datenbank-Firewallregeln können für die Master Datenbank und für Benutzer Datenbanken unter [!INCLUDE[ssSDS_md](../../includes/sssds-md.md)]konfiguriert und gelöscht werden.   
  
 
## <a name="syntax"></a>Syntax  
  
```    
sp_delete_database_firewall_rule [@name =] [N]'name'
[ ; ]  
```  
  
## <a name="arguments"></a>Argumente  
 `[@name =] [N]'name'`  
 Der Name der Firewalleinstellung auf Datenbankebene, die entfernt wird. *Name ist vom Datentyp* **nvarchar (128)** und hat keinen Standardwert. Der Unicode- `N` Bezeichner ist [!INCLUDE[ssSDS_md](../../includes/sssds-md.md)]optional für. 
  
## <a name="permissions"></a>Berechtigungen  
 Firewallregeln auf Datenbankebene können nur von der Prinzipal Anmeldung auf Serverebene oder einem Azure Active Directory Prinzipal, der als Administrator zugewiesen wurde, gelöscht werden.  
  
## <a name="example"></a>Beispiel  
 Im folgenden Beispiel wird die Firewalleinstellung auf Daten Bank `Example DB Setting 1`Ebene mit dem Namen entfernt.
  
```  
-- Remove database-level firewall setting  
EXECUTE sp_delete_database_firewall_rule N'Example DB Setting 1';  
  
```  
  
## <a name="see-also"></a>Weitere Informationen  
 [Azure SQL-Daten Bank Firewall](https://azure.microsoft.com/documentation/articles/sql-database-firewall-configure/)   
 [Vorgehensweise: Konfigurieren von Firewalleinstellungen (Azure SQL-Datenbank)](https://azure.microsoft.com/documentation/articles/sql-database-configure-firewall-settings/)   
 [sp_set_firewall_rule &#40;Azure SQL-Datenbank&#41;](../../relational-databases/system-stored-procedures/sp-set-firewall-rule-azure-sql-database.md)   
 [sp_set_database_firewall_rule &#40;Azure SQL-Datenbank&#41;](../../relational-databases/system-stored-procedures/sp-set-database-firewall-rule-azure-sql-database.md)   
 [sys. database_firewall_rules &#40;Azure SQL-Datenbank&#41;](../../relational-databases/system-catalog-views/sys-database-firewall-rules-azure-sql-database.md)  
  
  


