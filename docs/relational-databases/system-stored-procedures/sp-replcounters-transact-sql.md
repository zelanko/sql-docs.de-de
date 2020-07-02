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
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 98e5064c571a67afe445f265eaac693432cb5b38
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/01/2020
ms.locfileid: "85645450"
---
# <a name="sp_replcounters-transact-sql"></a>sp_replcounters (Transact-SQL)
[!INCLUDE [SQL Server SQL MI](../../includes/applies-to-version/sql-asdbmi.md)]

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
|**Replbeginlsn**|**binary(10)**|Protokollfolgenummer (LSN, Log Sequence Number) des aktuellen Abschneidepunkts im Protokoll.|  
|**Replnextlsn**|**binary(10)**|LSN des nächsten Commitdatensatzes, der auf die Übermittlung an die Verteilungsdatenbank wartet.|  
  
## <a name="remarks"></a>Hinweise  
 **sp_replcounters** wird für die Transaktionsreplikation verwendet.  
  
## <a name="permissions"></a>Berechtigungen  
 Erfordert die Mitgliedschaft in der festen Datenbankrolle **db_owner** oder der festen Serverrolle **sysadmin** .  
  
## <a name="see-also"></a>Weitere Informationen  
 [sp_replcmds &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/sp-replcmds-transact-sql.md)   
 [sp_repldone &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/sp-repldone-transact-sql.md)   
 [sp_replflush &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/sp-replflush-transact-sql.md)   
 [Gespeicherte Systemprozeduren &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
