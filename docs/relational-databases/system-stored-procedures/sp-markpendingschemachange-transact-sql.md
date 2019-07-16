---
title: Sp_markpendingschemachange (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/04/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- sp_markpendingschemachange
- sp_markpendingschemachange_TSQL
helpviewer_keywords:
- sp_markpendingschemachange
ms.assetid: 01100309-7bef-4154-85bf-f18489577e37
author: stevestein
ms.author: sstein
ms.openlocfilehash: a4d8864c28cb3569d4177103d10dd4d3da9b2e3d
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "68029983"
---
# <a name="spmarkpendingschemachange-transact-sql"></a>sp_markpendingschemachange (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Wird für die Unterstützung von Mergeveröffentlichungen verwendet, indem ein Administrator die Möglichkeit erhält, bestimmte ausstehende Schemaänderungen auszulassen, sodass sie nicht repliziert werden. Diese gespeicherte Prozedur wird auf dem Verleger für die Veröffentlichungsdatenbank ausgeführt.  
  
> [!CAUTION]  
>  Diese gespeicherte Prozedur kann zur Folge haben, dass Schemaänderungen nicht repliziert werden. Sie sollte nur zur Problembehandlung verwendet werden, nachdem andere Methoden, wie z. B. die erneute Initialisierung, bereits versucht wurden oder die Leistung zu stark einschränken.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
sp_markpendingschemachange [@publication = ] 'publication'  
    [ , [ @schemaversion = ] schemaversion ]  
    [ , [ @status = ] 'status' ]  
```  
  
## <a name="arguments"></a>Argumente  
 [ **@publication=** ] **"***Veröffentlichung***"**  
 Der Name der Veröffentlichung. *Veröffentlichung* ist **Sysname**, hat keinen Standardwert.  
  
`[ @schemaversion = ] schemaversion` Identifiziert eine ausstehende schemaänderung. *Schemaversion* ist **Int**, hat den Standardwert des **0**. Verwendung [Sp_enumeratependingschemachanges &#40;Transact-SQL&#41; ](../../relational-databases/system-stored-procedures/sp-enumeratependingschemachanges-transact-sql.md) um die ausstehenden schemaänderungen für die Veröffentlichung aufzulisten.  
  
`[ @status = ] 'status'` Ist, gibt an, ob eine ausstehende schemaänderung übersprungen wird. *Status* ist **nvarchar(10)** hat den Standardwert des **active**. Wenn der Wert des *Status* ist **übersprungen**, und klicken Sie dann die entsprechende schemaänderung nicht repliziert werden.  
  
## <a name="return-code-values"></a>Rückgabecodewerte  
 **0** (Erfolg) oder **1** (Fehler)  
  
## <a name="remarks"></a>Hinweise  
 **Sp_markpendingschemachange** wird bei der Mergereplikation verwendet.  
  
 **Sp_markpendingschemachange** ist eine gespeicherte Prozedur zur Unterstützung der Mergereplikation und sollte verwendet werden, nur, wenn andere Abhilfemaßnahmen, wie z. B. die erneute Initialisierung, nicht das Problem zu beheben oder zu in stark Begriffe der Leistung.  
  
## <a name="permissions"></a>Berechtigungen  
 Nur Mitglieder der der **Sysadmin** -Serverrolle sein oder **Db_owner** feste Datenbankrolle können ausführen **Sp_markpendingschemachange**.  
  
## <a name="see-also"></a>Siehe auch  
 [sysmergeschemachange &#40;Transact-SQL&#41;](../../relational-databases/system-tables/sysmergeschemachange-transact-sql.md)  
  
  
