---
title: sp_repldone (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/03/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- sp_repldone
- sp_repldone_TSQL
helpviewer_keywords:
- sp_repldone
ms.assetid: 045d3cd1-712b-44b7-a56a-c9438d4077b9
author: stevestein
ms.author: sstein
ms.openlocfilehash: 3df1b991f160aafdfcfd71818c8bd3e7cbd10ffa
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/26/2020
ms.locfileid: "72798389"
---
# <a name="sp_repldone-transact-sql"></a>sp_repldone (Transact-SQL)
[!INCLUDE[appliesto-ss-asdbmi-xxxx-xxx-md](../../includes/appliesto-ss-asdbmi-xxxx-xxx-md.md)]

  Aktualisiert den Datensatz, mit dem die letzte verteilte Transaktion des Servers identifiziert wird. Diese gespeicherte Prozedur wird auf dem Verleger für die Veröffentlichungs Datenbank ausgeführt.  
  
> [!CAUTION]  
>  Wenn Sie **sp_repldone** manuell ausführen, können Sie die Reihenfolge und Konsistenz abgeschlossener Transaktionen für ungültig erklären. **sp_repldone** sollten nur für die Problembehandlung der Replikation verwendet werden, wie von einem erfahrenen Supportmitarbeiter unterstützt.  
  
 ![Symbol für Themenlink](../../database-engine/configure-windows/media/topic-link.gif "Symbol für Themenlink") [Transact-SQL-Syntaxkonventionen](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```
sp_repldone [ @xactid= ] xactid   
        , [ @xact_seqno= ] xact_seqno   
    [ , [ @numtrans= ] numtrans ]   
    [ , [ @time= ] time   
    [ , [ @reset= ] reset ]  
```  
  
## <a name="arguments"></a>Argumente  
`[ @xactid = ] xactid`Die Protokoll Folge Nummer (Log Sequence Number, LSN) des ersten Datensatzes für die letzte verteilte Transaktion des Servers. *xactid* ist **Binär (10)** und hat keinen Standardwert.  
  
`[ @xact_seqno = ] xact_seqno`Die LSN des letzten Datensatzes für die letzte verteilte Transaktion des Servers. *xact_seqno* ist **Binary (10)** und hat keinen Standardwert.  
  
`[ @numtrans = ] numtrans`Die Anzahl der verteilten Transaktionen. *numtrans* ist vom Datentyp **int**und hat keinen Standardwert.  
  
`[ @time = ] time`Die Anzahl der Millisekunden, sofern vorhanden, die zum Verteilen des letzten Batches von Transaktionen benötigt wird. *time* ist vom Datentyp **int**und hat keinen Standardwert.  
  
`[ @reset = ] reset`Der Zurücksetzungs Status. *Reset* ist vom Datentyp **int**und hat keinen Standardwert. Bei **1**werden alle replizierten Transaktionen im Protokoll als verteilt gekennzeichnet. Wenn der Wert **0**ist, wird das Transaktionsprotokoll auf die erste replizierte Transaktion zurückgesetzt, und es werden keine replizierten Transaktionen als verteilt gekennzeichnet. *Reset* ist nur gültig, wenn sowohl *xactid* als auch *xact_seqno* NULL sind.  
  
## <a name="return-code-values"></a>Rückgabecodewerte  
 **0** (Erfolg) oder **1** (Fehler)  
  
## <a name="remarks"></a>Hinweise  
 **sp_repldone** wird bei der Transaktions Replikation verwendet.  
  
 **sp_repldone** wird vom Protokoll Leseprozess verwendet, um zu verfolgen, welche Transaktionen verteilt wurden.  
  
 Mit **sp_repldone**können Sie dem Server manuell mitteilen, dass eine Transaktion repliziert (an den Verteiler gesendet) wurde. Außerdem haben Sie damit die Möglichkeit, anstelle der entsprechend markierten Transaktion eine andere Transaktion für die nächste Replikation festzulegen. Sie können sich in der Liste mit den replizierten Transaktionen vorwärts oder rückwärts bewegen (alle Transaktionen vor dieser Transaktion und diese selbst werden als verteilt gekennzeichnet).  
  
 Die erforderlichen Parameter " *xactid* " und " *xact_seqno* " können mithilfe **sp_repltrans** oder **sp_replcmds**abgerufen werden.  
  
## <a name="permissions"></a>Berechtigungen  
 Mitglieder der festen Server Rolle **sysadmin** oder der festen Daten Bank Rolle **db_owner** können **sp_repldone**ausführen.  
  
## <a name="examples"></a>Beispiele  
 Wenn *xactid* NULL ist, *xact_seqno* NULL ist und *Reset* den Wert **1**hat, werden alle replizierten Transaktionen im Protokoll als verteilt gekennzeichnet. Dies bietet sich an, wenn replizierte Transaktionen im Protokoll nicht mehr gültig sind und das Protokoll abgeschnitten werden soll, wie im folgenden Beispiel:  
  
```sql
EXEC sp_repldone @xactid = NULL, @xact_seqno = NULL, @numtrans = 0, @time = 0, @reset = 1  
```  
  
> [!CAUTION]  
>  Diese Prozedur kann in Notsituationen verwendet werden, damit das Transaktionsprotokoll abgeschnitten werden kann, wenn Transaktionen mit ausstehender Replikation vorhanden sind.  
  
## <a name="see-also"></a>Weitere Informationen  
 [sp_replcmds &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/sp-replcmds-transact-sql.md)   
 [sp_replflush &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/sp-replflush-transact-sql.md)   
 [sp_repltrans &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/sp-repltrans-transact-sql.md)   
 [Gespeicherte Systemprozeduren &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
