---
title: Sys.Databases (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/09/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- databases
- databases_TSQL
- sys.databases
- sys.databases_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.databases catalog view
ms.assetid: 46c288c1-3410-4d68-a027-3bbf33239289
author: stevestein
ms.author: sstein
manager: craigg
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 627ed438618e48e8c43a46a0874c9b4fb46fe744
ms.sourcegitcommit: f62f70298651d6223fa5d215b6a7a0d2ffecbd0d
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/19/2018
ms.locfileid: "51947744"
---
# <a name="sysdatabases-transact-sql"></a>sys.databases (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

Enthält eine Zeile für jede Datenbank in der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Instanz.  
  
Wenn eine Datenbank nicht `ONLINE`, oder `AUTO_CLOSE` nastaven NA hodnotu `ON` und die Datenbank geschlossen wird, können die Werte einiger Spalten sein `NULL`. Wenn eine Datenbank ist `OFFLINE`, die entsprechende Zeile ist nicht für Benutzer mit geringen Privilegien sichtbar. Die entsprechende Zeile angezeigt, wenn die Datenbank ist `OFFLINE`, Benutzer benötigen mindestens die `ALTER ANY DATABASE` Berechtigung auf Serverebene, oder die `CREATE DATABASE` -Berechtigung für die `master` Datenbank.  
  
|Spaltenname|Datentyp|Description|  
|-----------------|---------------|-----------------|  
|**name**|**sysname**|Name der Datenbank, eindeutig innerhalb einer Instanz von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] oder innerhalb eines [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)]servers.|  
|**database_id**|**int**|ID der Datenbank, eindeutig innerhalb einer Instanz von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] oder innerhalb eines [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)]servers.|  
|**source_database_id**|**int**|Ungleich NULL = ID der Quelldatenbank dieser Datenbankmomentaufnahme.<br /> NULL = Keine Datenbankmomentaufnahme.|  
|**owner_sid**|**varbinary(85)**|SID (Sicherheits-ID) des externen Besitzers der Datenbank gemäß Registrierung beim Server. Weitere Informationen zu eine Datenbank besitzen können, finden Sie unter den **ALTER AUTHORIZATION für Datenbanken** Abschnitt [ALTER AUTHORIZATION](../../t-sql/statements/alter-authorization-transact-sql.md).|  
|**create_date**|**datetime**|Datum der Erstellung oder Umbenennung der Datenbank. Für **Tempdb**, dieser Wert ändert sich jedes Mal, wenn der Server neu gestartet.|  
|**compatibility_level**|**tinyint**|Ganze Zahl, die der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Version entspricht, deren Verhalten kompatibel ist:<br /> **Wert** &#124; **gilt für**<br /> 70 &#124; [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] über [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)]<br /> 80 &#124; [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] über [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)]<br /> 90 &#124; [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] über [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)]<br /> 100 &#124; [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] über [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] und [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)]<br /> 110 &#124; [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] über [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] und [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)]<br /> 120 &#124; [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] über [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] und [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)]<br /> 130 &#124; [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] über [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]<br /> 140 &#124; [!INCLUDE[ssSQL17](../../includes/sssql17-md.md)] über [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] <br /> 150&#124; [!INCLUDE[sql-server-2019](../../includes/sssqlv15-md.md)]  |  
|**collation_name**|**sysname**|Sortierung der Datenbank. Dient als Standardsortierung der Datenbank.<br /> NULL = Datenbank ist nicht online, oder AUTO_CLOSE auf ON festgelegt ist, und die Datenbank geschlossen.|  
|**user_access**|**tinyint**|Einstellung für den Benutzerzugriff:<br /> 0 = MULTI_USER angegeben<br /> 1 = SINGLE_USER angegeben<br /> 2 = RESTRICTED_USER angegeben|  
|**user_access_desc**|**nvarchar(60)**|Beschreibung der Einstellung für den Benutzerzugriff.|  
|**is_read_only**|**bit**|1 = Datenbank ist READ_ONLY<br /> 0 = Datenbank ist READ_WRITE|  
|**is_auto_close_on**|**bit**|1 = AUTO_CLOSE ist ON<br /> 0 = AUTO_CLOSE ist OFF|  
|**is_auto_shrink_on**|**bit**|1 = AUTO_SHRINK ist ON<br /> 0 = AUTO_SHRINK ist OFF|  
|**state**|**tinyint**|**Wert &#124; gilt für**<br /> 0 = ONLINE <br /> 1 = RESTORING <br /> 2 = beim Wiederherstellen eines &#124; [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] über [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]<br /> 3 = RECOVERY_PENDING &#124; [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] über [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]<br /> 4 = SUSPECT <br /> 5 = EMERGENCY &#124; [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] über [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]<br /> 6 = OFFLINE &#124; [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] über [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]<br /> 7 = KOPIEREN&AMP;#124; [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)] [!INCLUDE[ssGeoDR](../../includes/ssgeodr-md.md)] <br /> 10 = OFFLINE_SECONDARY&AMP;#124; [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)] [!INCLUDE[ssGeoDR](../../includes/ssgeodr-md.md)] <br /><br /> **Hinweis**: Abfragen für Always On-Datenbanken, die `database_state` oder `database_state_desc` Spalten [Sys. dm_hadr_database_replica_states](../../relational-databases/system-dynamic-management-views/sys-dm-hadr-database-replica-states-transact-sql.md).|  
|**state_desc**|**nvarchar(60)**|Beschreibung des Datenbankstatus. Status wird angezeigt.|  
|**is_in_standby**|**bit**|Datenbank ist für die Wiederherstellungsprotokollierung schreibgeschützt.|  
|**is_cleanly_shutdown**|**bit**|1 = Datenbank wurde ordnungsgemäß heruntergefahren, keine Wiederherstellung beim Starten erforderlich<br /> 0 = Datenbank wurde nicht ordnungsgemäß heruntergefahren, Wiederherstellung beim Starten erforderlich|  
|**is_supplemental_logging_enabled**|**bit**|1 = SUPPLEMENTAL_LOGGING ist ON<br /> 0 = SUPPLEMENTAL_LOGGING ist OFF|  
|**snapshot_isolation_state**|**tinyint**|Status zulässiger Momentaufnahme-Isolationstransaktionen gemäß Einstellung der ALLOW_SNAPSHOT_ISOLATION-Option:<br /> 0 = Momentaufnahmeisolationsstatus ist OFF (Standardeinstellung). Momentaufnahmeisolation ist unzulässig.<br /> 1 = Momentaufnahmeisolationsstatus ist ON. Momentaufnahmeisolation ist zulässig.<br /> 2 = Momentaufnahmeisolationsstatus ist im Übergang zum Status OFF. Die Änderungen aller Transaktionen sind versionsspezifisch. Neue Transaktionen können nicht mit der Momentaufnahmeisolation gestartet werden. Die Datenbank bleibt im Übergang zum Status OFF, bis alle Transaktionen, die beim Ausführen von ALTER DATABASE aktiv waren, abgeschlossen werden können.<br /> 3 = Momentaufnahmeisolationsstatus ist im Übergang zum Status ON. Die Änderungen neuer Transaktionen sind versionsspezifisch. Transaktionen können die Momentaufnahmeisolation erst verwenden, wenn der Status der Momentaufnahmeisolation zu 1 (ON) wechselt. Die Datenbank bleibt im Übergang zum Status ON, bis alle Updatetransaktionen, die beim Ausführen von ALTER DATABASE aktiv waren, abgeschlossen werden können.|  
|**snapshot_isolation_state_desc**|**nvarchar(60)**|Beschreibung des Status zulässiger Momentaufnahme-Isolationstransaktionen gemäß Einstellung der ALLOW_SNAPSHOT_ISOLATION-Option.|  
|**is_read_committed_snapshot_on**|**bit**|1 = Die READ_COMMITTED_SNAPSHOT-Option ist ON. Lesevorgänge unter der Isolationsstufe 'read-committed' basieren auf Momentaufnahmescans und aktivieren keine Sperren.<br /> 0 = Die READ_COMMITTED_SNAPSHOT-Option ist OFF (Standardeinstellung). Lesevorgänge unter der Isolationsstufe 'read-committed' verwenden gemeinsame Sperren.|  
|**recovery_model**|**tinyint**|Ausgewähltes Wiederherstellungsmodell:<br /> 1 = FULL<br /> 2 = BULK_LOGGED<br /> 3 = SIMPLE|  
|**recovery_model_desc**|**nvarchar(60)**|Beschreibung des ausgewählten Wiederherstellungsmodells.|  
|**page_verify_option**|**tinyint**|Einstellung der PAGE_VERIFY-Option:<br /> 0 = NONE<br /> 1 = TORN_PAGE_DETECTION<br /> 2 = CHECKSUM|  
|**page_verify_option_desc**|**nvarchar(60)**|Beschreibung der Einstellung der PAGE_VERIFY-Option.|  
|**is_auto_create_stats_on**|**bit**|1 = AUTO_CREATE_STATISTICS ist ON<br /> 0 = AUTO_CREATE_STATISTICS ist OFF|  
|**is_auto_create_stats_incremental_on**|**bit**|Gibt die Standardeinstellung für die Option zur inkrementellen Auto Stats-Erstellung an.<br /> 0 = Die Auto Stats-Erstellung ist nicht inkrementell<br /> 1 = Die Auto Stats-Erstellung ist inkrementell, falls möglich<br /> **Gilt für**: [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] bis [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].|  
|**is_auto_update_stats_on**|**bit**|1 = AUTO_UPDATE_STATISTICS ist ON<br /> 0 = AUTO_UPDATE_STATISTICS ist OFF|  
|**is_auto_update_stats_async_on**|**bit**|1 = AUTO_UPDATE_STATISTICS_ASYNC ist ON<br /> 0 = AUTO_UPDATE_STATISTICS_ASYNC ist OFF|  
|**is_ansi_null_default_on**|**bit**|1 = ANSI_NULL_DEFAULT ist ON<br /> 0 = ANSI_NULL_DEFAULT ist OFF|  
|**is_ansi_null_on**|**bit**|1 = ANSI_NULLS ist ON<br /> 0 = ANSI_NULLS ist OFF|  
|**is_ansi_padding_on**|**bit**|1 = ANSI_PADDING ist ON<br /> 0 = ANSI_PADDING ist OFF|  
|**is_ansi_warnings_on**|**bit**|1 = ANSI_WARNINGS ist ON<br /> 0 = ANSI_WARNINGS ist OFF|  
|**is_arithabort_on**|**bit**|1 = ARITHABORT ist ON<br /> 0 = ARITHABORT ist OFF|  
|**is_concat_null_yields_null_on**|**bit**|1 = CONCAT_NULL_YIELDS_NULL ist ON<br /> 0 = CONCAT_NULL_YIELDS_NULL ist OFF|  
|**is_numeric_roundabort_on**|**bit**|1 = NUMERIC_ROUNDABORT ist ON<br /> 0 = NUMERIC_ROUNDABORT ist OFF|  
|**is_quoted_identifier_on**|**bit**|1 = QUOTED_IDENTIFIER ist ON<br /> 0 = QUOTED_IDENTIFIER ist OFF|  
|**is_recursive_triggers_on**|**bit**|1 = RECURSIVE_TRIGGERS ist ON<br /> 0 = RECURSIVE_TRIGGERS ist OFF|  
|**is_cursor_close_on_commit_on**|**bit**|1 = CURSOR_CLOSE_ON_COMMIT ist ON<br /> 0 = CURSOR_CLOSE_ON_COMMIT ist OFF|  
|**is_local_cursor_default**|**bit**|1 = CURSOR_DEFAULT ist lokal<br /> 0 = CURSOR_DEFAULT ist global|  
|**is_fulltext_enabled**|**bit**|1 = Volltext ist für die Datenbank aktiviert<br /> 0 = Volltext ist für die Datenbank deaktiviert|  
|**is_trustworthy_on**|**bit**|1 = Datenbank wurde als vertrauenswürdig gekennzeichnet<br /> 0 = Datenbank wurde nicht als vertrauenswürdig gekennzeichnet|  
|**is_db_chaining_on**|**bit**|1 = Datenbankübergreifende Besitzverkettung ist ON<br /> 0 = Datenbankübergreifende Besitzverkettung ist OFF|  
|**is_parameterization_forced**|**bit**|1 = Parametrisierung ist FORCED<br /> 0 = Parametrisierung ist SIMPLE|  
|**is_master_key_encrypted_by_server**|**bit**|1 = Datenbank verfügt über verschlüsselten Hauptschlüssel<br /> 0 = Datenbank verfügt nicht über verschlüsselten Hauptschlüssel|  
|**is_query_store_on**|**bit**|1 = die Abfrage Speicher ist für diese Datenbank aktivieren. Überprüfen Sie [database_query_store_options](../../relational-databases/system-catalog-views/sys-database-query-store-options-transact-sql.md) Anzeigen des Status der Abfrage-Store.<br /> 0 = die Abfrage speichern ist nicht aktiviert.<br /> **Gilt für**: [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ([!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] bis [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]).|  
|**is_published**|**bit**|1 = Datenbank ist eine Veröffentlichungsdatenbank in einer Transaktions- oder Momentaufnahme-Replikationstopologie<br /> 0 = Keine Veröffentlichungsdatenbank|  
|**is_subscribed**|**bit**|Diese Spalte wird nicht verwendet. Gibt immer 0 zurück, unabhängig vom Abonnentenstatus der Datenbank.|  
|**is_merge_published**|**bit**|1 = Datenbank ist eine Veröffentlichungsdatenbank in einer Mergereplikationstopologie<br /> 0 = Keine Veröffentlichungsdatenbank in einer Mergereplikationstopologie|  
|**is_distributor**|**bit**|1 = Datenbank ist die Verteilungsdatenbank für eine Replikationstopologie<br /> 0 = Ist nicht die Verteilungsdatenbank für eine Replikationstopologie|  
|**is_sync_with_backup**|**bit**|1 = Datenbank ist für die Replikationssynchronisierung mit Sicherung gekennzeichnet<br /> 0 = Ist nicht für die Replikationssynchronisierung mit Sicherung gekennzeichnet|  
|**service_broker_guid**|**uniqueidentifier**|Bezeichner von Service Broker für diese Datenbank. Verwendet als die **Broker_instance** des Ziels in der Routingtabelle.|  
|**is_broker_enabled**|**bit**|1 = Der Broker in dieser Datenbank sendet und empfängt derzeit Nachrichten.<br /> 0 = Alle gesendeten Nachrichten bleiben in der Übertragungswarteschlange, und empfangene Nachrichten werden in dieser Datenbank nicht in Warteschlangen eingereiht.<br /> Bei wiederhergestellten oder angefügten Datenbanken ist der Broker standardmäßig deaktiviert. Die Ausnahme hiervon ist die Datenbankspiegelung, bei der der Broker nach einem Failover aktiviert wird.|  
|**log_reuse_wait**|**tinyint**|Wiederverwendung von Transaktionsprotokollspeicher wird auf eine der folgenden Ereignisse ab dem letzten Prüfpunkt gewartet. Ausführlichere Erklärungen dieser Werte finden Sie unter [das Transaktionsprotokoll](../../relational-databases/logs/the-transaction-log-sql-server.md).<br /> **Wert &#124; gilt für**<br /> 0 = Nichts<br />   1 = Prüfpunkt (Wenn eine Datenbank ein Wiederherstellungsmodell verwendet und eine Speicheroptimierte Datendateigruppe aufweist, Sie sollte aber in der `log_reuse_wait` die Spalte an, Prüfpunkt oder Xtp_checkpoint.) &#124; [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] über [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]<br />  2 = protokollsicherung &#124; [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] über [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]<br />  3 = aktive Sicherung oder Wiederherstellung &#124; [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] über [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]<br />  4 = aktive Transaktion &#124; [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] über [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]<br />  5 = datenbankspiegelung &#124; [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] über [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]<br />  6 = Replikation &#124; [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] über [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]<br />  7 = Erstellung der Datenbankmomentaufnahme &#124; [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] über [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]<br />  8 = Protokollscan <br />  9 = ein Always On Availability Groups sekundären-Replikat wendet Transaktionsprotokoll-Datensätze dieser Datenbank auf eine zugehörige sekundäre Datenbank. &#124;[!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] über [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]<br />  9 = Sonstiges (vorübergehend) & #124 bis zur und einschließlich [!INCLUDE[ssKilimanjaro](../../includes/ssKilimanjaro-md.md)]<br />  10 = nur zur internen Verwendung &#124; [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] über [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]<br />  11 = nur zur internen Verwendung &#124; [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] über [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]<br /> 12 = nur zur internen Verwendung &#124; [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] über [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]<br />13 = älteste Seite &#124; [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] über [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]<br /> 14 = andere &#124; [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] über [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]<br />  16 = XTP_CHECKPOINT (Wenn eine Datenbank ein Wiederherstellungsmodell verwendet und eine Speicheroptimierte Datendateigruppe aufweist, erwarten, zu der Spalte Log_reuse_wait der Prüfpunkt oder Xtp_checkpoint angezeigt.) &#124; [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] über [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]|  
|**log_reuse_wait_desc**|**nvarchar(60)**|Bei der Beschreibung der Wiederverwendung von Transaktionsprotokollspeicher wird derzeit auf eines der folgenden Ereignisse ab dem letzten Prüfpunkt gewartet.|  
|**is_date_correlation_on**|**bit**|1 = DATE_CORRELATION_OPTIMIZATION ist ON<br /> 0 = DATE_CORRELATION_OPTIMIZATION ist OFF|  
|**is_cdc_enabled**|**bit**|1 = Datenbank ist für Change Data Capture aktiviert. Weitere Informationen finden Sie unter [sp_cdc_enable_db &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sys-sp-cdc-enable-db-transact-sql.md).|  
|**is_encrypted**|**bit**|Gibt an, ob die Datenbank verschlüsselt ist (gibt den zuletzt mit festgelegten Status wieder der `ALTER DATABASE SET ENCRYPTION` Klausel). Kann einer der folgenden Werte sein:<br /> 1 = Verschlüsselt.<br /> 0 = Nicht verschlüsselt<br /> Weitere Informationen zur Datenbankverschlüsselung finden Sie unter [Transparent Data Encryption &#40;TDE&#41;](../../relational-databases/security/encryption/transparent-data-encryption.md).<br /> Wenn die Datenbank gerade entschlüsselt wird, `is_encrypted` zeigt den Wert 0. Sie können den Status der Verschlüsselungsstatus des Prozesses anzeigen, indem Sie mit der [Sys. dm_database_encryption_keys](../../relational-databases/system-dynamic-management-views/sys-dm-database-encryption-keys-transact-sql.md) dynamische verwaltungssicht.|  
|**is_honor_broker_priority_on**|**bit**|Gibt an, ob die Datenbank konversationsprioritäten berücksichtigt (gibt den zuletzt mit festgelegten Status wieder der `ALTER DATABASE SET HONOR_BROKER_PRIORITY` Klausel). Kann einer der folgenden Werte sein:<br /> 1 = HONOR_BROKER_PRIORITY ist ON<br /> 0 = HONOR_BROKER_PRIORITY ist OFF|  
|**replica_id**|**uniqueidentifier**|Eindeutiger Bezeichner des lokalen [!INCLUDE[ssHADR](../../includes/sshadr-md.md)]-Verfügbarkeitsreplikats der Verfügbarkeitsgruppe, an der die Datenbank ggf. teilnimmt.<br /> NULL = Datenbank ist kein Teil eines Verfügbarkeitsreplikats einer Verfügbarkeitsgruppe<br /> **Gilt für**: [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ([!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] über [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]) und [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)]|  
|**group_database_id**|**uniqueidentifier**|Eindeutiger Bezeichner der Datenbank in einer Always On-verfügbarkeitsgruppe sein, sofern vorhanden, in dem die Datenbank enthalten ist. **group_database_id** ist für diese Datenbank auf dem primären Replikat und jedem sekundären Replikat, auf dem die Datenbank der Verfügbarkeitsgruppe hinzugefügt wurde, identisch.<br /> NULL = Datenbank ist kein Teil eines Verfügbarkeitsreplikats einer beliebigen Verfügbarkeitsgruppe<br /> **Gilt für**: [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ([!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] über [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]) und [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)]|  
|**resource_pool_id**|**int**|Die ID des Ressourcenpools, der dieser Datenbank zugeordnet ist. Dieser Ressourcenpool steuert den insgesamt für speicheroptimierte Tabellen in dieser Datenbank verfügbaren Arbeitsspeicher.<br /> **Gilt für** : [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] bis [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]|  
|**default_language_lcid**|**smallint**|Gibt die lokale ID (lcid) der Standardsprache einer eigenständigen Datenbank an.<br /> **Hinweis**: Fungiert als die [Konfigurieren der Serverkonfigurationsoption Standardsprache](../../database-engine/configure-windows/configure-the-default-language-server-configuration-option.md) von `sp_configure`. Dieser Wert ist **null** für eine nicht enthaltene Datenbank.<br /> **Gilt für**: [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ([!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] über [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]) und [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)]|  
|**default_language_name**|**nvarchar(128)**|Gibt die Standardsprache einer eigenständigen Datenbank an.<br /> Dieser Wert ist **null** für eine nicht enthaltene Datenbank.<br /> **Gilt für**: [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ([!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] über [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]) und [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)]|  
|**default_fulltext_language_lcid**|**int**|Gibt die Gebietsschema-Id (Lcid) der Standard-Volltextsprache der eigenständigen Datenbank an.<br /> **Hinweis**: Fungiert als Standard [Konfigurieren der Serverkonfigurationsoption von Volltext-Standardsprache](../../database-engine/configure-windows/configure-the-default-full-text-language-server-configuration-option.md) von `sp_configure`. Dieser Wert ist **null** für eine nicht enthaltene Datenbank.<br /> **Gilt für**: [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ([!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] über [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]) und [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)]|  
|**default_fulltext_language_name**|**nvarchar(128)**|Gibt die Standard-Volltextsprache der eigenständigen Datenbank an.<br /> Dieser Wert ist **null** für eine nicht enthaltene Datenbank.<br /> **Gilt für**: [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ([!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] über [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]) und [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)]|  
|**is_nested_triggers_on**|**bit**|Gibt an, ob geschachtelte Trigger in der eigenständigen Datenbank zulässig sind.<br /> 0 = Geschachtelte Trigger sind nicht zulässig<br /> 1 = Geschachtelte Trigger sind zulässig<br /> **Hinweis**: Fungiert als die [Konfigurieren der Serverkonfigurationsoption für geschachtelte Trigger](../../database-engine/configure-windows/configure-the-nested-triggers-server-configuration-option.md) von `sp_configure`. Dieser Wert ist **null** für eine nicht enthaltene Datenbank. Finden Sie unter [sys.configurations &#40;Transact-SQL&#41; ](../../relational-databases/system-catalog-views/sys-configurations-transact-sql.md) für Weitere Informationen zu erhalten.<br /> **Gilt für**: [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ([!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] über [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]) und [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)]|  
|**is_transform_noise_words_on**|**bit**|Gibt an, ob Füllwörter in der eigenständigen Datenbank transformiert werden sollen.<br /> 0 = Füllwörter sollten nicht transformiert werden<br /> 1 = Füllwörter sollten transformiert werden<br /> **Hinweis**: Fungiert als die [Füllwörtertransformation Serverkonfigurationsoption](../../database-engine/configure-windows/transform-noise-words-server-configuration-option.md) von `sp_configure`. Dieser Wert ist **null** für eine nicht enthaltene Datenbank. Finden Sie unter [sys.configurations &#40;Transact-SQL&#41; ](../../relational-databases/system-catalog-views/sys-configurations-transact-sql.md) für Weitere Informationen zu erhalten.<br /> **Gilt für** : [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] bis [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]|  
|**two_digit_year_cutoff**|**smallint**|Gibt einen Wert zwischen 1753 und 9999 an, der das Umstellungsjahr für das Interpretieren zweistelliger Jahre als vierstellige Jahre darstellt.<br /> **Hinweis**: Fungiert als die [konfigurieren two Digit Year cutoff Server Configuration Option](../../database-engine/configure-windows/configure-the-two-digit-year-cutoff-server-configuration-option.md) von `sp_configure`. Dieser Wert ist **null** für eine nicht enthaltene Datenbank. Finden Sie unter [sys.configurations &#40;Transact-SQL&#41; ](../../relational-databases/system-catalog-views/sys-configurations-transact-sql.md) für Weitere Informationen zu erhalten.<br /> **Gilt für**: [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ([!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] über [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]) und [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)]|  
|**containment**|**Tinyint, die nicht null**|Zeigt den Kapselungsstatus der Datenbank an.<br />  0 = Datenbankkapselung ist deaktiviert. **Gilt für**: [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ([!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] über [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]) und [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)]<br /> 1 = Datenbank ist in teilkapselung **gilt für**: [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] über [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]|  
|**containment_desc**|**nvarchar(60) nicht null**|Zeigt den Kapselungsstatus der Datenbank an.<br /> NONE = Legacydatenbank (keine Kapselung)<br /> PARTIAL = Teilweise eigenständige Datenbank<br /> **Gilt für**: [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ([!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] über [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]) und [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)]|  
|**target_recovery_time_in_seconds**|**int**|Die geschätzte Zeit zum Wiederherstellen der Datenbank in Sekunden. NULL-Werte sind zulässig.<br /> **Gilt für**: [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ([!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] über [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]) und [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)]|  
|**delayed_durability**|**int**|Die verzögerte Dauerhaftigkeit-Einstellung:<br /> 0 = DEAKTIVIERT<br /> 1 = ZULÄSSIG<br /> 2 = ERZWUNGENES<br /> Weitere Informationen finden Sie im Thema [Steuern der Transaktionsdauerhaftigkeit](../../relational-databases/logs/control-transaction-durability.md).<br /> **Gilt für**: [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ([!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] bis [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]) und [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)].|  
|**delayed_durability_desc**|**nvarchar(60)**|Die verzögerte Dauerhaftigkeit-Einstellung:<br /> DISABLED<br /> ALLOWED<br /> FORCED<br /> **Gilt für**: [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ([!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] bis [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]) und [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)].|  
|**memory_optimized_elevate_to_snapshot**|**bit**|Auf speicheroptimierte Tabellen wird mit der SNAPSHOT-Isolation zugegriffen, wenn die Sitzungseinstellung TRANSACTION ISOLATION LEVEL auf eine niedrigere Isolationsstufe festgelegt ist (READ COMMITTED oder READ UNCOMMITTED).<br /> 1 = Isolationsstufe ist mindestens SNAPSHOT.<br /> 0 = Isolationsstufe ist nicht erhöht.|  
|**is_federation_member**|**bit**|Gibt an, ob die Datenbank Mitglied eines Verbunds ist.<br /> **Gilt für:** [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)]|  
|**is_remote_data_archive_enabled**|**bit**|Gibt an, ob die Datenbank gestreckt wird.<br /> 0 = die Datenbank ist nicht für die Stretch-aktivierten.<br /> 1 = die Datenbank ist Stretch-aktivierten.<br /> **Gilt für** : [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] bis [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]<br /> Weitere Informationen finden Sie unter [Stretch Database](../../sql-server/stretch-database/stretch-database.md).|  
|**is_mixed_page_allocation_on**|**bit**|Gibt an, ob Tabellen und Indizes in der Datenbank erste Seiten aus gemischten Blöcken zugewiesen werden können.<br /> 0 = der Tabellen und Indizes in der Datenbank zuordnen erste Seiten immer aus gleichartigen Blöcken.<br /> 1 = der Tabellen und Indizes in der Datenbank können erste Seiten aus gemischten Blöcken zugeordnet.<br /> **Gilt für** : [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] bis [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]<br /> Weitere Informationen finden Sie unter der Option SET MIXED_PAGE_ALLOCATION von [ALTER DATABASE SET Options &#40;Transact-SQL&#41;](../../t-sql/statements/alter-database-transact-sql-set-options.md).|  
|**is_temporal_retention_enabled**|**bit**|Gibt an, ob der Task ' Verlaufscleanup ' der temporalen Beibehaltung-Richtlinie aktiviert ist.<br /> **Gilt für:** [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)]|
|**catalog_collation_type**|**int**|Die sortierungseinstellung für den Katalog:<br />0 = DATABASE_DEFAULT<br />2 = SQL_Latin_1_General_CP1_CI_AS<br /> **Gilt für:** [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)]|
|**catalog_collation_type_desc**|**nvarchar(60)**|Die sortierungseinstellung für den Katalog:<br />DATABASE_DEFAULT<br />SQL_Latin_1_General_CP1_CI_AS<br /> **Gilt für:** [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)]|
  
## <a name="permissions"></a>Berechtigungen  
 Wenn der Aufrufer `sys.databases` ist nicht der Besitzer der Datenbank und die Datenbank ist nicht `master` oder `tempdb`, mindestens die Berechtigung erforderlich, um die entsprechende Zeile finden Sie unter `ALTER ANY DATABASE` oder `VIEW ANY DATABASE` Berechtigung auf Serverebene oder `CREATE DATABASE` -Berechtigung für die `master` Datenbank. Die Datenbank, mit denen der Aufrufer verbunden ist, immer in angezeigt werden kann `sys.databases`.  
  
> [!IMPORTANT]  
> Die public-Rolle verfügt standardmäßig über die `VIEW ANY DATABASE` -Berechtigung, sodass alle Anmeldenamen auf Datenbankinformationen. Eine Anmeldung über die Fähigkeit zum Erkennen von einer Datenbank blockiert `REVOKE` der `VIEW ANY DATABASE` Berechtigung `public`, oder `DENY` der `VIEW ANY DATABASE` Berechtigung für einzelne Anmeldenamen.  
  
## <a name="azure-sql-database-remarks"></a>Azure SQL-Datenbank "Hinweise"  
In [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)] in dieser Ansicht finden Sie in der `master` Datenbank und in Benutzerdatenbanken. In der `master` -Datenbank in dieser Ansicht gibt die Informationen zu den `master` und alle Benutzerdatenbanken auf dem Server. In einer Benutzerdatenbank gibt diese Sicht Informationen nur in der aktuellen Datenbank und der master-Datenbank zurück.  
  
 Verwenden Sie die `sys.databases`-Sicht in der `master`-Datenbank des [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)]servers, auf dem die neue Datenbank erstellt wird. Nachdem die Datenbankkopie gestartet wurde, können Sie Abfragen der `sys.databases` und `sys.dm_database_copies` -Sichten aus der `master` Datenbank des Zielservers auf Weitere Informationen zum Kopierstatus abrufen.  
  
