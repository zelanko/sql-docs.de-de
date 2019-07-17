---
title: Sp_deletetracertokenhistory (Transact-SQL) | Microsoft-Dokumentation
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
ms.openlocfilehash: 0a7f70f5cd56867add98150d471d61cbc70faad0
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "68111923"
---
# <a name="spdeletetracertokenhistory-transact-sql"></a>sp_deletetracertokenhistory (Transact-SQL)

[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

Entfernt Überwachungstoken-Datensätze aus der [MStracer_tokens &#40;Transact-SQL&#41; ](../../relational-databases/system-tables/mstracer-tokens-transact-sql.md) und [MStracer_history &#40;Transact-SQL&#41; ](../../relational-databases/system-tables/mstracer-history-transact-sql.md) -Systemtabellen. Diese gespeicherte Prozedur wird auf dem Verleger für die Veröffentlichungsdatenbank oder auf dem Verteiler für die Verteilungsdatenbank ausgeführt.

![Themenlinksymbol](../../database-engine/configure-windows/media/topic-link.gif "Topic link icon") [Transact-SQL Syntax Conventions (Transact-SQL-Syntaxkonventionen)](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)

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
Der Name der Veröffentlichung, in die das Überwachungstoken eingefügt wurde. Der Datentyp **Sysname**. Dieser Parameter ist erforderlich.

`[ @tracer_id= ] tracer_id`  
Die ID des zu löschenden Überwachungstokens. Der Datentyp **Int**. Der Standardwert ist *NULL*. Wenn *null*, alle Überwachungstoken, die zur Veröffentlichung gehörenden werden gelöscht.

`[ @cutoff_date= ] cutoff_date`  
Überwachungstoken, die in der Veröffentlichung eingefügt werden, vor diesem Datum werden gelöscht. Der Datentyp **"DateTime"** . Der Standardwert ist *NULL*.

`[ @publisher= ] 'publisher'`  
Der Name des Verlegers. Der Datentyp **Sysname**. Der Standardwert ist *NULL*.

> [!NOTE]
> Dieser Parameter sollte nur angegeben werden, für nicht - [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Herausgeber oder beim Ausführen der gespeicherten Prozedur vom Verteiler.

`[ @publisher_db= ] 'publisher_db'`  
Der Name der Veröffentlichungsdatenbank. Der Datentyp **Sysname**. Der Standardwert ist NULL. Dieser Parameter wird ignoriert, wenn die gespeicherte Prozedur auf dem Verleger ausgeführt wird.

> [!NOTE]
> Dieser Parameter sollte angegeben werden, wenn die gespeicherte Prozedur vom Verteiler ausgeführt.

## <a name="return-code-values"></a>Rückgabecodewerte

**0** (Erfolg) oder **1** (Fehler)

## <a name="remarks"></a>Hinweise

**Sp_deletetracertokenhistory** wird in Transaktionsreplikationen verwendet.  

Ein Fehler auftritt, wenn Sie beide Parameter angeben *Tracer_id* und *Cutoff_date*.

Wenn Sie nicht ausgeführt werden **Sp_deletetracertokenhistory** um Überwachungstoken-Metadaten zu löschen, die Informationen werden gelöscht, wenn die regelmäßig verlaufscleanups.

Überwachungstoken-IDs können bestimmt werden, indem Sie Ausführung [Sp_helptracertokens &#40;Transact-SQL&#41; ](../../relational-databases/system-stored-procedures/sp-helptracertokens-transact-sql.md) oder durch Abfragen der [MStracer_tokens &#40;Transact-SQL&#41; ](../../relational-databases/system-tables/mstracer-tokens-transact-sql.md) -Systemtabelle.

## <a name="permissions"></a>Berechtigungen

Nur die folgenden Mitarbeiter über die Berechtigung zum Ausführen verfügen **Sp_deletetracertokenhistory**:

- Mitglieder der **Replmonitor** Rollen in der Verteilungsdatenbank
- Mitglieder der **Sysadmin** -Serverrolle sein.
- Mitglieder der **Db_owner** festen Datenbankrolle, in der Veröffentlichungsdatenbank.
- Die **Db_owner** der festen Datenbankrolle.

## <a name="see-also"></a>Siehe auch

[Messen der Latenzzeit und Überprüfen der Verbindungen bei Transaktionsreplikationen](../../relational-databases/replication/monitor/measure-latency-and-validate-connections-for-transactional-replication.md)

[sp_helptracertokenhistory &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-helptracertokenhistory-transact-sql.md)
