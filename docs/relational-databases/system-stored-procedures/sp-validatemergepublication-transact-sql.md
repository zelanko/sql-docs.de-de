---
title: Sp_validatemergepublication (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- sp_validatemergepublication
- sp_validatemergepublication_TSQL
helpviewer_keywords:
- sp_validatemergepublication
ms.assetid: 5a862f1a-2be1-4758-9954-4cdc8c77d149
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 5706ea4c1fab79735afe9f9ec4873f112c9114cd
ms.sourcegitcommit: c44014af4d3f821e5d7923c69e8b9fb27aeb1afd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/27/2019
ms.locfileid: "58531087"
---
# <a name="spvalidatemergepublication-transact-sql"></a>sp_validatemergepublication (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Führt eine Überprüfung in der gesamten Veröffentlichung durch, bei der alle Abonnements (Push-, Pull- und anonyme Abonnements) jeweils einmal überprüft werden. Diese gespeicherte Prozedur wird auf dem Verleger für die Veröffentlichungsdatenbank ausgeführt.  
  
 ![Themenlinksymbol](../../database-engine/configure-windows/media/topic-link.gif "Topic link icon") [Transact-SQL Syntax Conventions (Transact-SQL-Syntaxkonventionen)](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```  
  
sp_validatemergepublication [@publication=] 'publication'  
        , [ @level = ] level  
```  
  
## <a name="arguments"></a>Argumente  
 [**@publication=**] **'***publication***'**  
 Der Name der Veröffentlichung. *Veröffentlichung* ist **Sysname**, hat keinen Standardwert.  
  
`[ @level = ] level` Ist der Typ der auszuführenden Überprüfung. *Ebene* ist **Tinyint**, hat keinen Standardwert. Level kann einen der folgenden Werte haben.  
  
|Level-Wert|Description|  
|-----------------|-----------------|  
|**1**|Nur Überprüfung der Zeilenanzahl.|  
|**2**|Überprüfung der Zeilenanzahl und der Prüfsumme. Für [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)]Abonnenten, dies wird automatisch festgelegt **3**.|  
|**3**|Dies ist der empfohlene Wert.|  
  
## <a name="return-code-values"></a>Rückgabecodewerte  
 **0** (Erfolg) oder **1** (Fehler)  
  
## <a name="remarks"></a>Hinweise  
 **Sp_validatemergepublication** wird bei der Mergereplikation verwendet.  
  
## <a name="permissions"></a>Berechtigungen  
 Nur Mitglieder der **Sysadmin** feste Serverrolle **Sp_validatemergepublication**.  
  
## <a name="see-also"></a>Siehe auch  
 [Gespeicherte Systemprozeduren &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)   
 [Überprüfen von replizierten Daten](../../relational-databases/replication/validate-data-at-the-subscriber.md)   
 [sp_validatemergesubscription &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-validatemergesubscription-transact-sql.md)  
  
  
