---
title: Sys. database_mirroring_witnesses (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.prod_service: database-engine
ms.component: system-catalog-views
ms.reviewer: ''
ms.suite: sql
ms.technology: system-objects
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- sys.database_mirroring_witnesses
- sys.database_mirroring_witnesses_TSQL
- database_mirroring_witnesses
- database_mirroring_witnesses_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- database mirroring [SQL Server], catalog views
- sys.database_mirroring_witnesses catalog view
- witness [SQL Server], sys.database_mirroring_witnesses catalog view
ms.assetid: 0dd5b794-733b-4a3c-b5a4-62f9f1f0f22d
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 52a56f07422da3dc0bf78a4560f9f6573000050f
ms.sourcegitcommit: 182b8f68bfb345e9e69547b6d507840ec8ddfd8b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/27/2018
ms.locfileid: "43031328"
---
# <a name="database-mirroring-witness-catalog-views---sysdatabasemirroringwitnesses"></a>Database Mirroring Witness-Katalogsichten - Sys. database_mirroring_witnesses
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

  Enthält eine Zeile für jede Zeugenrolle, die ein Server in einer Datenbankspiegelungspartnerschaft spielt. 
  
  Bei einer Sitzung zur Datenbankspiegelung ist ein Zeugenserver für das automatische Failover erforderlich. Im Idealfall befindet sich der Zeuge auf einem anderen Computer als die Prinzipal- und Spiegelserver. Der Zeuge dient nicht der Datenbank. Stattdessen überwacht er den Status der Prinzipal- und Spiegelserver. Wenn der Prinzipalserver ausfällt, kann der Zeuge Automatisches Failover zu dem gespiegelten Server initiieren. 
  
|Spaltenname|Datentyp|Description|  
|-----------------|---------------|-----------------|  
|**database_name**|**sysname**|Name der beiden Datenbankkopien in der Datenbankspiegelungssitzung.|  
|**principal_server_name**|**sysname**|Name des Partnerservers, dessen Datenbankkopie derzeit die Prinzipaldatenbank ist.|  
|**mirror_server_name**|**sysname**|Name des Partnerservers, dessen Datenbankkopie derzeit die Spiegeldatenbank ist.|  
|**safety_level**|**tinyint**|Transaktionssicherheitseinstellung für Updates der Spiegeldatenbank:<br /><br /> 0 = Unbekannter Status<br /><br /> 1 = Aus (asynchron)<br /><br /> 2 = Vollständig (synchron)<br /><br /> Die Verwendung eines Zeugen für das automatische Failover setzt die vollständige Transaktionssicherheit (Standardeinstellung) voraus.|  
|**safety_level_desc**|**nvarchar(60)**|Beschreibung der Sicherheitsgarantie für Updates der Spiegeldatenbank.<br /><br /> UNKNOWN<br /><br /> OFF<br /><br /> FULL|  
|**safety_sequence_number**|**int**|Updatesequenznummer für Änderungen an **Safety_level**.|  
|**role_sequence_number**|**int**|Updatesequenznummer für Änderungen an Prinizipal-/Spiegelrollen der Spiegelungspartner.|  
|**mirroring_guid**|**uniqueidentifier**|Bezeichner der Spiegelungspartnerschaft.|  
|**family_guid**|**uniqueidentifier**|Bezeichner der Sicherungsfamilie für die Datenbank. Wird zur Erkennung übereinstimmender Wiederherstellungsstatus verwendet.|  
|**is_suspended**|**bit**|Die datenbankspiegelung wird angehalten.|  
|**is_suspended_sequence_number**|**int**|Sequenznummer zum Festlegen **Is_suspended**.|  
|**partner_sync_state**|**tinyint**|Synchronisierungsstatus der Spiegelungssitzung:<br /><br /> 5 = die Partner sind synchronisiert. Failover ist eventuell möglich. Informationen zu den Anforderungen für Failovercluster finden Sie unter [Rollenwechsel während einer Datenbank-Spiegelungssitzung &#40;SQL Server&#41;](../../database-engine/database-mirroring/role-switching-during-a-database-mirroring-session-sql-server.md).<br /><br /> 6 = die Partner sind nicht synchronisiert. Failover ist jetzt nicht möglich.|  
|**partner_sync_state_desc**|**nvarchar(60)**|Beschreibung des Synchronisierungsstatus der Spiegelungssitzung:<br /><br /> SYNCHRONIZED<br /><br /> UNSYNCHRONIZED|  
  
## <a name="permissions"></a>Berechtigungen  
 [!INCLUDE[ssCatViewPerm](../../includes/sscatviewperm-md.md)] Weitere Informationen finden Sie unter [Metadata Visibility Configuration](../../relational-databases/security/metadata-visibility-configuration.md).  
  
## <a name="see-also"></a>Siehe auch  
 [Datenbank-Spiegelungszeuge](../../database-engine/database-mirroring/database-mirroring-witness.md)   
 [sys.database_mirroring &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-database-mirroring-transact-sql.md)   
 [sys.database_mirroring_endpoints (Transact-SQL)](../../relational-databases/system-catalog-views/sys-database-mirroring-endpoints-transact-sql.md)   
 [Häufig gestellte Fragen zu Abfragen des SQL Server-Systemkatalogs](../../relational-databases/system-catalog-views/querying-the-sql-server-system-catalog-faq.md)  
  
  
