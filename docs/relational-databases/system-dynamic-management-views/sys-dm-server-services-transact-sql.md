---
title: sys. dm_server_services (Transact-SQL) | Microsoft-Dokumentation
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
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 5bec144cae5726ce8c4d5ff7af8998a41232b5a7
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/01/2020
ms.locfileid: "85676329"
---
# <a name="sysdm_server_services-transact-sql"></a>sys.dm_server_services (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/applies-to-version/sqlserver.md)]

  Gibt Informationen über die SQL Server, den Volltext SQL Server-Launchpad Dienst (SQL Server 2017 +) und SQL Server-Agent Dienste in der aktuellen Instanz von zurück [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . Verwenden Sie diese dynamische Verwaltungssicht, um Statusinformationen zu diesen Diensten zu melden.  
  
 
|Spaltenname|Datentyp|BESCHREIBUNG|  
|-----------------|---------------|-----------------|  
|servicename|**nvarchar(256)**|Der Name des [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] -, Volltext-oder SQL Server-Agent Dienstanbieter. Lässt keine NULL-Werte zu.|  
|startup_type|**int**|Gibt den Startmodus des Dienstes an. Im folgenden sind die möglichen Werte und ihre entsprechenden Beschreibungen aufgeführt.<br /><br /> 0: Sonstige<br />1: Sonstige<br />2: automatisch<br />3: manuell<br />4: deaktiviert<br /><br /> Lässt NULL-Werte zu.|  
|startup_type_desc|**nvarchar(256)**|Beschreibt den Startmodus des Diensts. Im folgenden sind die möglichen Werte und ihre entsprechenden Beschreibungen aufgeführt.<br /><br /> Sonstige: Sonstige (Start Start)<br />Sonstiges: Sonstiges (Systemstart)<br />Automatisch: automatisch starten<br />Manuell: Start nach Bedarf<br />Deaktiviert: deaktiviert<br /><br /> Lässt keine NULL-Werte zu.|  
|status|**int**|Zeigt den aktuellen Status des Diensts an. Im folgenden sind die möglichen Werte und ihre entsprechenden Beschreibungen aufgeführt.<br /><br /> 1: beendet<br />2: Sonstige (Start ausstehend)<br />3: Sonstige (ausstehenden Vorgang nicht mehr)<br />4: wird ausgeführt<br />5: Sonstige (ausstehende Fortsetzung)<br />6: Sonstige (Anhalten steht aus)<br />7: angehalten<br /><br /> Lässt NULL-Werte zu.|  
|status_desc|**nvarchar(256)**|Beschreibt den aktuellen Status des Diensts. Im folgenden sind die möglichen Werte und ihre entsprechenden Beschreibungen aufgeführt.<br /><br /> Beendet: der Dienst wurde beendet.<br />Sonstige (Startvorgang steht aus): der Dienst wird gerade gestartet.<br />Sonstige (Stop-Vorgang steht aus): der Dienst wird gerade beendet.<br />Wird ausgeführt: der Dienst wird ausgeführt.<br />Sonstige (Continue-Vorgänge ausstehend): der Dienst befindet sich im Status "Ausstehend".<br />Sonstige (ausstehende Pause): der Dienst wird gerade angehalten.<br />Angehalten: der Dienst wurde angehalten.<br /><br /> Lässt keine NULL-Werte zu.|  
|process_id|**int**|Die Prozess-ID des Diensts. Lässt keine NULL-Werte zu.|  
|last_startup_time|**datetimeoffset(7)**|Das Datum und die Uhrzeit, zu der der Dienst zuletzt gestartet wurde. Lässt NULL-Werte zu.|  
|service_account|**nvarchar(256)**|Das Dienstkonto, das zum Steuern des Diensts autorisiert ist. Dieses Konto kann den Dienst starten oder beenden und die Diensteigenschaften bearbeiten. Lässt keine NULL-Werte zu.|  
|filename|**nvarchar(256)**|Der Pfad und Dateiname der ausführbaren Dienstdatei. Lässt keine NULL-Werte zu.|  
|is_clustered|**nvarchar (1)**|Gibt an, ob der Dienst als Ressource eines gruppierten Servers installiert ist. Lässt keine NULL-Werte zu.|  
|cluster_nodename|**nvarchar(256)**|Der Name des Clusterknotens, auf dem der Dienst installiert ist. Lässt NULL-Werte zu.|
|instant_file_initialization_enabled|**nvarchar (1)**|Gibt an, ob die sofortige Datei Initialisierung für den Dienst aktiviert ist [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] .<br /><br />Y = die sofortige Datei Initialisierung ist für den Dienst aktiviert.<br /><br />N = sofortige Datei Initialisierung ist für den Dienst deaktiviert.<br /><br /> Lässt NULL-Werte zu.<br /><br /> **Hinweis:** Gilt nicht für andere Dienste, z. b. die SQL Server-Agent.<br /><br /> **Gilt für:** [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] (Beginnend mit [!INCLUDE[sssql11](../../includes/sssql11-md.md)] SP4 und [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] SP1 und höher).|  

## <a name="security"></a>Sicherheit  
  
### <a name="permissions"></a>Berechtigungen  
 Erfordert die `VIEW SERVER STATE`-Berechtigung auf dem Server.  
  
## <a name="see-also"></a>Weitere Informationen  
 [sys. dm_server_registry &#40;Transact-SQL-&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-server-registry-transact-sql.md)  
  
