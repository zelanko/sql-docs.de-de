---
title: Sp_set_database_firewall_rule (Azure SQL-Datenbank) | Microsoft-Dokumentation
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
- sp_set_database_firewall_rule
- sp_set_database_firewall_rule_TSQL
- sys.sp_set_database_firewall_rule
- sys.sp_set_database_firewall_rule_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sp_set_database_firewall_rule
- firewall_rules, setting database rules
ms.assetid: 8f0506b6-a4ac-4e4d-91db-8077c40cb17a
author: VanMSFT
ms.author: vanto
manager: craigg
monikerRange: = azuresqldb-current || = sqlallproducts-allversions
ms.openlocfilehash: bdc27614f72f8b49027d2e39c1c81d22743a39f4
ms.sourcegitcommit: 182b8f68bfb345e9e69547b6d507840ec8ddfd8b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/27/2018
ms.locfileid: "43022684"
---
# <a name="spsetdatabasefirewallrule-azure-sql-database"></a>sp_set_database_firewall_rule (Azure SQL-Datenbank)
[!INCLUDE[tsql-appliesto-xxxxxx-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-xxxxxx-asdb-xxxx-xxx-md.md)]

  Erstellt oder aktualisiert die Firewallregeln auf Datenbankebene für Ihre [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)]. Datenbank-Firewall-Regeln konfiguriert werden können, für die **master** -Datenbank und für Benutzerdatenbanken in [!INCLUDE[ssSDS](../../includes/sssds-md.md)]. Datenbank-Firewallregeln sind besonders nützlich, wenn eigenständige Datenbankbenutzer verwenden. Weitere Informationen finden Sie unter [Eigenständige Datenbankbenutzer - machen Sie Ihre Datenbank portabel](../../relational-databases/security/contained-database-users-making-your-database-portable.md).  
  
## <a name="syntax"></a>Syntax  
  
```  
  
sp_set_database_firewall_rule [@name = ] [N]'name'  
, [@start_ip_address =] 'start_ip_address'  
, [@end_ip_address =] 'end_ip_address'
[ ; ]  
```  
  
## <a name="arguments"></a>Argumente  
 **[@name**  =] [N]'*Namen*"  
 Der verwendete Name, um die Firewalleinstellung auf Datenbankebene zu beschreiben und von anderen zu unterscheiden. *Namen* ist **vom Datentyp nvarchar(128)** hat keinen Standardwert. Der Unicode-Bezeichner `N` ist optional für [!INCLUDE[ssSDS_md](../../includes/sssds-md.md)]. 
  
 **[@start_ip_address**  =] '*Start_ip_address*"  
 Die niedrigste IP-Adresse im Bereich der Firewalleinstellung auf Datenbankebene. IP-Adressen, die gleich oder größer dieser IP-Adresse sind, können versuchen, eine Verbindung mit der [!INCLUDE[ssSDS](../../includes/sssds-md.md)]-Instanz herzustellen. Die niedrigste mögliche IP-Adresse ist `0.0.0.0`. *Start_ip_address* ist **varchar(50)-Spalte** hat keinen Standardwert.  
  
 [**@end_ip_address** =] '*End_ip_address*"  
 Die höchste IP-Adresse im Bereich der Firewalleinstellung auf Datenbankebene. IP-Adressen gleich oder kleiner als dieser versuchen kann, für die Verbindung der [!INCLUDE[ssSDS](../../includes/sssds-md.md)] Instanz. Die höchste mögliche IP-Adresse ist `255.255.255.255`. *End_ip_address* ist **varchar(50)-Spalte** hat keinen Standardwert.  
  
 In der folgende Tabelle veranschaulicht die unterstützten Argumente und Optionen in [!INCLUDE[ssSDS](../../includes/sssds-md.md)].  
  
> [!NOTE]  
>  Azure-Verbindungsversuche sind zulässig, wenn sowohl dieses Feld und die *Start_ip_address* Feld `0.0.0.0`.  
  
## <a name="remarks"></a>Hinweise  
 Die Namen der Firewalleinstellungen auf Datenbankebene für eine Datenbank müssen eindeutig sein. Wenn der Name der für die gespeicherte Prozedur bereitgestellten Firewalleinstellung auf Datenbankebene bereits in der Tabelle mit den Firewalleinstellungen auf Datenbankebene vorhanden ist, werden die Start- und End-IP-Adressen aktualisiert. Andernfalls wird eine neue Firewalleinstellung auf Datenbankebene erstellt.  
  
 Beim Hinzufügen einer firewalleinstellung auf Datenbankebene, in dem die erste und letzte IP-Adressen gleich sind `0.0.0.0`, Sie ermöglichen des Zugriffs auf Ihre Datenbank in der [!INCLUDE[ssSDS](../../includes/sssds-md.md)] Server aus allen Azure-Ressourcen. Geben Sie einen Wert für die *Namen* Parameter, mit denen Sie denken Sie daran, welchem Zweck die firewalleinstellung dient.  
  
## <a name="permissions"></a>Berechtigungen  
 Erfordert die **CONTROL**-Berechtigung für die Datenbank.  
  
## <a name="examples"></a>Beispiele  
 Der folgende Code erstellt eine Firewall auf Datenbankebene, die Einstellung `Allow Azure` ermöglicht, die Zugriff auf Ihre Datenbank von Azure.  
  
```  
-- Enable Azure connections.  
EXECUTE sp_set_database_firewall_rule N'Allow Azure', '0.0.0.0', '0.0.0.0';  
  
```  
  
 Der folgende Code erstellt eine Firewall auf Datenbankebene, die Einstellung `Example DB Setting 1` nur die IP-Adresse `0.0.0.4`. Anschließend wird die `sp_set_database firewall_rule` gespeicherte Prozedur erneut aufgerufen, um die End-IP-Adresse zu aktualisieren `0.0.0.6`, Firewall-Einstellungen. Erstellt einen Bereich der IP-Adressen ermöglichen `0.0.0.4`, `0.0.0.5`, und `0.0.0.6` Zugriff auf die Datenbank.
  
```  
-- Create database-level firewall setting for only IP 0.0.0.4  
EXECUTE sp_set_database_firewall_rule N'Example DB Setting 1', '0.0.0.4', '0.0.0.4';  
  
-- Update database-level firewall setting to create a range of allowed IP addresses
EXECUTE sp_set_database_firewall_rule N'Example DB Setting 1', '0.0.0.4', '0.0.0.6';  
  
```  
  
## <a name="see-also"></a>Siehe auch  
 [Azure SQL-Datenbankfirewall](https://azure.microsoft.com/documentation/articles/sql-database-firewall-configure/)   
 [Vorgehensweise: Konfigurieren der Firewalleinstellungen (Azure SQL-Datenbank)](https://azure.microsoft.com/documentation/articles/sql-database-configure-firewall-settings/)   
 [Sp_set_firewall_rule &#40;Azure SQL-Datenbank&#41;](../../relational-databases/system-stored-procedures/sp-set-firewall-rule-azure-sql-database.md)   
 [Sp_delete_database_firewall_rule &#40;Azure SQL-Datenbank&#41;](../../relational-databases/system-stored-procedures/sp-delete-database-firewall-rule-azure-sql-database.md)   
 [Sys. database_firewall_rules &#40;Azure SQL-Datenbank&#41;](../../relational-databases/system-catalog-views/sys-database-firewall-rules-azure-sql-database.md)  
  
  
