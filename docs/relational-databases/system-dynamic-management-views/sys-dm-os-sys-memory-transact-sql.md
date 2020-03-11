---
title: sys. dm_os_sys_memory (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/15/2017
ms.prod: sql
ms.prod_service: database-engine, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- dm_os_sys_memory
- sys.dm_os_sys_memory_TSQL
- sys.dm_os_sys_memory
- dm_os_sys_memory_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.dm_os_sys_memory dynamic management view
ms.assetid: 1ca58814-1caa-44c1-b307-ff0bdcbbef62
author: stevestein
ms.author: sstein
monikerRange: '>=aps-pdw-2016||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 891ae8c4f21d0a38302a7213aab22b8a70e855ba
ms.sourcegitcommit: 7008c7fe451a20d6610e40bb8f61dece86c0f17e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/10/2020
ms.locfileid: "79027944"
---
# <a name="sysdm_os_sys_memory-transact-sql"></a>sys.dm_os_sys_memory (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-asdw-pdw-md](../../includes/tsql-appliesto-ss2008-xxxx-asdw-pdw-md.md)]

  Gibt Arbeitsspeicherinformationen vom Betriebssystem zurück.  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ist begrenzt durch den extern verfügbaren Arbeitsspeicher auf Betriebssystemebene sowie durch die physischen Grenzen der zugrunde liegenden Hardware und passt seine Leistung den entsprechenden Gegebenheiten an. Die Ermittlung des Gesamtsystemstatus ist deshalb eine wichtige Komponente zur Auswertung der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Speicherauslastung.  
  
> [!NOTE]  
>  Um dies von oder [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)] [!INCLUDE[ssPDW](../../includes/sspdw-md.md)]aus aufzurufen, verwenden Sie den Namen **sys. dm_pdw_nodes_os_sys_memory**.  
  
|Spaltenname|Datentyp|BESCHREIBUNG|  
|-----------------|---------------|-----------------|  
|**total_physical_memory_kb**|**bigint**|Physischer Gesamtspeicher in Kilobytes (KB), der dem Betriebssystem zur Verfügung steht.|  
|**available_physical_memory_kb**|**bigint**|Verfügbarer physischer Arbeitsspeicher in KB.|  
|**total_page_file_kb**|**bigint**|Die vom Betriebssystem gemeldete Commitgrenze in KB.|  
|**available_page_file_kb**|**bigint**|Die Gesamtmenge der Auslagerungs Datei, die nicht verwendet wird, in KB.|  
|**system_cache_kb**|**bigint**|Gesamter Arbeitsspeicher im Systemcache in KB.|  
|**kernel_paged_pool_kb**|**bigint**|Gesamtgröße des ausgelagerten Kernelpools in KB.|  
|**kernel_nonpaged_pool_kb**|**bigint**|Gesamtgröße des nicht ausgelagerten Kernelpools in KB.|  
|**system_high_memory_signal_state**|**bit**|Benachrichtigung zum Systemstatus: Speicherressourcen sind ausreichend. Ein Wert von 1 gibt an, dass das Signal für ausreichende Speicherressourcen von Windows festgelegt wurde. Weitere Informationen finden Sie unter " [kreatememoryresourcenotifi"](https://go.microsoft.com/fwlink/?LinkId=82427) in der MSDN Library.|  
|**system_low_memory_signal_state**|**bit**|Benachrichtigung zum Systemstatus: Speicherressourcen sind nicht ausreichend. Ein Wert von 1 gibt an, dass das Signal für nicht ausreichende Speicherressourcen von Windows festgelegt wurde. Weitere Informationen finden Sie unter " [kreatememoryresourcenotifi"](https://go.microsoft.com/fwlink/?LinkId=82427) in der MSDN Library.|  
|**system_memory_state_desc**|**nvarchar(256)**|Beschreibung des Speicherstatus. Siehe hierzu die nachstehende Tabelle.|  
|**pdw_node_id**|**int**|**Gilt für**: [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)],[!INCLUDE[ssPDW](../../includes/sspdw-md.md)]<br /><br /> Der Bezeichner für den Knoten, auf dem sich diese Distribution befindet.|  
  
|Bedingung|value|  
|---------------|-----------|  
|system_high_memory_signal_state = 1<br /><br /> and<br /><br /> system_low_memory_signal_state = 0|Ausreichend physischer Speicher verfügbar|  
|system_high_memory_signal_state = 0<br /><br /> and<br /><br /> system_low_memory_signal_state = 1|Nicht ausreichend physischer Speicher verfügbar|  
|system_high_memory_signal_state = 0<br /><br /> and<br /><br /> system_low_memory_signal_state = 0|Konstante physische Speicherauslastung|  
|system_high_memory_signal_state = 1<br /><br /> and<br /><br /> system_low_memory_signal_state = 1|Physischer Speicherstatus befindet sich im Übergang.<br /><br /> Die Signale für ausreichenden und nicht ausreichenden Speicher dürfen nicht gleichzeitig aktiviert sein. Kurzfristige Änderungen auf Betriebssystemebene können jedoch dazu führen, dass eine Benutzermodusanwendung beide Werte als aktiviert betrachtet. Werden beide Signale als aktiviert dargestellt, wird dies als Übergangsstatus interpretiert.|  
  
## <a name="permissions"></a>Berechtigungen  
 Erfordert die VIEW SERVER STATE-Berechtigung auf dem Server.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Dynamische Verwaltungssichten und -funktionen &#40;Transact-SQL&#41;](~/relational-databases/system-dynamic-management-views/system-dynamic-management-views.md)   
 [SQL Server dynamischen Verwaltungs Sichten im Zusammenhang mit dem Betriebs System &#40;Transact-SQL-&#41;](../../relational-databases/system-dynamic-management-views/sql-server-operating-system-related-dynamic-management-views-transact-sql.md)  
  
  


