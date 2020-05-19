---
title: Tools für erweiterte Ereignisse | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xevents
ms.topic: conceptual
helpviewer_keywords:
- extended events [SQL Server], using
- extended events [SQL Server], options for using
ms.assetid: d312a9ff-50ba-4721-baef-50bfd3169d38
author: rothja
ms.author: jroth
manager: craigg
ms.openlocfilehash: 2521810771713833a10f7e01f1e83480c3050369
ms.sourcegitcommit: b72c9fc9436c44c6a21fd96223c73bf94706c06b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/01/2020
ms.locfileid: "82706770"
---
# <a name="extended-events-tools"></a>Tools für erweiterte Ereignisse
  Sie können die folgenden Tools verwenden, um [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Sitzungen für erweiterte Ereignisse zu erstellen und zu verwalten:  
  
-   DDL-Anweisungen (Data Definition Language, Datendefinitionssprache) Damit können Sie eine Sitzung für erweiterte Ereignisse erstellen und ändern.  
  
-   Dynamische Verwaltungssichten, Katalogsichten und Systemtabellen Diese ermöglichen Ihnen das Abrufen von Sitzungsdaten und Metadaten mithilfe von [!INCLUDE[tsql](../../includes/tsql-md.md)] -Anweisungen. Anhand der Systemtabellen können Sie die Entsprechungen für vorhandene erweitere Ereignisse für SQL-Ablaufverfolgungs-Ereignisklassen und -Spalten bestimmen.  
  
-   Der Knoten **Erweiterte Ereignisse** von Objekt-Explorer. Auf diese Weise können Sie eine Sitzung starten, beenden oder löschen oder Sitzungsvorlagen importieren und exportieren.  
  
-   Der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] PowerShell-Anbieter. Dabei handelt es sich um ein leistungsstarkes Tool, mit dem Sie Sitzungen für erweiterte Ereignisse erstellen, ändern und verwalten können. Weitere Informationen finden Sie unter [Verwenden des PowerShell-Anbieters für erweiterte Ereignisse](use-the-powershell-provider-for-extended-events.md).  
  
-   [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]. Damit können Sie die in den Themen zu erweiterten Ereignissen bereitgestellten Codebeispiele erstellen und ausführen. Weitere Informationen finden Sie unter [Objekt-Explorer](../../ssms/object/object-explorer.md).  
  
 Zusätzlich zu Sitzungen, die Sie erstellen, ist auf dem Server eine standardmäßige Systemintegritätssitzung vorhanden. In der Sitzung werden Systemdaten erfasst, mit deren Hilfe Sie Leistungsprobleme beheben können. Weitere Informationen finden Sie unter [Verwenden der system_health Sitzung](use-the-ssms-xe-profiler.md).  
  
## <a name="ddl-statements"></a>DDL-Anweisungen  
 Verwenden Sie die folgenden DDL-Anweisungen, um eine Sitzung für erweiterte Ereignisse zu erstellen, zu ändern und zu löschen.  
  
