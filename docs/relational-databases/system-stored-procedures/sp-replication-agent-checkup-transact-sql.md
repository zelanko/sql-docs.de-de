---
title: Sp_replication_agent_checkup (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/04/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- sp_replication_agent_checkup_TSQL
- sp_replication_agent_checkup
helpviewer_keywords:
- sp_replication_agent_checkup
ms.assetid: 50357c2e-71aa-4e13-9e2e-0977a3655cc9
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 73335322d9e4c8602e299255ebcd3b3b183aaaec
ms.sourcegitcommit: c44014af4d3f821e5d7923c69e8b9fb27aeb1afd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/27/2019
ms.locfileid: "58529872"
---
# <a name="spreplicationagentcheckup-transact-sql"></a>sp_replication_agent_checkup (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Überprüft alle Verteilungsdatenbanken auf Replikations-Agents, die zwar ausgeführt werden, aber innerhalb des angegebenen Taktintervalls keine Verlaufsdaten protokolliert haben. Diese gespeicherte Prozedur wird auf dem Verteiler für jede Datenbank ausgeführt.  
  
 ![Themenlinksymbol](../../database-engine/configure-windows/media/topic-link.gif "Topic link icon") [Transact-SQL Syntax Conventions (Transact-SQL-Syntaxkonventionen)](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```  
  
sp_replication_agent_checkup [ [ @heartbeat_interval = ] heartbeat_interval ]  
```  
  
## <a name="arguments"></a>Argumente  
`[ @heartbeat_interval = ] 'heartbeat_interval'` Ist die maximale Anzahl von Minuten an, denen ein Agent ohne Protokollierung einer verlaufsmeldung aufgenommen werden kann. *Heartbeat_interval* ist **Int**, hat den Standardwert von 10 Minuten.  
  
## <a name="return-code-values"></a>Rückgabecodewerte  
 **Sp_replication_agent_checkup** löst Fehler 14151 aus, für die einzelnen Agents, die als verdächtig erkannt. Außerdem wird eine Fehlerverlaufsmeldung für die Agents protokolliert.  
  
## <a name="remarks"></a>Hinweise  
 **Sp_replication_agent_checkup** wird in Momentaufnahme-, Transaktions- und Mergereplikation verwendet.  
  
## <a name="permissions"></a>Berechtigungen  
 Nur Mitglieder der **Sysadmin** feste Serverrolle **Sp_replication_agent_checkup**.  
  
## <a name="see-also"></a>Siehe auch  
 [Gespeicherte Systemprozeduren &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
