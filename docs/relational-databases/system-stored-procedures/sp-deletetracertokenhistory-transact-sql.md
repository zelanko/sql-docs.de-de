---
title: sp_deletetracertokenhistory (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/15/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- sp_deletetracertokenhistory
- sp_deletetracertokenhistory_TSQL
helpviewer_keywords:
- sp_deletetracertokenhistory
ms.assetid: 9ae1be14-0d2f-40b1-9d6e-22d79726abf4
author: stevestein
ms.author: sstein
ms.openlocfilehash: cf591964e5dfef0536c79b0b35e5918d4f46d972
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/27/2020
ms.locfileid: "68771140"
---
# <a name="sp_deletetracertokenhistory-transact-sql"></a>sp_deletetracertokenhistory (Transact-SQL)

[!INCLUDE[appliesto-ss-asdbmi-xxxx-xxx-md](../../includes/appliesto-ss-asdbmi-xxxx-xxx-md.md)]

Entfernt Überwachungs Token-Datensätze aus den [MStracer_tokens &#40;Transact-SQL-&#41;](../../relational-databases/system-tables/mstracer-tokens-transact-sql.md) und MStracer_history &#40;Systemtabellen von [Transact-SQL](../../relational-databases/system-tables/mstracer-history-transact-sql.md) . Diese gespeicherte Prozedur wird auf dem Verleger für die Veröffentlichungsdatenbank oder auf dem Verteiler für die Verteilungsdatenbank ausgeführt.

![Symbol für Themenlink](../../database-engine/configure-windows/media/topic-link.gif "Symbol für Themenlink") [Transact-SQL-Syntaxkonventionen](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)

## <a name="syntax"></a>Syntax

```
sp_deletetracertokenhistory [ @publication = ] 'publication'
    [ , [ @tracer_id = ] tracer_id ]
    [ , [ @cutoff_date = ] cutoff_date ]
    [ , [ @publisher = ] 'publisher' ]
    [ , [ @publisher_db = ] 'publisher_db' ]
```

## <a name="arguments"></a>Argumente

`@publication= 'publication'`  
Der Name der Veröffentlichung, in die das Überwachungstoken eingefügt wurde. Der Datentyp ist vom Datentyp **vom Datentyp sysname**. Dieser Parameter ist erforderlich.

`[ @tracer_id= ] tracer_id`  
Die ID des zu löschenden Überwachungstokens. Der Datentyp ist " **int**". Der Standardwert ist *null*. Wenn der Wert *null*ist, werden alle Überwachungs Token gelöscht, die zur Veröffentlichung gehören.

`[ @cutoff_date= ] cutoff_date`  
Überwachungs Token, die vor diesem Datum in die Veröffentlichung eingefügt wurden, werden gelöscht. Der **Datentyp ist "DateTime**". Der Standardwert ist *NULL*.

`[ @publisher= ] 'publisher'`  
Der Name des Verlegers. Der Datentyp ist vom Datentyp **vom Datentyp sysname**. Der Standardwert ist *NULL*.

> [!NOTE]
> Dieser Parameter sollte nur für nicht-- [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Verleger oder beim Ausführen der gespeicherten Prozedur vom Verteiler angegeben werden.

`[ @publisher_db= ] 'publisher_db'`  
Der Name der Veröffentlichungsdatenbank. Der Datentyp ist vom Datentyp **vom Datentyp sysname**. Der Standardwert ist NULL. Dieser Parameter wird ignoriert, wenn die gespeicherte Prozedur auf dem Verleger ausgeführt wird.

> [!NOTE]
> Dieser Parameter muss beim Ausführen der gespeicherten Prozedur vom Verteiler angegeben werden.

## <a name="return-code-values"></a>Rückgabecodewerte

**0** (Erfolg) oder **1** (Fehler)

## <a name="remarks"></a>Bemerkungen

**sp_deletetracertokenhistory** wird bei der Transaktions Replikation verwendet.  

Wenn Sie beide Parameter *tracer_id* und *cutoff_date*angeben, tritt ein Fehler auf.

Wenn Sie **sp_deletetracertokenhistory** nicht zum Löschen von Überwachungs Token-Metadaten ausführen, werden die Informationen beim regelmäßigen geplanten Verlaufs Bereinigung gelöscht.

Überwachungs Token-IDs können durch Ausführen [sp_helptracertokens &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/sp-helptracertokens-transact-sql.md) oder durch Abfragen der [MStracer_tokens &#40;Transact-SQL-&#41;](../../relational-databases/system-tables/mstracer-tokens-transact-sql.md) Systemtabelle ermittelt werden.

## <a name="permissions"></a>Berechtigungen

Nur die folgenden Mitarbeiter verfügen über die Berechtigung, **sp_deletetracertokenhistory**auszuführen:

- Mitglieder der **replmonitor** -Rollen in der Verteilungs Datenbank
- Mitglieder der festen Server Rolle **sysadmin** .
- Mitglieder der Daten Bank Rolle **db_owner** in der Veröffentlichungs Datenbank.
- Der **db_owner** der fixierten Datenbank.

## <a name="see-also"></a>Weitere Informationen

[Messen der Latenzzeit und Überprüfen der Verbindungen bei Transaktionsreplikationen](../../relational-databases/replication/monitor/measure-latency-and-validate-connections-for-transactional-replication.md)

[sp_helptracertokenhistory &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/sp-helptracertokenhistory-transact-sql.md)
