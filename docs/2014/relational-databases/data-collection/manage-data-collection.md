---
title: Verwalten der Datensammlung | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- data collection [SQL Server]
- data collector [SQL Server], Transact-SQL
- data collector [SQL Server], SQL Server Management Studio
ms.assetid: bc137daa-9f37-4c01-9766-8b7350c75af8
caps.latest.revision: 25
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 770b7651aa9359677e610e610938cd33cc5fffa9
ms.sourcegitcommit: 8ae6e6618a7e9186aab3c6a37ea43776aa9a382b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/06/2018
ms.locfileid: "43810056"
---
# <a name="manage-data-collection"></a>Verwalten von Datensammlungen
  Sie können [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] oder [!INCLUDE[tsql](../../includes/tsql-md.md)] gespeicherte Prozeduren und Funktionen, um unterschiedliche Aspekte der Datensammlung zu verwalten, wie z. B. das Aktivieren oder Deaktivieren der Datensammlung, das Ändern einer sammlungssatzkonfiguration oder das Anzeigen von Daten im Verwaltungs-Datawarehouse .  
  
## <a name="manage-data-collection-by-using-sql-server-management-studio"></a>Verwalten der Datensammlung mit SQL Server Management Studio  
 Sie können die folgenden Daten datensammlerbezogenen Tasks ausführen, indem Sie mithilfe des Objekt-Explorers in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]:  
  
