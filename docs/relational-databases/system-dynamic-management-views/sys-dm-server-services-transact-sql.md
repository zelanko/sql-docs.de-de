---
title: dm_server_services (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/07/2018
ms.prod: sql
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- dm_server_services
- sys.dm_server_services
- sys.dm_server_services_TSQL
- dm_server_services_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.dm_server_services dynamic management view
ms.assetid: 3f0defd0-478d-4e7f-96be-8795c9de4e3f
author: stevestein
ms.author: sstein
ms.openlocfilehash: c968c1c7445b89d0291faf97056417952e417dec
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "68090678"
---
# <a name="sysdmserverservices-transact-sql"></a>sys.dm_server_services (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Gibt Informationen zum SQL Server, Volltext- und SQL Server-Agent-Dienst in der aktuellen Instanz von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]zurück. Verwenden Sie diese dynamische Verwaltungssicht, um Statusinformationen zu diesen Diensten zu melden.  
  
 
|Spaltenname|Datentyp|Beschreibung|  
|-----------------|---------------|-----------------|  
|servicename|**nvarchar(256)**|Name des der [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)], Volltext- oder SQL Server-Agent-Dienst. Lässt keine NULL-Werte zu.|  
|startup_type|**int**|Gibt den Startmodus des Dienstes an. Im folgenden sind die möglichen Werte und die entsprechenden Beschreibungen.<br /><br /> 0: Andere<br />1: Andere<br />2: Automatic<br />3: Manuell<br />4: Disabled<br /><br /> Lässt NULL-Werte zu.|  
|startup_desc|**nvarchar(256)**|Beschreibt den Startmodus des Diensts. Im folgenden sind die möglichen Werte und die entsprechenden Beschreibungen.<br /><br /> Andere: Sonstige (Bootstart)<br />Andere: Sonstige (Systemstart)<br />Automatisch: Automatischer start<br />Manuell: Bei Bedarf gestartet<br />Deaktiviert: Disabled<br /><br /> Lässt keine NULL-Werte zu.|  
|status|**int**|Zeigt den aktuellen Status des Diensts an. Im folgenden sind die möglichen Werte und die entsprechenden Beschreibungen.<br /><br /> 1: Beendet<br />2: Sonstige (Start steht aus)<br />3: Sonstige (Beenden steht aus)<br />4: Wird ausgeführt<br />5: Andere (Fortsetzung steht aus)<br />6: Sonstige (Anhalten steht aus)<br />7: Angehalten<br /><br /> Lässt NULL-Werte zu.|  
|status_desc|**nvarchar(256)**|Beschreibt den aktuellen Status des Diensts. Im folgenden sind die möglichen Werte und die entsprechenden Beschreibungen.<br /><br /> Beendet: Der -Dienst wurde beendet.<br />Sonstige (Startvorgang steht aus): Der Dienst wird gerade gestartet.<br />Sonstige (Beendigungsvorgang steht aus): Der Dienst wird gerade beendet.<br />Ausgeführte: Der Dienst wird ausgeführt.<br />Andere (Fortsetzungsvorgang steht aus): Der Dienst ist im Status "Ausstehend".<br />Sonstige (Anhalten steht aus): Der Dienst wird gerade angehalten.<br />Angehalten: Der Dienst wurde angehalten.<br /><br /> Lässt keine NULL-Werte zu.|  
|process_id|**int**|Die Prozess-ID des Diensts. Lässt keine NULL-Werte zu.|  
|last_startup_time|**datetimeoffset(7)**|Das Datum und die Uhrzeit, zu der der Dienst zuletzt gestartet wurde. Lässt NULL-Werte zu.|  
|service_account|**nvarchar(256)**|Das Dienstkonto, das zum Steuern des Diensts autorisiert ist. Dieses Konto kann den Dienst starten oder beenden und die Diensteigenschaften bearbeiten. Lässt keine NULL-Werte zu.|  
|filename|**nvarchar(256)**|Der Pfad und Dateiname der ausführbaren Dienstdatei. Lässt keine NULL-Werte zu.|  
|is_clustered|**nvarchar(1)**|Gibt an, ob der Dienst als Ressource eines gruppierten Servers installiert ist. Lässt keine NULL-Werte zu.|  
|cluster_nodename|**nvarchar(256)**|Der Name des Clusterknotens, auf dem der Dienst installiert ist. Lässt NULL-Werte zu.|
|Sys. dm_server_services|**nvarchar(1)**|Gibt an, ob die sofortige dateiinitialisierung aktiviert ist, für die [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] Service.<br /><br />Y = sofortige dateiinitialisierung für den Dienst aktiviert ist.<br /><br />N = sofortige dateiinitialisierung für den Dienst deaktiviert ist.<br /><br /> Lässt NULL-Werte zu.<br /><br /> **Hinweis**: Gilt nicht für andere Dienste wie SQL Server-Agent.<br /><br /> **Gilt für:** [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] (Beginnend mit [!INCLUDE[sssql11](../../includes/sssql11-md.md)] SP4 und [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] SP1 über [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]).|  

## <a name="security"></a>Sicherheit  
  
### <a name="permissions"></a>Berechtigungen  
 Erfordert die `VIEW SERVER STATE`-Berechtigung auf dem Server.  
  
## <a name="see-also"></a>Siehe auch  
 [sys.dm_server_registry &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-server-registry-transact-sql.md)  
  
