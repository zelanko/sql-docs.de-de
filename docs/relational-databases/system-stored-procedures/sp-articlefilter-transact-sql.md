---
title: sp_articlefilter (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- sp_articlefilter_TSQL
- sp_articlefilter
helpviewer_keywords:
- sp_articlefilter
ms.assetid: 4c3fee32-a43f-4757-a029-30aef4696afb
author: stevestein
ms.author: sstein
ms.openlocfilehash: d90cd0ba957da820ce5a937ae687e39ca0302025
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "68769056"
---
# <a name="sp_articlefilter-transact-sql"></a>sp_articlefilter (Transact-SQL)
[!INCLUDE[appliesto-ss-asdbmi-xxxx-xxx-md](../../includes/appliesto-ss-asdbmi-xxxx-xxx-md.md)]

  Filtert Daten, die auf Grundlage eines Tabellenartikels veröffentlicht werden. Diese gespeicherte Prozedur wird auf dem Verleger für die Veröffentlichungs Datenbank ausgeführt.  
  
 ![Symbol für Themenlink](../../database-engine/configure-windows/media/topic-link.gif "Symbol für Themenlink") [Transact-SQL-Syntaxkonventionen](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```  
  
sp_articlefilter [ @publication = ] 'publication'  
        , [ @article = ] 'article'  
    [ , [ @filter_name = ] 'filter_name' ]  
    [ , [ @filter_clause = ] 'filter_clause' ]  
    [ , [ @force_invalidate_snapshot = ] force_invalidate_snapshot ]  
    [ , [ @force_reinit_subscription = ] force_reinit_subscription ]  
    [ , [ @publisher = ] 'publisher' ]  
```  
  
## <a name="arguments"></a>Argumente  
`[ @publication = ] 'publication'`Der Name der Veröffentlichung, die den Artikel enthält. *Publication* ist vom **Datentyp vom Datentyp sysname**und hat keinen Standardwert.  
  
`[ @article = ] 'article'`Der Name des Artikels. der *Artikel* ist vom **Datentyp vom Datentyp sysname**und hat keinen Standardwert.  
  
`[ @filter_name = ] 'filter_name'`Der Name der gespeicherten Filter Prozedur, die aus der *filter_name*erstellt werden soll. *filter_name* ist vom Datentyp **nvarchar (386)** und hat den Standardwert NULL. Sie müssen einen eindeutigen Namen für den Artikelfilter angeben.  
  
`[ @filter_clause = ] 'filter_clause'`Eine Einschränkungs Klausel (WHERE), die einen horizontalen Filter definiert. Wenn Sie die Einschränkungs Klausel eingeben, lassen Sie das Schlüsselwort aus. *filter_clause* ist vom Typ **ntext**und hat den Standardwert NULL.  
  
`[ @force_invalidate_snapshot = ] force_invalidate_snapshot`Bestätigt, dass die von dieser gespeicherten Prozedur ausgeführte Aktion eine vorhandene Momentaufnahme für ungültig erklären kann. *force_invalidate_snapshot* ist ein **Bit**, der Standardwert ist **0**.  
  
 der Wert **0** gibt an, dass Änderungen am Artikel nicht bewirken, dass die Momentaufnahme ungültig wird. Wenn die gespeicherte Prozedur erkennt, dass die Änderungen eine neue Momentaufnahme erfordern, tritt ein Fehler auf und es werden keine Änderungen vorgenommen.  
  
 der Wert **1** gibt an, dass Änderungen am Artikel bewirken können, dass die Momentaufnahme ungültig wird. wenn Abonnements vorhanden sind, die eine neue Momentaufnahme erfordern, wird die Berechtigung erteilt, die vorhandene Momentaufnahme als veraltet zu markieren und eine neue Momentaufnahme zu generieren.  
  
`[ @force_reinit_subscription = ] force_reinit_subscription`Bestätigt, dass die von dieser gespeicherten Prozedur ausgeführte Aktion möglicherweise erfordert, dass vorhandene Abonnements erneut initialisiert werden. *force_reinit_subscription* ist ein **Bit**, der Standardwert ist **0**.  
  
 der Wert **0** gibt an, dass Änderungen am Artikel nicht bewirken, dass Abonnements erneut initialisiert werden müssen. Wenn die gespeicherte Prozedur erkennt, dass die Änderung die erneute Initialisierung der Abonnements erfordert, tritt ein Fehler auf, und es werden keine Änderungen vorgenommen.  
  
 mit **1** wird angegeben, dass vorhandene Abonnements durch Änderungen am Artikel erneut initialisiert werden, und es wird die Berechtigung für die erneute Initialisierung des Abonnements erteilt.  
  
`[ @publisher = ] 'publisher'`Gibt einen nicht- [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Verleger an. *Publisher* ist vom **Datentyp vom Datentyp sysname**und hat den Standardwert NULL.  
  
> [!NOTE]  
>  *Publisher* sollte nicht mit einem [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Verleger verwendet werden.  
  
## <a name="return-code-values"></a>Rückgabecodewerte  
 **0** (Erfolg) oder **1** (Fehler)  
  
## <a name="remarks"></a>Bemerkungen  
 **sp_articlefilter** wird bei der Momentaufnahme-und Transaktions Replikation verwendet.  
  
 Wenn Sie **sp_articlefilter** für einen Artikel mit vorhandenen Abonnements ausführen, müssen diese Abonnements erneut initialisiert werden.  
  
 **sp_articlefilter** den Filter erstellt, fügt die ID der gespeicherten Filter Prozedur in die Spalte **Filter** der Tabelle [sysarticles &#40;Transact-SQL-&#41;](../../relational-databases/system-tables/sysarticles-transact-sql.md) ein und fügt dann den Text der Einschränkungs Klausel in die **filter_clause** Spalte ein.  
  
 Um einen Artikel mit einem horizontalen Filter zu erstellen, führen Sie [sp_addarticle &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/sp-addarticle-transact-sql.md) ohne *Filter* Parameter aus. Führen Sie **sp_articlefilter**aus, und geben Sie alle Parameter einschließlich *filter_clause*an. führen Sie dann [sp_articleview &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/sp-articleview-transact-sql.md)aus, und geben Sie alle Parameter einschließlich der identischen *filter_clause*an. Wenn der Filter bereits vorhanden ist und der **Typ** in **sysarticles** **1** (Protokoll basierter Artikel) ist, wird der vorherige Filter gelöscht, und es wird ein neuer Filter erstellt.  
  
 Wenn *filter_name* und *filter_clause* nicht bereitgestellt werden, wird der vorherige Filter gelöscht, und die Filter-ID wird auf **0**festgelegt.  
  
## <a name="example"></a>Beispiel  
 [!code-sql[HowTo#sp_AddTranArticle](../../relational-databases/replication/codesnippet/tsql/sp-articlefilter-transac_1.sql)]  
  
## <a name="permissions"></a>Berechtigungen  
 Nur Mitglieder der festen Server Rolle **sysadmin** oder der festen Daten Bank Rolle **db_owner** können **sp_articlefilter**ausführen.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Define an Article](../../relational-databases/replication/publish/define-an-article.md)   
 [Definieren und Ändern eines statischen Zeilen Filters](../../relational-databases/replication/publish/define-and-modify-a-static-row-filter.md)   
 [sp_addarticle &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/sp-addarticle-transact-sql.md)   
 [sp_articleview &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/sp-articleview-transact-sql.md)   
 [sp_changearticle &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/sp-changearticle-transact-sql.md)   
 [sp_droparticle &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/sp-droparticle-transact-sql.md)   
 [sp_helparticle &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/sp-helparticle-transact-sql.md)   
 [Gespeicherte Automatisierungsprozeduren &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/replication-stored-procedures-transact-sql.md)  
  
  