|Name|BESCHREIBUNG|  
|----------|-----------------|  
|[CREATE EVENT SESSION &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-event-session-transact-sql)|Erstellt ein Sitzungsobjekt für erweiterte Ereignisse, das die Quelle der Ereignisse, die Ereignissitzungsziele und die Ereignissitzungsparameter identifiziert.|  
|[ALTER EVENT SESSION &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-event-session-transact-sql)|Startet oder beendet eine Ereignissitzung oder ändert die Konfiguration einer Ereignissitzung.|  
|[DROP EVENT SESSION &#40;Transact-SQL&#41;](/sql/t-sql/statements/drop-event-session-transact-sql)|Löscht eine Ereignissitzung.|  
  
## <a name="catalog-views"></a>Katalogsichten  
 Verwenden Sie die folgenden Katalogsichten, um die beim Erstellen einer Ereignissitzung erstellten Metadaten abzurufen.  
  
|Name|BESCHREIBUNG|  
|----------|-----------------|  
|[sys.server_event_sessions &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-server-event-sessions-transact-sql)|Listet alle Ereignissitzungsdefinitionen auf.|  
|[sys.server_event_session_actions &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-server-event-session-actions-transact-sql)|Gibt für jede Aktion jedes Ereignisses einer Ereignissitzung eine Zeile zurück.|  
|[sys.server_event_session_events &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-server-event-session-events-transact-sql)|Gibt eine Zeile für jedes Ereignis in einer Ereignissitzung zurück.|  
|[sys.server_event_session_fields &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-server-event-session-fields-transact-sql)|Gibt eine Zeile für jede anpassbare Spalte zurück, die explizit für Ereignisse und Ziele festgelegt wurde.|  
|[sys.server_event_session_targets &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-server-event-session-targets-transact-sql)|Gibt für eine Ereignissitzung eine Zeile für jedes Ereignisziel zurück.|  
  
## <a name="dynamic-management-views"></a>Dynamische Verwaltungssichten  
 Verwenden Sie die folgenden dynamischen Verwaltungssichten, um Sitzungsmetadaten und Sitzungsdaten abzurufen. Die Metadaten werden aus den Katalogsichten abgerufen, und die Sitzungsdaten werden erstellt, wenn Sie eine Ereignissitzung starten und ausführen.  
  
> [!NOTE]  
>  Diese Sichten weisen erst Sitzungsdaten auf, wenn eine Sitzung gestartet wird.  
  
|Name|BESCHREIBUNG|  
|----------|-----------------|  
|[sys.dm_os_dispatcher_pools &#40;Transact-SQL&#41;](/sql/relational-databases/system-dynamic-management-views/sys-dm-os-dispatcher-pools-transact-sql)|Gibt Informationen zu Sitzungsverteilerpools zurück.|  
|[sys.dm_xe_objects &#40;Transact-SQL&#41;](/sql/relational-databases/system-dynamic-management-views/sys-dm-xe-objects-transact-sql)|Gibt eine Zeile für jedes Objekt zurück, das von einem Ereignispaket verfügbar gemacht wird.|  
|[sys.dm_xe_object_columns &#40;Transact-SQL&#41;](/sql/relational-databases/system-dynamic-management-views/sys-dm-xe-object-columns-transact-sql)|Gibt die Schemainformationen für alle Objekte zurück.|  
|[sys.dm_xe_packages &#40;Transact-SQL&#41;](/sql/relational-databases/system-dynamic-management-views/sys-dm-xe-packages-transact-sql)|Listet alle für die Engine für erweiterte Ereignisse registrierten Pakete auf.|  
|[sys.dm_xe_sessions &#40;Transact-SQL&#41;](/sql/relational-databases/system-dynamic-management-views/sys-dm-xe-sessions-transact-sql)|Gibt Informationen über eine aktive Sitzung mit erweiterten Ereignissen zurück.|  
|[sys.dm_xe_session_targets &#40;Transact-SQL&#41;](/sql/relational-databases/system-dynamic-management-views/sys-dm-xe-session-targets-transact-sql)|Gibt Informationen zu Sitzungszielen zurück.|  
|[sys.dm_xe_session_events &#40;Transact-SQL&#41;](/sql/relational-databases/system-dynamic-management-views/sys-dm-xe-session-events-transact-sql)|Gibt Informationen zu Sitzungsereignissen zurück.|  
|[sys.dm_xe_session_event_actions &#40;Transact-SQL&#41;](/sql/relational-databases/system-dynamic-management-views/sys-dm-xe-session-event-actions-transact-sql)|Gibt Informationen zu Ereignissitzungsaktionen zurück.|  
|[sys.dm_xe_map_values &#40;Transact-SQL&#41;](/sql/relational-databases/system-dynamic-management-views/sys-dm-xe-map-values-transact-sql)|Stellt eine Zuordnung von internen numerischen Schlüsseln zu für den Benutzer lesbarem Text bereit.|  
|[sys.dm_xe_session_object_columns &#40;Transact-SQL&#41;](/sql/relational-databases/system-dynamic-management-views/sys-dm-xe-session-object-columns-transact-sql)|Zeigt die Konfigurationswerte für Objekte an, die an eine Sitzung gebunden sind.|  
  
## <a name="system-tables"></a>Systemtabellen  
 Verwenden Sie die folgenden Systemtabellen, um Informationen zu den Entsprechungen für erweiterte Ereignissen für SQL-Ablaufverfolgungs-Ereignisklassen und -Spalten abzurufen.  
  
|Name|BESCHREIBUNG|  
|----------|-----------------|  
|[trace_xe_event_map &#40;Transact-SQL&#41;](/sql/relational-databases/system-tables/extended-events-tables-trace-xe-event-map)|Enthält eine Zeile für jedes einer SQL-Ablaufverfolgungs-Ereignisklasse zugeordnete Ereignis für erweiterte Ereignisse.|  
|[trace_xe_action_map &#40;Transact-SQL&#41;](/sql/relational-databases/system-tables/extended-events-tables-trace-xe-action-map)|Enthält eine Zeile für jede Aktion für erweiterte Ereignisse, die der Spalten-ID für eine SQL-Ablaufverfolgung zugeordnet ist.|  
  
## <a name="see-also"></a>Weitere Informationen  
 [Dynamische Verwaltungs Sichten und Funktionen &#40;Transact-SQL-&#41;](../views/views.md)   
 [Katalog Sichten &#40;Transact-SQL-&#41;](/sql/relational-databases/system-catalog-views/catalog-views-transact-sql)   
 [SQL Server Tabellen für erweiterte Ereignisse &#40;Transact-SQL-&#41;](/sql/relational-databases/system-tables/system-tables-transact-sql)   
 [Verwenden der system_health Sitzung](use-the-ssms-xe-profiler.md)   
 [Verwenden des PowerShell-Anbieters für erweiterte Ereignisse](use-the-powershell-provider-for-extended-events.md)  
  
  
