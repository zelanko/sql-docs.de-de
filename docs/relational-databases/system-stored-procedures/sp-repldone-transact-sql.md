---
title: Sp_repldone (Transact-SQL) | Microsoft-Dokumentation
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
ms.openlocfilehash: 5ed4502b7f3e737b8e3adbfae852c2a513e2ccd4
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "68006886"
---
# <a name="sprepldone-transact-sql"></a>sp_repldone (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Aktualisiert den Datensatz, mit dem die letzte verteilte Transaktion des Servers identifiziert wird. Diese gespeicherte Prozedur wird auf dem Verleger für die Veröffentlichungsdatenbank ausgeführt.  
  
> [!CAUTION]  
>  Wenn Sie nicht ausführen **Sp_repldone** manuell Sie die Reihenfolge und Konsistenz übermittelter Transaktionen ungültig machen können. **Sp_repldone** sollte nur für die Problembehandlung bei der Replikation ein erfahrener Supportmitarbeiter verwendet werden.  
  
 ![Themenlinksymbol](../../database-engine/configure-windows/media/topic-link.gif "Topic link icon") [Transact-SQL Syntax Conventions (Transact-SQL-Syntaxkonventionen)](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```  
  
sp_repldone [ @xactid= ] xactid   
        , [ @xact_seqno= ] xact_seqno   
    [ , [ @numtrans= ] numtrans ]   
    [ , [ @time= ] time   
    [ , [ @reset= ] reset ]  
```  
  
## <a name="arguments"></a>Argumente  
`[ @xactid = ] xactid` Ist die protokollfolgenummer (LSN) des ersten Datensatzes für die letzte verteilte Transaktion des Servers an. *Xactid* ist **Binary(10)-Wert**, hat keinen Standardwert.  
  
`[ @xact_seqno = ] xact_seqno` Ist die LSN des letzten Datensatzes für die letzte verteilte Transaktion des Servers an. *Xact_seqno* ist **Binary(10)-Wert**, hat keinen Standardwert.  
  
`[ @numtrans = ] numtrans` Ist die Anzahl der verteilten Transaktionen. *Numtrans* ist **Int**, hat keinen Standardwert.  
  
`[ @time = ] time` Die Anzahl der Millisekunden, ist Wenn angegeben, erforderlich, um die letzten Transaktionsbatches zu verteilen. *Zeit* ist **Int**, hat keinen Standardwert.  
  
`[ @reset = ] reset` Entspricht dem rücksetzungsstatus. *Zurücksetzen* ist **Int**, hat keinen Standardwert. Wenn **1**, werden alle replizierten Transaktionen im Protokoll markiert werden als verteilt. Wenn **0**, das Transaktionsprotokoll wird auf die erste replizierte Transaktion zurückgesetzt und es werden keine replizierten Transaktionen gekennzeichnet. als verteilt. *Zurücksetzen* ist nur gültig, wenn beide *Xactid* und *Xact_seqno* NULL sind.  
  
## <a name="return-code-values"></a>Rückgabecodewerte  
 **0** (Erfolg) oder **1** (Fehler)  
  
## <a name="remarks"></a>Hinweise  
 **Sp_repldone** wird in Transaktionsreplikationen verwendet.  
  
 **Sp_repldone** vom Protokollleserprozess verwendet, um nachzuverfolgen, welche Transaktionen verteilt wurden.  
  
 Mit **Sp_repldone**, Sie können dem Server manuell mitteilen, dass eine Transaktion repliziert (an den Verteiler gesendet) wurde. Außerdem haben Sie damit die Möglichkeit, anstelle der entsprechend markierten Transaktion eine andere Transaktion für die nächste Replikation festzulegen. Sie können sich in der Liste mit den replizierten Transaktionen vorwärts oder rückwärts bewegen (alle Transaktionen vor dieser Transaktion und diese selbst werden als verteilt gekennzeichnet).  
  
 Die erforderlichen Parameter *Xactid* und *Xact_seqno* erhalten Sie, indem Sie mithilfe von **Sp_repltrans** oder **Sp_replcmds**.  
  
## <a name="permissions"></a>Berechtigungen  
 Mitglieder der **Sysadmin** festen Serverrolle oder die **Db_owner** feste Datenbankrolle können ausführen **Sp_repldone**.  
  
## <a name="examples"></a>Beispiele  
 Wenn *Xactid* NULL ist, *Xact_seqno* NULL ist, und *zurücksetzen* ist **1**, werden alle replizierten Transaktionen im Protokoll markiert werden als verteilt. Dies bietet sich an, wenn replizierte Transaktionen im Protokoll nicht mehr gültig sind und das Protokoll abgeschnitten werden soll, wie im folgenden Beispiel:  
  
```  
EXEC sp_repldone @xactid = NULL, @xact_segno = NULL, @numtrans = 0,     @time = 0, @reset = 1  
```  
  
> [!CAUTION]  
>  Diese Prozedur kann in Notsituationen verwendet werden, damit das Transaktionsprotokoll abgeschnitten werden kann, wenn Transaktionen mit ausstehender Replikation vorhanden sind.  
  
## <a name="see-also"></a>Siehe auch  
 [sp_replcmds &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-replcmds-transact-sql.md)   
 [sp_replflush &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-replflush-transact-sql.md)   
 [Sp_repltrans &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-repltrans-transact-sql.md)   
 [Gespeicherte Systemprozeduren &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
