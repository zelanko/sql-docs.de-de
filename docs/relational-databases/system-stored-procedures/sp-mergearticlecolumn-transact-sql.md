---
description: sp_mergearticlecolumn (Transact-SQL)
title: sp_mergearticlecolumn (Transact-SQL) | Microsoft-Dokumentation
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
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: d1036539564811e25be7764a3afb1106e05b1f37
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/17/2020
ms.locfileid: "88473970"
---
# <a name="sp_mergearticlecolumn-transact-sql"></a>sp_mergearticlecolumn (Transact-SQL)
[!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

  Führt eine vertikale Partitionierung einer Mergeveröffentlichung durch. Diese gespeicherte Prozedur wird auf dem Verleger für die Veröffentlichungs Datenbank ausgeführt.  
  
 ![Symbol für Themenlink](../../database-engine/configure-windows/media/topic-link.gif "Symbol für Themenlink") [Transact-SQL-Syntaxkonventionen](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
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
`[ @publication = ] 'publication'` Der Name der Veröffentlichung. *Publication* ist vom **Datentyp vom Datentyp sysname**und hat keinen Standardwert.  
  
`[ @article = ] 'article'` Der Name des Artikels in der Veröffentlichung. der *Artikel* ist vom **Datentyp vom Datentyp sysname**und hat keinen Standardwert.  
  
`[ @column = ] 'column'` Identifiziert die Spalten, für die die vertikale Partition erstellt werden soll. *Column* ist vom **Datentyp vom Datentyp sysname**und hat den Standardwert NULL. Bei den Werten NULL und `@operation = N'add'` werden dem Artikel standardmäßig alle Spalten in der Quelltabelle hinzugefügt. die *Spalte* darf nicht NULL sein, wenn der *Vorgang* auf **Drop**festgelegt ist. Um Spalten aus einem Artikel auszuschließen, führen Sie **sp_mergearticlecolumn** aus, und geben Sie *column* `@operation = N'drop'` für jede Spalte, die aus dem angegebenen *Artikel*entfernt werden soll, eine Spalte an.  
  
`[ @operation = ] 'operation'` Der Replikations Status. der *Vorgang* ist vom Datentyp **nvarchar (4)** und hat den Standardwert Add. **Hinzufügen** markiert die Spalte für die Replikation. **Drop** löscht die Spalte.  
  
`[ @schema_replication = ] 'schema_replication'` Gibt an, dass eine Schema Änderung weitergegeben wird, wenn die Merge-Agent ausgeführt wird. *schema_replication* ist vom Datentyp **nvarchar (5)** und hat den Standardwert false.  
  
> [!NOTE]  
>  Für *schema_replication*wird nur **false** unterstützt.  
  
`[ @force_invalidate_snapshot = ] force_invalidate_snapshot` Aktiviert oder deaktiviert die Möglichkeit, eine Momentaufnahme für ungültig zu erklären. *force_invalidate_snapshot* ist ein **Bit**, der Standardwert ist **0**.  
  
 der Wert **0** gibt an, dass Änderungen am Mergeartikel nicht bewirken, dass die Momentaufnahme ungültig wird.  
  
 der Wert **1** gibt an, dass Änderungen am Mergeartikel bewirken können, dass die Momentaufnahme ungültig wird. wenn dies der Fall ist, wird mit dem Wert **1** die Berechtigung zum Eintreten der neuen Momentaufnahme erteilt.  
  
`[ @force_reinit_subscription = ]force_reinit_subscription_` Aktiviert oder deaktiviert die Möglichkeit, dass das Abonnement erneut initialisiert werden kann. *force_reinit_subscription* ist ein Bit mit einem Standardwert von **0**.  
  
 der Wert **0** gibt an, dass Änderungen am Mergeartikel nicht bewirken, dass das Abonnement erneut initialisiert wird.  
  
 der Wert **1** gibt an, dass Änderungen am Mergeartikel bewirken können, dass das Abonnement erneut initialisiert wird. wenn dies der Fall ist, wird mit dem Wert **1** die Berechtigung für die erneute Initialisierung des Abonnements erteilt.  
  
## <a name="return-code-values"></a>Rückgabecodewerte  
 **0** (Erfolg) oder **1** (Fehler)  
  
## <a name="remarks"></a>Bemerkungen  
 **sp_mergearticlecolumn** wird bei der Mergereplikation verwendet.  
  
 Eine Identitätsspalte kann nicht aus dem Artikel gelöscht werden, wenn die automatische Identitätsbereichsverwaltung verwendet wird. Weitere Informationen finden Sie unter [Replizieren von Identitätsspalten](../../relational-databases/replication/publish/replicate-identity-columns.md).  
  
 Wenn eine Anwendung eine neue vertikale Partition festlegt, nachdem die Anfangsmomentaufnahme erstellt wurde, muss eine neue Momentaufnahme generiert und auf jedes Abonnement erneut angewendet werden. Momentaufnahmen werden angewendet, wenn die nächste geplante Momentaufnahme und der Verteilungs- oder Merge-Agent ausgeführt werden.  
  
 Falls die Zeilennachverfolgung zur Konflikterkennung verwendet wird (Standardeinstellung), kann die Basistabelle maximal 1.024 Spalten enthalten. Die Spalten müssen jedoch im Artikel gefiltert werden, sodass maximal 246 Spalten veröffentlicht werden. Wenn Spaltennachverfolgung verwendet wird, kann die Basistabelle maximal 246 Spalten enthalten.  
  
## <a name="example"></a>Beispiel  
 [!code-sql[HowTo#sp_AddMergeArticle](../../relational-databases/replication/codesnippet/tsql/sp-mergearticlecolumn-tr_1.sql)]  
  
## <a name="permissions"></a>Berechtigungen  
 Nur Mitglieder der festen Server Rolle **sysadmin** oder der festen Daten Bank Rolle **db_owner** können **sp_mergearticlecolumn**ausführen.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Definieren und Ändern eines Verknüpfungsfilters zwischen Mergeartikeln](../../relational-databases/replication/publish/define-and-modify-a-join-filter-between-merge-articles.md)   
 [Definieren und Ändern eines parametrisierten Zeilenfilters für einen Mergeartikel](../../relational-databases/replication/publish/define-and-modify-a-parameterized-row-filter-for-a-merge-article.md)   
 [Filtern von veröffentlichten Daten](../../relational-databases/replication/publish/filter-published-data.md)   
 [Gespeicherte Automatisierungsprozeduren &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/replication-stored-procedures-transact-sql.md)  
  
  
