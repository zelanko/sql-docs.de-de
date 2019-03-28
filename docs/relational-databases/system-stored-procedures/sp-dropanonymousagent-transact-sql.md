---
title: Sp_dropanonymousagent (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/04/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- sp_dropanonymousagent
- sp_dropanonymousagent_TSQL
helpviewer_keywords:
- sp_dropanonymousagent
ms.assetid: 4cb96efa-9358-44a3-a8ee-a7e181bed089
ms.author: vanto
manager: craigg
ms.openlocfilehash: 82519f069aaa59020e2dccb760df5d2a24c9178b
ms.sourcegitcommit: c44014af4d3f821e5d7923c69e8b9fb27aeb1afd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/27/2019
ms.locfileid: "58537882"
---
# <a name="spdropanonymousagent-transact-sql"></a>sp_dropanonymousagent (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Löscht einen anonymen Agent für die Replikationsüberwachung auf dem Verteiler vom Verleger. Diese gespeicherte Prozedur wird auf dem Verleger für jede Datenbank ausgeführt.  
  
 ![Themenlinksymbol](../../database-engine/configure-windows/media/topic-link.gif "Topic link icon") [Transact-SQL Syntax Conventions (Transact-SQL-Syntaxkonventionen)](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```  
  
sp_dropanonymousagent [ @subid= ] sub_id    , [ @type= ] type  
```  
  
## <a name="arguments"></a>Argumente  
`[ @subid = ] sub_id` Ist der globale Bezeichner für ein anonymes Abonnement. *Sub_id* ist **Uniqueidentifier**, hat keinen Standardwert. Dieser Bezeichner kann abgerufen werden, auf dem Abonnenten mit **Sp_helppullsubscription**. Der Wert in der **Subid** Feld des zurückgegebenen Resultsets stellt diesen globalen Bezeichner.  
  
`[ @type = ] type` Ist der Typ des Abonnements. *Typ* ist **Int**, hat keinen Standardwert. Gültige Werte sind **1** oder **2**. Geben Sie **1**, wenn die momentaufnahmereplikation oder Transaktionsreplikation mit der Verteilungs-Agent eine Momentaufnahme. Geben Sie **2**, wenn der Merge-Agent mithilfe der Mergereplikation.  
  
## <a name="return-code-values"></a>Rückgabecodewerte  
 **0** (Erfolg) oder **1** (Fehler)  
  
## <a name="remarks"></a>Hinweise  
 **Sp_dropanonymousagent** wird in allen Replikationstypen verwendet.  
  
 Diese gespeicherte Prozedur wird nur verwendet, um anonyme Abonnement-Agents zu löschen, und kann nicht verwendet werden, um bekannte Abonnements zu löschen.  
  
## <a name="permissions"></a>Berechtigungen  
 Nur Mitglieder der **Db_owner** -Datenbankrolle in der Verteilungsdatenbank kann ausführen **Sp_dropanonymousagent**.  
  
## <a name="see-also"></a>Siehe auch  
 [Gespeicherte Automatisierungsprozeduren &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/replication-stored-procedures-transact-sql.md)  
  
  
