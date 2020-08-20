---
description: sp_set_firewall_rule (Azure SQL-Datenbank)
title: sp_set_firewall_rule (Azure SQL-Datenbank) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 07/28/2016
ms.service: sql-database
ms.reviewer: ''
ms.topic: language-reference
f1_keywords:
- sp_set_firewall_rule
- sp_set_firewall_rule_TSQL
- sys.sp_set_firewall_rule
- sys.sp_set_firewall_rule_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sp_set_firewall_rule
- firewall_rules, setting server rules
ms.assetid: a974a561-5382-4039-8499-3a56767bcefe
author: VanMSFT
ms.author: vanto
monikerRange: = azuresqldb-current || = azure-sqldw-latest || = sqlallproducts-allversions
ms.openlocfilehash: 372aad3acb06910c3c905a12486a6ece4adbd6ce
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/17/2020
ms.locfileid: "88493046"
---
# <a name="sp_set_firewall_rule-azure-sql-database"></a>sp_set_firewall_rule (Azure SQL-Datenbank)
[!INCLUDE [asdb-asa](../../includes/applies-to-version/asdb-asa.md)]

  Erstellt oder aktualisiert die Firewalleinstellungen auf Serverebene für den [!INCLUDE[ssSDS](../../includes/sssds-md.md)]-Server. Diese gespeicherte Prozedur ist nur in der Master-Datenbank für den Prinzipal Anmelde Namen auf Serverebene oder für den zugewiesenen Azure Active Directory Prinzipal verfügbar.  
  
  
## <a name="syntax"></a>Syntax  
  
```
sp_set_firewall_rule [@name =] 'name', 
    [@start_ip_address =] 'start_ip_address', 
    [@end_ip_address =] 'end_ip_address'
[ ; ]  
```  
  
## <a name="arguments"></a>Argumente  
 In der folgenden Tabelle werden die unterstützten Argumente und Optionen in veranschaulicht [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)] .  
  
|Name|Datatype|Beschreibung|  
|----------|--------------|-----------------|  
|[ @name =] ' Name '|**Nvarchar (128)**|Der verwendete Name, um die Firewalleinstellung auf Serverebene zu beschreiben und von anderen zu unterscheiden.|  
|[ @start_ip_address =] ' start_ip_address '|**Varchar (50)**|Die niedrigste IP-Adresse im Bereich der Firewalleinstellung auf Serverebene. IP-Adressen, die gleich oder größer dieser IP-Adresse sind, können versuchen, eine Verbindung mit dem [!INCLUDE[ssSDS](../../includes/sssds-md.md)]-Server herzustellen. Die niedrigste mögliche IP-Adresse ist `0.0.0.0`.|  
|[ @end_ip_address =] ' end_ip_address '|**Varchar (50)**|Die höchste IP-Adresse im Bereich der Firewalleinstellung auf Serverebene. IP-Adressen, die kleiner oder gleich dieser IP-Adresse sind, können versuchen, eine Verbindung mit dem [!INCLUDE[ssSDS](../../includes/sssds-md.md)]-Server herzustellen. Die höchste mögliche IP-Adresse ist `255.255.255.255`.<br /><br /> Hinweis: Azure-Verbindungsversuche sind zulässig, wenn sowohl dieses Feld als auch das *start_ip_address* Feld gleich sind `0.0.0.0` .|  
  
## <a name="remarks"></a>Bemerkungen  
 Die Namen der Firewalleinstellungen auf Serverebene müssen eindeutig sein. Wenn der Name der für die gespeicherte Prozedur bereitgestellten Einstellung bereits in der Tabelle mit den Firewalleinstellungen vorhanden ist, werden die Start- und End-IP-Adressen aktualisiert. Andernfalls wird eine neue Firewalleinstellung auf Serverebene erstellt.  
  
 Durch Hinzufügen einer Firewalleinstellung auf Serverebene, bei der die Anfangs- und die End-IP-Adresse auf `0.0.0.0` festgelegt sind, wird der Zugriff auf den [!INCLUDE[ssSDS](../../includes/sssds-md.md)]-Server durch Azure ermöglicht. Geben Sie einen Wert für den *Name* -Parameter an, der Ihnen hilft, die Firewalleinstellung auf Serverebene zu merken.  
  
 In [!INCLUDE[ssSDS](../../includes/sssds-md.md)] werden Anmeldedaten, die für die Authentifizierung einer Verbindung und Firewallregeln auf Serverebene erforderlich sind, über einen gewissen Zeitraum in jeder Datenbank gespeichert. Dieser Cache wird regelmäßig aktualisiert. Führen Sie [DBCC FLUSHAUTHCACHE &#40;Transact-SQL&#41;](../../t-sql/database-console-commands/dbcc-flushauthcache-transact-sql.md) aus, um das Aktualisieren der Authentifizierungsdatenbank zu erzwingen und sicherzustellen, dass die Datenbank über die aktuelle Version der Anmeldungstabelle verfügt.  
  
## <a name="permissions"></a>Berechtigungen  
 Firewallregeln auf Serverebene können nur durch die Prinzipal Anmeldung auf Serverebene oder durch einen als Administrator zugewiesenen Azure Active Directory Prinzipal auf Serverebene erstellt oder geändert werden. Der Benutzer muss mit der Master-Datenbank verbunden sein, um sp_set_firewall_rule ausführen zu können.  
  
## <a name="examples"></a>Beispiele  
 Im folgenden Code wird eine Firewalleinstellung auf Serverebene mit der Bezeichnung `Allow Azure` erstellt, durch die der Zugriff über Azure ermöglicht wird: Führen Sie den folgenden Befehl in der virtuellen Master Datenbank aus.  
  
```  
-- Enable Azure connections.  
exec sp_set_firewall_rule N'Allow Azure', '0.0.0.0', '0.0.0.0';  
  
```  
  
 Der folgende Code erstellt eine Firewalleinstellung auf Serverebene namens `Example setting 1` nur für die IP-Adresse `0.0.0.2`. Anschließend wird die `sp_set_firewall_rule` gespeicherte Prozedur erneut aufgerufen, um die End-IP-Adresse `0.0.0.4` in dieser Firewalleinstellung auf zu aktualisieren. Dadurch wird ein Bereich erstellt, der die IP-Adressen `0.0.0.2` , und ermöglicht, `0.0.0.3` `0.0.0.4` auf den Server zuzugreifen.  
  
```  
-- Create server-level firewall setting for only IP 0.0.0.2  
exec sp_set_firewall_rule N'Example setting 1', '0.0.0.2', '0.0.0.2';  
  
-- Update server-level firewall setting to create a range of allowed IP addresses
exec sp_set_firewall_rule N'Example setting 1', '0.0.0.2', '0.0.0.4';  
  
```  
  
## <a name="see-also"></a>Weitere Informationen  
 [Azure SQL-Daten Bank Firewall](https://azure.microsoft.com/documentation/articles/sql-database-firewall-configure/)   
 [Vorgehensweise: Konfigurieren von Firewalleinstellungen (Azure SQL-Datenbank)](https://azure.microsoft.com/documentation/articles/sql-database-configure-firewall-settings/)   
 [sys. firewall_rules &#40;Azure SQL-Datenbank&#41;](../../relational-databases/system-catalog-views/sys-firewall-rules-azure-sql-database.md)
