---
title: Sys. firewall_rules (Azure SQL-Datenbank) | Microsoft-Dokumentation
ms.date: 03/26/2019
ms.prod: sql
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sys.firewall_rules
- firewall_rules
- sys.firewall_rules_TSQL
- firewall_rules_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- firewall_rules
- sys.firewall_rules
ms.assetid: 140d2cd8-9aa1-4cc5-870d-e1dbc873b3fe
author: CarlRabeler
ms.author: carlrab
manager: craigg
monikerRange: = azuresqldb-current || = sqlallproducts-allversions
ms.openlocfilehash: 5127dacf628231199c5ce5ac49fdb2377c82f270
ms.sourcegitcommit: 2db83830514d23691b914466a314dfeb49094b3c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/27/2019
ms.locfileid: "58494033"
---
# <a name="sysfirewallrules-azure-sql-database"></a>sys.firewall_rules (Azure SQL-Datenbank)
[!INCLUDE[tsql-appliesto-xxxxxx-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-xxxxxx-asdb-xxxx-xxx-md.md)]

  Gibt Informationen zu den Einstellungen der Firewall auf Serverebene im Zusammenhang mit Ihrer [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)].  
  
 Die `sys.firewall_rules` -Sicht enthält die folgenden Spalten:  
  
|Spaltenname|Datentyp|Description|  
|-----------------|---------------|-----------------|  
|id|**INT**|Der Bezeichner der Firewalleinstellung auf Serverebene.|  
|NAME|**NVARCHAR(128)**|Der ausgewählte Name, um die Firewalleinstellung auf Serverebene zu beschreiben und von anderen zu unterscheiden.|  
|start_ip_address|**VARCHAR(45)**|Die niedrigste IP-Adresse im Bereich der Firewalleinstellung auf Serverebene. IP-Adressen, die gleich oder größer dieser IP-Adresse sind, können versuchen, eine Verbindung mit dem [!INCLUDE[ssSDS](../../includes/sssds-md.md)]-Server herzustellen. Die niedrigste mögliche IP-Adresse ist `0.0.0.0`.|  
|end_ip_address|**VARCHAR(45)**|Die höchste IP-Adresse im Bereich der Firewalleinstellung auf Serverebene. IP-Adressen, die kleiner oder gleich dieser IP-Adresse sind, können versuchen, eine Verbindung mit dem [!INCLUDE[ssSDS](../../includes/sssds-md.md)]-Server herzustellen. Die höchste mögliche IP-Adresse ist `255.255.255.255`.<br /><br /> Hinweis: Windows Azure-Verbindungsversuche sind zulässig, wenn sowohl dieses Feld und die **Start_ip_address** Feld `0.0.0.0`.|  
|create_date|**DATETIME**|UTC-Datum und -Uhrzeit der Erstellung der Firewalleinstellung auf Serverebene.<br /><br /> Hinweis: UTC ist ein Akronym für die koordinierte Weltzeit (Coordinated Universal Time).|  
|modify_date|**DATETIME**|UTC-Datum und -Uhrzeit der letzten Änderung der Firewalleinstellung auf Serverebene.|  
  
## <a name="remarks"></a>Hinweise

 Gibt zurück, um Informationen über die Firewall auf Datenbankebene Einstellungen im Zusammenhang mit Ihrem Microsoft Azure SQL-Datenbank verwenden [Sys. database_firewall_rules &#40;Azure SQL-Datenbank&#41;](../../relational-databases/system-catalog-views/sys-database-firewall-rules-azure-sql-database.md).  
  
## <a name="permissions"></a>Berechtigungen

 Nur-Lese Zugriff auf diese Sicht wird für alle Benutzer mit der Berechtigung zum Herstellen einer Verbindung mit der **master** Datenbank.  
  
## <a name="see-also"></a>Siehe auch

[sp_set_firewall_rule &#40;Azure SQL-Datenbank&#41;](../../relational-databases/system-stored-procedures/sp-set-firewall-rule-azure-sql-database.md)  
[Sp_delete_firewall_rule &#40;Azure SQL-Datenbank&#41;](../../relational-databases/system-stored-procedures/sp-delete-firewall-rule-azure-sql-database.md)   
[sp_set_database_firewall_rule &#40;Azure SQL-Datenbank&#41;](../../relational-databases/system-stored-procedures/sp-set-database-firewall-rule-azure-sql-database.md)  
[Sp_delete_database_firewall_rule &#40;Azure SQL-Datenbank&#41;](../../relational-databases/system-stored-procedures/sp-delete-database-firewall-rule-azure-sql-database.md)  
[Sys. database_firewall_rules &#40;Azure SQL-Datenbank&#41;](../../relational-databases/system-catalog-views/sys-database-firewall-rules-azure-sql-database.md)  
[Konfigurieren einer Windows-Firewall für Datenbank-Engine-Zugriff](../../database-engine/configure-windows/configure-a-windows-firewall-for-database-engine-access.md)     
[Konfigurieren einer Firewall für FILESTREAM-Zugriff](../../relational-databases/blob/configure-a-firewall-for-filestream-access.md)  
[Konfigurieren einer Firewall für den Zugriff auf den Berichtsserver](../../reporting-services/report-server/configure-a-firewall-for-report-server-access.md) 
