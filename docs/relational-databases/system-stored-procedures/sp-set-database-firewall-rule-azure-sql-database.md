---
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
ms.openlocfilehash: dfe41ee68412414df24bc7f0bd583bbb0109b3db
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/27/2020
ms.locfileid: "74055087"
---
# <a name="sp_set_database_firewall_rule-azure-sql-database"></a>sp_set_database_firewall_rule (Azure SQL-Datenbank)
[!INCLUDE[tsql-appliesto-xxxxxx-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-xxxxxx-asdb-xxxx-xxx-md.md)]

  Erstellt oder aktualisiert die Firewallregeln auf Datenbankebene [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)]für den. Datenbank-Firewallregeln können für die **Master** Datenbank und für Benutzer Datenbanken unter [!INCLUDE[ssSDS](../../includes/sssds-md.md)]konfiguriert werden. Datenbank-Firewallregeln sind besonders nützlich, wenn eigenständige Datenbankbenutzer verwendet werden. Weitere Informationen finden Sie unter [Eigenständige Datenbankbenutzer - machen Sie Ihre Datenbank portabel](../../relational-databases/security/contained-database-users-making-your-database-portable.md).  
  
## <a name="syntax"></a>Syntax  
  
```  
  
sp_set_database_firewall_rule [@name = ] [N]'name'  
, [@start_ip_address =] 'start_ip_address'  
, [@end_ip_address =] 'end_ip_address'
[ ; ]  
```  
  
## <a name="arguments"></a>Argumente  
`[ @name = ] [N]'name'`Der Name, mit dem die Firewalleinstellung auf Datenbankebene beschrieben und unterschieden wird. *Name ist vom Datentyp* **nvarchar (128)** und hat keinen Standardwert. Der Unicode- `N` Bezeichner ist [!INCLUDE[ssSDS_md](../../includes/sssds-md.md)]optional für. 
  
`[ @start_ip_address = ] 'start_ip_address'`Die niedrigste IP-Adresse im Bereich der Firewalleinstellung auf Datenbankebene. IP-Adressen, die gleich oder größer dieser IP-Adresse sind, können versuchen, eine Verbindung mit der [!INCLUDE[ssSDS](../../includes/sssds-md.md)] -Instanz herzustellen. Die niedrigste mögliche IP-Adresse ist `0.0.0.0`. *start_ip_address* ist vom Datentyp **varchar (50)** und hat keinen Standardwert.  
  
`[ @end_ip_address = ] 'end_ip_address'`Die höchste IP-Adresse im Bereich der Firewalleinstellung auf Datenbankebene. IP-Adressen, die kleiner oder gleich dieser IP-Adresse sind, können versuchen, eine Verbindung mit der [!INCLUDE[ssSDS](../../includes/sssds-md.md)] -Instanz herzustellen. Die höchste mögliche IP-Adresse ist `255.255.255.255`. *end_ip_address* ist vom Datentyp **varchar (50)** und hat keinen Standardwert.  
  
 In der folgenden Tabelle werden die unterstützten Argumente und [!INCLUDE[ssSDS](../../includes/sssds-md.md)]Optionen in veranschaulicht.  
  
> [!NOTE]  
>  Azure-Verbindungsversuche sind zulässig, wenn sowohl dieses Feld *start_ip_address* als auch das `0.0.0.0`start_ip_address Feld gleich sind.  
  
## <a name="remarks"></a>Bemerkungen  
 Die Namen der Firewalleinstellungen auf Datenbankebene für eine Datenbank müssen eindeutig sein. Wenn der Name der für die gespeicherte Prozedur bereitgestellten Firewalleinstellung auf Datenbankebene bereits in der Tabelle mit den Firewalleinstellungen auf Datenbankebene vorhanden ist, werden die Start- und End-IP-Adressen aktualisiert. Andernfalls wird eine neue Firewalleinstellung auf Datenbankebene erstellt.  
  
 Wenn Sie eine Firewalleinstellung auf Datenbankebene hinzufügen `0.0.0.0`, bei der die Start-und End-IP-Adressen gleich sind, aktivieren [!INCLUDE[ssSDS](../../includes/sssds-md.md)] Sie den Zugriff auf die Datenbank auf dem Server aus einer beliebigen Azure-Ressource. Geben Sie einen Wert für den *Name* -Parameter an, der Ihnen hilft, die Firewalleinstellung zu merken.  
  
## <a name="permissions"></a>Berechtigungen  
 Erfordert die **CONTROL**-Berechtigung für die Datenbank.  
  
## <a name="examples"></a>Beispiele  
 Im folgenden Code wird eine Firewalleinstellung auf Datenbankebene mit der Bezeichnung `Allow Azure` erstellt, durch die der Zugriff auf die Datenbank durch Azure ermöglicht wird:  
  
```  
-- Enable Azure connections.  
EXECUTE sp_set_database_firewall_rule N'Allow Azure', '0.0.0.0', '0.0.0.0';  
  
```  
  
 Der folgende Code erstellt eine Firewalleinstellung auf Datenbankebene namens `Example DB Setting 1` nur für die IP-Adresse `0.0.0.4`. Anschließend wird die `sp_set_database firewall_rule` gespeicherte Prozedur erneut aufgerufen, um die End-IP-Adresse `0.0.0.6`in dieser Firewalleinstellung auf zu aktualisieren. Dadurch wird ein Bereich erstellt, der den `0.0.0.4`Zugriff `0.0.0.5`auf die `0.0.0.6` Datenbank durch IP-Adressen, und ermöglicht.
  
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
  
  
