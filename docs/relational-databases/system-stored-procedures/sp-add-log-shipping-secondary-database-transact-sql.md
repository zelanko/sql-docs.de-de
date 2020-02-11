---
title: sp_add_log_shipping_secondary_database (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_add_log_shipping_secondary_database
- sp_add_log_shipping_secondary_database_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sp_add_log_shipping_secondary_database
ms.assetid: d29e1c24-3a3c-47a4-a726-4584afa6038a
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: e26fa9b22578d91636eb554c75a55f184869d529
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "68046211"
---
# <a name="sp_add_log_shipping_secondary_database-transact-sql"></a>sp_add_log_shipping_secondary_database (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Richtet eine sekundäre Datenbank für den Protokoll Versand ein.  
  
 ![Symbol für Themenlink](../../database-engine/configure-windows/media/topic-link.gif "Symbol für Themenlink") [Transact-SQL-Syntaxkonventionen](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```  
  
sp_add_log_shipping_secondary_database  
[ @secondary_database = ] 'secondary_database',  
[ @primary_server = ] 'primary_server',   
[ @primary_database = ] 'primary_database',  
[, [ @restore_delay = ] 'restore_delay']  
[, [ @restore_all = ] 'restore_all']  
[, [ @restore_mode = ] 'restore_mode']  
[, [ @disconnect_users = ] 'disconnect_users']  
[, [ @block_size = ] 'block_size']  
[, [ @buffer_count = ] 'buffer_count']  
[, [ @max_transfer_size = ] 'max_transfer_size']  
[, [ @restore_threshold = ] 'restore_threshold']   
[, [ @threshold_alert = ] 'threshold_alert']   
[, [ @threshold_alert_enabled = ] 'threshold_alert_enabled']   
[, [ @history_retention_period = ] 'history_retention_period']  
```  
  
## <a name="arguments"></a>Argumente  
`[ @secondary_database = ] 'secondary_database'`Der Name der sekundären Datenbank. *secondary_database* ist vom **Datentyp vom Datentyp sysname**und hat keinen Standardwert.  
  
`[ @primary_server = ] 'primary_server'`Der Name der primären Instanz von [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] in der Protokoll Versand Konfiguration. *primary_server* ist vom **Datentyp vom Datentyp sysname** und darf nicht NULL sein.  
  
`[ @primary_database = ] 'primary_database'`Der Name der Datenbank auf dem primären Server. *primary_database* ist vom **Datentyp vom Datentyp sysname**und hat keinen Standardwert.  
  
`[ @restore_delay = ] 'restore_delay'`Die Zeitspanne in Minuten, die der sekundäre Server wartet, bevor er eine bestimmte Sicherungsdatei wiederherstellt. *restore_delay* ist vom Datentyp **int** und kann nicht NULL sein. Der Standardwert ist 0.  
  
`[ @restore_all = ] 'restore_all'`Wenn der Wert auf 1 festgelegt ist, stellt der sekundäre Server bei Ausführung des Wiederherstellungs Auftrags alle verfügbaren Transaktionsprotokoll Sicherungen wieder her. Andernfalls wird der Vorgang nach der Wiederherstellung einer Datei beendet. *restore_all* ist vom **Bit** und kann nicht NULL sein.  
  
`[ @restore_mode = ] 'restore_mode'`Der Wiederherstellungs Modus für die sekundäre Datenbank.  
  
 0 = Das Protokoll wird mit NORECOVERY wiederhergestellt.  
  
 1 = RESTORE LOG with Standby.  
  
 *Restore* ist ein **Bit** und kann nicht NULL sein.  
  
`[ @disconnect_users = ] 'disconnect_users'`Wenn der Wert auf 1 festgelegt ist, werden die Benutzer von der sekundären Datenbank getrennt, wenn ein Wiederherstellungs Vorgang ausgeführt wird. Standardwert = 0. die *Trennung* von Benutzern ist **Bit** und darf nicht NULL sein.  
  
`[ @block_size = ] 'block_size'`Die Größe in Bytes, die als Blockgröße für das Sicherungsmedium verwendet wird. *block_size* ist vom Datentyp **int** und hat den Standardwert-1.  
  
`[ @buffer_count = ] 'buffer_count'`Die Gesamtanzahl der Puffer, die vom Sicherungs-oder Wiederherstellungs Vorgang verwendet werden. *buffer_count* ist vom Datentyp **int** und hat den Standardwert-1.  
  
`[ @max_transfer_size = ] 'max_transfer_size'`Die Größe der maximalen Eingabe-oder Ausgabeanforderung in Bytes, die von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] an das Sicherungsmedium ausgegeben wird. *max_transfersize* ist vom Datentyp **int** und kann NULL sein.  
  
`[ @restore_threshold = ] 'restore_threshold'`Die zulässige Anzahl von Minuten zwischen Wiederherstellungs Vorgängen, bevor eine Warnung generiert wird. *restore_threshold* ist vom Datentyp **int** und kann nicht NULL sein.  
  
`[ @threshold_alert = ] 'threshold_alert'`Die Warnung, die ausgelöst werden soll, wenn der Sicherungs Schwellenwert überschritten wird. *threshold_alert* ist vom Datentyp **int**und hat den Standardwert 14.420.  
  
`[ @threshold_alert_enabled = ] 'threshold_alert_enabled'`Gibt an, ob eine Warnung ausgelöst wird, wenn *backup_threshold* überschritten wird. Der Standardwert 1 bedeutet, dass die Warnung ausgelöst wird. *threshold_alert_enabled* ist **Bit**.  
  
`[ @history_retention_period = ] 'history_retention_period'`Der Zeitraum in Minuten, in dem der Verlauf beibehalten wird. *history_retention_period* ist vom Datentyp **int**und hat den Standardwert NULL. Falls nichts angegeben wird, wird ein Wert von 14420 verwendet.  
  
## <a name="return-code-values"></a>Rückgabecodewerte  
 „0“ (erfolgreich) oder „1“ (fehlerhaft)  
  
## <a name="result-sets"></a>Resultsets  
 Keine  
  
## <a name="remarks"></a>Bemerkungen  
 **sp_add_log_shipping_secondary_database** muss von der **Master** -Datenbank auf dem sekundären Server ausgeführt werden. Diese gespeicherte Prozedur führt folgende Aktionen aus:  
  
1.  **sp_add_log_shipping_secondary_primary** sollte vor dieser gespeicherten Prozedur aufgerufen werden, um die Informationen zu den primären Protokoll Versand Datenbanken auf dem sekundären Server zu initialisieren.  
  
2.  Fügt einen Eintrag für die sekundäre Datenbank in **log_shipping_secondary_databases** mit den bereitgestellten Argumenten hinzu.  
  
3.  Fügt einen lokalen Überwachungsdaten Satz in **log_shipping_monitor_secondary** auf dem sekundären Server mithilfe der angegebenen Argumente hinzu.  
  
4.  Wenn der Überwachungs Server nicht mit dem sekundären Server identisch ist, wird in **log_shipping_monitor_secondary** auf dem Überwachungs Server ein Überwachungsdaten Satz mithilfe der angegebenen Argumente hinzugefügt.  
  
## <a name="permissions"></a>Berechtigungen  
 Nur Mitglieder der festen Serverrolle **sysadmin** können diese Prozedur ausführen.  
  
## <a name="examples"></a>Beispiele  
 Dieses Beispiel veranschaulicht die Verwendung der gespeicherten Prozedur **sp_add_log_shipping_secondary_database** , um die Datenbank **LogShipAdventureWorks** als sekundäre Datenbank in einer Protokoll Versand Konfiguration hinzuzufügen, wobei [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] sich die primäre Datenbank auf dem primären Server befindet.  
  
```  
EXEC master.dbo.sp_add_log_shipping_secondary_database   
@secondary_database = N'LogShipAdventureWorks'   
,@primary_server = N'TRIBECA'   
,@primary_database = N'AdventureWorks2012'   
,@restore_delay = 0   
,@restore_mode = 1   
,@disconnect_users = 0   
,@restore_threshold = 45     
,@threshold_alert_enabled = 0   
,@history_retention_period = 1440 ;  
GO  
```  
  
## <a name="see-also"></a>Weitere Informationen  
 [Informationen zum Protokollversand &#40;SQL Server&#41;](../../database-engine/log-shipping/about-log-shipping-sql-server.md)   
 [Gespeicherte Systemprozeduren &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
