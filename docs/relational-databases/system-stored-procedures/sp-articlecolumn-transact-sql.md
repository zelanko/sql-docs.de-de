---
description: sp_articlecolumn (Transact-SQL)
title: sp_articlecolumn (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- sp_articlecolumn
- sp_articlecolumn_TSQL
helpviewer_keywords:
- sp_articlecolumn
ms.assetid: 8abaa8c1-d99e-4788-970f-c4752246c577
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: f296017c21cba6e13b7cbb112b1591af6af27d93
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/17/2020
ms.locfileid: "88489537"
---
# <a name="sp_articlecolumn-transact-sql"></a>sp_articlecolumn (Transact-SQL)
[!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

  Wird verwendet, um die in einem Artikel enthaltenen Spalten zum vertikalen Filtern der Daten in einer veröffentlichten Tabelle anzugeben. Diese gespeicherte Prozedur wird auf dem Verleger für die Veröffentlichungs Datenbank ausgeführt.  
  
 ![Symbol für Themenlink](../../database-engine/configure-windows/media/topic-link.gif "Symbol für Themenlink") [Transact-SQL-Syntaxkonventionen](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```  
  
sp_articlecolumn [ @publication = ] 'publication'  
        , [ @article = ] 'article'  
    [ , [ @column = ] 'column' ]  
    [ , [ @operation = ] 'operation' ]  
    [ , [ @refresh_synctran_procs = ] refresh_synctran_procs ]  
    [ , [ @ignore_distributor = ] ignore_distributor ]  
    [ , [ @change_active = ] change_actve ]  
    [ , [ @force_invalidate_snapshot = ] force_invalidate_snapshot ]  
    [ , [ @force_reinit_subscription = ] force_reinit_subscription ]  
    [ , [ @publisher = ] 'publisher' ]  
    [ , [ @internal = ] 'internal' ]  
```  
  
## <a name="arguments"></a>Argumente  
`[ @publication = ] 'publication'` Der Name der Veröffentlichung, die diesen Artikel enthält. *Publication* ist vom **Datentyp vom Datentyp sysname**und hat keinen Standardwert.  
  
`[ @article = ] 'article'` Der Name des Artikels. der *Artikel* ist vom **Datentyp vom Datentyp sysname**und hat keinen Standardwert.  
  
`[ @column = ] 'column'` Der Name der Spalte, die hinzugefügt oder gelöscht werden soll. *Column* ist vom **Datentyp vom Datentyp sysname**und hat den Standardwert NULL. Bei NULL werden alle Spalten veröffentlicht.  
  
`[ @operation = ] 'operation'` Gibt an, ob Spalten in einem Artikel hinzugefügt oder gelöscht werden sollen. der *Vorgang* ist vom Datentyp **nvarchar (5)**. der Standardwert ist hinzufügen. **Hinzufügen** markiert die Spalte für die Replikation. **Drop** hebt die Markierung der Spalte auf.  
  
`[ @refresh_synctran_procs = ] refresh_synctran_procs` Gibt an, ob die gespeicherten Prozeduren, die Abonnements mit sofortigem Update unterstützen, neu generiert werden *refresh_synctran_procs* ist vom Typ **Bit**und hat den Standardwert **1**. Bei **1**werden die gespeicherten Prozeduren neu generiert.  
  
`[ @ignore_distributor = ] ignore_distributor` Gibt an, ob diese gespeicherte Prozedur ausgeführt wird, ohne eine Verbindung mit dem Verteiler herzustellen. *ignore_distributor* ist vom Typ **Bit**. der Standardwert ist **0**. Wenn der Wert **0**ist, muss die Datenbank für die Veröffentlichung aktiviert werden, und der Artikel Cache sollte aktualisiert werden, um die neuen, vom Artikel replizierten Spalten widerzuspiegeln. Wenn der Wert **1**ist, können Artikel Spalten für Artikel, die sich in einer nicht veröffentlichten Datenbank befinden, gelöscht werden. sollte nur in Wiederherstellungs Situationen verwendet werden.  
  
`[ @change_active = ] change_active` Ermöglicht das Ändern von Spalten in Veröffentlichungen, die über Abonnements verfügen. *change_active* ist vom Datentyp **int** und hat den Standardwert **0**. Wenn der Wert **0**ist, werden die Spalten nicht geändert. Wenn der Wert **1**ist, können Spalten in aktiven Artikeln mit Abonnements hinzugefügt oder gelöscht werden.  
  
`[ @force_invalidate_snapshot = ] force_invalidate_snapshot` Bestätigt, dass die von dieser gespeicherten Prozedur ausgeführte Aktion eine vorhandene Momentaufnahme für ungültig erklären kann. *force_invalidate_snapshot* ist ein **Bit**, der Standardwert ist **0**.  
  
 der Wert **0** gibt an, dass Änderungen am Artikel nicht bewirken, dass die Momentaufnahme ungültig wird. Wenn die gespeicherte Prozedur erkennt, dass die Änderungen eine neue Momentaufnahme erfordern, tritt ein Fehler auf und es werden keine Änderungen vorgenommen.  
  
 der Wert **1** gibt an, dass Änderungen am Artikel bewirken können, dass die Momentaufnahme ungültig wird. wenn Abonnements vorhanden sind, die eine neue Momentaufnahme erfordern, wird die Berechtigung erteilt, die vorhandene Momentaufnahme als veraltet zu markieren und eine neue Momentaufnahme zu generieren.  
  
 [** @force_reinit_subscription =** ] *force_reinit_subscription*  
 Bestätigt, dass die von dieser gespeicherten Prozedur ausgeführte Aktion möglicherweise erfordert, dass vorhandene Abonnements erneut initialisiert werden. *force_reinit_subscription* ist ein **Bit**, der Standardwert ist **0**.  
  
 der Wert **0** gibt an, dass Änderungen am Artikel nicht bewirken, dass das Abonnement erneut initialisiert wird. Wenn die gespeicherte Prozedur erkennt, dass die Änderung die erneute Initialisierung der Abonnements erfordert, tritt ein Fehler auf, und es werden keine Änderungen vorgenommen. der Wert **1** gibt an, dass Änderungen am Artikel bewirken, dass vorhandene Abonnements erneut initialisiert werden, und erteilt die Berechtigung für die erneute Initialisierung des Abonnements.  
  
`[ @publisher = ] 'publisher'` Gibt einen nicht-- [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Verleger an. *Publisher* ist vom **Datentyp vom Datentyp sysname**und hat den Standardwert NULL.  
  
> [!NOTE]  
>  *Publisher* sollte nicht mit einem Verleger verwendet werden [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
`[ @internal = ] 'internal'` Nur interne Verwendung.  
  
## <a name="return-code-values"></a>Rückgabecodewerte  
 **0** (Erfolg) oder **1** (Fehler)  
  
## <a name="remarks"></a>Bemerkungen  
 **sp_articlecolumn** wird bei der Momentaufnahme-und Transaktions Replikation verwendet.  
  
 Nur ein nicht abonnierter Artikel kann mit **sp_articlecolumn**gefiltert werden.  
  
## <a name="example"></a>Beispiel  
 [!code-sql[HowTo#sp_AddTranArticle](../../relational-databases/replication/codesnippet/tsql/sp-articlecolumn-transac_1.sql)]  
  
## <a name="permissions"></a>Berechtigungen  
 Nur Mitglieder der festen Server Rolle **sysadmin** oder der festen Daten Bank Rolle **db_owner** können **sp_articlecolumn**ausführen.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Define an Article](../../relational-databases/replication/publish/define-an-article.md)   
 [Definieren und Ändern eines Spalten Filters](../../relational-databases/replication/publish/define-and-modify-a-column-filter.md)   
 [Filtern von veröffentlichten Daten](../../relational-databases/replication/publish/filter-published-data.md)   
 [sp_addarticle &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/sp-addarticle-transact-sql.md)   
 [sp_articleview &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/sp-articleview-transact-sql.md)   
 [sp_changearticle &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/sp-changearticle-transact-sql.md)   
 [sp_droparticle &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/sp-droparticle-transact-sql.md)   
 [sp_helparticle &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-helparticle-transact-sql.md)   
 [sp_helparticlecolumns &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/sp-helparticlecolumns-transact-sql.md)   
 [Gespeicherte Automatisierungsprozeduren &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/replication-stored-procedures-transact-sql.md)  
  
  
