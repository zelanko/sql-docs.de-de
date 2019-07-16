---
title: Sp_setreplfailovermode (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- sp_setreplfailovermode
- sp_setreplfailovermode_TSQL
helpviewer_keywords:
- sp_setreplfailovermode
ms.assetid: ca98a4c3-bea4-4130-88d7-79e0fd1e85f6
author: stevestein
ms.author: sstein
ms.openlocfilehash: a32c5eb0a7dcd18558b3d1a931d9a8c83cfeca0c
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "68104368"
---
# <a name="spsetreplfailovermode-transact-sql"></a>sp_setreplfailovermode (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Ermöglicht das Festlegen des Failoveroperationsmodus für Abonnements, die für sofortige Updates mit Updates über eine Warteschlange als Failover aktiviert sind. Diese gespeicherte Prozedur wird auf dem Abonnenten für die Abonnementdatenbank ausgeführt. Weitere Informationen zu failovermodi finden Sie unter [aktualisierbaren Abonnements für Transaktionsreplikationen](../../relational-databases/replication/transactional/updatable-subscriptions-for-transactional-replication.md).  
  
 ![Themenlinksymbol](../../database-engine/configure-windows/media/topic-link.gif "Topic link icon") [Transact-SQL Syntax Conventions (Transact-SQL-Syntaxkonventionen)](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```  
  
sp_setreplfailovermode [ @publisher= ] 'publisher'  
    [ , [ @publisher_db = ] 'publisher_db' ]  
    [ , [ @publication= ] 'publication' ]  
    [ , [ @failover_mode= ] 'failover_mode' ]  
    [ , [ @override = ] override ]  
```  
  
## <a name="arguments"></a>Argumente  
`[ @publisher = ] 'publisher'` Ist der Name der Veröffentlichung. *Veröffentlichung* ist **Sysname**, hat keinen Standardwert. Die Veröffentlichung muss bereits vorhanden sein.  
  
`[ @publisher_db = ] 'publisher_db'` Ist der Name der Veröffentlichungsdatenbank. *Publisher_db* ist **Sysname**, hat keinen Standardwert.  
  
`[ @publication = ] 'publication'` Ist der Name der Veröffentlichung. *Veröffentlichung*ist **Sysname**, hat keinen Standardwert.  
  
 [ **@failover_mode=** ] **"***Failover_mode***"**  
 Der Failovermodus für das Abonnement. *Failover_mode* ist **nvarchar(10)** und kann einen der folgenden Werte sein.  
  
|Wert|Beschreibung|  
|-----------|-----------------|  
|**sofortige** oder **synchronisieren**|Datenänderungen, die auf dem Abonnenten durchgeführt werden, werden bei ihrem Auftreten mithilfe eines Massenkopiervorgangs auf den Verleger übertragen.|  
|**In der Warteschlange**|Datenänderungen werden gespeichert, einem [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Warteschlange.|  
  
> [!NOTE]  
>  [!INCLUDE[msCoName](../../includes/msconame-md.md)] Message Queuing wurde als veraltet markiert und wird nicht mehr unterstützt.  
  
`[ @override = ] override` Nur interne Verwendung.  
  
## <a name="return-code-values"></a>Rückgabecodewerte  
 **0** (Erfolg) oder **1** (Fehler)  
  
## <a name="remarks"></a>Hinweise  
 **Sp_setreplfailovermode** wird verwendet, bei Momentaufnahme- oder Transaktionsreplikation für die Abonnements aktiviert sind, entweder für Updates mit Failover zum sofortigen Aktualisieren, in der Warteschlange oder für sofortige Updates mit Failover in die Warteschlange eingereiht wird aktualisiert.  
  
## <a name="permissions"></a>Berechtigungen  
 Nur Mitglieder der der **Sysadmin** -Serverrolle sein oder **Db_owner** feste Datenbankrolle können ausführen **Sp_setreplfailovermode**.  
  
## <a name="see-also"></a>Siehe auch  
 [Umschalten zwischen Updatemodi für ein aktualisierbares Transaktionsabonnement](../../relational-databases/replication/administration/switch-between-update-modes-for-an-updatable-transactional-subscription.md)   
 [Gespeicherte Systemprozeduren &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
