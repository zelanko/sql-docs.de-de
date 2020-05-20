---
title: sp_droppublication (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/17/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- sp_droppublication_TSQL
- sp_droppublication
helpviewer_keywords:
- sp_droppublication
ms.assetid: b52b37e6-4fec-40cf-abba-7dce4ff395fd
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 3ef56f46696a2cb145804105d4d5f22fded6fe1f
ms.sourcegitcommit: 4d3896882c5930248a6e441937c50e8e027d29fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/05/2020
ms.locfileid: "82830007"
---
# <a name="sp_droppublication-transact-sql"></a>sp_droppublication (Transact-SQL)
[!INCLUDE[appliesto-ss-asdbmi-xxxx-xxx-md](../../includes/appliesto-ss-asdbmi-xxxx-xxx-md.md)]

  Löscht eine Veröffentlichung und den ihr zugeordneten Momentaufnahme-Agent. Vor dem Löschen einer Veröffentlichung müssen alle Abonnements gelöscht werden. Die Artikel in der Veröffentlichung werden automatisch gelöscht. Diese gespeicherte Prozedur wird auf dem Verleger für die Veröffentlichungs Datenbank ausgeführt.  
  
 ![Symbol für Themenlink](../../database-engine/configure-windows/media/topic-link.gif "Symbol für Themenlink") [Transact-SQL-Syntaxkonventionen](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```  
  
sp_droppublication [ @publication= ] 'publication'   
    [ , [ @ignore_distributor = ] ignore_distributor ]  
```  
  
## <a name="arguments"></a>Argumente  
`[ @publication = ] 'publication'`Der Name der Veröffentlichung, die gelöscht werden soll. *Publication* ist vom **Datentyp vom Datentyp sysname**und hat keinen Standardwert. Wenn **all** angegeben wird, werden alle Veröffentlichungen aus der Veröffentlichungs Datenbank gelöscht, mit Ausnahme derjenigen, die Abonnements sind.  
  
`[ @ignore_distributor = ] ignore_distributor` [!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]  
  
## <a name="return-code-values"></a>Rückgabecodewerte  
 **0** (Erfolg) oder **1** (Fehler)  
  
## <a name="remarks"></a>Bemerkungen  
 **sp_droppublication** wird bei der Momentaufnahme-und Transaktions Replikation verwendet.  
  
 **sp_droppublication** löscht alle Artikel, die einer Veröffentlichung zugeordnet sind, rekursiv und löscht dann die Veröffentlichung selbst. Solange für eine Veröffentlichung ein Abonnement vorhanden ist, kann sie nicht gelöscht werden. Weitere Informationen zum Entfernen von Abonnements finden Sie unter [Löschen eines Pushabonnements](../../relational-databases/replication/delete-a-push-subscription.md) und [Löschen eines](../../relational-databases/replication/delete-a-pull-subscription.md)Pullabonnements.  
  
 Durch das Ausführen **sp_droppublication** zum Löschen einer Veröffentlichung werden veröffentlichte Objekte nicht aus der Veröffentlichungs Datenbank oder den entsprechenden Objekten aus der Abonnement Datenbank entfernt. Verwenden \< Sie Drop Object>, um diese Objekte bei Bedarf manuell zu entfernen.  
  
## <a name="permissions"></a>Berechtigungen  
 Nur Mitglieder der festen Server Rolle **sysadmin** können **sp_droppublication**ausführen.  
  
## <a name="examples"></a>Beispiele  
 [!code-sql[HowTo#sp_droppublication](../../relational-databases/replication/codesnippet/tsql/sp-droppublication-trans_1.sql)]  
  
## <a name="see-also"></a>Weitere Informationen  
 [Löschen einer Veröffentlichung](../../relational-databases/replication/publish/delete-a-publication.md)   
 [sp_addpublication &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/sp-addpublication-transact-sql.md)   
 [sp_changepublication &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/sp-changepublication-transact-sql.md)   
 [sp_helppublication &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/sp-helppublication-transact-sql.md)   
 [Gespeicherte Automatisierungsprozeduren &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/replication-stored-procedures-transact-sql.md)  
  
  
