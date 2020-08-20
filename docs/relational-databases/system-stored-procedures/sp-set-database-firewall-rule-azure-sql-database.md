---
description: sp_set_database_firewall_rule (Azure SQL-Datenbank)
title: sp_set_database_firewall_rule
titleSuffix: Azure SQL Database
ms.date: 08/04/2017
ms.service: sql-database
ms.prod_service: sql-database
ms.reviewer: ''
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
monikerRange: = azuresqldb-current || = sqlallproducts-allversions
ms.custom: seo-dt-2019
ms.openlocfilehash: b43c386f803c1d9fea8a1e7645d1764ece3a7eef
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/17/2020
ms.locfileid: "88493033"
---
# <a name="sp_set_database_firewall_rule-azure-sql-database"></a>sp_set_database_firewall_rule (Azure SQL-Datenbank)
[!INCLUDE[Azure SQL Database Azure SQL Managed Instance](../../includes/applies-to-version/asdb-asdbmi.md)]

  Erstellt oder aktualisiert die Firewallregeln auf Datenbankebene für den [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)] . Datenbank-Firewallregeln können für die **Master** Datenbank und für Benutzer Datenbanken unter konfiguriert werden [!INCLUDE[ssSDS](../../includes/sssds-md.md)] . Datenbank-Firewallregeln sind besonders nützlich, wenn eigenständige Datenbankbenutzer verwendet werden. Weitere Informationen finden Sie unter [Eigenständige Datenbankbenutzer - machen Sie Ihre Datenbank portabel](../../relational-databases/security/contained-database-users-making-your-database-portable.md).  
  
## <a name="syntax"></a>Syntax  
  
```  
  
sp_set_database_firewall_rule [@name = ] [N]'name'  
, [@start_ip_address =] 'start_ip_address'  
, [@end_ip_address =] 'end_ip_address'
[ ; ]  
```  
  
## <a name="arguments"></a>Argumente  
`[ @name = ] [N]'name'` Der Name, mit dem die Firewalleinstellung auf Datenbankebene beschrieben und unterschieden wird. *Name ist vom Datentyp* **nvarchar (128)** und hat keinen Standardwert. Der Unicode-Bezeichner `N` ist optional für [!INCLUDE[ssSDS_md](../../includes/sssds-md.md)] . 
  
`[ @start_ip_address = ] 'start_ip_address'` Die niedrigste IP-Adresse im Bereich der Firewalleinstellung auf Datenbankebene. IP-Adressen, die gleich oder größer dieser IP-Adresse sind, können versuchen, eine Verbindung mit der [!INCLUDE[ssSDS](../../includes/sssds-md.md)] -Instanz herzustellen. Die niedrigste mögliche IP-Adresse ist `0.0.0.0`. *start_ip_address* ist vom Datentyp **varchar (50)** und hat keinen Standardwert.  
  
`[ @end_ip_address = ] 'end_ip_address'` Die höchste IP-Adresse im Bereich der Firewalleinstellung auf Datenbankebene. IP-Adressen, die kleiner oder gleich dieser IP-Adresse sind, können versuchen, eine Verbindung mit der [!INCLUDE[ssSDS](../../includes/sssds-md.md)] -Instanz herzustellen. Die höchste mögliche IP-Adresse ist `255.255.255.255`. *end_ip_address* ist vom Datentyp **varchar (50)** und hat keinen Standardwert.  
  
 In der folgenden Tabelle werden die unterstützten Argumente und Optionen in veranschaulicht [!INCLUDE[ssSDS](../../includes/sssds-md.md)] .  
  
> [!NOTE]  
>  Azure-Verbindungsversuche sind zulässig, wenn sowohl dieses Feld als auch das *start_ip_address* Feld gleich sind `0.0.0.0` .  
  
## <a name="remarks"></a>Bemerkungen  
 Die Namen der Firewalleinstellungen auf Datenbankebene für eine Datenbank müssen eindeutig sein. Wenn der Name der für die gespeicherte Prozedur bereitgestellten Firewalleinstellung auf Datenbankebene bereits in der Tabelle mit den Firewalleinstellungen auf Datenbankebene vorhanden ist, werden die Start- und End-IP-Adressen aktualisiert. Andernfalls wird eine neue Firewalleinstellung auf Datenbankebene erstellt.  
  
 Wenn Sie eine Firewalleinstellung auf Datenbankebene hinzufügen, bei der die Start-und End-IP-Adressen gleich sind `0.0.0.0` , aktivieren Sie den Zugriff auf die Datenbank auf dem [!INCLUDE[ssSDS](../../includes/sssds-md.md)] Server aus einer beliebigen Azure-Ressource. Geben Sie einen Wert für den *Name* -Parameter an, der Ihnen hilft, die Firewalleinstellung zu merken.  
  
## <a name="permissions"></a>Berechtigungen  
 Erfordert die **CONTROL**-Berechtigung für die Datenbank.  
  
## <a name="examples"></a>Beispiele  
 Im folgenden Code wird eine Firewalleinstellung auf Datenbankebene mit der Bezeichnung `Allow Azure` erstellt, durch die der Zugriff auf die Datenbank durch Azure ermöglicht wird:  
  
```  
-- Enable Azure connections.  
EXECUTE sp_set_database_firewall_rule N'Allow Azure', '0.0.0.0', '0.0.0.0';  
  
```  
  
 Der folgende Code erstellt eine Firewalleinstellung auf Datenbankebene namens `Example DB Setting 1` nur für die IP-Adresse `0.0.0.4`. Anschließend wird die `sp_set_database firewall_rule` gespeicherte Prozedur erneut aufgerufen, um die End-IP-Adresse `0.0.0.6` in dieser Firewalleinstellung auf zu aktualisieren. Dadurch wird ein Bereich erstellt, der `0.0.0.4` `0.0.0.5` `0.0.0.6` den Zugriff auf die Datenbank durch IP-Adressen, und ermöglicht.
  
```  
-- Create database-level firewall setting for only IP 0.0.0.4  
EXECUTE sp_set_database_firewall_rule N'Example DB Setting 1', '0.0.0.4', '0.0.0.4';  
  
-- Update database-level firewall setting to create a range of allowed IP addresses
EXECUTE sp_set_database_firewall_rule N'Example DB Setting 1', '0.0.0.4', '0.0.0.6';  
  
```  
  
## <a name="see-also"></a>Weitere Informationen  
 [Azure SQL-Daten Bank Firewall](https://azure.microsoft.com/documentation/articles/sql-database-firewall-configure/)   
 [Vorgehensweise: Konfigurieren von Firewalleinstellungen (Azure SQL-Datenbank)](https://azure.microsoft.com/documentation/articles/sql-database-configure-firewall-settings/)   
 [sp_set_firewall_rule &#40;Azure SQL-Datenbank&#41;](../../relational-databases/system-stored-procedures/sp-set-firewall-rule-azure-sql-database.md)   
 [sp_delete_database_firewall_rule &#40;Azure SQL-Datenbank&#41;](../../relational-databases/system-stored-procedures/sp-delete-database-firewall-rule-azure-sql-database.md)   
 [sys. database_firewall_rules &#40;Azure SQL-Datenbank&#41;](../../relational-databases/system-catalog-views/sys-database-firewall-rules-azure-sql-database.md)  
  
  