-   [Konfigurieren des Verwaltungs-Data Warehouses &#40;SQL Server Management Studio&#41;](configure-the-management-data-warehouse-sql-server-management-studio.md)  
  
-   [Konfigurieren der Eigenschaften eines Datensammlers](configure-properties-of-a-data-collector.md)  
  
-   [Aktivieren oder Deaktivieren der Datensammlung](data-collection.md)  
  
-   [Starten oder Beenden eines Sammlungssatzes](start-or-stop-a-collection-set.md)  
  
-   [Verwenden von SQL Server Profiler zum Erstellen eines Sammlungssatzes für die SQL-Ablaufverfolgung &#40;SQL Server Management Studio&#41;](use-sql-server-profiler-to-create-a-sql-trace-collection-set.md)  
  
-   [Anzeigen von Sammlungssatzprotokollen &#40;SQL Server Management Studio&#41;](view-collection-set-logs-sql-server-management-studio.md)  
  
-   [Anzeigen oder Ändern von Sammlungssatz-Zeitplänen &#40;SQL Server Management Studio&#41;](view-or-change-collection-set-schedules-sql-server-management-studio.md)  
  
-   [Anzeigen eines Sammlungssatzberichts &#40;SQL Server Management Studio&#41;](view-a-collection-set-report-sql-server-management-studio.md)  
  
## <a name="manage-data-collection-by-using-transact-sql"></a>Verwalten der Datensammlung mithilfe von Transact-SQL  
 Der Datensammler stellt eine umfassende Sammlung von gespeicherten Prozeduren bereit, die Sie verwenden können, um beliebige datensammlerbezogene Tasks auszuführen. Sie können mit [!INCLUDE[tsql](../../includes/tsql-md.md)]beispielsweise die folgenden Aufgaben ausführen:  
  
-   [Konfigurieren von Parametern für die Datensammlung &#40;Transact-SQL&#41;](configure-data-collection-parameters-transact-sql.md)  
  
-   [Aktivieren oder Deaktivieren der Datensammlung](data-collection.md)  
  
-   [Starten oder Beenden eines Sammlungssatzes](start-or-stop-a-collection-set.md)  
  
-   [Erstellen eines benutzerdefinierten Sammlungssatzes, der einen generischen T-SQL-Abfragesammlertyp verwendet &#40;Transact-SQL&#41;](create-custom-collection-set-generic-t-sql-query-collector-type.md)  
  
-   [Hinzufügen eines Sammelelements zu einem Sammlungssatz &#40;Transact-SQL&#41;](add-a-collection-item-to-a-collection-set-transact-sql.md)  
  
 Außerdem gibt es Funktionen und Sichten, mit denen Konfigurationsdaten für die msdb- und Verwaltungs-Data Warehouse-Datenbanken, Ausführungsprotokolldaten und im Verwaltungs-Data Warehouse gespeicherte Daten abgerufen werden können.  
  
 Sie können die bereitgestellten gespeicherten Prozeduren, Funktionen und Sichten verwenden, um eigene End-to-End-Datensammlungszenarios zu erstellen.  
  
> [!IMPORTANT]  
>  Im Gegensatz zu regulären gespeicherten Prozeduren verwenden die gespeicherten Prozeduren des Datensammlers genau eingegebene Parameter und unterstützen die automatische Datentypkonvertierung nicht. Wenn diese Parameter nicht mit den richtigen Datentypen für Eingabeparameter aufgerufen werden, wie in der Argumentbeschreibung angegeben, gibt die gespeicherte Prozedur einen Fehler zurück.  
  
 Sie können [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] erstellen und führen Sie die bereitgestellten Codebeispiele. Weitere Informationen finden Sie unter [Objekt-Explorer](../../ssms/object/object-explorer.md). Alternativ können Sie die Abfrage in einem Editor erstellen und in einer Textdatei mit der Dateinamenerweiterung ".sql" speichern. Sie können die Abfrage ausführen, von der Windows-Eingabeaufforderung unter Verwendung der `sqlcmd` Hilfsprogramm. Weitere Informationen finden Sie unter [Verwenden des Hilfsprogramms „sqlcmd“](../scripting/sqlcmd-use-the-utility.md).  
  
### <a name="stored-procedures-and-views"></a>Gespeicherte Prozeduren und Sichten  
 **Arbeiten mit dem Datensammler**  
  
 In der folgenden Tabelle werden die gespeicherten Prozeduren beschrieben, die Sie zum Arbeiten mit dem Datensammler verwenden können.  
  
|Name der Prozedur|Description|  
|--------------------|-----------------|  
|[sp_syscollector_enable_collector](/sql/relational-databases/system-stored-procedures/sp-syscollector-enable-collector-transact-sql)|Aktiviert den Datensammler.|  
|[sp_syscollector_disable_collector](/sql/relational-databases/system-stored-procedures/sp-syscollector-disable-collector-transact-sql)|Deaktiviert den Datensammler.|  
  
 **Arbeiten mit Sammlungssätzen**  
  
 In der folgenden Tabelle werden die gespeicherten Prozeduren beschrieben, die Sie zum Arbeiten mit Sammlungssätzen verwenden können.  
  
|Name der Prozedur|Description|  
|--------------------|-----------------|  
|[sp_syscollector_run_collection_set &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-syscollector-run-collection-set-transact-sql)|Führt bei Bedarf einen Sammlungssatz aus.|  
|[sp_syscollector_start_collection_set &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-syscollector-start-collection-set-transact-sql)|Startet einen Sammlungssatz.|  
|[sp_syscollector_stop_collection_set &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-syscollector-stop-collection-set-transact-sql)|Beendet einen Sammlungssatz.|  
|[sp_syscollector_create_collection_set &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-syscollector-create-collection-set-transact-sql)|Erstellt einen Sammlungssatz.|  
|[sp_syscollector_delete_collection_set &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-syscollector-delete-collection-set-transact-sql)|Löscht einen Sammlungssatz.|  
|[sp_syscollector_update_collection_set &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-syscollector-update-collection-set-transact-sql)|Ändert die Konfiguration eines Sammlungssatzes.|  
|[sp_syscollector_upload_collection_set &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-syscollector-upload-collection-set-transact-sql)|Lädt Sammlungssatzdaten in das Management Data Warehouse hoch. Dies ist im Prinzip ein bedarfsgesteuerter Upload.|  
  
 **Arbeiten mit Sammelelementen**  
  
 In der folgenden Tabelle werden die gespeicherten Prozeduren beschrieben, die Sie zum Arbeiten mit Sammelelementen verwenden können.  
  
|Name der Prozedur|Description|  
|--------------------|-----------------|  
|[sp_syscollector_create_collection_item &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-syscollector-create-collection-item-transact-sql)|Erstellt ein Auflistelement.|  
|[sp_syscollector_delete_collection_item &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-syscollector-delete-collection-item-transact-sql)|Löscht ein Sammelelement.|  
|[sp_syscollector_update_collection_item &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-syscollector-update-collection-item-transact-sql)|Aktualisiert ein Sammelelement.|  
  
 **Arbeiten mit Sammlertypen**  
  
 In der folgenden Tabelle werden die gespeicherten Prozeduren beschrieben, die Sie zum Arbeiten mit Sammlertypen verwenden können.  
  
|Name der Prozedur|Description|  
|--------------------|-----------------|  
|[sp_syscollector_create_collector_type &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-syscollector-create-collector-type-transact-sql)|Erstellt einen Sammlertyp.|  
|[sp_syscollector_update_collector_type &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-syscollector-update-collector-type-transact-sql)|Aktualisiert einen Sammlertyp.|  
|[sp_syscollector_delete_collector_type &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-syscollector-delete-collector-type-transact-sql)|Löscht einen Sammlertyp.|  
  
 **Abrufen von Konfigurationsinformationen**  
  
 In der folgenden Tabelle werden die Sichten beschrieben, die Sie zum Abrufen von Konfigurationsinformationen und Ausführungsprotokolldaten verwenden können.  
  
|Sichtname|Description|  
|---------------|-----------------|  
|[syscollector_config_store &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/syscollector-config-store-transact-sql)|Ruft die Datensammlerkonfiguration ab.|  
|[syscollector_collection_items &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/syscollector-collection-items-transact-sql)|Ruft Informationen zum Sammelelement ab.|  
|[syscollector_collection_sets &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/syscollector-collection-sets-transact-sql)|Ruft Informationen zum Sammlungssatz ab.|  
|[syscollector_collector_types &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/syscollector-collector-types-transact-sql)|Ruft Informationen zum Sammlertyp ab.|  
|[syscollector_execution_log &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/syscollector-execution-log-transact-sql)|Ruft Informationen über den Sammlungssatz und die Paketausführung ab.|  
|[syscollector_execution_stats &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/syscollector-execution-stats-transact-sql)|Ruft Informationen über die Taskausführung ab.|  
|[syscollector_execution_log_full &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/syscollector-execution-log-full-transact-sql)|Ruft Informationen ab, wenn das Ausführungsprotokoll voll ist.|  
  
 **Konfigurieren des Zugriffs auf das Management Date Warehouse**  
  
 In der folgenden Tabelle werden die gespeicherten Prozeduren beschrieben, die Sie zum Konfigurieren des Zugriffs auf das Management Data Warehouse verwenden können.  
  
|Name der Prozedur|Description|  
|--------------------|-----------------|  
|[sp_syscollector_set_warehouse_database_name &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-syscollector-set-warehouse-database-name-transact-sql)|Gibt den in der Verbindungszeichenfolge für das Management Data Warehouse definierten Datenbanknamen an.|  
|[sp_syscollector_set_warehouse_instance_name &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-syscollector-set-warehouse-instance-name-transact-sql)|Gibt die in der Verbindungszeichenfolge für das Management Data Warehouse definierte Instanz an.|  
  
 **Konfigurieren des Management Date Warehouse**  
  
 In der folgenden Tabelle werden die gespeicherten Prozeduren beschrieben, die Sie zum Arbeiten mit der Konfiguration des Management Data Warehouse verwenden können.  
  
|Name der Prozedur|Description|  
|--------------------|-----------------|  
|[core.sp_create_snapshot &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/core-sp-create-snapshot-transact-sql)|Erstellt einen Auflistungssnapshot im Management Data Warehouse.|  
|[core.sp_update_data_source &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/core-sp-update-data-source-transact-sql)|Aktualisiert die Datenquelle für die Datensammlung.|  
|[core.sp_add_collector_type &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/core-sp-add-collector-type-transact-sql)|Fügt dem Management Data Warehouse einen Sammlertyp hinzu.|  
|[core.sp_remove_collector_type &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/core-sp-remove-collector-type-transact-sql)|Entfernt einen Sammlertyp aus dem Management Data Warehouse.|  
|[core.sp_purge_data &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/core-sp-purge-data-transact-sql)|Löscht Daten aus dem Management Data Warehouse.|  
  
 **Arbeiten mit Uploadpaketen**  
  
 In der folgenden Tabelle werden die gespeicherten Prozeduren beschrieben, die Sie zum Arbeiten mit Uploadpaketen verwenden können.  
  
|Name der Prozedur|Description|  
|--------------------|-----------------|  
|[sp_syscollector_set_cache_window &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-syscollector-set-cache-window-transact-sql)|Konfiguriert die Anzahl von Wiederholungen für Datenuploads.|  
|[sp_syscollector_set_cache_directory &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-syscollector-set-cache-directory-transact-sql)|Gibt eine temporäre Speicherung für Daten zwischen Uploadwiederholungen an.|  
  
 **Arbeiten mit dem Ausführungsprotokoll der Datensammlung**  
  
 In der folgenden Tabelle werden die gespeicherten Prozeduren beschrieben, die Sie zum Arbeiten mit dem Ausführungsprotokoll der Datensammlung verwenden können.  
  
|Name der Prozedur|Description|  
|--------------------|-----------------|  
|[sp_syscollector_delete_execution_log_tree &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-syscollector-delete-execution-log-tree-transact-sql)|Löscht Einträge des Sammlungssatzes aus dem Ausführungsprotokoll.|  
  
### <a name="functions"></a>Funktionen  
 In der folgenden Tabelle werden die Funktionen beschrieben, die Sie zum Abrufen von Ausführungs- und Überwachungsinformationen verwenden können.  
  
|Funktionsname|Description|  
|-------------------|-----------------|  
|[fn_syscollector_get_execution_details &#40;Transact-SQL&#41;](/sql/relational-databases/system-functions/fn-syscollector-get-execution-details-transact-sql)|Ruft [!INCLUDE[ssIS](../../includes/ssis-md.md)] -Ausführungsprotokolldaten für ein bestimmtes Paket ab.|  
|[fn_syscollector_get_execution_stats &#40;Transact-SQL&#41;](/sql/relational-databases/system-functions/fn-syscollector-get-execution-stats-transact-sql)|Ruft Ausführungsstatistiken für einen Sammlungssatz oder ein Paket ab. Diese Informationen umfassen Fehler, die protokolliert werden.|  
|[snapshots.fn_trace_getdata &#40;Transact-SQL&#41;](/sql/relational-databases/system-functions/snapshots-fn-trace-getdata-transact-sql)|Ruft die Ereignisse ab, die protokolliert werden, wenn der generische SQL-Ablaufverfolgungs-Sammlertyp für das Sammeln von Daten verwendet wird.|  
  
## <a name="see-also"></a>Siehe auch  
 [Ausführen einer gespeicherten Prozedur](../stored-procedures/execute-a-stored-procedure.md)   
 [Verwenden von SQL Server Management Studio](../../database-engine/use-sql-server-management-studio.md)   
 [Datensammlung](data-collection.md)  
  
  
