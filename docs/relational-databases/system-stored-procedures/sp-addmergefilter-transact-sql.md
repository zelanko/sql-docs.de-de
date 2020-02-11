---
title: sp_addmergefilter (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- sp_addmergefilter
- sp_addmergefilter_TSQL
helpviewer_keywords:
- sp_addmergefilter
ms.assetid: 4c118cb1-2008-44e2-a797-34b7dc34d6b1
author: stevestein
ms.author: sstein
ms.openlocfilehash: 0ba0e2384ec63d29d3a5030c0b018998896dc8cb
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "68769182"
---
# <a name="sp_addmergefilter-transact-sql"></a>sp_addmergefilter (Transact-SQL)
[!INCLUDE[appliesto-ss-asdbmi-xxxx-xxx-md](../../includes/appliesto-ss-asdbmi-xxxx-xxx-md.md)]

  Fügt einen neuen Mergefilter hinzu, um eine Partition auf der Basis eines Joins mit einer anderen Tabelle zu erstellen. Diese gespeicherte Prozedur wird auf dem Verleger für die Veröffentlichungs Datenbank ausgeführt.  
  
 ![Symbol für Themenlink](../../database-engine/configure-windows/media/topic-link.gif "Symbol für Themenlink") [Transact-SQL-Syntaxkonventionen](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```  
  
sp_addmergefilter [ @publication = ] 'publication'   
        , [ @article = ] 'article'   
        , [ @filtername = ] 'filtername'   
        , [ @join_articlename = ] 'join_articlename'   
        , [ @join_filterclause = ] join_filterclause  
    [ , [ @join_unique_key = ] join_unique_key ]  
    [ , [ @force_invalidate_snapshot = ] force_invalidate_snapshot ]  
    [ , [ @force_reinit_subscription = ] force_reinit_subscription ]  
    [ , [ @filter_type = ] filter_type ]  
```  
  
## <a name="arguments"></a>Argumente  
`[ @publication = ] 'publication'`Der Name der Veröffentlichung, in der der Mergefilter hinzugefügt wird. *Publication* ist vom **Datentyp vom Datentyp sysname**und hat keinen Standardwert.  
  
`[ @article = ] 'article'`Der Name des Artikels, für den der Mergefilter hinzugefügt wird. der *Artikel* ist vom **Datentyp vom Datentyp sysname**und hat keinen Standardwert.  
  
`[ @filtername = ] 'filtername'`Der Name des Filters. *Filter Name* ist ein erforderlicher Parameter. *Filter Name*ist vom **Datentyp vom Datentyp sysname**und hat keinen Standardwert.  
  
`[ @join_articlename = ] 'join_articlename'`Der übergeordnete Artikel, mit dem der durch *Artikel*angegebene untergeordnete Artikel mithilfe der von *join_filterclause*angegebenen joinklausel verknüpft werden muss, um die Zeilen im untergeordneten Artikel zu ermitteln, die das Filter Kriterium des Mergefilters erfüllen. *join_articlename* ist vom **Datentyp vom Datentyp sysname**und hat keinen Standardwert. Der Artikel muss in der Veröffentlichung vorliegen, die von der *Veröffentlichung*angegeben wird.  
  
`[ @join_filterclause = ] join_filterclause`Die Join-Klausel, die verwendet werden muss, um den untergeordneten Artikel, der durch den *Artikel*angegeben ist, und den von *join_article*angegebenen übergeordneten Artikel zu verknüpfen, um die Zeilen zu bestimmen, die den Mergefilter *join_filterclause* ist vom Datentyp **nvarchar (1000)**.  
  
`[ @join_unique_key = ] join_unique_key`Gibt an, ob der Join zwischen dem untergeordneten *Artikel und dem übergeordneten Artikel* *join_article*"1: n", "eins zu eins", "n:1" oder "m:n" ist. *join_unique_key* ist vom Datentyp **int**und hat den Standardwert 0. der Wert **0** gibt einen n:1-oder eine m:n-Join an. **1** gibt einen 1:1-oder 1: n-Join an. Dieser Wert ist **1** , wenn die Joinspalten einen eindeutigen Schlüssel in *join_article*bilden, oder wenn *join_filterclause* zwischen einem Fremdschlüssel in einem *Artikel* und einem Primärschlüssel in *join_article*liegt.  
  
> [!CAUTION]  
>  Legen Sie diesen Parameter nur auf **1** fest, wenn eine Einschränkung für die Spalte beitreten in der zugrunde liegenden Tabelle für den übergeordneten Artikel vorhanden ist, der die Eindeutigkeit gewährleistet. Wenn *join_unique_key* falsch festgelegt ist, kann **eine** nicht Konvergenz von Daten auftreten.  
  
`[ @force_invalidate_snapshot = ] force_invalidate_snapshot`Bestätigt, dass die von dieser gespeicherten Prozedur ausgeführte Aktion eine vorhandene Momentaufnahme für ungültig erklären kann. *force_invalidate_snapshot* ist ein **Bit**und hat den Standardwert **0**.  
  
 der Wert **0** gibt an, dass Änderungen am Mergeartikel nicht bewirken, dass die Momentaufnahme ungültig wird. Wenn die gespeicherte Prozedur erkennt, dass die Änderung eine neue Momentaufnahme erfordert, tritt ein Fehler auf, und es werden keine Änderungen vorgenommen.  
  
 der Wert **1** gibt an, dass Änderungen am Mergeartikel bewirken können, dass die Momentaufnahme ungültig wird. wenn Abonnements vorhanden sind, die eine neue Momentaufnahme erfordern, wird die Berechtigung erteilt, die vorhandene Momentaufnahme als veraltet zu markieren und eine neue Momentaufnahme zu generieren.  
  
`[ @force_reinit_subscription = ] force_reinit_subscription`Bestätigt, dass die von dieser gespeicherten Prozedur ausgeführte Aktion möglicherweise erfordert, dass vorhandene Abonnements erneut initialisiert werden. *force_reinit_subscription* ist ein **Bit**, der Standardwert ist 0.  
  
 der Wert **0** gibt an, dass Änderungen am Mergeartikel nicht bewirken, dass das Abonnement erneut initialisiert wird. Wenn die gespeicherte Prozedur erkennt, dass die Änderung die erneute Initialisierung von Abonnements erfordert, tritt ein Fehler auf, und es werden keine Änderungen durchgeführt.  
  
 der Wert **1** gibt an, dass Änderungen am Mergeartikel bewirken, dass vorhandene Abonnements erneut initialisiert werden, und erteilt die Berechtigung für die erneute Initialisierung des Abonnements.  
  
`[ @filter_type = ] filter_type`Gibt den hinzu zufügenden Filtertyp an. *filter_type* ist vom Datentyp **tinyint**. die folgenden Werte sind möglich:  
  
|value|BESCHREIBUNG|  
|-----------|-----------------|  
|**1**|Nur Joinfilter. Erforderlich zur unter [!INCLUDE[ssEW](../../includes/ssew-md.md)] Stützung von-Abonnenten.|  
|**2**|Nur logische Datensatzbeziehung.|  
|**€**|Sowohl Joinfilter als auch logische Datensatzbeziehung.|  
  
 Weitere Informationen finden Sie unter [Gruppieren von Änderungen an verknüpften Zeilen mithilfe von logischen Datensätzen](../../relational-databases/replication/merge/group-changes-to-related-rows-with-logical-records.md).  
  
## <a name="return-code-values"></a>Rückgabecodewerte  
 **0** (Erfolg) oder **1** (Fehler)  
  
## <a name="remarks"></a>Bemerkungen  
 **sp_addmergefilter** wird bei der Mergereplikation verwendet.  
  
 **sp_addmergefilter** können nur mit Tabellen Artikeln verwendet werden. Artikel für Sichten und indizierte Sichten werden nicht unterstützt.  
  
 Dieses Verfahren kann auch verwendet werden, um eine logische Beziehung zwischen zwei Artikeln hinzuzufügen, zwischen denen möglicherweise ein Joinfilter vorhanden ist. *filter_type* wird verwendet, um anzugeben, ob der hinzugefügte Zusammenführungs Filter ein Joinfilter, eine logische Beziehung oder beides ist.  
  
 Um logische Datensätze verwenden zu können, müssen die Veröffentlichung und die Artikel eine Reihe von Anforderungen erfüllen. Weitere Informationen finden Sie unter [Gruppieren von Änderungen an verknüpften Zeilen mithilfe von logischen Datensätzen](../../relational-databases/replication/merge/group-changes-to-related-rows-with-logical-records.md).  
  
 Diese Option wird normalerweise für einen Artikel verwendet, in dem ein Fremdschlüsselverweis auf eine veröffentlichte Primärschlüsseltabelle vorhanden ist und in dem für die Primärschlüsseltabelle ein Filter für den Artikel definiert ist. Mithilfe der Teilmenge von Primärschlüsselzeilen werden die Fremdschlüsselzeilen ermittelt, die auf den Abonnenten repliziert werden.  
  
 Wenn die Quelltabellen für zwei veröffentlichte Artikel denselben Tabellenobjektnamen aufweisen, können Sie keinen Joinfilter für die beiden Artikel hinzufügen. In einem solchen Fall kann kein Joinfilter erstellt werden, selbst wenn beide Tabellen im Besitz unterschiedlicher Schemas sind und eindeutige Artikelnamen aufweisen.  
  
 Werden sowohl ein parametrisierter Zeilenfilter als auch ein Joinfilter für einen Tabellenartikel verwendet, ermittelt die Replikation, ob eine Zeile der Partition eines Abonnenten angehört. Dies erfolgt durch Auswerten der Filterfunktion oder des Joinfilters (mit dem [or](../../t-sql/language-elements/or-transact-sql.md) -Operator), anstatt die Schnittmenge der beiden Bedingungen (mit dem [and-](../../t-sql/language-elements/and-transact-sql.md) Operator) auszuwerten.  
  
## <a name="example"></a>Beispiel  
 [!code-sql[HowTo#sp_addmergefilter](../../relational-databases/replication/codesnippet/tsql/sp-addmergefilter-transa_1.sql)]  
  
## <a name="permissions"></a>Berechtigungen  
 Nur Mitglieder der festen Server Rolle **sysadmin** oder der festen Daten Bank Rolle **db_owner** können **sp_addmergefilter**ausführen.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Define an Article](../../relational-databases/replication/publish/define-an-article.md)   
 [Definieren und Ändern eines Joinfilters zwischen Mergeartikeln](../../relational-databases/replication/publish/define-and-modify-a-join-filter-between-merge-articles.md)   
 [Join Filters](../../relational-databases/replication/merge/join-filters.md)   
 [sp_changemergefilter &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/sp-changemergefilter-transact-sql.md)   
 [sp_dropmergefilter &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/sp-dropmergefilter-transact-sql.md)   
 [sp_helpmergefilter &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/sp-helpmergefilter-transact-sql.md)   
 [Gespeicherte Automatisierungsprozeduren &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/replication-stored-procedures-transact-sql.md)  
  
  
