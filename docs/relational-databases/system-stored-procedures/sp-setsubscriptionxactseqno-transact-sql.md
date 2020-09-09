---
description: sp_setsubscriptionxactseqno (Transact-SQL)
title: sp_setsubscriptionxactseqno (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- sp_setsubscriptionxactseqno
- sp_setsubscriptionxactseqno_TSQL
helpviewer_keywords:
- sp_setsubscriptionxactseqno
ms.assetid: cdb4e0ba-5370-4905-b03f-0b0c6f080ca6
author: markingmyname
ms.author: maghan
ms.openlocfilehash: c7908e6cc064a5ad5c973236be759bdea313c5f6
ms.sourcegitcommit: dd36d1cbe32cd5a65c6638e8f252b0bd8145e165
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/08/2020
ms.locfileid: "89547886"
---
# <a name="sp_setsubscriptionxactseqno-transact-sql"></a>sp_setsubscriptionxactseqno (Transact-SQL)
[!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

  Wird während der Problembehandlung verwendet, um die zuletzt übermittelte Transaktion mithilfe der Protokoll Folge Nummer (Log Sequence Number, LSN) anzugeben, sodass die Verteilungs-Agent die Übermittlung bei der nächsten Transaktion beginnen kann. Beim Neustart gibt das Verteilungs-Agent Transaktionen zurück, die größer sind als dieses Wasserzeichen (LSN) aus dem Cache der Verteilungs Datenbank (MSrepl_commands). Diese gespeicherte Prozedur wird auf dem Abonnenten für die Abonnement Datenbank ausgeführt. Wird nicht für Nicht-SQL Server-Abonnenten unterstützt.  
  
> [!CAUTION]  
>  Eine falsche Verwendung dieser gespeicherten Prozedur oder die Angabe eines falschen LSN-Werts kann den Verteilungs-Agent dazu veranlassen, Änderungen, die bereits auf den Abonnenten angewendet wurden, rückgängig zu machen oder alle noch verbleibenden Änderungen auszulassen.  
  
 ![Symbol für Themenlink](../../database-engine/configure-windows/media/topic-link.gif "Symbol für Themenlink") [Transact-SQL-Syntaxkonventionen](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```  
  
sp_setsubscriptionxactseqno [ @publisher = ] 'publisher'  
        , [ @publisher_db = ] 'publisher_db'  
        , [ @publication = ] 'publication'  
        , [ @xact_seqno = ] xact_seqno   
```  
  
## <a name="arguments"></a>Argumente  
`[ @publisher = ] 'publisher'` Der Name des Verlegers. *Publisher* ist vom **Datentyp vom Datentyp sysname**und hat keinen Standardwert.  
  
`[ @publisher_db = ] 'publisher_db'` Der Name der Veröffentlichungs Datenbank. *publisher_db* ist vom **Datentyp vom Datentyp sysname**und hat keinen Standardwert. Bei einem nicht-SQL Server Verleger ist *publisher_db* der Name der Verteilungs Datenbank.  
  
`[ @publication = ] 'publication'` Der Name der Veröffentlichung. *Publication* ist vom **Datentyp vom Datentyp sysname**und hat keinen Standardwert. Wenn die Verteilungs-Agent von mehreren Veröffentlichungen gemeinsam verwendet wird, müssen Sie den Wert all für *Publication*angeben.  
  
`[ @xact_seqno = ] xact_seqno` Die LSN der nächsten Transaktion auf dem Verteiler, die auf dem Abonnenten angewendet werden soll. *xact_seqno* ist vom Datentyp **varbinary (16)** und hat keinen Standardwert.  
  
## <a name="result-set"></a>Resultset  
  
|Spaltenname|Datentyp|BESCHREIBUNG|  
|-----------------|---------------|-----------------|  
|**ORIGINAL XACT_SEQNO**|**varbinary(16)**|Die ursprüngliche LSN der nächsten Transaktion, die auf dem Abonnenten angewendet werden soll.|  
|**UPDATED XACT_SEQNO**|**varbinary(16)**|Die aktualisierte LSN der nächsten Transaktion, die auf dem Abonnenten angewendet werden soll.|  
|**SUBSCRIPTION STREAM COUNT**|**int**|Die Anzahl der bei der letzten Synchronisierung verwendeten Abonnementdatenströme.|  
  
## <a name="return-code-values"></a>Rückgabecodewerte  
 **0** (Erfolg) oder **1** (Fehler)  
  
## <a name="remarks"></a>Hinweise  
 **sp_setsubscriptionxactseqno** wird bei der Transaktions Replikation verwendet.  
  
 **sp_setsubscriptionxactseqno** kann nicht in einer Peer-zu-Peer-Transaktions Replikations Topologie verwendet werden.  
  
 **sp_setsubscriptionxactseqno** kann verwendet werden, um eine bestimmte Transaktion zu überspringen, die einen Fehler verursacht, wenn auf dem Abonnenten angewendet wird. Wenn ein Fehler auftritt und der Verteilungs-Agent beendet wird, rufen Sie [sp_helpsubscriptionerrors &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/sp-helpsubscriptionerrors-transact-sql.md) auf dem Verteiler auf, um den xact_seqno Wert der fehlgeschlagenen Transaktion abzurufen, und rufen Sie dann **sp_setsubscriptionxactseqno**auf, und übergeben Sie den Wert für *xact_seqno*. Dadurch wird sichergestellt, dass nur die Befehle nach dieser LSN verarbeitet werden.  
  
 Geben Sie den Wert **0** für *xact_seqno* an, um alle ausstehenden Befehle in der Verteilungs Datenbank an den Abonnenten zu übermitteln.  
  
 **sp_setsubscriptionxactseqno** schlägt möglicherweise fehl, wenn die Verteilungs-Agent multiabonnementstreams verwendet.  
  
 Wenn dieser Fehler auftritt, müssen Sie den Verteilungs-Agent mit einem Datenstrom für ein einzelnes Abonnement ausführen. Weitere Informationen finden Sie unter [Replication Distribution Agent](../../relational-databases/replication/agents/replication-distribution-agent.md).  
  
## <a name="permissions"></a>Berechtigungen  
 Nur Mitglieder der festen Server Rolle **sysadmin** oder der festen Daten Bank Rolle **db_owner** können **sp_setsubscriptionxactseqno**ausführen.  
  
## <a name="see-more"></a>Weitere Informationen

[Blog: Überspringen einer Transaktion](https://repltalk.com/2019/05/28/how-to-skip-a-transaction/)  
