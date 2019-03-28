---
title: Sp_mergearticlecolumn (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- sp_mergearticlecolumn
- sp_mergearticlecolumn_TSQL
helpviewer_keywords:
- sp_mergearticlecolumn
ms.assetid: b4f2b888-e094-4759-a472-d893638995eb
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: d2cb929ffc3506d6dcb4a0745c53b47a45fdb469
ms.sourcegitcommit: c44014af4d3f821e5d7923c69e8b9fb27aeb1afd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/27/2019
ms.locfileid: "58538612"
---
# <a name="spmergearticlecolumn-transact-sql"></a>sp_mergearticlecolumn (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Führt eine vertikale Partitionierung einer Mergeveröffentlichung durch. Diese gespeicherte Prozedur wird auf dem Verleger für die Veröffentlichungsdatenbank ausgeführt.  
  
 ![Themenlinksymbol](../../database-engine/configure-windows/media/topic-link.gif "Topic link icon") [Transact-SQL Syntax Conventions (Transact-SQL-Syntaxkonventionen)](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```  
  
sp_mergearticlecolumn [ @publication = ] 'publication'  
        , [ @article = ] 'article'  
    [ , [ @column = ] 'column'  
    [ , [ @operation = ] 'operation'   
    [ , [ @schema_replication = ] 'schema_replication' ]  
    [ , [ @force_invalidate_snapshot = ] force_invalidate_snapshot ]   
    [ , [ @force_reinit_subscription = ] force_reinit_subscription ]   
```  
  
## <a name="arguments"></a>Argumente  
`[ @publication = ] 'publication'` Ist der Name der Veröffentlichung. *Veröffentlichung* ist **Sysname**, hat keinen Standardwert.  
  
`[ @article = ] 'article'` Ist der Name des Artikels in der Veröffentlichung. *Artikel* ist **Sysname**, hat keinen Standardwert.  
  
`[ @column = ] 'column'` Gibt die Spalten für die die vertikale Partition erstellt. *Spalte* ist **Sysname**, hat den Standardwert NULL. Bei den Werten NULL und `@operation = N'add'` werden dem Artikel standardmäßig alle Spalten in der Quelltabelle hinzugefügt. *Spalte* darf nicht NULL sein, wenn *Vorgang* nastaven NA hodnotu **löschen**. Führen Sie zum Ausschließen von Spalten aus einem Artikel **Sp_mergearticlecolumn** , und geben Sie *Spalte* und `@operation = N'drop'` für jede Spalte, die entfernt werden aus dem angegebenen *Artikel*.  
  
`[ @operation = ] 'operation'` Ist der Replikationsstatus. *Vorgang* ist **nvarchar(4)**, hat den Standardwert ADD. **Hinzufügen** markiert die Spalte für die Replikation. **Drop** wird die Spalte gelöscht.  
  
`[ @schema_replication = ] 'schema_replication'` Gibt an, dass eine schemaänderung weitergegeben wird, wenn der Merge-Agent ausgeführt wird. *Schema_replication* ist **nvarchar(5)**, hat den Standardwert "false".  
  
> [!NOTE]  
>  Nur **"false"** wird für unterstützt *Schema_replication*.  
  
`[ @force_invalidate_snapshot = ] force_invalidate_snapshot` Aktiviert oder deaktiviert die Möglichkeit, eine Momentaufnahme für ungültig erklärt. *Force_invalidate_snapshot* ist eine **Bit**, hat den Standardwert **0**.  
  
 **0** gibt an, dass Änderungen am Mergeartikel nicht die Momentaufnahme ungültig werden.  
  
 **1** gibt an, dass Änderungen am Mergeartikel die Momentaufnahme ungültig ist, wird möglicherweise Wenn dies zutrifft, wird ein Wert von **1** die Berechtigung für das Auftreten der neuen Momentaufnahme erteilt.  
  
`[ @force_reinit_subscription = ]force_reinit_subscription_` Aktiviert oder deaktiviert die Möglichkeit, die das Abonnement erneut zu initialisieren. *Force_reinit_subscription* ähnelt ein wenig mit dem Standardwert **0**.  
  
 **0** gibt an, dass Änderungen am Mergeartikel nicht werden dazu, dass das Abonnement erneut initialisiert werden.  
  
 **1** gibt an, dass Änderungen am Mergeartikel bewirken, dass das Abonnement erneut initialisiert werden, können und wenn dies der Fall, der Wert ist **1** erteilt die Berechtigung für die Initialisierung des Abonnements erfolgen.  
  
## <a name="return-code-values"></a>Rückgabecodewerte  
 **0** (Erfolg) oder **1** (Fehler)  
  
## <a name="remarks"></a>Hinweise  
 **Sp_mergearticlecolumn** wird bei der Mergereplikation verwendet.  
  
 Eine Identitätsspalte kann nicht aus dem Artikel gelöscht werden, wenn die automatische Identitätsbereichsverwaltung verwendet wird. Weitere Informationen finden Sie unter [Replizieren von Identitätsspalten](../../relational-databases/replication/publish/replicate-identity-columns.md).  
  
 Wenn eine Anwendung eine neue vertikale Partition festlegt, nachdem die Anfangsmomentaufnahme erstellt wurde, muss eine neue Momentaufnahme generiert und auf jedes Abonnement erneut angewendet werden. Momentaufnahmen werden angewendet, wenn die nächste geplante Momentaufnahme und der Verteilungs- oder Merge-Agent ausgeführt werden.  
  
 Falls die Zeilennachverfolgung zur Konflikterkennung verwendet wird (Standardeinstellung), kann die Basistabelle maximal 1.024 Spalten enthalten. Die Spalten müssen jedoch im Artikel gefiltert werden, sodass maximal 246 Spalten veröffentlicht werden. Wenn Spaltennachverfolgung verwendet wird, kann die Basistabelle maximal 246 Spalten enthalten.  
  
## <a name="example"></a>Beispiel  
 [!code-sql[HowTo#sp_AddMergeArticle](../../relational-databases/replication/codesnippet/tsql/sp-mergearticlecolumn-tr_1.sql)]  
  
## <a name="permissions"></a>Berechtigungen  
 Nur Mitglieder der der **Sysadmin** -Serverrolle sein oder **Db_owner** feste Datenbankrolle können ausführen **Sp_mergearticlecolumn**.  
  
## <a name="see-also"></a>Siehe auch  
 [Definieren und Ändern eines Verknüpfungsfilters zwischen Mergeartikeln](../../relational-databases/replication/publish/define-and-modify-a-join-filter-between-merge-articles.md)   
 [Definieren und Ändern eines parametrisierten Zeilenfilters für einen Mergeartikel](../../relational-databases/replication/publish/define-and-modify-a-parameterized-row-filter-for-a-merge-article.md)   
 [Filtern von veröffentlichten Daten](../../relational-databases/replication/publish/filter-published-data.md)   
 [Gespeicherte Automatisierungsprozeduren &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/replication-stored-procedures-transact-sql.md)  
  
  
