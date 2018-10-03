---
title: Sp_articlecolumn (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology:
- replication
ms.topic: language-reference
f1_keywords:
- sp_articlecolumn
- sp_articlecolumn_TSQL
helpviewer_keywords:
- sp_articlecolumn
ms.assetid: 8abaa8c1-d99e-4788-970f-c4752246c577
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 72d9238e5b0f8ad5480e05ded3a0154eb5510904
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/01/2018
ms.locfileid: "47640718"
---
# <a name="sparticlecolumn-transact-sql"></a>sp_articlecolumn (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Wird verwendet, um die in einem Artikel enthaltenen Spalten zum vertikalen Filtern der Daten in einer veröffentlichten Tabelle anzugeben. Diese gespeicherte Prozedur wird auf dem Verleger für die Veröffentlichungsdatenbank ausgeführt.  
  
 ![Themenlinksymbol](../../database-engine/configure-windows/media/topic-link.gif "Topic link icon") [Transact-SQL Syntax Conventions (Transact-SQL-Syntaxkonventionen)](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
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
 [ **@publication=**] **'***publication***'**  
 Der Name der Veröffentlichung, die diesen Artikel enthält. *Veröffentlichung* ist **Sysname**, hat keinen Standardwert.  
  
 [  **@article=**] **"***Artikel***"**  
 Der Name des Artikels. *Artikel* ist **Sysname**, hat keinen Standardwert.  
  
 [  **@column=**] **"***Spalte***"**  
 Der Name der Spalte, die hinzugefügt oder gelöscht werden soll. *Spalte* ist **Sysname**, hat den Standardwert NULL. Bei NULL werden alle Spalten veröffentlicht.  
  
 [  **@operation=**] **"***Vorgang***"**  
 Gibt an, ob Spalten in einem Artikel hinzugefügt oder gelöscht werden sollen. *Vorgang* ist **nvarchar(5)**, hat den Standardwert Add. **Hinzufügen** markiert die Spalte für die Replikation. **Drop** hebt die Markierung der Spalte.  
  
 [  **@refresh_synctran_procs=**] *Refresh_synctran_procs*  
 Gibt an, ob die gespeicherten Prozeduren, die Abonnements mit sofortigem Update unterstützen, entsprechend der Anzahl replizierter Spalten erneut generiert werden. *Refresh_synctran_procs* ist **Bit**, hat den Standardwert **1**. Wenn **1**, die gespeicherten Prozeduren werden neu generiert.  
  
 [  **@ignore_distributor =**] *Ignore_distributor*  
 Gibt an, wenn diese gespeicherte Prozedur, die ohne eine Verbindung mit dem Verteiler ausgeführt wird. *Ignore_distributor* ist **Bit**, hat den Standardwert **0**. Wenn **0**, die Datenbank muss aktiviert sein, für die Veröffentlichung und der Artikelcache sollte aktualisiert werden, entsprechend der neuen vom Artikel replizierten Spalten. Wenn **1**, können Artikelspalten für Artikel gelöscht werden, die befinden sich in einer nicht veröffentlichten Datenbank sollte nur in Wiederherstellungsszenarien verwendet werden.  
  
 [  **@change_active =** ] *Change_active*  
 Ermöglicht das Ändern der Spalten in Veröffentlichungen, für die Abonnements vorhanden sind. *Change_active* ist ein **Int** hat den Standardwert **0**. Wenn **0**, Spalten nicht geändert werden. Wenn **1**, Spalten hinzugefügt oder aus der aktiven Artikeln, die Abonnements gelöscht werden können.  
  
 [  **@force_invalidate_snapshot =** ] *Force_invalidate_snapshot*  
 Bestätigt, dass durch die von dieser gespeicherten Prozedur ausgeführte Aktion möglicherweise eine vorhandene Momentaufnahme ungültig wird. *Force_invalidate_snapshot* ist eine **Bit**, hat den Standardwert **0**.  
  
 **0** gibt an, dass Änderungen am Artikel bewirken nicht, die Momentaufnahme ungültig wird. Wenn die gespeicherte Prozedur erkennt, dass die Änderungen eine neue Momentaufnahme erfordern, tritt ein Fehler auf und es werden keine Änderungen vorgenommen.  
  
 **1** gibt an, dass Änderungen am Artikel kann dazu führen, dass die Momentaufnahme ungültig wird, und wenn es sind Abonnements vorhanden, die eine neue Momentaufnahme erfordern würden Berechtigung erteilt, die vorhandene Momentaufnahme als veraltet zu markieren und eine neue Momentaufnahme zu generieren.  
  
 [ **@force_reinit_subscription =** ] *Force_reinit_subscription*  
 Bestätigt, dass die von dieser gespeicherten Prozedur ausgeführte Aktion die erneute Initialisierung vorhandener Abonnements erfordern kann. *Force_reinit_subscription* ist eine **Bit**, hat den Standardwert **0**.  
  
 **0** gibt an, dass Änderungen am Artikel bewirken nicht, das Abonnement erneut initialisiert werden. Wenn die gespeicherte Prozedur erkennt, dass die Änderung die erneute Initialisierung von Abonnements erfordert, wird ein Fehler auftritt und keine Änderungen vorgenommen werden. **1** gibt an, dass Änderungen am Artikel dazu führen, vorhandene Abonnements erneut initialisiert werden dass, und erteilt die Berechtigung für die Initialisierung des Abonnements erfolgen.  
  
 [  **@publisher=** ] **"***Verleger***"**  
 Gibt einen nicht-[!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Verleger. *Publisher* ist **Sysname**, hat den Standardwert NULL.  
  
> [!NOTE]  
>  *Publisher* sollte nicht verwendet werden, mit einem [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Verleger.  
  
 [  **@internal=** ] **"***interne***"**  
 Nur interne Verwendung.  
  
## <a name="return-code-values"></a>Rückgabecodewerte  
 **0** (Erfolg) oder **1** (Fehler)  
  
## <a name="remarks"></a>Hinweise  
 **Sp_articlecolumn** wird bei Momentaufnahme- und Transaktionsreplikation verwendet.  
  
 Nur nicht abonnierte Artikel kann gefiltert werden, mithilfe von **Sp_articlecolumn**.  
  
## <a name="example"></a>Beispiel  
 [!code-sql[HowTo#sp_AddTranArticle](../../relational-databases/replication/codesnippet/tsql/sp-articlecolumn-transac_1.sql)]  
  
## <a name="permissions"></a>Berechtigungen  
 Nur Mitglieder der der **Sysadmin** -Serverrolle sein oder **Db_owner** feste Datenbankrolle können ausführen **Sp_articlecolumn**.  
  
## <a name="see-also"></a>Siehe auch  
 [Define an Article](../../relational-databases/replication/publish/define-an-article.md)   
 [Definieren und Ändern eines Spaltenfilters](../../relational-databases/replication/publish/define-and-modify-a-column-filter.md)   
 [Filtern von veröffentlichten Daten](../../relational-databases/replication/publish/filter-published-data.md)   
 [sp_addarticle &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-addarticle-transact-sql.md)   
 [Sp_articleview &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-articleview-transact-sql.md)   
 [sp_changearticle &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-changearticle-transact-sql.md)   
 [sp_droparticle &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-droparticle-transact-sql.md)   
 [sp_helparticle &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-helparticle-transact-sql.md)   
 [Sp_helparticlecolumns &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-helparticlecolumns-transact-sql.md)   
 [Gespeicherte Automatisierungsprozeduren &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/replication-stored-procedures-transact-sql.md)  
  
  
