---
description: Gespeicherte Systemprozeduren (Transact-SQL)
title: Gespeicherte System Prozeduren (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 02/21/2016
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sql13.TSQLSysNoExpandPortal.f1
- sql13.TSQLSysNoExpandPortal.f1_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- stored procedures [SQL Server]
- APIs [SQL Server]
- stored procedures [SQL Server], categories
- system stored procedures [SQL Server], categories
- system stored procedures [SQL Server]
ms.assetid: a5c4d5b8-5a24-4a2d-99b4-d003b546ee3a
author: VanMSFT
ms.author: vanto
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: 05be8467516ff84c45268357eb6ab743d5599a05
ms.sourcegitcommit: 331b8495e4ab37266945c81ff5b93d250bdaa6da
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/20/2020
ms.locfileid: "88645076"
---
# <a name="system-stored-procedures-transact-sql"></a>Gespeicherte Systemprozeduren (Transact-SQL)

[!INCLUDE [sqlserver2016-asdb-asdbmi](../../includes/applies-to-version/sqlserver2016-asdb-asdbmi.md)]

  In [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] können viele Verwaltungs- und Informationsabläufe mithilfe gespeicherter Systemprozeduren ausgeführt werden. Die gespeicherten Systemprozeduren sind in die in der folgenden Tabelle gezeigten Kategorien unterteilt.  
  
## <a name="in-this-section"></a>In diesem Abschnitt  
  
|Category|BESCHREIBUNG|  
|--------------|-----------------|  
|[Gespeicherte Prozeduren für die aktive georeplikation](https://msdn.microsoft.com/library/81658ee4-4422-4d73-bf7a-86a07422cb0d)|Dient zum Verwalten von zum Verwalten von Konfigurationen für die aktive georeplikation in Azure SQL-Datenbank.|  
|[Gespeicherte Katalogprozeduren](../../relational-databases/system-stored-procedures/catalog-stored-procedures-transact-sql.md)|Implementieren Funktionen ODBC-Datenwörterbüchern und isolieren ODBC-Anwendungen von Änderungen an den zugrunde liegenden Systemtabellen.|  
|[Gespeicherte Prozeduren für Change Data Capture](../../relational-databases/system-stored-procedures/change-data-capture-stored-procedures-transact-sql.md)|Wird verwendet, um Change Data Capture-Objekte zu aktivieren, zu deaktivieren oder über sie zu berichten.|  
|[Gespeicherte Cursorprozeduren](../../relational-databases/system-stored-procedures/cursor-stored-procedures-transact-sql.md)|Werden zum Implementieren von Cursorvariablenfunktionen verwendet.|  
|[Gespeicherte Prozeduren für den Datensammler](../../relational-databases/system-stored-procedures/data-collector-stored-procedures-transact-sql.md)|Wird zum Arbeiten mit dem Datensammler und folgenden Komponenten verwendet: Auflistsätze, Auflistelemente und Auflisttypen.|  
|[Gespeicherte Datenbank-Engine-Prozeduren](../../relational-databases/system-stored-procedures/database-engine-stored-procedures-transact-sql.md)|Werden für die allgemeine Wartung von [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] verwendet.|  
|[Datenbank-E-Mail gespeicherter Prozeduren &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/database-mail-stored-procedures-transact-sql.md)|Werden zum Ausführen von E-Mail-Operationen innerhalb einer Instanz von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] verwendet.|  
|[Gespeicherte Prozeduren für Datenbank-Wartungspläne](../../relational-databases/system-stored-procedures/database-maintenance-plan-stored-procedures-transact-sql.md)|Werden zum Einrichten zentraler Wartungsaufgaben verwendet, die zur Optimierung der Datenbankleistung ausgeführt werden müssen.|  
|[Gespeicherte Prozeduren für verteilte Abfragen](../../relational-databases/system-stored-procedures/distributed-queries-stored-procedures-transact-sql.md)|Werden zum Implementieren und Verwalten verteilter Abfragen verwendet.|  
|[Gespeicherte FILESTREAM-und FILETABLE-Prozeduren &#40;Transact-SQL-&#41;](https://msdn.microsoft.com/library/54beca08-c012-4ebd-aa68-d8a10d221b64)|Werden zum Konfigurieren und Verwalten der FILESTREAM- und FileTable-Funktionen verwendet.|  
|[Gespeicherte Prozeduren für Firewallregeln &#40;Azure SQL-Datenbank&#41;](../../relational-databases/system-stored-procedures/firewall-rules-stored-procedures-azure-sql-database.md)|Wird zum Konfigurieren der Firewall für die Azure SQL-Datenbank verwendet.|  
|[Gespeicherte Prozeduren für die Volltextsuche](../../relational-databases/system-stored-procedures/full-text-search-and-semantic-search-stored-procedures-transact-sql.md)|Werden zum Implementieren und Abfragen von Volltextindizes verwendet.|  
|[Gespeicherte allgemeine erweiterte Prozeduren](../../relational-databases/system-stored-procedures/general-extended-stored-procedures-transact-sql.md)|Werden zur Bereitstellung einer Schnittstelle zwischen einer Instanz von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] und externen Programmen für verschiedene Wartungsaktivitäten verwendet.|  
|[Gespeicherte Prozeduren für den Protokollversand](../../relational-databases/system-stored-procedures/log-shipping-stored-procedures-transact-sql.md)|Werden zum Konfigurieren, Ändern und Überwachen von Protokollversandkonfigurationen verwendet.|  
|[Gespeicherte Prozeduren für das Verwaltungs-Data Warehouse &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/management-data-warehouse-stored-procedures-transact-sql.md)|Wird verwendet, um die Verwaltungs Data Warehouse zu konfigurieren.|  
|[Gespeicherte OLE-Automatisierungs Prozeduren](../../relational-databases/system-stored-procedures/ole-automation-stored-procedures-transact-sql.md)|Werden zur Aktivierung standardmäßiger Automatisierungsobjekte für die Verwendung innerhalb eines [!INCLUDE[tsql](../../includes/tsql-md.md)]-Standardbatches verwendet.|  
|[Gespeicherte Prozeduren für die richtlinienbasierte Verwaltung](../../relational-databases/system-stored-procedures/policy-based-management-stored-procedures-transact-sql.md)|Werden für die richtlinienbasierte Verwaltung verwendet.|  
|[Gespeicherte PolyBase-Prozeduren](https://msdn.microsoft.com/library/a522b303-bd1b-410b-92d1-29c950a15ede)|Hinzufügen oder Entfernen eines Computers aus einer polybase-Erweiterungsgruppe.|  
|[Gespeicherte Prozeduren für den Abfragespeicher &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/query-store-stored-procedures-transact-sql.md)|Dient zum Optimieren der Leistung.|  
|[Gespeicherte Replikations Prozedur](../../relational-databases/system-stored-procedures/replication-stored-procedures-transact-sql.md)|Werden für die Replikation verwendet.|  
|[Gespeicherte Sicherheitsprozeduren](../../relational-databases/system-stored-procedures/security-stored-procedures-transact-sql.md)|Werden für die Verwaltung der Sicherheit verwendet.|  
|[Gespeicherte Momentaufnahme Sicherungs Prozeduren](https://msdn.microsoft.com/library/c278db87-5770-4037-a1e6-b9853a943339)|Wird verwendet, um die FILE_SNAPSHOT Sicherung zusammen mit allen zugehörigen Momentaufnahmen zu löschen oder eine einzelne Sicherungsdatei-Momentaufnahme zu löschen.|  
|[Gespeicherte Prozeduren für Räumlichkeitsindizes](https://msdn.microsoft.com/library/1be0f34e-3d5a-4a1f-9299-bd482362ec7a)|Wird verwendet, um die Indexleistung räumlicher Indizes zu analysieren und zu verbessern.|  
|[Gespeicherte SQL Server-Agent-Prozeduren](../../relational-databases/system-stored-procedures/sql-server-agent-stored-procedures-transact-sql.md)|Werden von [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] verwendet, um die Leistung und die Aktivitäten zu überwachen.|  
|[Gespeicherte Prozeduren für SQL Server Profiler](../../relational-databases/system-stored-procedures/sql-server-profiler-stored-procedures-transact-sql.md)|Werden vom [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Agent zum Verwalten geplanter und ereignisgesteuerter Aktivitäten verwendet.|  
|[Gespeicherte Prozeduren Stretch Database](../../relational-databases/system-stored-procedures/stretch-database-extended-stored-procedures-transact-sql.md)|Wird zum Verwalten von Stretch-Datenbanken verwendet.|  
|[Temporale Tabellen gespeicherte Prozeduren](https://msdn.microsoft.com/library/f28ca74e-7876-4592-b794-e78e3690fff6)|Verwendung für temporale Tabellen|  
|[Gespeicherte XML-Prozeduren](../../relational-databases/system-stored-procedures/xml-stored-procedures-transact-sql.md)|Werden für die XML-Textverwaltung verwendet.|  
  
> [!NOTE]  
>  Alle gespeicherten Systemprozeduren geben den Wert 0 für einen erfolgreichen Vorgang zurück, wenn nicht anders angegeben. Ein Wert ungleich 0 wird zurückgegeben, um einen Fehler anzuzeigen.  
  
## <a name="api-system-stored-procedures"></a>Gespeicherte API-Systemprozeduren  
 Benutzer, die [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] für ADO-, OLE DB- und ODBC-Anwendungen ausführen, werden möglicherweise feststellen, dass diese Anwendungen gespeicherte Systemprozeduren verwenden, die nicht in der [!INCLUDE[tsql](../../includes/tsql-md.md)]-Referenz behandelt werden. Diese gespeicherten Prozeduren werden vom [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB-Anbieter und dem [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client-ODBC-Treiber verwendet, um die Funktionalität einer Datenbank-API zu implementieren. Diese gespeicherten Prozeduren sind lediglich der Mechanismus, mit dem der Anbieter oder Treiber Benutzeranforderungen an [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] weitergeben. Sie sind ausschließlich für die interne Verwendung des Anbieters oder Treibers gedacht. Das explizite Aufrufen von einer [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -basierten Anwendung wird nicht unterstützt.  
  
 Die gespeicherten Prozeduren sp_createorphan und sp_droporphans werden für die ODBC- **ntext**-, **Text**-und **Image** -Verarbeitung verwendet.  
  
 Die gespeicherte Prozedur sp_reset_connection wird von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] zur Unterstützung von Aufrufen remote gespeicherter Prozeduren in Transaktionen verwendet. Durch diese gespeicherte Prozedur werden auch Audit Login- und Audit Logout-Ereignisse ausgelöst, wenn eine Verbindung in einem Verbindungspool wiederverwendet wird.  
  
 Die gespeicherten Systemprozeduren in den folgenden Tabellen werden nur innerhalb einer Instanz von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] oder über Client-APIs verwendet und sind nicht zur allgemeinen Verwendung durch die Benutzer gedacht. Sie können geändert werden, und ihre Kompatibilität wird nicht garantiert.  
  
 Die folgenden gespeicherten Prozeduren werden in der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Onlinedokumentation beschrieben:  
  
:::row:::
    :::column:::
        sp_catalogs
    :::column-end:::
    :::column:::
        sp_column_privileges
    :::column-end:::
:::row-end:::  
:::row:::
    :::column:::
        sp_column_privileges_ex
    :::column-end:::
    :::column:::
        sp_columns
    :::column-end:::
:::row-end:::  
:::row:::
    :::column:::
        sp_columns_ex
    :::column-end:::
    :::column:::
        sp_databases
    :::column-end:::
:::row-end:::  
:::row:::
    :::column:::
        sp_cursor
    :::column-end:::
    :::column:::
        sp_cursorclose
    :::column-end:::
:::row-end:::  
:::row:::
    :::column:::
        sp_cursorexecute
    :::column-end:::
    :::column:::
        sp_cursorfetch
    :::column-end:::
:::row-end:::  
:::row:::
    :::column:::
        sp_cursoroption
    :::column-end:::
    :::column:::
        sp_cursoropen
    :::column-end:::
:::row-end:::  
:::row:::
    :::column:::
        sp_cursorprepare
    :::column-end:::
    :::column:::
        sp_cursorprepexec
    :::column-end:::
:::row-end:::  
:::row:::
    :::column:::
        sp_cursorunprepare
    :::column-end:::
    :::column:::
        sp_execute
    :::column-end:::
:::row-end:::  
:::row:::
    :::column:::
        sp_datatype_info
    :::column-end:::
    :::column:::
        sp_fkeys
    :::column-end:::
:::row-end:::  
:::row:::
    :::column:::
        sp_foreignkeys
    :::column-end:::
    :::column:::
        sp_indexes
    :::column-end:::
:::row-end:::  
:::row:::
    :::column:::
        sp_pkeys
    :::column-end:::
    :::column:::
        sp_primarykeys
    :::column-end:::
:::row-end:::  
:::row:::
    :::column:::
        sp_prepare
    :::column-end:::
    :::column:::
        sp_prepexec
    :::column-end:::
:::row-end:::  
:::row:::
    :::column:::
        sp_prepexecrpc
    :::column-end:::
    :::column:::
        sp_unprepare
    :::column-end:::
:::row-end:::  
:::row:::
    :::column:::
        sp_server_info
    :::column-end:::
    :::column:::
        sp_special_columns
    :::column-end:::
:::row-end:::  
:::row:::
    :::column:::
        sp_sproc_columns
    :::column-end:::
    :::column:::
        sp_statistics
    :::column-end:::
:::row-end:::  
:::row:::
    :::column:::
        sp_table_privileges
    :::column-end:::
    :::column:::
        sp_table_privileges_ex
    :::column-end:::
:::row-end:::  
:::row:::
    :::column:::
        sp_tables
    :::column-end:::
    :::column:::
        sp_tables_ex
    :::column-end:::
:::row-end:::

&nbsp;
  
Die folgenden gespeicherten Prozeduren sind nicht dokumentiert:  

:::row:::
    :::column:::
        sp_assemblies_rowset
    :::column-end:::
    :::column:::
        sp_assemblies_rowset_rmt
    :::column-end:::
:::row-end:::  
:::row:::
    :::column:::
        sp_assemblies_rowset2
    :::column-end:::
    :::column:::
        sp_assembly_dependencies_rowset
    :::column-end:::
:::row-end:::  
:::row:::
    :::column:::
        sp_assembly_dependencies_rowset_rmt
    :::column-end:::
    :::column:::
        sp_assembly_dependencies_rowset2
    :::column-end:::
:::row-end:::  
:::row:::
    :::column:::
        sp_bcp_dbcmptlevel
    :::column-end:::
    :::column:::
        sp_catalogs_rowset
    :::column-end:::
:::row-end:::  
:::row:::
    :::column:::
        sp_catalogs_rowset;2
    :::column-end:::
    :::column:::
        sp_catalogs_rowset;5
    :::column-end:::
:::row-end:::  
:::row:::
    :::column:::
        sp_catalogs_rowset_rmt
    :::column-end:::
    :::column:::
        sp_catalogs_rowset2
    :::column-end:::
:::row-end:::  
:::row:::
    :::column:::
        sp_check_constbytable_rowset
    :::column-end:::
    :::column:::
        sp_check_constbytable_rowset;2
    :::column-end:::
:::row-end:::  
:::row:::
    :::column:::
        sp_check_constbytable_rowset2
    :::column-end:::
    :::column:::
        sp_check_constraints_rowset
    :::column-end:::
:::row-end:::  
:::row:::
    :::column:::
        sp_check_constraints_rowset;2
    :::column-end:::
    :::column:::
        sp_check_constraints_rowset2
    :::column-end:::
:::row-end:::  
:::row:::
    :::column:::
        sp_column_privileges_rowset
    :::column-end:::
    :::column:::
        sp_column_privileges_rowset;2
    :::column-end:::
:::row-end:::  
:::row:::
    :::column:::
        sp_column_privileges_rowset;5
    :::column-end:::
    :::column:::
        sp_column_privileges_rowset_rmt
    :::column-end:::
:::row-end:::  
:::row:::
    :::column:::
        sp_column_privileges_rowset2
    :::column-end:::
    :::column:::
        sp_columns_90
    :::column-end:::
:::row-end:::  
:::row:::
    :::column:::
        sp_columns_90_rowset
    :::column-end:::
    :::column:::
        sp_columns_90_rowset_rmt
    :::column-end:::
:::row-end:::  
:::row:::
    :::column:::
        sp_columns_90_rowset2
    :::column-end:::
    :::column:::
        sp_columns_ex_90
    :::column-end:::
:::row-end:::  
:::row:::
    :::column:::
        sp_columns_rowset
    :::column-end:::
    :::column:::
        sp_columns_rowset;2
    :::column-end:::
:::row-end:::  
:::row:::
    :::column:::
        sp_columns_rowset;5
    :::column-end:::
    :::column:::
        sp_columns_rowset_rmt
    :::column-end:::
:::row-end:::  
:::row:::
    :::column:::
        sp_columns_rowset2
    :::column-end:::
    :::column:::
        sp_constr_col_usage_rowset
    :::column-end:::
:::row-end:::  
:::row:::
    :::column:::
        sp_datatype_info_90
    :::column-end:::
    :::column:::
        sp_ddopen;1
    :::column-end:::
:::row-end:::  
:::row:::
    :::column:::
        sp_ddopen;10
    :::column-end:::
    :::column:::
        sp_ddopen;11
    :::column-end:::
:::row-end:::  
:::row:::
    :::column:::
        sp_ddopen;12
    :::column-end:::
    :::column:::
        sp_ddopen;13
    :::column-end:::
:::row-end:::  
:::row:::
    :::column:::
        sp_ddopen;2
    :::column-end:::
    :::column:::
        sp_ddopen;3
    :::column-end:::
:::row-end:::  
:::row:::
    :::column:::
        sp_ddopen;4
    :::column-end:::
    :::column:::
        sp_ddopen;5
    :::column-end:::
:::row-end:::  
:::row:::
    :::column:::
        sp_ddopen;6
    :::column-end:::
    :::column:::
        sp_ddopen;7
    :::column-end:::
:::row-end:::  
:::row:::
    :::column:::
        sp_ddopen;8
    :::column-end:::
    :::column:::
        sp_ddopen;9
    :::column-end:::
:::row-end:::  
:::row:::
    :::column:::
        sp_foreign_keys_rowset
    :::column-end:::
    :::column:::
        sp_foreign_keys_rowset;2
    :::column-end:::
:::row-end:::  
:::row:::
    :::column:::
        sp_foreign_keys_rowset;3
    :::column-end:::
    :::column:::
        sp_foreign_keys_rowset;5
    :::column-end:::
:::row-end:::  
:::row:::
    :::column:::
        sp_foreign_keys_rowset_rmt
    :::column-end:::
    :::column:::
        sp_foreign_keys_rowset2
    :::column-end:::
:::row-end:::  
:::row:::
    :::column:::
        sp_foreign_keys_rowset3
    :::column-end:::
    :::column:::
        sp_indexes_90_rowset
    :::column-end:::
:::row-end:::  
:::row:::
    :::column:::
        sp_indexes_90_rowset_rmt
    :::column-end:::
    :::column:::
        sp_indexes_90_rowset2
    :::column-end:::
:::row-end:::  
:::row:::
    :::column:::
        sp_indexes_rowset
    :::column-end:::
    :::column:::
        sp_indexes_rowset;2
    :::column-end:::
:::row-end:::  
:::row:::
    :::column:::
        sp_indexes_rowset;5
    :::column-end:::
    :::column:::
        sp_indexes_rowset_rmt
    :::column-end:::
:::row-end:::  
:::row:::
    :::column:::
        sp_indexes_rowset2
    :::column-end:::
    :::column:::
        sp_linkedservers_rowset
    :::column-end:::
:::row-end:::  
:::row:::
    :::column:::
        sp_linkedservers_rowset;2
    :::column-end:::
    :::column:::
        sp_linkedservers_rowset2
    :::column-end:::
:::row-end:::  
:::row:::
    :::column:::
        sp_oledb_database
    :::column-end:::
    :::column:::
        sp_oledb_defdb
    :::column-end:::
:::row-end:::  
:::row:::
    :::column:::
        sp_oledb_deflang
    :::column-end:::
    :::column:::
        sp_oledb_language
    :::column-end:::
:::row-end:::  
:::row:::
    :::column:::
        sp_oledb_ro_usrname
    :::column-end:::
    :::column:::
        sp_primary_keys_rowset
    :::column-end:::
:::row-end:::  
:::row:::
    :::column:::
        sp_primary_keys_rowset;2
    :::column-end:::
    :::column:::
        sp_primary_keys_rowset;3
    :::column-end:::
:::row-end:::  
:::row:::
    :::column:::
        sp_primary_keys_rowset;5
    :::column-end:::
    :::column:::
        sp_primary_keys_rowset_rmt
    :::column-end:::
:::row-end:::  
:::row:::
    :::column:::
        sp_primary_keys_rowset2
    :::column-end:::
    :::column:::
        sp_procedure_params_90_rowset
    :::column-end:::
:::row-end:::  
:::row:::
    :::column:::
        sp_procedure_params_90_rowset2
    :::column-end:::
    :::column:::
        sp_procedure_params_rowset
    :::column-end:::
:::row-end:::  
:::row:::
    :::column:::
        sp_procedure_params_rowset;2
    :::column-end:::
    :::column:::
        sp_procedure_params_rowset2
    :::column-end:::
:::row-end:::  
:::row:::
    :::column:::
        sp_procedures_rowset
    :::column-end:::
    :::column:::
        sp_procedures_rowset;2
    :::column-end:::
:::row-end:::  
:::row:::
    :::column:::
        sp_procedures_rowset2
    :::column-end:::
    :::column:::
        sp_provider_types_90_rowset
    :::column-end:::
:::row-end:::  
:::row:::
    :::column:::
        sp_provider_types_rowset
    :::column-end:::
    :::column:::
        sp_schemata_rowset
    :::column-end:::
:::row-end:::  
:::row:::
    :::column:::
        sp_schemata_rowset;3
    :::column-end:::
    :::column:::
        sp_special_columns_90
    :::column-end:::
:::row-end:::  
:::row:::
    :::column:::
        sp_sproc_columns_90
    :::column-end:::
    :::column:::
        sp_statistics_rowset
    :::column-end:::
:::row-end:::  
:::row:::
    :::column:::
        sp_statistics_rowset;2
    :::column-end:::
    :::column:::
        sp_statistics_rowset2
    :::column-end:::
:::row-end:::  
:::row:::
    :::column:::
        sp_stored_procedures
    :::column-end:::
    :::column:::
        sp_table_constraints_rowset
    :::column-end:::
:::row-end:::  
:::row:::
    :::column:::
        sp_table_constraints_rowset;2
    :::column-end:::
    :::column:::
        sp_table_constraints_rowset2
    :::column-end:::
:::row-end:::  
:::row:::
    :::column:::
        sp_table_privileges_rowset
    :::column-end:::
    :::column:::
        sp_table_privileges_rowset;2
    :::column-end:::
:::row-end:::  
:::row:::
    :::column:::
        sp_table_privileges_rowset;5
    :::column-end:::
    :::column:::
        sp_table_privileges_rowset_rmt
    :::column-end:::
:::row-end:::  
:::row:::
    :::column:::
        sp_table_privileges_rowset2
    :::column-end:::
    :::column:::
        sp_table_statistics_rowset
    :::column-end:::
:::row-end:::  
:::row:::
    :::column:::
        sp_table_statistics_rowset;2
    :::column-end:::
    :::column:::
        sp_table_statistics2_rowset
    :::column-end:::
:::row-end:::  
:::row:::
    :::column:::
        sp_tablecollations
    :::column-end:::
    :::column:::
        sp_tablecollations_90
    :::column-end:::
:::row-end:::  
:::row:::
    :::column:::
        sp_tables_info_90_rowset
    :::column-end:::
    :::column:::
        sp_tables_info_90_rowset_64
    :::column-end:::
:::row-end:::  
:::row:::
    :::column:::
        sp_tables_info_90_rowset2
    :::column-end:::
    :::column:::
        sp_tables_info_90_rowset2_64
    :::column-end:::
:::row-end:::  
:::row:::
    :::column:::
        sp_tables_info_rowset
    :::column-end:::
    :::column:::
        sp_tables_info_rowset;2
    :::column-end:::
:::row-end:::  
:::row:::
    :::column:::
        sp_tables_info_rowset_64
    :::column-end:::
    :::column:::
        sp_tables_info_rowset_64;2
    :::column-end:::
:::row-end:::  
:::row:::
    :::column:::
        sp_tables_info_rowset2
    :::column-end:::
    :::column:::
        sp_tables_info_rowset2_64
    :::column-end:::
:::row-end:::  
:::row:::
    :::column:::
        sp_tables_rowset;2
    :::column-end:::
    :::column:::
        sp_tables_rowset;5
    :::column-end:::
:::row-end:::  
:::row:::
    :::column:::
        sp_tables_rowset_rmt
    :::column-end:::
    :::column:::
        sp_tables_rowset2
    :::column-end:::
:::row-end:::  
:::row:::
    :::column:::
        sp_usertypes_rowset
    :::column-end:::
    :::column:::
        sp_usertypes_rowset_rmt
    :::column-end:::
:::row-end:::  
:::row:::
    :::column:::
        sp_usertypes_rowset2
    :::column-end:::
    :::column:::
        sp_views_rowset
    :::column-end:::
:::row-end:::  
:::row:::
    :::column:::
        sp_views_rowset2
    :::column-end:::
    :::column:::
        sp_xml_schema_rowset
    :::column-end:::
:::row-end:::  
:::row:::
    :::column:::
        sp_xml_schema_rowset2
    :::column-end:::
    :::column:::
    :::column-end:::
:::row-end:::  

## <a name="see-also"></a>Weitere Informationen  
 [CREATE PROCEDURE &#40;Transact-SQL&#41;](../../t-sql/statements/create-procedure-transact-sql.md)   
 [Gespeicherte Prozeduren &#40;Datenbank-Engine&#41;](../../relational-databases/stored-procedures/stored-procedures-database-engine.md)   
 [Ausführen gespeicherter Prozeduren &#40;OLE DB&#41;](../../relational-databases/native-client/ole-db/stored-procedures-running.md)   
 [Gespeicherte Prozeduren](../../relational-databases/native-client-odbc-stored-procedures/running-stored-procedures.md)   
 [Datenbank-Engine gespeicherter Prozeduren &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/database-engine-stored-procedures-transact-sql.md)   
 [Ausführen gespeicherter Prozeduren](../../relational-databases/native-client-odbc-stored-procedures/running-stored-procedures.md)  
  
  
