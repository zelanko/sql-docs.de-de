---
title: sp_change_log_shipping_secondary_database (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_change_log_shipping_secondary_database
- sp_change_log_shipping_secondary_database_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sp_change_log_shipping_secondary_database
ms.assetid: 3ebcf2f1-980f-4543-a84b-fbaeea54eeac
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: d0bd62fe3462441d4eab9d3d89bce20cf1144131
ms.sourcegitcommit: 2a06c87aa195bc6743ebdc14b91eb71ab6b91298
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/25/2019
ms.locfileid: "72909554"
---
# <a name="sp_change_log_shipping_secondary_database-transact-sql"></a>sp_change_log_shipping_secondary_database (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Ändert Einstellungen sekundärer Datenbanken.  
  
 ![Themen Link Symbol](../../database-engine/configure-windows/media/topic-link.gif "Link Symbol "Thema"") [Transact-SQL-Syntax Konventionen](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```  
  
sp_change_log_shipping_secondary_database  
[ @secondary_database = ] 'secondary_database',  
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
`[ @restore_delay = ] 'restore_delay'` die Zeitspanne in Minuten, die der sekundäre Server wartet, bevor er eine angegebene Sicherungsdatei wiederherstellt. *restore_delay* ist vom Datentyp **int** und kann nicht NULL sein. Der Standardwert ist 0.  
  
`[ @restore_all = ] 'restore_all'` wenn der Wert auf 1 festgelegt ist, stellt der sekundäre Server bei Ausführung des Wiederherstellungs Auftrags alle verfügbaren Transaktionsprotokoll Sicherungen wieder her. Andernfalls wird Sie beendet, nachdem eine Datei wieder hergestellt wurde. *restore_all* ist vom **Bit** und kann nicht NULL sein.  
  
`[ @restore_mode = ] 'restore_mode'` den Wiederherstellungs Modus für die sekundäre Datenbank.  
  
 0 = Wiederherstellungsprotokoll mit NORECOVERY.  
  
 1 = RESTORE LOG with Standby.  
  
 *Restore* ist ein **Bit** und kann nicht NULL sein.  
  
`[ @disconnect_users = ] 'disconnect_users'` wenn der Wert auf 1 festgelegt ist, werden die Benutzer von der sekundären Datenbank getrennt, wenn ein Wiederherstellungs Vorgang ausgeführt wird. Standardwert = 0. *disconnect_users* ist vom **Bit** und kann nicht NULL sein.  
  
`[ @block_size = ] 'block_size'` die Größe in Bytes, die als Blockgröße für das Sicherungsmedium verwendet wird. *block_size* ist vom Datentyp **int** und hat den Standardwert-1.  
  
`[ @buffer_count = ] 'buffer_count'` die Gesamtanzahl der Puffer, die vom Sicherungs-oder Wiederherstellungs Vorgang verwendet werden. *buffer_count* ist vom Datentyp **int** und hat den Standardwert-1.  
  
`[ @max_transfer_size = ] 'max_transfer_size'` die Größe der maximalen Eingabe-oder Ausgabeanforderung in Bytes an, die von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] an das Sicherungsmedium ausgegeben wird. *max_transfersize* ist vom Datentyp **int** und kann NULL sein.  
  
`[ @restore_threshold = ] 'restore_threshold'` die Anzahl der zulässigen Minuten zwischen Wiederherstellungs Vorgängen, bevor eine Warnung generiert wird. *restore_threshold* ist vom Datentyp **int** und kann nicht NULL sein.  
  
`[ @threshold_alert = ] 'threshold_alert'` ist die Warnung, die ausgelöst werden soll, wenn der Wiederherstellungs Schwellenwert überschritten wird. *threshold_alert* ist vom Datentyp **int**und hat den Standardwert 14420.  
  
`[ @threshold_alert_enabled = ] 'threshold_alert_enabled'` gibt an, ob eine Warnung ausgelöst wird, wenn *restore_threshold*überschritten wird. 1 = aktiviert; 0 = deaktiviert. *threshold_alert_enabled* ist vom **Bit** und kann nicht NULL sein.  
  
`[ @history_retention_period = ] 'history_retention_period'` ist die Zeitspanne in Minuten, in der der Verlauf beibehalten wird. *history_retention_period* ist vom Datentyp **int**. Der Wert 1440 wird verwendet, wenn kein Wert angegeben wird.  
  
## <a name="return-code-values"></a>Rückgabecodewerte  
 0 (Erfolg) oder 1 (Fehler)  
  
## <a name="result-sets"></a>Resultsets  
 InclusionThresholdSetting  
  
## <a name="remarks"></a>Bemerkungen  
 **sp_change_log_shipping_secondary_database** muss von der **Master** -Datenbank auf dem sekundären Server ausgeführt werden. Diese gespeicherte Prozedur führt folgende Aktionen aus:  
  
1.  Ändert die Einstellungen in den **log_shipping_secondary_database** -Datensätzen nach Bedarf.  
  
2.  Ändert den lokalen Überwachungsdaten Satz in **log_shipping_monitor_secondary** auf dem sekundären Server mithilfe der angegebenen Argumente, falls erforderlich.  

## <a name="permissions"></a>Berechtigungen  
 Nur Mitglieder der festen Serverrolle **sysadmin** können diese Prozedur ausführen.  
  
## <a name="examples"></a>Beispiele  
 In diesem Beispiel wird die Verwendung von **sp_change_log_shipping_secondary_database** zum Aktualisieren der Parameter der sekundären Datenbank für die **LogShipAdventureWorks**-Datenbank veranschaulicht.  
  
```  
EXEC master.dbo.sp_change_log_shipping_secondary_database   
 @secondary_database =  'LogShipAdventureWorks'  
,  @restore_delay = 0  
,  @restore_all = 1  
,  @restore_mode = 0  
,  @disconnect_users = 0  
,  @threshold_alert = 14420  
,  @threshold_alert_enabled = 1  
,  @history_retention_period = 14420;  
```  
  
## <a name="see-also"></a>Weitere Informationen finden Sie unter  
 [Informationen zum Protokollversand &#40;SQL Server&#41;](../../database-engine/log-shipping/about-log-shipping-sql-server.md)   
 [Gespeicherte Systemprozeduren &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
