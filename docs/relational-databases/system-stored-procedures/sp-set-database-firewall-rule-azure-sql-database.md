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
ms.openlocfilehash: 2a465e03c3b77b8d05437fa0cfaf3354434ce973
ms.sourcegitcommit: f688a37bb6deac2e5b7730344165bbe2c57f9b9c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/08/2019
ms.locfileid: "73843854"
---
# <a name="sp_set_database_firewall_rule-azure-sql-database"></a>sp_set_database_firewall_rule (Azure SQL-Datenbank)
[!INCLUDE[tsql-appliesto-xxxxxx-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-xxxxxx-asdb-xxxx-xxx-md.md)]

  Erstellt oder aktualisiert die Firewallregeln auf Datenbankebene für Ihre [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)]. Datenbank-Firewallregeln können für die **Master** Datenbank und für Benutzer Datenbanken auf [!INCLUDE[ssSDS](../../includes/sssds-md.md)]konfiguriert werden. Datenbank-Firewallregeln sind besonders nützlich, wenn eigenständige Datenbankbenutzer verwendet werden. Weitere Informationen finden Sie unter [Eigenständige Datenbankbenutzer – machen Sie Ihre Datenbank portabel](../../relational-databases/security/contained-database-users-making-your-database-portable.md).  
  
## <a name="syntax"></a>Syntax  
  
```  
  
sp_set_database_firewall_rule [@name = ] [N]'name'  
, [@start_ip_address =] 'start_ip_address'  
, [@end_ip_address =] 'end_ip_address'
[ ; ]  
```  
  
## <a name="arguments"></a>Argumente  
 **[@name** =] [N] '*Name*'  
 Der verwendete Name, um die Firewalleinstellung auf Datenbankebene zu beschreiben und von anderen zu unterscheiden. *Name ist vom Datentyp* **nvarchar (128)** und hat keinen Standardwert. Der Unicode-Bezeichner `N` ist für [!INCLUDE[ssSDS_md](../../includes/sssds-md.md)]optional. 
  
 **[@start_ip_address** =] "*start_ip_address*"  
 Die niedrigste IP-Adresse im Bereich der Firewalleinstellung auf Datenbankebene. IP-Adressen, die gleich oder größer dieser IP-Adresse sind, können versuchen, eine Verbindung mit der [!INCLUDE[ssSDS](../../includes/sssds-md.md)] -Instanz herzustellen. Die niedrigste mögliche IP-Adresse ist `0.0.0.0`. *start_ip_address* ist vom Datentyp **varchar (50)** und hat keinen Standardwert.  
  
 [ **@end_ip_address** =] "*end_ip_address*"  
 Die höchste IP-Adresse im Bereich der Firewalleinstellung auf Datenbankebene. IP-Adressen, die kleiner oder gleich dieser IP-Adresse sind, können versuchen, eine Verbindung mit der [!INCLUDE[ssSDS](../../includes/sssds-md.md)] -Instanz herzustellen. Die höchste mögliche IP-Adresse ist `255.255.255.255`. *end_ip_address* ist vom Datentyp **varchar (50)** und hat keinen Standardwert.  
  
 In der folgenden Tabelle werden die unterstützten Argumente und Optionen in [!INCLUDE[ssSDS](../../includes/sssds-md.md)]veranschaulicht.  
  
> [!NOTE]  
>  Azure-Verbindungsversuche sind zulässig, wenn sowohl dieses Feld als auch das *start_ip_address* Feld `0.0.0.0`entsprechen.  
  
## <a name="remarks"></a>Hinweise  
 Die Namen der Firewalleinstellungen auf Datenbankebene für eine Datenbank müssen eindeutig sein. Wenn der Name der für die gespeicherte Prozedur bereitgestellten Firewalleinstellung auf Datenbankebene bereits in der Tabelle mit den Firewalleinstellungen auf Datenbankebene vorhanden ist, werden die Start- und End-IP-Adressen aktualisiert. Andernfalls wird eine neue Firewalleinstellung auf Datenbankebene erstellt.  
  
 Wenn Sie eine Firewalleinstellung auf Datenbankebene hinzufügen, bei der die Start-und die End-IP-Adresse `0.0.0.0`entsprechen, aktivieren Sie den Zugriff auf die Datenbank auf dem [!INCLUDE[ssSDS](../../includes/sssds-md.md)] Server aus jeder beliebigen Azure-Ressource. Geben Sie einen Wert für den *Name* -Parameter an, der Ihnen hilft, die Firewalleinstellung zu merken.  
  
## <a name="permissions"></a>Berechtigungen  
 Erfordert die **CONTROL**-Berechtigung für die Datenbank.  
  
## <a name="examples"></a>Beispiele  
 Mit dem folgenden Code wird eine Firewalleinstellung auf Datenbankebene namens `Allow Azure` erstellt, die den Zugriff auf Ihre Datenbank aus Azure ermöglicht.  
  
```  
-- Enable Azure connections.  
EXECUTE sp_set_database_firewall_rule N'Allow Azure', '0.0.0.0', '0.0.0.0';  
  
```  
  
 Der folgende Code erstellt eine Firewalleinstellung auf Datenbankebene namens `Example DB Setting 1` nur für die IP-Adresse `0.0.0.4`. Anschließend wird die gespeicherte Prozedur `sp_set_database firewall_rule` erneut aufgerufen, um die End-IP-Adresse auf `0.0.0.6`in dieser Firewalleinstellung zu aktualisieren. Dadurch wird ein Bereich erstellt, der IP-Adressen `0.0.0.4`, `0.0.0.5`und `0.0.0.6` für den Zugriff auf die Datenbank zulässt.
  
```  
-- Create database-level firewall setting for only IP 0.0.0.4  
EXECUTE sp_set_database_firewall_rule N'Example DB Setting 1', '0.0.0.4', '0.0.0.4';  
  
-- Update database-level firewall setting to create a range of allowed IP addresses
EXECUTE sp_set_database_firewall_rule N'Example DB Setting 1', '0.0.0.4', '0.0.0.6';  
  
```  
  
## <a name="see-also"></a>Siehe auch  
 Firewall-  für [Azure SQL-Datenbank](https://azure.microsoft.com/documentation/articles/sql-database-firewall-configure/)  
 Vorgehens [Weise: Konfigurieren von Firewalleinstellungen (Azure SQL-Datenbank)](https://azure.microsoft.com/documentation/articles/sql-database-configure-firewall-settings/)   
 [sp_set_firewall_rule &#40;von Azure SQL&#41; -Datenbank](../../relational-databases/system-stored-procedures/sp-set-firewall-rule-azure-sql-database.md)   
 [sp_delete_database_firewall_rule &#40;von Azure SQL&#41; -Datenbank](../../relational-databases/system-stored-procedures/sp-delete-database-firewall-rule-azure-sql-database.md)   
 [sys. database_firewall_rules &#40;Azure SQL-Datenbank&#41;](../../relational-databases/system-catalog-views/sys-database-firewall-rules-azure-sql-database.md)  
  
  
