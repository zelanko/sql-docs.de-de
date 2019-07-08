---
title: Sp_change_log_shipping_secondary_database (Transact-SQL) | Microsoft-Dokumentation
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
manager: craigg
ms.openlocfilehash: 5af98bd479738785c341b2618561eaab3f43b5d1
ms.sourcegitcommit: cff8dd63959d7a45c5446cadf1f5d15ae08406d8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/05/2019
ms.locfileid: "67586017"
---
# <a name="spchangelogshippingsecondarydatabase-transact-sql"></a>sp_change_log_shipping_secondary_database (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Ändert Einstellungen sekundärer Datenbanken.  
  
 ![Themenlinksymbol](../../database-engine/configure-windows/media/topic-link.gif "Topic link icon") [Transact-SQL Syntax Conventions (Transact-SQL-Syntaxkonventionen)](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
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
`[ @restore_delay = ] 'restore_delay'` Die Zeitspanne in Minuten, die der sekundäre Server vor dem Wiederherstellen einer bestimmten Sicherungsdatei wartet. *Restore_delay* ist **Int** und darf nicht NULL sein. Der Standardwert ist 0.  
  
`[ @restore_all = ] 'restore_all'` Wenn der Wert gleich 1, der sekundäre Server alle verfügbaren Sicherungen des Transaktionsprotokolls wiederhergestellt, wenn der Wiederherstellungsauftrag ausgeführt wird. Andernfalls wird es beendet, nachdem eine Datei wiederhergestellt wurde. *Restore_all* ist **Bit** und darf nicht NULL sein.  
  
`[ @restore_mode = ] 'restore_mode'` Der Wiederherstellungsmodus für die sekundäre Datenbank.  
  
 0 = Wiederherstellungsprotokoll mit NORECOVERY.  
  
 1 = das Protokoll mit STANDBY wiederhergestellt.  
  
 *Wiederherstellen* ist **Bit** und darf nicht NULL sein.  
  
`[ @disconnect_users = ] 'disconnect_users'` Wenn Benutzer 1 festgelegt ist, von der sekundären Datenbank getrennt ist, wenn ein Wiederherstellungsvorgang ausgeführt wird. Standard = 0. *Disconnect_users* ist **Bit** und darf nicht NULL sein.  
  
`[ @block_size = ] 'block_size'` Die Größe in Bytes, die als Blockgröße für das Sicherungsmedium verwendet wird. *Block_size* ist **Int** hat den Standardwert 1.  
  
`[ @buffer_count = ] 'buffer_count'` Die Gesamtanzahl von Puffern, die von des Backup- oder Restore-Vorgangs verwendet werden soll. *Buffer_count* ist **Int** hat den Standardwert 1.  
  
`[ @max_transfer_size = ] 'max_transfer_size'` Die Größe in Bytes, der maximalen Eingabe- oder ausgabeanforderung ausgestellt hat [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] auf das Sicherungsmedium. *Max_transfersize* ist **Int** und kann NULL sein.  
  
`[ @restore_threshold = ] 'restore_threshold'` Die Anzahl der Minuten zwischen Wiederherstellungsvorgängen verstreichen darf, bevor eine Warnung generiert wird, Wiederherstellungsvorgänge an. *Restore_threshold* ist **Int** und darf nicht NULL sein.  
  
`[ @threshold_alert = ] 'threshold_alert'` Ist die Warnung ausgelöst wird, wenn die wiederherstellungsschwelle überschritten wird. *Threshold_alert* ist **Int**, hat den Standardwert 14420.  
  
`[ @threshold_alert_enabled = ] 'threshold_alert_enabled'` Gibt an, ob eine Warnung wird ausgelöst, wenn *Restore_threshold*überschritten wird. 1 = aktiviert; 0 = deaktiviert. *Threshold_alert_enabled* ist **Bit** und darf nicht NULL sein.  
  
`[ @history_retention_period = ] 'history_retention_period'` Ist die Zeitdauer in Minuten, die in denen der Verlauf beibehalten werden. *History_retention_period* ist **Int**. Der Wert 1440 wird verwendet, wenn keine Angabe erfolgt.  
  
## <a name="return-code-values"></a>Rückgabecodewerte  
 0 (Erfolg) oder 1 (Fehler)  
  
## <a name="result-sets"></a>Resultsets  
 None  
  
## <a name="remarks"></a>Hinweise  
 **Sp_change_log_shipping_secondary_database** muss ausgeführt werden, aus der **master** Datenbank auf dem sekundären Server. Diese gespeicherte Prozedur führt folgende Aktionen aus:  
  
1.  Ändert die Einstellungen in der **Log_shipping_secondary_database** Datensätzen, sofern erforderlich.  
  
2.  Ändert den lokalen Überwachungsdatensatz in **Log_shipping_monitor_secondary** auf dem sekundären Server mithilfe bereitgestellter Argumente, falls erforderlich.  

[!INCLUDE[freshInclude](../../includes/paragraph-content/fresh-note-steps-feedback.md)]

## <a name="permissions"></a>Berechtigungen  
 Nur Mitglieder der festen Serverrolle **sysadmin** können diese Prozedur ausführen.  
  
## <a name="examples"></a>Beispiele  
 In diesem Beispiel wird die Verwendung **Sp_change_log_shipping_secondary_database** Parameter sekundärer Datenbanken für die Datenbank aktualisieren **LogShipAdventureWorks**.  
  
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
  
## <a name="see-also"></a>Siehe auch  
 [Über den Protokollversand &#40;SQLServer&#41;](../../database-engine/log-shipping/about-log-shipping-sql-server.md)   
 [Gespeicherte Systemprozeduren &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