## <a name="examples"></a>Beispiele  
  
### <a name="a-query-the-sysdatabases-view"></a>A. Abfragen der sys.databases-Sicht  
 Das folgende Beispiel gibt ein Paar die verfügbaren Spalten bei der `sys.databases` anzeigen.  
  
```sql  
SELECT name, user_access_desc, is_read_only, state_desc, recovery_model_desc  
FROM sys.databases;  
```  
  
### <a name="b-check-the-copying-status-in-includesssdsincludessssds-mdmd"></a>B. Überprüfen des Kopierstatus in [!INCLUDE[ssSDS](../../includes/sssds-md.md)]  
 Das folgende Beispiel fragt die `sys.databases` und `sys.dm_database_copies` Ansichten zum Zurückgeben von Informationen zu einer Datenbank-Kopiervorgang.  
  
**Gilt für:** [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)]  
  
```sql  
-- Execute from the master database.  
SELECT a.name, a.state_desc, b.start_date, b.modify_date, b.percentage_complete  
FROM sys.databases AS a  
INNER JOIN sys.dm_database_copies AS b ON a.database_id = b.database_id  
WHERE a.state = 7;  
```  
### <a name="c-check-the-temporal-retention-policy-status-in-includesssdsincludessssds-mdmd"></a>C. Überprüfen Sie der temporalen Beibehaltung Richtlinienstatus [!INCLUDE[ssSDS](../../includes/sssds-md.md)]  
 Das folgende Beispiel fragt die `sys.databases` Informationen zurückgegeben werden sollen, ob der Task "Wartungscleanup" temporalen Beibehaltung aktiviert ist. Denken Sie daran, dass nach dem Wiederherstellungsvorgang temporalen Beibehaltung standardmäßig deaktiviert ist. Verwendung `ALTER DATABASE` explizit aktivieren.
  
**Gilt für:** [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)]  
  
```sql  
-- Execute from the master database.  
SELECT a.name, a.is_temporal_history_retention_enabled 
FROM sys.databases AS a;
```  
  
## <a name="see-also"></a>Siehe auch  
 [ALTER DATABASE &#40;Transact-SQL&#41;](../../t-sql/statements/alter-database-transact-sql.md)   
 [sys.database_mirroring_witnesses &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/database-mirroring-witness-catalog-views-sys-database-mirroring-witnesses.md)   
 [Sys. database_recovery_status &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-database-recovery-status-transact-sql.md)   
 [Datenbanken und Dateikatalogsichten &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/databases-and-files-catalog-views-transact-sql.md)   
 [sys.dm_database_copies &#40;Azure SQL-Datenbank&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-database-copies-azure-sql-database.md)  
  
  
