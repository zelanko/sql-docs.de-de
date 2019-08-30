---
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
ms.openlocfilehash: 9bc37626879b743eb3a5d0864490dc3543a8d8a9
ms.sourcegitcommit: 5e45cc444cfa0345901ca00ab2262c71ba3fd7c6
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/29/2019
ms.locfileid: "70152064"
---
# <a name="sp_set_firewall_rule-azure-sql-database"></a>sp_set_firewall_rule (Azure SQL-Datenbank)
[!INCLUDE[tsql-appliesto-xxxxxx-asdb-asdw-xxx-md](../../includes/tsql-appliesto-xxxxxx-asdb-asdw-xxx-md.md)]

  Erstellt oder aktualisiert die Firewalleinstellungen auf Serverebene für den [!INCLUDE[ssSDS](../../includes/sssds-md.md)]-Server. Diese gespeicherte Prozedur ist nur in der Master-Datenbank für den Prinzipal Anmelde Namen auf Serverebene oder für den zugewiesenen Azure Active Directory Prinzipal verfügbar.  
  
  
## <a name="syntax"></a>Syntax  
  
```
sp_set_firewall_rule [@name =] 'name', 
    [@start_ip_address =] 'start_ip_address', 
    [@end_ip_address =] 'end_ip_address'
[ ; ]  
```  
  
## <a name="arguments"></a>Argumente  
 In der folgenden Tabelle werden die unterstützten Argumente und [!INCLUDE[msCoName](../../includes/msconame-md.md)] Optionen in [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)]veranschaulicht.  
  
|Name|Datatype|Beschreibung|  
|----------|--------------|-----------------|  
|[@name =] ' Name '|**NVARCHAR (128)**|Der verwendete Name, um die Firewalleinstellung auf Serverebene zu beschreiben und von anderen zu unterscheiden.|  
|[@start_ip_address =] ' start_ip_address '|**VARCHAR (50)**|Die niedrigste IP-Adresse im Bereich der Firewalleinstellung auf Serverebene. IP-Adressen, die gleich oder größer dieser IP-Adresse sind, können versuchen, eine Verbindung mit dem [!INCLUDE[ssSDS](../../includes/sssds-md.md)]-Server herzustellen. Die niedrigste mögliche IP-Adresse ist `0.0.0.0`.|  
|[@end_ip_address =] ' end_ip_address '|**VARCHAR (50)**|Die höchste IP-Adresse im Bereich der Firewalleinstellung auf Serverebene. IP-Adressen, die kleiner oder gleich dieser IP-Adresse sind, können versuchen, eine Verbindung mit dem [!INCLUDE[ssSDS](../../includes/sssds-md.md)]-Server herzustellen. Die höchste mögliche IP-Adresse ist `255.255.255.255`.<br /><br /> Hinweis: Azure-Verbindungsversuche sind zulässig, wenn sowohl dieses Feld als auch das `0.0.0.0`start_ip_address-Feld gleich sind.|  
  
## <a name="remarks"></a>Hinweise  
 Die Namen der Firewalleinstellungen auf Serverebene müssen eindeutig sein. Wenn der Name der für die gespeicherte Prozedur bereitgestellten Einstellung bereits in der Tabelle mit den Firewalleinstellungen vorhanden ist, werden die Start- und End-IP-Adressen aktualisiert. Andernfalls wird eine neue Firewalleinstellung auf Serverebene erstellt.  
  
 Wenn Sie eine Firewalleinstellung auf Serverebene hinzufügen `0.0.0.0`, bei der die Start-und End-IP-Adressen gleich sind, aktivieren Sie den Zugriff auf Ihren [!INCLUDE[ssSDS](../../includes/sssds-md.md)] Server von Azure. Geben Sie einen Wert für den *Name* -Parameter an, der Ihnen hilft, die Firewalleinstellung auf Serverebene zu merken.  
  
 In [!INCLUDE[ssSDS](../../includes/sssds-md.md)] werden Anmeldedaten, die für die Authentifizierung einer Verbindung und Firewallregeln auf Serverebene erforderlich sind, über einen gewissen Zeitraum in jeder Datenbank gespeichert. Dieser Cache wird regelmäßig aktualisiert. Führen Sie [DBCC FLUSHAUTHCACHE &#40;Transact-SQL&#41;](../../t-sql/database-console-commands/dbcc-flushauthcache-transact-sql.md) aus, um das Aktualisieren der Authentifizierungsdatenbank zu erzwingen und sicherzustellen, dass die Datenbank über die aktuelle Version der Anmeldungstabelle verfügt.  
  
## <a name="permissions"></a>Berechtigungen  
 Firewallregeln auf Serverebene können nur durch die Prinzipal Anmeldung auf Serverebene oder durch einen als Administrator zugewiesenen Azure Active Directory Prinzipal auf Serverebene erstellt oder geändert werden. Der Benutzer muss mit der Master-Datenbank verbunden sein, um sp_set_firewall_rule auszuführen.  
  
## <a name="examples"></a>Beispiele  
 Mit dem folgenden Code wird eine Firewalleinstellung auf Server `Allow Azure` Ebene mit dem Namen erstellt, die den Zugriff von Azure ermöglicht. Führen Sie den folgenden Befehl in der virtuellen Master Datenbank aus.  
  
```  
-- Enable Azure connections.  
exec sp_set_firewall_rule N'Allow Azure', '0.0.0.0', '0.0.0.0';  
  
```  
  
 Der folgende Code erstellt eine Firewalleinstellung auf Serverebene namens `Example setting 1` nur für die IP-Adresse `0.0.0.2`. Anschließend wird die `sp_set_firewall_rule` gespeicherte Prozedur erneut aufgerufen, um die End-IP-Adresse `0.0.0.4`in dieser Firewalleinstellung auf zu aktualisieren. Dadurch wird ein Bereich erstellt, der die `0.0.0.2`IP `0.0.0.3`-Adressen `0.0.0.4` , und ermöglicht, auf den Server zuzugreifen.  
  
```  
-- Create server-level firewall setting for only IP 0.0.0.2  
exec sp_set_firewall_rule N'Example setting 1', '0.0.0.2', '0.0.0.2';  
  
-- Update server-level firewall setting to create a range of allowed IP addresses
exec sp_set_firewall_rule N'Example setting 1', '0.0.0.2', '0.0.0.4';  
  
```  
  
## <a name="see-also"></a>Siehe auch  
 [Azure SQL-Daten Bank Firewall](https://azure.microsoft.com/documentation/articles/sql-database-firewall-configure/)   
 [Vorgehensweise: Konfigurieren von Firewalleinstellungen (Azure SQL-Datenbank)](https://azure.microsoft.com/documentation/articles/sql-database-configure-firewall-settings/)   
 [sys. firewall_rules &#40;Azure SQL-Datenbank&#41;](../../relational-databases/system-catalog-views/sys-firewall-rules-azure-sql-database.md)
