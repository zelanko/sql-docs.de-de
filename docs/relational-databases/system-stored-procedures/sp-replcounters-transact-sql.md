---
title: sp_replcounters (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/03/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- sp_replcounters
- sp_replcounters_TSQL
helpviewer_keywords:
- sp_replcounters
ms.assetid: fe585b1f-edda-421f-81d6-8a03a3a535d2
author: stevestein
ms.author: sstein
ms.openlocfilehash: 12ddbfe11a2b1a29dadaacde845f96e70959bebb
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "68771004"
---
# <a name="sp_replcounters-transact-sql"></a>sp_replcounters (Transact-SQL)
[!INCLUDE[appliesto-ss-asdbmi-xxxx-xxx-md](../../includes/appliesto-ss-asdbmi-xxxx-xxx-md.md)]

  Gibt Replikationsstatistiken über Latenz, Durchsatz und Transaktionsanzahl für alle veröffentlichten Datenbanken zurück. Diese gespeicherte Prozedur wird auf dem Verleger für jede Datenbank ausgeführt.  
  
 ![Symbol für Themenlink](../../database-engine/configure-windows/media/topic-link.gif "Symbol für Themenlink") [Transact-SQL-Syntaxkonventionen](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```  
  
sp_replcounters  
  
```  
  
## <a name="result-sets"></a>Resultsets  
  
|Spaltenname|Datentyp|BESCHREIBUNG|  
|-----------------|---------------|-----------------|  
|**Datenbank**|**sysname**|Der Name der Datenbank.|  
|**Replicated transactions**|**int**|Anzahl der Transaktionen im Protokoll, die darauf warten, an die Verteilungsdatenbank übermittelt zu werden.|  
|**Replication rate trans/sec**|**float**|Durchschnittliche Anzahl der Transaktionen, die pro Sekunde an die Verteilungsdatenbank übermittelt wurden.|  
|**Replikations Latenz**|**float**|Durchschnittliche Zeit in Sekunden, für die Transaktionen im Protokoll verblieben, bevor sie verteilt wurden.|  
|**Replbeginlsn**|**Binär (10)**|Protokollfolgenummer (LSN, Log Sequence Number) des aktuellen Abschneidepunkts im Protokoll.|  
|**Replnextlsn**|**Binär (10)**|LSN des nächsten Commitdatensatzes, der auf die Übermittlung an die Verteilungsdatenbank wartet.|  
  
## <a name="remarks"></a>Bemerkungen  
 **sp_replcounters** wird bei der Transaktions Replikation verwendet.  
  
## <a name="permissions"></a>Berechtigungen  
 Erfordert die Mitgliedschaft in der festen Datenbankrolle **db_owner** oder der festen Serverrolle **sysadmin** .  
  
## <a name="see-also"></a>Weitere Informationen  
 [sp_replcmds &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-replcmds-transact-sql.md)   
 [sp_repldone &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/sp-repldone-transact-sql.md)   
 [sp_replflush &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/sp-replflush-transact-sql.md)   
 [Gespeicherte Systemprozeduren &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
