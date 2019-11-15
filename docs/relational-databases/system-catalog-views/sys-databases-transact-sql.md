---
title: sys. Datenbanken (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 11/14/2019
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
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: c33f30366ef2d63f888684c9afedb2a949ecd589
ms.sourcegitcommit: 15fe0bbba963d011472cfbbc06d954d9dbf2d655
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/14/2019
ms.locfileid: "74095869"
---
# <a name="sysdatabases-transact-sql"></a>group_database_id
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

Enthält eine Zeile für jede Datenbank in der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Instanz.  
  
Wenn eine Datenbank nicht `ONLINE`oder `AUTO_CLOSE` auf `ON` festgelegt ist und die Datenbank geschlossen ist, werden die Werte einiger Spalten möglicherweise `NULL`. Wenn eine Datenbank `OFFLINE`ist, ist die entsprechende Zeile für Benutzer mit niedrigen Berechtigungen nicht sichtbar. Um die entsprechende Zeile anzuzeigen, wenn die Datenbank `OFFLINE`ist, muss ein Benutzer mindestens über die Berechtigung `ALTER ANY DATABASE` Serverebene oder über die Berechtigung `CREATE DATABASE` in der `master` Datenbank verfügen.  
  
|Spaltenname|Datentyp|und Beschreibung|  
|-----------------|---------------|-----------------|  
|**name**|**sysname**|Name der Datenbank, eindeutig innerhalb einer Instanz von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] oder innerhalb eines [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)]servers.|  
|**database_id**|**int**|ID der Datenbank, eindeutig innerhalb einer Instanz von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] oder innerhalb eines [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)]servers.|  
|**source_database_id**|**int**|Ungleich NULL = ID der Quelldatenbank dieser Datenbankmomentaufnahme.<br /> NULL = Keine Datenbankmomentaufnahme.|  
|**owner_sid**|**varbinary(85)**|SID (Sicherheits-ID) des externen Besitzers der Datenbank gemäß Registrierung beim Server. Informationen dazu, wer eine Datenbank besitzen kann, finden Sie im Abschnitt **Alter Authorization for** Database unter [ALTER AUTHORIZATION](../../t-sql/statements/alter-authorization-transact-sql.md).|  
|**create_date**|**datetime**|Datum der Erstellung oder Umbenennung der Datenbank. Bei **tempdb**ändert sich dieser Wert jedes Mal, wenn der Server neu gestartet wird.|  
|**compatibility_level**|**tinyint**|Ganze Zahl, die der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Version entspricht, deren Verhalten kompatibel ist:<br /> **Wert** &#124; **gilt für**<br /> 70 &#124; [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] durch [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)]<br /> 80 &#124; [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] durch [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)]<br /> 90 &#124; [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] durch [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)]<br /> 100 &#124; [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] und höher und [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)]<br /> 110 &#124; [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] und höher und [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)]<br /> 120 &#124; [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] und höher und [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)]<br /> 130 &#124; [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] und höher<br /> 140 &#124; [!INCLUDE[ssSQL17](../../includes/sssql17-md.md)] und höher <br /> 150 &#124; [!INCLUDE[sql-server-2019](../../includes/sssqlv15-md.md)]  |  
|**collation_name**|**sysname**|Sortierung der Datenbank. Dient als Standardsortierung der Datenbank.<br /> NULL = Datenbank ist nicht online, oder AUTO_CLOSE ist auf ON festgelegt, und die Datenbank ist geschlossen.|  
|**user_access**|**tinyint**|Einstellung für den Benutzerzugriff:<br /> 0 = MULTI_USER angegeben<br /> 1 = SINGLE_USER angegeben<br /> 2 = RESTRICTED_USER angegeben|  
|**user_access_desc**|**nvarchar(60)**|Beschreibung der Einstellung für den Benutzerzugriff.|  
|**is_read_only**|**bit**|1 = Datenbank ist READ_ONLY<br /> 0 = Datenbank ist READ_WRITE|  
|**is_auto_close_on**|**bit**|1 = AUTO_CLOSE ist ON<br /> 0 = AUTO_CLOSE ist OFF|  
|**is_auto_shrink_on**|**bit**|1 = AUTO_SHRINK ist ON<br /> 0 = AUTO_SHRINK ist OFF|  
|**state**|**tinyint**|**Wert &#124; gilt für**<br /> 0 = ONLINE <br /> 1 = RESTORING <br /> 2 = wieder &#124; Herstellen von [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] und höher<br /> 3 = RECOVERY_PENDING &#124; [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] und höher<br /> 4 = SUSPECT <br /> 5 = Notfall &#124; [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] und höher<br /> 6 = Offline &#124; [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] und höher<br /> 7 = kopieren &#124; von [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)] [!INCLUDE[ssGeoDR](../../includes/ssgeodr-md.md)] <br /> 10 = OFFLINE_SECONDARY &#124; [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)] [!INCLUDE[ssGeoDR](../../includes/ssgeodr-md.md)] <br /><br /> **Hinweis:** Fragen Sie für Always on-Datenbanken die `database_state` oder `database_state_desc` Spalten von [sys. dm_hadr_database_replica_states](../../relational-databases/system-dynamic-management-views/sys-dm-hadr-database-replica-states-transact-sql.md)ab.|  
|**state_desc**|**nvarchar(60)**|Beschreibung des Datenbankstatus. Siehe Status.|  
|**is_in_standby**|**bit**|Datenbank ist für die Wiederherstellungsprotokollierung schreibgeschützt.|  
|**is_cleanly_shutdown**|**bit**|1 = Datenbank wurde ordnungsgemäß heruntergefahren, keine Wiederherstellung beim Starten erforderlich<br /> 0 = Datenbank wurde nicht ordnungsgemäß heruntergefahren, Wiederherstellung beim Starten erforderlich|  
|**is_supplemental_logging_enabled**|**bit**|1 = SUPPLEMENTAL_LOGGING ist ON<br /> 0 = SUPPLEMENTAL_LOGGING ist OFF|  
|**snapshot_isolation_state**|**tinyint**|Status zulässiger Momentaufnahme-Isolationstransaktionen gemäß Einstellung der ALLOW_SNAPSHOT_ISOLATION-Option:<br /> 0 = Momentaufnahmeisolationsstatus ist OFF (Standardeinstellung). Momentaufnahmeisolation ist unzulässig.<br /> 1 = Momentaufnahmeisolationsstatus ist ON. Momentaufnahmeisolation ist zulässig.<br /> 2 = Momentaufnahmeisolationsstatus ist im Übergang zum Status OFF. Die Änderungen aller Transaktionen sind versionsspezifisch. Neue Transaktionen können nicht mit der Momentaufnahmeisolation gestartet werden. Die Datenbank bleibt im Übergang zum Status OFF, bis alle Transaktionen, die beim Ausführen von ALTER DATABASE aktiv waren, abgeschlossen werden können.<br /> 3 = Momentaufnahmeisolationsstatus ist im Übergang zum Status ON. Die Änderungen neuer Transaktionen sind versionsspezifisch. Transaktionen können die Momentaufnahmeisolation erst verwenden, wenn der Status der Momentaufnahmeisolation zu 1 (ON) wechselt. Die Datenbank bleibt im Übergang zum Status ON, bis alle Updatetransaktionen, die beim Ausführen von ALTER DATABASE aktiv waren, abgeschlossen werden können.|  
|**snapshot_isolation_state_desc**|**nvarchar(60)**|Beschreibung des Status zulässiger Momentaufnahme-Isolationstransaktionen gemäß Einstellung der ALLOW_SNAPSHOT_ISOLATION-Option.|  
|**is_read_committed_snapshot_on**|**bit**|1 = Die READ_COMMITTED_SNAPSHOT-Option ist ON. Lesevorgänge unter der Isolationsstufe 'read-committed' basieren auf Momentaufnahmescans und aktivieren keine Sperren.<br /> 0 = Die READ_COMMITTED_SNAPSHOT-Option ist OFF (Standardeinstellung). Lesevorgänge unter der Isolationsstufe 'read-committed' verwenden gemeinsame Sperren.|  
|**recovery_model**|**tinyint**|Ausgewähltes Wiederherstellungsmodell:<br /> 1 = FULL<br /> 2 = BULK_LOGGED<br /> 3 = SIMPLE|  
|**recovery_model_desc**|**nvarchar(60)**|Beschreibung des ausgewählten Wiederherstellungs Modells.|  
|**page_verify_option**|**tinyint**|Einstellung der PAGE_VERIFY-Option:<br /> 0 = NONE<br /> 1 = TORN_PAGE_DETECTION<br /> 2 = CHECKSUM|  
|**page_verify_option_desc**|**nvarchar(60)**|Beschreibung der Einstellung der PAGE_VERIFY-Option.|  
|**is_auto_create_stats_on**|**bit**|1 = AUTO_CREATE_STATISTICS ist ON<br /> 0 = AUTO_CREATE_STATISTICS ist OFF|  
|**is_auto_create_stats_incremental_on**|**bit**|Gibt die Standardeinstellung für die Option zur inkrementellen Auto Stats-Erstellung an.<br /> 0 = Die Auto Stats-Erstellung ist nicht inkrementell<br /> 1 = Die Auto Stats-Erstellung ist inkrementell, falls möglich<br /> **Gilt für**: [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] und höher.|  
|**is_auto_update_stats_on**|**bit**|1 = AUTO_UPDATE_STATISTICS ist ON<br /> 0 = AUTO_UPDATE_STATISTICS ist OFF|  
|**is_auto_update_stats_async_on**|**bit**|1 = AUTO_UPDATE_STATISTICS_ASYNC ist ON<br /> 0 = AUTO_UPDATE_STATISTICS_ASYNC ist OFF|  
|**is_ansi_null_default_on**|**bit**|1 = ANSI_NULL_DEFAULT ist ON<br /> 0 = ANSI_NULL_DEFAULT ist OFF|  
|**is_ansi_nulls_on**|**bit**|1 = ANSI_NULLS ist ON<br /> 0 = ANSI_NULLS ist OFF|  
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
|**is_trustworthy_on**|**bit**|1 = Datenbank wurde als vertrauenswürdig gekennzeichnet<br /> 0 = Datenbank wurde nicht als vertrauenswürdig gekennzeichnet<br /> Bei wiederhergestellten oder angefügten Datenbanken ist der Broker standardmäßig deaktiviert. Die Ausnahme hiervon ist die Datenbankspiegelung, bei der der Broker nach einem Failover aktiviert wird.|  
|**is_db_chaining_on**|**bit**|1 = Datenbankübergreifende Besitzverkettung ist ON<br /> 0 = Datenbankübergreifende Besitzverkettung ist OFF|  
|**is_parameterization_forced**|**bit**|1 = Parametrisierung ist FORCED<br /> 0 = Parametrisierung ist SIMPLE|  
|**is_master_key_encrypted_by_server**|**bit**|1 = Datenbank verfügt über verschlüsselten Hauptschlüssel<br /> 0 = Datenbank verfügt nicht über verschlüsselten Hauptschlüssel|  
|**is_query_store_on**|**bit**|1 = der Abfrage Speicher ist für diese Datenbank aktiviert. Überprüfen Sie [sys. database_query_store_options](../../relational-databases/system-catalog-views/sys-database-query-store-options-transact-sql.md) , um den Abfrage Speicherstatus anzuzeigen.<br /> 0 = der Abfrage Speicher ist nicht aktiviert.<br /> **Gilt für**: [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ([!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] und höher).|  
|**is_published**|**bit**|1 = Datenbank ist eine Veröffentlichungsdatenbank in einer Transaktions- oder Momentaufnahme-Replikationstopologie<br /> 0 = Keine Veröffentlichungsdatenbank|  
|**is_subscribed**|**bit**|Diese Spalte wird nicht verwendet. Gibt immer 0 zurück, unabhängig vom Abonnentenstatus der Datenbank.|  
|**is_merge_published**|**bit**|1 = Datenbank ist eine Veröffentlichungsdatenbank in einer Mergereplikationstopologie<br /> 0 = Keine Veröffentlichungsdatenbank in einer Mergereplikationstopologie|  
|**is_distributor**|**bit**|1 = Datenbank ist die Verteilungsdatenbank für eine Replikationstopologie<br /> 0 = Ist nicht die Verteilungsdatenbank für eine Replikationstopologie|  
|**is_sync_with_backup**|**bit**|1 = Datenbank ist für die Replikationssynchronisierung mit Sicherung gekennzeichnet<br /> 0 = Ist nicht für die Replikationssynchronisierung mit Sicherung gekennzeichnet|  
|**service_broker_guid**|**uniqueidentifier**|Bezeichner von Service Broker für diese Datenbank. Wird als **BROKER_INSTANCE** des Ziels in der Routing Tabelle verwendet.|  
|**is_broker_enabled**|**bit**|1 = Der Broker in dieser Datenbank sendet und empfängt derzeit Nachrichten.<br /> 0 = Alle gesendeten Nachrichten bleiben in der Übertragungswarteschlange, und empfangene Nachrichten werden in dieser Datenbank nicht in Warteschlangen eingereiht.<br /> Bei wiederhergestellten oder angefügten Datenbanken ist der Broker standardmäßig deaktiviert. Die Ausnahme hiervon ist die Datenbankspiegelung, bei der der Broker nach einem Failover aktiviert wird.|  
|**log_reuse_wait**|**tinyint**|Die Wiederverwendung des Transaktionsprotokoll-Speicherplatzes wartet zurzeit auf einen der folgenden Punkte als des letzten Prüf Punkts. Ausführlichere Erläuterungen zu diesen Werten finden Sie [im Transaktionsprotokoll](../../relational-databases/logs/the-transaction-log-sql-server.md).<br /> **Wert &#124; gilt für**<br /> 0 = Nichts<br />   1 = Prüfpunkt (wenn für eine Datenbank ein Wiederherstellungs Modell verwendet wird und eine Speicher optimierte Daten Dateigruppe vorhanden ist, wird erwartet, dass die `log_reuse_wait` Spalte Prüfpunkt oder xtp_checkpoint anzeigt.) &#124; [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] und höher<br />  2 = Protokoll Sicherung &#124; [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] und höher<br />  3 = aktive Sicherung oder wieder &#124; Herstellung [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] und höher<br />  4 = aktive Transaktions &#124; [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] und höher<br />  5 = Daten Bank &#124; Spiegelung [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] und höher<br />  6 = Replikations &#124; [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] und höher<br />  7 = Erstellung &#124; der Datenbank-Momentaufnahme [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] und höher<br />  8 = Protokollscan <br />  9 = ein sekundäres Replikat einer Always on Verfügbarkeits Gruppe wendet Transaktionsprotokoll-Datensätze dieser Datenbank auf eine zugehörige sekundäre Datenbank an. &#124;[!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] und höher<br />  9 = Sonstige (flüchtig &#124; ) bis einschließlich [!INCLUDE[ssKilimanjaro](../../includes/ssKilimanjaro-md.md)]<br />  10 = nur &#124; für die interne Verwendung [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] und höher<br />  11 = nur &#124; für die interne Verwendung [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] und höher<br /> 12 = nur &#124; für die interne Verwendung [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] und höher<br />13 = älteste Seite &#124; [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] und höher<br /> 14 = andere &#124; [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] und höher<br />  16 = XTP_CHECKPOINT (wenn für eine Datenbank ein Wiederherstellungs Modell verwendet wird und eine Speicher optimierte Daten Dateigruppe vorhanden ist, sollten Sie davon ausgehen, dass in der Spalte log_reuse_wait der Prüfpunkt oder xtp_checkpoint angezeigt wird.) &#124; [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] und höher|  
|**log_reuse_wait_desc**|**nvarchar(60)**|Bei der Beschreibung der Wiederverwendung von Transaktionsprotokollspeicher wird derzeit auf eines der folgenden Ereignisse ab dem letzten Prüfpunkt gewartet.|  
|**is_date_correlation_on**|**bit**|1 = DATE_CORRELATION_OPTIMIZATION ist ON<br /> 0 = DATE_CORRELATION_OPTIMIZATION ist OFF|  
|**is_cdc_enabled**|**bit**|1 = Datenbank ist für Change Data Capture aktiviert. Weitere Informationen finden Sie unter [sys. sp_cdc_enable_db &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sys-sp-cdc-enable-db-transact-sql.md).|  
|**is_encrypted**|**bit**|Gibt an, ob die Datenbank verschlüsselt ist (gibt den zuletzt festgelegten Status mit der `ALTER DATABASE SET ENCRYPTION`-Klausel wieder). Kann einer der folgenden Werte sein:<br /> 1 = Verschlüsselt.<br /> 0 = Nicht verschlüsselt<br /> Weitere Informationen zur Datenbankverschlüsselung finden Sie unter [Transparent Data Encryption &#40;TDE&#41;](../../relational-databases/security/encryption/transparent-data-encryption.md).<br /> Wenn die Datenbank gerade entschlüsselt wird, zeigt `is_encrypted` den Wert 0 an. Sie können den Status des Verschlüsselungs Prozesses mithilfe der dynamischen Verwaltungs Sicht [sys. dm_database_encryption_keys](../../relational-databases/system-dynamic-management-views/sys-dm-database-encryption-keys-transact-sql.md) anzeigen.|  
|**is_honor_broker_priority_on**|**bit**|Gibt an, ob die Datenbank die Konversations Prioritäten berücksichtigt (gibt den zuletzt festgelegten Status mit der `ALTER DATABASE SET HONOR_BROKER_PRIORITY`-Klausel wieder). Kann einer der folgenden Werte sein:<br /> 1 = HONOR_BROKER_PRIORITY ist ON<br /> 0 = HONOR_BROKER_PRIORITY ist OFF<br /> Bei wiederhergestellten oder angefügten Datenbanken ist der Broker standardmäßig deaktiviert. Die Ausnahme hiervon ist die Datenbankspiegelung, bei der der Broker nach einem Failover aktiviert wird.|  
|**replica_id**|**uniqueidentifier**|Eindeutiger Bezeichner des lokalen [!INCLUDE[ssHADR](../../includes/sshadr-md.md)]-Verfügbarkeitsreplikats der Verfügbarkeitsgruppe, an der die Datenbank ggf. teilnimmt.<br /> NULL = Datenbank ist kein Teil eines Verfügbarkeitsreplikats einer Verfügbarkeitsgruppe<br /> **Gilt für**: [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ([!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] und höher) und [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)]|  
|**group_database_id**|**uniqueidentifier**|Eindeutiger Bezeichner der Datenbank in einer Always on Verfügbarkeits Gruppe, in der die Datenbank beteiligt ist, falls vorhanden. **group_database_id** ist für diese Datenbank auf dem primären Replikat und jedem sekundären Replikat, auf dem die Datenbank der Verfügbarkeitsgruppe hinzugefügt wurde, identisch.<br /> NULL = Datenbank ist kein Teil eines Verfügbarkeitsreplikats einer beliebigen Verfügbarkeitsgruppe<br /> **Gilt für**: [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ([!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] und höher) und [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)]|  
|**resource_pool_id**|**int**|Die ID des Ressourcenpools, der dieser Datenbank zugeordnet ist. Dieser Ressourcenpool steuert den insgesamt für speicheroptimierte Tabellen in dieser Datenbank verfügbaren Arbeitsspeicher.<br /> **Gilt für**: [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] und höher|  
|**default_language_lcid**|**smallint**|Gibt die lokale ID (lcid) der Standardsprache einer eigenständigen Datenbank an.<br /> **Hinweis:** Fungiert als die [Server Konfigurations Option Standardsprache konfigurieren](../../database-engine/configure-windows/configure-the-default-language-server-configuration-option.md) von `sp_configure`. Dieser Wert ist für eine nicht enthaltene Datenbank **null** .<br /> **Gilt für**: [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ([!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] und höher) und [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)]|  
|**default_language_name**|**nvarchar(128)**|Gibt die Standardsprache einer eigenständigen Datenbank an.<br /> Dieser Wert ist für eine nicht enthaltene Datenbank **null** .<br /> **Gilt für**: [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ([!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] und höher) und [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)]|  
|**default_fulltext_language_lcid**|**int**|Gibt die Gebiets Schema-ID (LCID) der Standard-voll Text Sprache der eigenständigen Datenbank an.<br /> **Hinweis:** Functions als Standard [Konfigurieren der standardmäßigen voll Text Sprache Server Konfigurations Option](../../database-engine/configure-windows/configure-the-default-full-text-language-server-configuration-option.md) von `sp_configure`. Dieser Wert ist für eine nicht enthaltene Datenbank **null** .<br /> **Gilt für**: [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ([!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] und höher) und [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)]|  
|**default_fulltext_language_name**|**nvarchar(128)**|Gibt die Standard-Volltextsprache der eigenständigen Datenbank an.<br /> Dieser Wert ist für eine nicht enthaltene Datenbank **null** .<br /> **Gilt für**: [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ([!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] und höher) und [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)]|  
|**is_nested_triggers_on**|**bit**|Gibt an, ob geschachtelte Trigger in der eigenständigen Datenbank zulässig sind.<br /> 0 = Geschachtelte Trigger sind nicht zulässig<br /> 1 = Geschachtelte Trigger sind zulässig<br /> **Hinweis:** Fungiert als die [Server Konfigurations Option "configure the netsted](../../database-engine/configure-windows/configure-the-nested-triggers-server-configuration-option.md) Triggers" von `sp_configure`. Dieser Wert ist für eine nicht enthaltene Datenbank **null** . Weitere Informationen finden Sie unter [sys. &#40;Konfigurationen&#41; Transact-SQL](../../relational-databases/system-catalog-views/sys-configurations-transact-sql.md) .<br /> **Gilt für**: [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ([!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] und höher) und [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)]|  
|**is_transform_noise_words_on**|**bit**|Gibt an, ob Füllwörter in der eigenständigen Datenbank transformiert werden sollen.<br /> 0 = Füllwörter sollten nicht transformiert werden<br /> 1 = Füllwörter sollten transformiert werden<br /> **Hinweis:** Fungiert als die [Server Konfigurations Option "transform noise words](../../database-engine/configure-windows/transform-noise-words-server-configuration-option.md) " von `sp_configure`. Dieser Wert ist für eine nicht enthaltene Datenbank **null** . Weitere Informationen finden Sie unter [sys. &#40;Konfigurationen&#41; Transact-SQL](../../relational-databases/system-catalog-views/sys-configurations-transact-sql.md) .<br /> **Gilt für**: [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] und höher|  
|**two_digit_year_cutoff**|**smallint**|Gibt einen Wert zwischen 1753 und 9999 an, der das Umstellungsjahr für das Interpretieren zweistelliger Jahre als vierstellige Jahre darstellt.<br /> **Hinweis:** Fungiert als die [Server Konfigurations Option](../../database-engine/configure-windows/configure-the-two-digit-year-cutoff-server-configuration-option.md) "Umstellungs Jahr für Umstellungs Jahr mit zwei Ziffern" `sp_configure`. Dieser Wert ist für eine nicht enthaltene Datenbank **null** . Weitere Informationen finden Sie unter [sys. &#40;Konfigurationen&#41; Transact-SQL](../../relational-databases/system-catalog-views/sys-configurations-transact-sql.md) .<br /> **Gilt für**: [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ([!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] und höher) und [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)]|  
|**containment**|**tinyint not NULL**|Zeigt den Kapselungsstatus der Datenbank an.<br />  0 = Datenbankkapselung ist deaktiviert. **Gilt für**: [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ([!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] und höher) und [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)]<br /> 1 = Datenbank ist Teil Kapselung **, gilt für**: [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] und höher|  
|**containment_desc**|**nvarchar (60) nicht NULL**|Zeigt den Kapselungsstatus der Datenbank an.<br /> NONE = Legacydatenbank (keine Kapselung)<br /> PARTIAL = Teilweise eigenständige Datenbank<br /> **Gilt für**: [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ([!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] und höher) und [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)]|  
|**target_recovery_time_in_seconds**|**int**|Die geschätzte Zeit zum Wiederherstellen der Datenbank in Sekunden. NULL-Werte sind zulässig.<br /> **Gilt für**: [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ([!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] und höher) und [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)]|  
|**delayed_durability**|**int**|Die Einstellung für die verzögerte Dauerhaftigkeit:<br /> 0 = deaktiviert<br /> 1 = zulässig<br /> 2 = erzwungen<br /> Weitere Informationen finden Sie im Thema [Steuern der Transaktionsdauerhaftigkeit](../../relational-databases/logs/control-transaction-durability.md).<br /> **Gilt für**: [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ([!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] und höher) und [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)].|  
|**delayed_durability_desc**|**nvarchar(60)**|Die Einstellung für die verzögerte Dauerhaftigkeit:<br /> DISABLED<br /> ALLOWED<br /> FORCED<br /> **Gilt für**: [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ([!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] und höher) und [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)].|  
|**is_memory_optimized_elevate_to_snapshot_on**|**bit**|Auf speicheroptimierte Tabellen wird mit der SNAPSHOT-Isolation zugegriffen, wenn die Sitzungseinstellung TRANSACTION ISOLATION LEVEL auf eine niedrigere Isolationsstufe festgelegt ist (READ COMMITTED oder READ UNCOMMITTED).<br /> 1 = Isolationsstufe ist mindestens SNAPSHOT.<br /> 0 = Isolationsstufe ist nicht erhöht.|  
|**is_federation_member**|**bit**|Gibt an, ob die Datenbank Mitglied eines Verbunds ist.<br /> **Gilt für:** [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)]|  
|**is_remote_data_archive_enabled**|**bit**|Gibt an, ob die Datenbank gestreckt wird.<br /> 0 = die Datenbank ist nicht Stretch-aktiviert.<br /> 1 = die Datenbank ist Stretch-aktiviert.<br /> **Gilt für**: [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] und höher<br /> Weitere Informationen finden Sie unter [Stretch Database](../../sql-server/stretch-database/stretch-database.md).|  
|**is_mixed_page_allocation_on**|**bit**|Gibt an, ob Tabellen und Indizes in der Datenbank anfängliche Seiten aus gemischten Blöcken zuordnen können.<br /> 0 = Tabellen und Indizes in der Datenbank weisen immer anfängliche Seiten aus einheitlichen Blöcken zu.<br /> 1 = Tabellen und Indizes in der Datenbank können ursprüngliche Seiten aus gemischten Blöcken zuordnen.<br /> **Gilt für**: [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] und höher<br /> Weitere Informationen finden Sie unter der Option Set MIXED_PAGE_ALLOCATION von [ALTER DATABASE Set options &#40;Transact-SQL&#41;](../../t-sql/statements/alter-database-transact-sql-set-options.md).|  
|**is_temporal_retention_enabled**|**bit**|Gibt an, ob die cleanupaufgabe der temporalen Aufbewahrungs Richtlinie aktiviert ist.<br /> **Gilt für:** [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)]|
|**catalog_collation_type**|**int**|Die Einstellung für die Katalog Sortierung:<br />0 = DATABASE_DEFAULT<br />2 = SQL_Latin_1_General_CP1_CI_AS<br /> **Gilt für:** [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)]|
|**catalog_collation_type_desc**|**nvarchar(60)**|Die Einstellung für die Katalog Sortierung:<br />DATABASE_DEFAULT<br />SQL_Latin_1_General_CP1_CI_AS<br /> **Gilt für:** [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)]|
|**is_result_set_caching_on**|**int**|1 = is_result_set_caching_on ist on</br>0 = is_result_set_caching_on ist Off</br>**Gilt für**: Azure SQL Data Warehouse Gen2. Diese Features werden für alle Regionen bereitgestellt. Überprüfen Sie jedoch die Version, die für die-Instanz bereitgestellt wurde, und die neuesten Versions [Anmerkungen zu Azure SQL DW](/azure/sql-data-warehouse/release-notes-10-0-10106-0) für die Verfügbarkeit von Features.|
  
## <a name="permissions"></a>Berechtigungen  
 Wenn der Aufrufer von `sys.databases` nicht der Besitzer der Datenbank ist und die Datenbank nicht `master` oder `tempdb`ist, sind die Mindestberechtigungen, die zum Anzeigen der entsprechenden Zeile erforderlich sind, `ALTER ANY DATABASE` oder die `VIEW ANY DATABASE`-Berechtigung auf Serverebene oder `CREATE DATABASE` Berechtigung in der `master` Datenbank. Die Datenbank, mit der der Aufrufer verbunden ist, kann in `sys.databases`immer angezeigt werden.  
  
> [!IMPORTANT]  
> Standardmäßig verfügt die public-Rolle über die `VIEW ANY DATABASE`-Berechtigung, sodass allen Anmeldungen Datenbankinformationen angezeigt werden können. Zum Blockieren einer Anmeldung von der Fähigkeit, eine Datenbank zu erkennen, `REVOKE` die `VIEW ANY DATABASE`-Berechtigung von `public`oder `DENY` die `VIEW ANY DATABASE` Berechtigung für einzelne Anmeldungen.  
  
## <a name="azure-sql-database-remarks"></a>Hinweise zu Azure SQL-Datenbank  
In [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)] diese Ansicht in der `master`-Datenbank und in Benutzer Datenbanken verfügbar. In der `master`-Datenbank gibt diese Sicht die Informationen über die `master` Datenbank und alle Benutzer Datenbanken auf dem Server zurück. In einer Benutzerdatenbank gibt diese Sicht Informationen nur in der aktuellen Datenbank und der master-Datenbank zurück.  
  
 Verwenden Sie die `sys.databases`-Sicht in der `master`-Datenbank des [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)]servers, auf dem die neue Datenbank erstellt wird. Nachdem der Daten Bank Kopiervorgang gestartet wurde, können Sie die `sys.databases` und die `sys.dm_database_copies` Sichten aus der `master`-Datenbank des Zielservers Abfragen, um weitere Informationen zum Kopier Status abzurufen.  
  
## <a name="examples"></a>Beispiele  
  
### <a name="a-query-the-sysdatabases-view"></a>A. Abfragen der sys.databases-Sicht  
 Im folgenden Beispiel werden einige der Spalten zurückgegeben, die in der `sys.databases` Ansicht verfügbar sind.  
  
```sql  
SELECT name, user_access_desc, is_read_only, state_desc, recovery_model_desc  
FROM sys.databases;  
```  
  
### <a name="b-check-the-copying-status-in-includesssdsincludessssds-mdmd"></a>B. Überprüfen des Kopierstatus in [!INCLUDE[ssSDS](../../includes/sssds-md.md)]  
 Im folgenden Beispiel werden die `sys.databases`-und `sys.dm_database_copies` Sichten abgefragt, um Informationen zu einem Daten Bank Kopiervorgang zurückzugeben.  
  
**Gilt für:** [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)]  
  
```sql  
-- Execute from the master database.  
SELECT a.name, a.state_desc, b.start_date, b.modify_date, b.percentage_complete  
FROM sys.databases AS a  
INNER JOIN sys.dm_database_copies AS b ON a.database_id = b.database_id  
WHERE a.state = 7;  
```  
### <a name="c-check-the-temporal-retention-policy-status-in-includesssdsincludessssds-mdmd"></a>C. Überprüfen Sie den Status der temporalen Aufbewahrungs Richtlinie in [!INCLUDE[ssSDS](../../includes/sssds-md.md)]  
 Im folgenden Beispiel wird der `sys.databases` abgefragt, um Informationen darüber zurückzugeben, ob die Task ' Temporale Beibehaltungs Bereinigung Beachten Sie, dass die Temporale Aufbewahrung nach dem Wiederherstellungs Vorgang standardmäßig deaktiviert ist. Verwenden Sie `ALTER DATABASE`, um es explizit zu aktivieren.
  
**Gilt für:** [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)]  
  
```sql  
-- Execute from the master database.  
SELECT a.name, a.is_temporal_history_retention_enabled 
FROM sys.databases AS a;
```  
  
## <a name="see-also"></a>Siehe auch  
 [ALTER DATABASE &#40;Transact-SQL&#41;](../../t-sql/statements/alter-database-transact-sql.md)   
 [sys.database_mirroring_witnesses &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/database-mirroring-witness-catalog-views-sys-database-mirroring-witnesses.md)   
 [sys.database_recovery_status &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-database-recovery-status-transact-sql.md)   
 [Datenbanken und Dateikatalogsichten &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/databases-and-files-catalog-views-transact-sql.md)   
 [sys.dm_database_copies &#40;Azure SQL-Datenbank&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-database-copies-azure-sql-database.md)  
  
  
