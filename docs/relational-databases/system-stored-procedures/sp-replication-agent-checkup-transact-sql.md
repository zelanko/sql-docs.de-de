---
title: Sp_replication_agent_checkup (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/04/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology:
- replication
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
ms.openlocfilehash: e47b20344f9fc636445d0c322c0736b7aea1d7b4
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/01/2018
ms.locfileid: "47603589"
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
 [ **@heartbeat_interval** =] **"***Heartbeat_interval***"**  
 Die maximale Anzahl von Minuten, für die ein Agent ausgeführt werden kann, ohne dass eine Statusmeldung protokolliert wird. *Heartbeat_interval* ist **Int**, hat den Standardwert von 10 Minuten.  
  
## <a name="return-code-values"></a>Rückgabecodewerte  
 **Sp_replication_agent_checkup** löst Fehler 14151 aus, für die einzelnen Agents, die als verdächtig erkannt. Außerdem wird eine Fehlerverlaufsmeldung für die Agents protokolliert.  
  
## <a name="remarks"></a>Hinweise  
 **Sp_replication_agent_checkup** wird in Momentaufnahme-, Transaktions- und Mergereplikation verwendet.  
  
## <a name="permissions"></a>Berechtigungen  
 Nur Mitglieder der **Sysadmin** feste Serverrolle **Sp_replication_agent_checkup**.  
  
## <a name="see-also"></a>Siehe auch  
 [Gespeicherte Systemprozeduren &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
