---
title: sp_articleview (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- sp_articleview
- sp_articleview_TSQL
helpviewer_keywords:
- sp_articleview
ms.assetid: a3d63fd6-f360-4a2f-8a82-a0dc15f650b3
author: stevestein
ms.author: sstein
ms.openlocfilehash: 7cc40187ccafebee672214a0926a3ca0d0bc4176
ms.sourcegitcommit: 728a4fa5a3022c237b68b31724fce441c4e4d0ab
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/03/2019
ms.locfileid: "68768993"
---
# <a name="sparticleview-transact-sql"></a>sp_articleview (Transact-SQL)
[!INCLUDE[appliesto-ss-asdbmi-xxxx-xxx-md](../../includes/appliesto-ss-asdbmi-xxxx-xxx-md.md)]

  Erstellt die Sicht für die Definition des veröffentlichten Artikels, wenn eine Tabelle vertikal oder horizontal gefiltert wird. Diese Sicht wird als gefilterte Quelle des Schemas und der Daten für die Zieltabellen verwendet. Mit dieser gespeicherten Prozedur können nur nicht abonnierte Artikel geändert werden. Diese gespeicherte Prozedur wird auf dem Verleger für die Veröffentlichungs Datenbank ausgeführt.  
  
 ![Themenlinksymbol](../../database-engine/configure-windows/media/topic-link.gif "Topic link icon") [Transact-SQL Syntax Conventions (Transact-SQL-Syntaxkonventionen)](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```  
  
sp_articleview [ @publication = ] 'publication'  
        , [ @article = ] 'article'  
    [ , [ @view_name = ] 'view_name']  
    [ , [ @filter_clause = ] 'filter_clause']  
    [ , [ @change_active = ] change_active ]  
    [ , [ @force_invalidate_snapshot = ] force_invalidate_snapshot ]  
    [ , [ @force_reinit_subscription = ] force_reinit_subscription ]  
    [ , [ @publisher = ] 'publisher' ]  
    [ , [ @refreshsynctranprocs = ] refreshsynctranprocs ]  
    [ , [ @internal = ] internal ]  
```  
  
## <a name="arguments"></a>Argumente  
`[ @publication = ] 'publication'`Der Name der Veröffentlichung, die den Artikel enthält. *Publication* ist vom **Datentyp vom Datentyp sysname**und hat keinen Standardwert.  
  
`[ @article = ] 'article'`Der Name des Artikels. der *Artikel* ist vom **Datentyp vom Datentyp sysname**und hat keinen Standardwert.  
  
`[ @view_name = ] 'view_name'`Der Name der Sicht, die den veröffentlichten Artikel definiert. *view_name* ist vom Datentyp **nvarchar (386)** und hat den Standardwert NULL.  
  
`[ @filter_clause = ] 'filter_clause'`Eine Einschränkungs Klausel (WHERE), die einen horizontalen Filter definiert. Wenn Sie die Einschränkungsklausel eingeben, lassen Sie das Schlüsselwort WHERE weg. *filter_clause* ist vom Typ **ntext**und hat den Standardwert NULL.  
  
`[ @change_active = ] change_active`Ermöglicht das Ändern von Spalten in Veröffentlichungen, die über Abonnements verfügen. *change_active* ist vom Datentyp **int**und hat den Standardwert **0**. Wenn der Wert **0**ist, werden die Spalten nicht geändert. Wenn der Wert **1**ist, können Sichten für aktive Artikel mit Abonnements erstellt oder neu erstellt werden.  
  
`[ @force_invalidate_snapshot = ] force_invalidate_snapshot`Bestätigt, dass die von dieser gespeicherten Prozedur ausgeführte Aktion eine vorhandene Momentaufnahme für ungültig erklären kann. *force_invalidate_snapshot* ist vom Typ **Bit**und hat den Standardwert **0**.  
  
 der Wert **0** gibt an, dass Änderungen am Artikel nicht bewirken, dass die Momentaufnahme ungültig wird. Wenn die gespeicherte Prozedur erkennt, dass die Änderungen eine neue Momentaufnahme erfordern, tritt ein Fehler auf und es werden keine Änderungen vorgenommen.  
  
 der Wert **1** gibt an, dass Änderungen am Artikel bewirken können, dass die Momentaufnahme ungültig wird. wenn Abonnements vorhanden sind, die eine neue Momentaufnahme erfordern, wird die Berechtigung erteilt, die vorhandene Momentaufnahme als veraltet zu markieren und eine neue Momentaufnahme zu generieren.  
  
`[ @force_reinit_subscription = ] _force_reinit_subscription_`Bestätigt, dass die von dieser gespeicherten Prozedur ausgeführte Aktion möglicherweise erfordert, dass vorhandene Abonnements erneut initialisiert werden. *force_reinit_subscription* ist ein **Bit** mit einem Standardwert von **0**.  
  
 der Wert **0** gibt an, dass Änderungen am Artikel nicht bewirken, dass das Abonnement erneut initialisiert wird. Wenn die gespeicherte Prozedur erkennt, dass die Änderung die erneute Initialisierung der Abonnements erfordert, tritt ein Fehler auf, und es werden keine Änderungen vorgenommen.  
  
 der Wert **1** gibt an, dass das vorhandene Abonnement durch Änderungen am Artikel erneut initialisiert wird, und erteilt die Berechtigung für die erneute Initialisierung des Abonnements.  
  
`[ @publisher = ] 'publisher'`Gibt einen nicht- [!INCLUDE[msCoName](../../includes/msconame-md.md)] - [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Verleger an. *Publisher* ist vom **Datentyp vom Datentyp sysname**und hat den Standardwert NULL.  
  
> [!NOTE]  
>  der *Verleger* sollte beim Veröffentlichen von einem [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Verleger nicht verwendet werden.  
  
`[ @refreshsynctranprocs = ] refreshsynctranprocs`Gibt an, ob die zum Synchronisieren der Replikation verwendeten gespeicherten Prozeduren automatisch neu erstellt werden. der Wert für " *erfrischendes synctranprocs* " ist " **Bit**". der Standardwert ist 1.  
  
 **1** bedeutet, dass die gespeicherten Prozeduren neu erstellt werden.  
  
 **0** bedeutet, dass die gespeicherten Prozeduren nicht neu erstellt werden.  
  
`[ @internal = ] internal` [!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]  
  
## <a name="return-code-values"></a>Rückgabecodewerte  
 **0** (Erfolg) oder **1** (Fehler)  
  
## <a name="remarks"></a>Hinweise  
 **sp_articleview** erstellt die Sicht, die den veröffentlichten Artikel definiert, fügt die ID dieser Sicht in die **sync_objid** -Spalte der [sysarticles &#40;-Transact-&#41; SQL](../../relational-databases/system-tables/sysarticles-transact-sql.md) -Tabelle ein und fügt den Text der Einschränkungs Klausel ein. die **filter_clause** -Spalte. Wenn alle Spalten repliziert werden und kein **filter_clause**vorhanden ist, wird der **sync_objid** -Wert in der [ &#40;sysarticles&#41; -Tabelle Transact-SQL](../../relational-databases/system-tables/sysarticles-transact-sql.md) auf die ID der Basistabelle festgelegt, und die Verwendung von **sp_articleview** ist nicht erforderlich.  
  
 Zum Veröffentlichen einer vertikal gefilterten Tabelle (d. h. zum Filtern von Spalten) führen Sie zuerst **sp_addarticle** ohne *sync_object* -Parameter aus, führen Sie [sp_articlecolumn &#40;Transact-SQL&#41; ](../../relational-databases/system-stored-procedures/sp-articlecolumn-transact-sql.md) für jede zu replizierende Spalte aus (definieren der vertikaler Filter), und führen Sie dann **sp_articleview** aus, um die Ansicht zu erstellen, die den veröffentlichten Artikel definiert.  
  
 Zum Veröffentlichen einer horizontal gefilterten Tabelle (d. h. zum Filtern von Zeilen) führen Sie [sp_addarticle &#40;Transact&#41; -SQL](../../relational-databases/system-stored-procedures/sp-addarticle-transact-sql.md) ohne *Filter* Parameter aus. Führen [Sie &#40;sp_articlefilter Transact-&#41;SQL](../../relational-databases/system-stored-procedures/sp-articlefilter-transact-sql.md)aus, und geben Sie alle Parameter einschließlich *filter_clause*an. Führen Sie dann **sp_articleview**aus, und geben Sie alle Parameter an, einschließlich der identischen *filter_clause*.  
  
 Zum Veröffentlichen einer vertikalen und horizontal gefilterten Tabelle führen [Sie &#40;sp_addarticle Transact-&#41; SQL](../../relational-databases/system-stored-procedures/sp-addarticle-transact-sql.md) ohne *sync_object* oder *Filter* Parameter aus. Führen [Sie &#40;sp_articlecolumn Transact-&#41; SQL](../../relational-databases/system-stored-procedures/sp-articlecolumn-transact-sql.md) für jede zu replizierende Spalte einmal aus, und führen Sie dann [sp_articlefilter &#40;Transact-SQL&#41; ](../../relational-databases/system-stored-procedures/sp-articlefilter-transact-sql.md) und **sp_articleview**aus.  
  
 Wenn der Artikel bereits eine Ansicht enthält, in der der veröffentlichte Artikel definiert ist, löscht **sp_articleview** die vorhandene Sicht und erstellt automatisch eine neue Sicht. Wenn die Ansicht manuell erstellt wurde (**Type** in [sysarticles &#40;Transact-SQL&#41; ](../../relational-databases/system-tables/sysarticles-transact-sql.md) ist **5**), wird die vorhandene Sicht nicht gelöscht.  
  
 Wenn Sie eine benutzerdefinierte gespeicherte Filter Prozedur und eine Ansicht erstellen, die den veröffentlichten Artikel manuell definiert, führen Sie **sp_articleview**nicht aus. Geben Sie diese stattdessen als *Filter* -und *sync_object* -Parameter [für &#40;sp_addarticle Transact-&#41;SQL](../../relational-databases/system-stored-procedures/sp-addarticle-transact-sql.md)an, zusammen mit dem entsprechenden *Typwert* .  
  
## <a name="example"></a>Beispiel  
 [!code-sql[HowTo#sp_AddTranArticle](../../relational-databases/replication/codesnippet/tsql/sp-articleview-transact-_1.sql)]  
  
## <a name="permissions"></a>Berechtigungen  
 Nur Mitglieder der festen Server Rolle **sysadmin** oder der festen Daten Bank Rolle **db_owner** können **sp_articleview**ausführen.  
  
## <a name="see-also"></a>Siehe auch  
 [Define an Article](../../relational-databases/replication/publish/define-an-article.md)   
 [Definieren und Ändern eines statischen Zeilenfilters](../../relational-databases/replication/publish/define-and-modify-a-static-row-filter.md)   
 [sp_addarticle &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-addarticle-transact-sql.md)   
 [sp_articlefilter &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-articlefilter-transact-sql.md)   
 [sp_changearticle &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-changearticle-transact-sql.md)   
 [sp_droparticle &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-droparticle-transact-sql.md)   
 [sp_helparticle &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-helparticle-transact-sql.md)   
 [Gespeicherte Automatisierungsprozeduren &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/replication-stored-procedures-transact-sql.md)  
  
  
