---
title: sys. firewall_rules (Azure SQL-Datenbank) | Microsoft-Dokumentation
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
monikerRange: = azuresqldb-current || = sqlallproducts-allversions
ms.openlocfilehash: 91c3a4101f19afe4a986514fea8dab207c6d9b48
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "70155553"
---
# <a name="sysfirewall_rules-azure-sql-database"></a>sys.firewall_rules (Azure SQL-Datenbank)
[!INCLUDE[tsql-appliesto-xxxxxx-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-xxxxxx-asdb-xxxx-xxx-md.md)]

  Gibt Informationen zu den Firewalleinstellungen auf Serverebene zurück, [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)]die Ihrem zugeordnet sind.  
  
 Die `sys.firewall_rules` -Sicht enthält die folgenden Spalten:  
  
|Spaltenname|Datentyp|BESCHREIBUNG|  
|-----------------|---------------|-----------------|  
|id|**Wartenden**|Der Bezeichner der Firewalleinstellung auf Serverebene.|  
|name|**Nvarchar (128)**|Der ausgewählte Name, um die Firewalleinstellung auf Serverebene zu beschreiben und von anderen zu unterscheiden.|  
|start_ip_address|**Varchar (45)**|Die niedrigste IP-Adresse im Bereich der Firewalleinstellung auf Serverebene. IP-Adressen, die gleich oder größer dieser IP-Adresse sind, können versuchen, eine Verbindung mit dem [!INCLUDE[ssSDS](../../includes/sssds-md.md)]-Server herzustellen. Die niedrigste mögliche IP-Adresse ist `0.0.0.0`.|  
|end_ip_address|**Varchar (45)**|Die höchste IP-Adresse im Bereich der Firewalleinstellung auf Serverebene. IP-Adressen, die kleiner oder gleich dieser IP-Adresse sind, können versuchen, eine Verbindung mit dem [!INCLUDE[ssSDS](../../includes/sssds-md.md)]-Server herzustellen. Die höchste mögliche IP-Adresse ist `255.255.255.255`.<br /><br /> Hinweis: Azure-Verbindungsversuche sind zulässig, wenn sowohl dieses Feld **** als auch das `0.0.0.0`start_ip_address Feld gleich sind.|  
|create_date|**DateTime**|UTC-Datum und -Uhrzeit der Erstellung der Firewalleinstellung auf Serverebene.<br /><br /> Hinweis: UTC ist ein Akronym für die koordinierte Weltzeit.|  
|modify_date|**DateTime**|UTC-Datum und -Uhrzeit der letzten Änderung der Firewalleinstellung auf Serverebene.|  
  
## <a name="remarks"></a>Bemerkungen

 Um Informationen zu den Firewalleinstellungen auf Datenbankebene zurückgegeben, die mit Ihrem Microsoft Azure SQL-Datenbank verknüpft sind, verwenden Sie [sys. database_firewall_rules &#40;Azure SQL-Daten Bank&#41;](../../relational-databases/system-catalog-views/sys-database-firewall-rules-azure-sql-database.md).  
  
## <a name="permissions"></a>Berechtigungen

 Der schreibgeschützte Zugriff auf diese Ansicht ist für alle Benutzer verfügbar, die über die Berechtigung zum Herstellen einer Verbindung mit der **Master** -Datenbank verfügen.  
  
## <a name="see-also"></a>Weitere Informationen

[sp_set_firewall_rule &#40;Azure SQL-Datenbank&#41;](../../relational-databases/system-stored-procedures/sp-set-firewall-rule-azure-sql-database.md)  
[sp_delete_firewall_rule &#40;Azure SQL-Datenbank&#41;](../../relational-databases/system-stored-procedures/sp-delete-firewall-rule-azure-sql-database.md)   
[sp_set_database_firewall_rule &#40;Azure SQL-Datenbank&#41;](../../relational-databases/system-stored-procedures/sp-set-database-firewall-rule-azure-sql-database.md)  
[sp_delete_database_firewall_rule &#40;Azure SQL-Datenbank&#41;](../../relational-databases/system-stored-procedures/sp-delete-database-firewall-rule-azure-sql-database.md)  
[sys. database_firewall_rules &#40;Azure SQL-Datenbank&#41;](../../relational-databases/system-catalog-views/sys-database-firewall-rules-azure-sql-database.md)  
[Konfigurieren einer Windows-Firewall für den Datenbank-Engine Zugriff](../../database-engine/configure-windows/configure-a-windows-firewall-for-database-engine-access.md)     
[Konfigurieren einer Firewall für FILESTREAM-Zugriff](../../relational-databases/blob/configure-a-firewall-for-filestream-access.md)  
[Konfigurieren einer Firewall für den Zugriff auf den Berichtsserver](../../reporting-services/report-server/configure-a-firewall-for-report-server-access.md) 
