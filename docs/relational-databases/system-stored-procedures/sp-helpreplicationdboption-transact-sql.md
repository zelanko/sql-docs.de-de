---
title: Sp_helpreplicationdboption (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/03/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- sp_helpreplicationdboption_TSQL
- sp_helpreplicationdboption
helpviewer_keywords:
- sp_helpreplicationdboption
ms.assetid: 143ce689-108b-49d7-9892-fd3a86897f38
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: a56e8cb4531fbe48e2a66242d23406d6d647573c
ms.sourcegitcommit: c44014af4d3f821e5d7923c69e8b9fb27aeb1afd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/27/2019
ms.locfileid: "58536702"
---
# <a name="sphelpreplicationdboption-transact-sql"></a>sp_helpreplicationdboption (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Zeigt an, ob die Datenbanken auf dem Verleger für die Replikation aktiviert sind. Diese gespeicherte Prozedur wird auf dem Verleger für jede Datenbank ausgeführt. *Für Oracle-Verlegern unterstützt nicht.*  
  
 ![Themenlinksymbol](../../database-engine/configure-windows/media/topic-link.gif "Topic link icon") [Transact-SQL Syntax Conventions (Transact-SQL-Syntaxkonventionen)](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```  
  
sp_helpreplicationdboption [ [ @dbname =] 'dbname' ]  
    [ , [ @type = ] 'type' ]  
    [ , [ @reserved = ] reserved ]  
```  
  
## <a name="arguments"></a>Argumente  
`[ @dbname = ] 'dbname'` Ist der Name der Datenbank. *Dbname* ist **Sysname**, hat den Standardwert **%**. Wenn **%**, klicken Sie dann das Resultset enthält alle Datenbanken auf dem Verleger, andernfalls nur Informationen für die angegebene Datenbank zurückgegeben. Es werden keine Informationen für Datenbanken zurückgegeben, für die der Benutzer wie nachstehend beschrieben keine entsprechenden Berechtigungen besitzt.  
  
`[ @type = ] 'type'` Beschränkt das Resultset enthält nur Datenbanken, für die der angegebenen Replikationsoption *Typ* Wert aktiviert wurde. *Typ* ist **Sysname**, und kann einen der folgenden Werte.  
  
|Wert|Description|  
|-----------|-----------------|  
|**publish**|Transaktionsreplikation ist zulässig.|  
|**Veröffentlichen von Merge**|Mergereplikation ist zulässig.|  
|**Replikation zulässig** (Standard)|Transaktionsreplikation und Mergereplikation sind zulässig.|  
  
`[ @reserved = ] reserved` Gibt an, ob Informationen zu vorhandenen Veröffentlichungen und Abonnements zurückgegeben werden. *reservierte* ist **Bit**, hat den Standardwert 0. Wenn **1**, enthält das Resultset Informationen dazu, ob die angegebene Datenbank über vorhandene Veröffentlichungen oder Abonnements verfügt.  
  
## <a name="result-sets"></a>Resultsets  
  
|Spaltenname|Datentyp|Description|  
|-----------------|---------------|-----------------|  
|**name**|**sysname**|Der Name der Datenbank.|  
|**id**|**int**|Datenbankbezeichner.|  
|**transpublish**|**bit**|Wenn die Datenbank für Momentaufnahme- oder transaktionsveröffentlichungen aktiviert wurde; ein Wert von **1** bedeutet, dass die Momentaufnahme- oder transaktionsveröffentlichungen aktiviert ist.|  
|**mergepublish**|**bit**|Wenn die Datenbank für die Mergereplikation, die Veröffentlichung aktiviert wurde; ein Wert von **1** bedeutet, dass mergeveröffentlichungen aktiviert ist.|  
|**dbowner**|**bit**|Wenn der Benutzer Mitglied ist die **Db_owner** festen; ein Wert von **1** gibt an, dass der Benutzer ein Mitglied dieser Rolle ist.|  
|**dbreadonly**|**bit**|Ist, wenn die Datenbank als schreibgeschützt markiert ist. ein Wert von **1** bedeutet, dass die Datenbank schreibgeschützt ist.|  
|**haspublications**|**bit**|Ist, wenn die Datenbank vorhandenen Veröffentlichungen aufweist. ein Wert von **1** bedeutet, dass Veröffentlichungen vorhanden sind.|  
|**haspullsubscriptions**|**bit**|Ist, wenn die Datenbank vorhandene Pullabonnements verfügt. ein Wert von **1** bedeutet, dass Pullabonnements vorhanden sind.|  
  
## <a name="return-code-values"></a>Rückgabecodewerte  
 **0** (Erfolg) oder **1** (Fehler)  
  
## <a name="remarks"></a>Hinweise  
 **Sp_helpreplicationdboption** wird bei Momentaufnahme-, Transaktions- und Mergereplikation verwendet.  
  
## <a name="permissions"></a>Berechtigungen  
 Mitglieder der **Sysadmin** feste Serverrolle **Sp_helpreplicationdboption** für jede beliebige Datenbank. Mitglieder der **Db_owner** feste Datenbankrolle können ausführen **Sp_helpreplicationdboption** für diese Datenbank.  
  
## <a name="see-also"></a>Siehe auch  
 [sp_replicationdboption &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-replicationdboption-transact-sql.md)   
 [Gespeicherte Systemprozeduren &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
