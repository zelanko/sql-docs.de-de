---
description: sys.database_firewall_rules (Azure SQL Database)
title: sys. database_firewall_rules (Azure SQL-Datenbank) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/14/2017
ms.service: sql-database
ms.reviewer: ''
ms.topic: language-reference
f1_keywords:
- sys.database_firewall_rules_TSQL
- database_firewall_rules_TSQL
- sys.database_firewall_rules
- database_firewall_rules
dev_langs:
- TSQL
helpviewer_keywords:
- database_firewall_rules
- sys.database_firewall_rules
ms.assetid: 2e821593-3b9f-43d6-a99b-1ceffe177faf
author: VanMSFT
ms.author: vanto
monikerRange: = azuresqldb-current || = sqlallproducts-allversions
ms.openlocfilehash: 49a48533c800093090465819610052009633839f
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/17/2020
ms.locfileid: "88475463"
---
# <a name="sysdatabase_firewall_rules-azure-sql-database"></a>sys.database_firewall_rules (Azure SQL Database)
[!INCLUDE[Azure SQL Database Azure SQL Managed Instance](../../includes/applies-to-version/asdb-asdbmi.md)]

  Gibt Informationen zu den Firewalleinstellungen auf Datenbankebene zurück, die Ihrem zugeordnet sind [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)] . Firewalleinstellungen auf Datenbankebene sind besonders nützlich, wenn eigenständige Datenbankbenutzer verwendet werden. Weitere Informationen finden Sie unter [Eigenständige Datenbankbenutzer - machen Sie Ihre Datenbank portabel](../../relational-databases/security/contained-database-users-making-your-database-portable.md).  
  
 Die `sys.database_firewall_rules` -Sicht enthält die folgenden Spalten:  
  
|Spaltenname|Datentyp|BESCHREIBUNG|  
|-----------------|---------------|-----------------|  
|id|**Zah**|Der Bezeichner der Firewalleinstellung auf Datenbankebene.|  
|name|**Nvarchar (128)**|Der ausgewählte Name, um die Firewalleinstellung auf Datenbankebene zu beschreiben und von anderen zu unterscheiden.|  
|start_ip_address|**Varchar (45)**|Die niedrigste IP-Adresse im Bereich der Firewalleinstellung auf Datenbankebene. IP-Adressen, die gleich oder größer dieser IP-Adresse sind, können versuchen, eine Verbindung mit der [!INCLUDE[ssSDS](../../includes/sssds-md.md)] -Instanz herzustellen. Die niedrigste mögliche IP-Adresse ist `0.0.0.0`.|  
|end_ip_address|**Varchar (45)**|Die höchste IP-Adresse im Bereich der Firewalleinstellung. IP-Adressen, die kleiner oder gleich dieser IP-Adresse sind, können versuchen, eine Verbindung mit der [!INCLUDE[ssSDS](../../includes/sssds-md.md)] -Instanz herzustellen. Die höchste mögliche IP-Adresse ist `255.255.255.255`.<br /><br /> Hinweis: Azure-Verbindungsversuche sind zulässig, wenn sowohl dieses Feld als auch das **start_ip_address** Feld gleich sind `0.0.0.0` .|  
|create_date|**DateTime**|UTC-Datum und -Uhrzeit der Erstellung der Firewalleinstellung auf Datenbankebene.|  
|modify_date|**DateTime**|UTC-Datum und -Uhrzeit der letzten Änderung der Firewalleinstellung auf Datenbankebene.|  
  
## <a name="remarks"></a>Bemerkungen  
 Verwenden Sie [sys. firewall_rules (Azure SQL-Datenbank)](../../relational-databases/system-catalog-views/sys-firewall-rules-azure-sql-database.md), um Informationen zu den Firewalleinstellungen auf Serverebene zurückzugeben, die mit Ihrem Microsoft Azure SQL-Datenbank verknüpft sind.  
  
## <a name="permissions"></a>Berechtigungen  
 Diese Sicht ist in der **master** -Datenbank und in jeder Benutzerdatenbank verfügbar. Alle Benutzer, die berechtigt sind, eine Verbindung mit der Datenbank herzustellen, haben schreibgeschützten Zugriff auf diese Sicht.  
  
## <a name="see-also"></a>Weitere Informationen
[sp_set_database_firewall_rule &#40;Azure SQL-Datenbank&#41;](../../relational-databases/system-stored-procedures/sp-set-database-firewall-rule-azure-sql-database.md)  
[sp_delete_database_firewall_rule &#40;Azure SQL-Datenbank&#41;](../../relational-databases/system-stored-procedures/sp-delete-database-firewall-rule-azure-sql-database.md)  
[sp_set_firewall_rule &#40;Azure SQL-Datenbank&#41;](../../relational-databases/system-stored-procedures/sp-set-firewall-rule-azure-sql-database.md)  
[sp_delete_firewall_rule &#40;Azure SQL-Datenbank&#41;](../../relational-databases/system-stored-procedures/sp-delete-firewall-rule-azure-sql-database.md)   
[sys. firewall_rules &#40;Azure SQL-Datenbank&#41;](../../relational-databases/system-catalog-views/sys-firewall-rules-azure-sql-database.md)  
[Konfigurieren einer Windows-Firewall für den Datenbank-Engine Zugriff](../../database-engine/configure-windows/configure-a-windows-firewall-for-database-engine-access.md)     
[Konfigurieren einer Firewall für FILESTREAM-Zugriff](../../relational-databases/blob/configure-a-firewall-for-filestream-access.md)  
[Konfigurieren einer Firewall für den Zugriff auf den Berichtsserver](../../reporting-services/report-server/configure-a-firewall-for-report-server-access.md)  
