---
title: Sys. firewall_rules (Azure SQL-Datenbank) | Microsoft-Dokumentation
ms.date: 03/14/2017
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
ms.openlocfilehash: 6901ac9e301906569a54e763ecd213602ec1410c
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/01/2018
ms.locfileid: "47705488"
---
# <a name="sysfirewallrules-azure-sql-database"></a>sys.firewall_rules (Azure SQL-Datenbank)
[!INCLUDE[tsql-appliesto-xxxxxx-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-xxxxxx-asdb-xxxx-xxx-md.md)]

  Gibt Informationen zu den Einstellungen der Firewall auf Serverebene im Zusammenhang mit Ihrer [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)].  
  
 Die `sys.firewall_rules` -Ansicht enthält die folgenden Spalten:  
  
|Spaltenname|Datentyp|Description|  
|-----------------|---------------|-----------------|  
|id|**INT**|Der Bezeichner der Firewalleinstellung auf Serverebene.|  
|NAME|**VOM DATENTYP NVARCHAR(128)**|Der ausgewählte Name, um die Firewalleinstellung auf Serverebene zu beschreiben und von anderen zu unterscheiden.|  
|start_ip_address|**VARCHAR(50)-SPALTE**|Die niedrigste IP-Adresse im Bereich der Firewalleinstellung auf Serverebene. IP-Adressen, die gleich oder größer dieser IP-Adresse sind, können versuchen, eine Verbindung mit dem [!INCLUDE[ssSDS](../../includes/sssds-md.md)]-Server herzustellen. Die niedrigste mögliche IP-Adresse ist `0.0.0.0`.|  
|end_ip_address|**VARCHAR(50)-SPALTE**|Die höchste IP-Adresse im Bereich der Firewalleinstellung auf Serverebene. IP-Adressen, die kleiner oder gleich dieser IP-Adresse sind, können versuchen, eine Verbindung mit dem [!INCLUDE[ssSDS](../../includes/sssds-md.md)]-Server herzustellen. Die höchste mögliche IP-Adresse ist `255.255.255.255`.<br /><br /> Hinweis: Windows Azure-Verbindungsversuche sind zulässig, wenn sowohl dieses Feld und die **Start_ip_address** Feld `0.0.0.0`.|  
|create_date|**"DATETIME"**|UTC-Datum und -Uhrzeit der Erstellung der Firewalleinstellung auf Serverebene.<br /><br /> Hinweis: UTC ist ein Akronym für die koordinierte Weltzeit.|  
|modify_date|**"DATETIME"**|UTC-Datum und -Uhrzeit der letzten Änderung der Firewalleinstellung auf Serverebene.|  
  
## <a name="remarks"></a>Hinweise  
 Verwenden Sie zum Entfernen einer Datenbank-Firewallregel [Sp_delete_firewall_rule &#40;Azure SQL-Datenbank&#41;](../../relational-databases/system-stored-procedures/sp-delete-firewall-rule-azure-sql-database.md). Um eine Firewallregel für eine einzelne Datenbank festgelegt werden, finden Sie unter [Sys. database_firewall_rules &#40;Azure SQL-Datenbank&#41;](../../relational-databases/system-catalog-views/sys-database-firewall-rules-azure-sql-database.md). Um Informationen zu vorhandenen Firewallregeln zurückzugeben, Fragen Sie sys. firewall_rules (Azure SQL-Datenbank).  
  
## <a name="permissions"></a>Berechtigungen  
 Nur-Lese Zugriff auf diese Sicht wird für alle Benutzer mit der Berechtigung zum Herstellen einer Verbindung mit der **master** Datenbank.  
  
## <a name="see-also"></a>Siehe auch  
 [Sys. database_firewall_rules &#40;Azure SQL-Datenbank&#41;](../../relational-databases/system-catalog-views/sys-database-firewall-rules-azure-sql-database.md)   
 [Sp_set_firewall_rule &#40;Azure SQL-Datenbank&#41;](../../relational-databases/system-stored-procedures/sp-set-firewall-rule-azure-sql-database.md)   
 [Konfigurieren einer Windows-Firewall für Datenbank-Engine-Zugriff](../../database-engine/configure-windows/configure-a-windows-firewall-for-database-engine-access.md)   
 [Konfigurieren einer Firewall für FILESTREAM-Zugriff](../../relational-databases/blob/configure-a-firewall-for-filestream-access.md)   
 [Konfigurieren einer Firewall für den Zugriff auf den Berichtsserver](../../reporting-services/report-server/configure-a-firewall-for-report-server-access.md)   
 [Gewusst wie: Konfigurieren von Firewalleinstellungen (Azure SQL-Datenbank)](https://azure.microsoft.com/documentation/articles/sql-database-configure-firewall-settings/)  
  
  
