---
title: sp_getqueuedrows (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/04/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- sp_getqueuedrows_TSQL
- sp_getqueuedrows
helpviewer_keywords:
- sp_getqueuedrows
ms.assetid: 139e834f-1988-4b4d-ac81-db1f89ea90e8
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: fa6ce6b4e0d1c3fbefe7256f3ca96c84d59e664d
ms.sourcegitcommit: c44014af4d3f821e5d7923c69e8b9fb27aeb1afd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/27/2019
ms.locfileid: "58535412"
---
# <a name="spgetqueuedrows-transact-sql"></a>sp_getqueuedrows (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Ruft beim Abonnenten Zeilen ab, die über ausstehende Updates in der Warteschlange verfügen. Diese gespeicherte Prozedur wird auf dem Abonnenten für die Abonnementdatenbank ausgeführt.  
  
 ![Themenlinksymbol](../../database-engine/configure-windows/media/topic-link.gif "Topic link icon") [Transact-SQL Syntax Conventions (Transact-SQL-Syntaxkonventionen)](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```  
  
sp_getqueuedrows [ @tablename = ] 'tablename'  
    [ , [ @owner = ] 'owner'  
    [ , [ @tranid = ] 'transaction_id' ]  
```  
  
## <a name="arguments"></a>Argumente  
`[ @tablename = ] 'tablename'` Ist der Name der Tabelle. *TableName* ist **Sysname**, hat keinen Standardwert. Die Tabelle muss Teil eines Abonnements in einer Warteschlange sein.  
  
`[ @owner = ] 'owner'` Ist der Besitzer des Abonnements an. *Besitzer* ist **Sysname**, hat den Standardwert NULL.  
  
`[ @tranid = ] 'transaction_id'` Die Ausgabe nach der Transaktions-ID gefiltert werden können *Transaction_id* ist **nvarchar(70)**, hat den Standardwert NULL. Falls angegeben, wird die Transaktions-ID angezeigt, die dem Befehl in der Warteschlange zugeordnet ist. Bei einem Wert von NULL werden alle Befehle in der Warteschlange angezeigt.  
  
## <a name="return-code-values"></a>Rückgabecodewerte  
 **0** (Erfolg) oder **1** (Fehler)  
  
## <a name="result-sets"></a>Resultsets  
 Zeigt alle Zeilen an, die zurzeit über mindestens eine Transaktion in der Warteschlange für die abonnierte Tabelle verfügen.  
  
|Spaltenname|Datentyp|Description|  
|-----------------|---------------|-----------------|  
|**Aktion**|**nvarchar(10)**|Aktionstyp, der bei der Synchronisierung durchgeführt werden soll.<br /><br /> INS= Einfügen<br /><br /> DEL = Löschen<br /><br /> UPD = Aktualisieren|  
|**Tranid**|**nvarchar(70)**|Die Transaktions-ID, unter der der Befehl ausgeführt wurde.|  
|**Tabelle column1... n**||Der Wert für jede Spalte der Tabelle im angegebenen *Tablename*.|  
|**msrepl_tran_version**|**uniqueidentifier**|Diese Spalte wird zum Nachverfolgen von Änderungen an replizierten Daten und für die Konflikterkennung auf dem Verleger verwendet. Diese Spalte wird automatisch der Tabelle hinzugefügt.|  
  
## <a name="remarks"></a>Hinweise  
 **Sp_getqueuedrows** wird auf den Abonnenten Aktualisieren über eine Warteschlange verwendet.  
  
 **Sp_getqueuedrows** sucht Zeilen einer gegebenen Tabelle in einem Abonnement-Datenbank, die ein Update über eine Warteschlange beteiligt, aber derzeit nicht behoben wurden durch den Warteschlangenlese-Agent.  
  
## <a name="permissions"></a>Berechtigungen  
 **Sp_getqueuedrows** erfordert SELECT-Berechtigungen für die Tabelle im angegebenen *Tablename*.  
  
## <a name="see-also"></a>Siehe auch  
 [Updatable Subscriptions for Transactional Replication](../../relational-databases/replication/transactional/updatable-subscriptions-for-transactional-replication.md)   
 [Konflikterkennung und -lösung beim verzögerten Update über eine Warteschlange](../../relational-databases/replication/transactional/updatable-subscriptions-queued-updating-conflict-resolution.md)   
 [Gespeicherte Systemprozeduren &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
