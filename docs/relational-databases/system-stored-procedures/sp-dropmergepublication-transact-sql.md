---
title: Sp_dropmergepublication (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/03/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- sp_dropmergepublication
- sp_dropmergepublication_TSQL
helpviewer_keywords:
- sp_dropmergepublication
ms.assetid: 9e1cb96e-5889-4f97-88cd-f60cf313ce68
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 74aa782a7dcf6abdc71ca82dc104406948f21989
ms.sourcegitcommit: ceb7e1b9e29e02bb0c6ca400a36e0fa9cf010fca
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/03/2018
ms.locfileid: "52802302"
---
# <a name="spdropmergepublication-transact-sql"></a>sp_dropmergepublication (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Löscht eine Mergeveröffentlichung und den zugehörigen Momentaufnahme-Agent. Vor dem Löschen einer Mergeveröffentlichung müssen alle Abonnements gelöscht werden. Die Artikel in der Veröffentlichung werden automatisch gelöscht. Diese gespeicherte Prozedur wird auf dem Verleger für die Veröffentlichungsdatenbank ausgeführt.  
  
 ![Themenlinksymbol](../../database-engine/configure-windows/media/topic-link.gif "Topic link icon") [Transact-SQL Syntax Conventions (Transact-SQL-Syntaxkonventionen)](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```  
  
sp_dropmergepublication [ @publication= ] 'publication'   
    [ , [ @ignore_distributor = ] ignore_distributor ]   
    [ , [ @reserved = ] reserved ]  
    [ , [ @ignore_merge_metadata = ] ignore_merge_metadata ]  
```  
  
## <a name="arguments"></a>Argumente  
 [ **@publication=**] **'***publication***'**  
 Der Name der Veröffentlichung, die gelöscht werden soll. *Veröffentlichung* ist **Sysname**, hat keinen Standardwert. Wenn **alle**, alle vorhandenen mergeveröffentlichungen werden entfernt, und der Momentaufnahme-Agent-Auftrag zugeordnet werden. Wenn Sie einen bestimmten Wert für angeben *Veröffentlichung*, nur diese Veröffentlichung und die zugeordneten Momentaufnahme-Agent-Auftrag gelöscht werden.  
  
 [  **@ignore_distributor =**] *Ignore_distributor*  
 Wird verwendet, um eine Veröffentlichung zu löschen, ohne beim Verteiler Cleanuptasks auszuführen. *Ignore_distributor* ist **Bit**, hat den Standardwert **0**. Dieser Parameter wird auch bei der Neuinstallation des Verteilers verwendet.  
  
 [  **@reserved=**] *reserviert*  
 Ist für die zukünftige Verwendung reserviert. *reservierte* ist **Bit**, hat den Standardwert **0**.  
  
 [  **@ignore_merge_metadata=** ] *Ignore_merge_metadata*  
 Nur interne Verwendung.  
  
## <a name="return-code-values"></a>Rückgabecodewerte  
 **0** (Erfolg) oder **1** (Fehler)  
  
## <a name="remarks"></a>Hinweise  
 **Sp_dropmergepublication** wird bei der Mergereplikation verwendet.  
  
 **Sp_dropmergepublication** rekursiv löscht alle Artikel, die einer Veröffentlichung zugeordnet sind, und anschließend wird die Veröffentlichung selbst gelöscht. Solange für eine Veröffentlichung ein Abonnement vorhanden ist, kann sie nicht gelöscht werden. Weitere Informationen zum Entfernen von Abonnements finden Sie unter [Delete a Push Subscription](../../relational-databases/replication/delete-a-push-subscription.md) und [Delete a Pull Subscription](../../relational-databases/replication/delete-a-pull-subscription.md).  
  
 Ausführen von **Sp_dropmergepublication** zum Löschen einer Veröffentlichung entfernt nicht veröffentlichten Objekte aus der Veröffentlichungsdatenbank oder der entsprechenden Objekte aus der Abonnementdatenbank. Verwenden Sie DROP \<Objekt > um diese Objekte manuell ggf. entfernen.  
  
## <a name="example"></a>Beispiel  
 [!code-sql[HowTo#sp_dropmergepublication](../../relational-databases/replication/codesnippet/tsql/sp-dropmergepublication-_1.sql)]  
  
## <a name="permissions"></a>Berechtigungen  
 Nur Mitglieder der der **Sysadmin** -Serverrolle sein oder die **Db_owner** feste Datenbankrolle können ausführen **Sp_dropmergepublication**.  
  
## <a name="see-also"></a>Siehe auch  
 [Löschen einer Veröffentlichung](../../relational-databases/replication/publish/delete-a-publication.md)   
 [Sp_addmergepublication &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-addmergepublication-transact-sql.md)   
 [sp_changemergepublication &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-changemergepublication-transact-sql.md)   
 [sp_helpmergepublication &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-helpmergepublication-transact-sql.md)   
 [Gespeicherte Automatisierungsprozeduren &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/replication-stored-procedures-transact-sql.md)  
  
  
