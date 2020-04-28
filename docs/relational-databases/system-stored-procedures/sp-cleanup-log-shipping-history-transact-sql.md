---
title: sp_cleanup_log_shipping_history (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 08/09/2016
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_cleanup_log_shipping_history_TSQL
- sp_cleanup_log_shipping_history
dev_langs:
- TSQL
helpviewer_keywords:
- sp_cleanup_log_shipping_history
ms.assetid: 96d236a9-1d0e-4f83-a4d3-f825b7381e46
author: stevestein
ms.author: sstein
ms.openlocfilehash: 7470baabb9a35a923995d8306b314f9272de0b5c
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/27/2020
ms.locfileid: "68070367"
---
# <a name="sp_cleanup_log_shipping_history-transact-sql"></a>sp_cleanup_log_shipping_history (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Diese gespeicherte Prozedur führt basierend auf der Aufbewahrungsdauer sowohl lokal als auch auf dem Überwachungsserver ein Cleanup des Verlaufs aus.  
  
 ![Symbol für Themenlink](../../database-engine/configure-windows/media/topic-link.gif "Symbol für Themenlink") [Transact-SQL-Syntaxkonventionen](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```  
  
sp_cleanup_log_shipping_history  
[ @agent_id = ] 'agent_id',  
[ @agent_type = ] 'agent_type'  
```  
  
## <a name="arguments"></a>Argumente  
`[ @agent_id = ] 'agent_id',`Die primäre ID für die Sicherung oder die sekundäre ID für kopieren oder wiederherstellen. *agent_id* ist vom Datentyp **uniqueidentifier** und darf nicht NULL sein.  
  
`[ @agent_type = ] 'agent_type'`Der Typ des Protokoll Versand Auftrags. 0 = Sichern, 1 = Kopieren, 2 = Wiederherstellen. *agent_type* ist vom Datentyp **tinyint** und kann nicht NULL sein.  
  
## <a name="return-code-values"></a>Rückgabecodewerte  
 „0“ (erfolgreich) oder „1“ (fehlerhaft)  
  
## <a name="result-sets"></a>Resultsets  
 Keine  
  
## <a name="remarks"></a>Bemerkungen  
 **sp_cleanup_log_shipping_history** muss in der **master** -Datenbank auf einem Protokollversandserver ausgeführt werden. Diese gespeicherte Prozedur führt ein Cleanup lokaler und remote gespeicherter Kopien von **log_shipping_monitor_history_detail** und **log_shipping_monitor_error_detail** basierend auf der Aufbewahrungsdauer für den Verlauf aus.  
  
## <a name="permissions"></a>Berechtigungen  
 Nur Mitglieder der festen Serverrolle **sysadmin** können diese Prozedur ausführen.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Informationen zum Protokoll Versand &#40;SQL Server&#41;](../../database-engine/log-shipping/about-log-shipping-sql-server.md)   
 [Gespeicherte Systemprozeduren &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
