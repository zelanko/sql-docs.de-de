---
title: Sp_changemergefilter (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- sp_changemergefilter_TSQL
- sp_changemergefilter
helpviewer_keywords:
- sp_changemergefilter
ms.assetid: e08fdfdd-d242-4e85-817b-9f7a224fe567
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 32facb58645e0fbb3750ca02da0d3a22b320fc67
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "62997047"
---
# <a name="spchangemergefilter-transact-sql"></a>sp_changemergefilter (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Ändert einige Mergefiltereigenschaften. Diese gespeicherte Prozedur wird auf dem Verleger für die Veröffentlichungsdatenbank ausgeführt.  
  
 ![Themenlinksymbol](../../database-engine/configure-windows/media/topic-link.gif "Topic link icon") [Transact-SQL Syntax Conventions (Transact-SQL-Syntaxkonventionen)](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```  
  
sp_changemergefilter [ @publication= ] 'publication'  
        , [ @article= ] 'article'  
        , [ @filtername= ] 'filtername'  
        , [ @property= ] 'property'  
        , [ @value= ] 'value'  
    [ , [ @force_invalidate_snapshot = ] force_invalidate_snapshot ]  
    [ , [ @force_reinit_subscription = ] force_reinit_subscription ]  
```  
  
## <a name="arguments"></a>Argumente  
`[ @publication = ] 'publication'` Ist der Name der Veröffentlichung. *Veröffentlichung* ist **Sysname**, hat keinen Standardwert.  
  
`[ @article = ] 'article'` Ist der Name des Artikels. *Artikel* ist **Sysname**, hat keinen Standardwert.  
  
`[ @filtername = ] 'filtername'` Ist der aktuelle Name des Filters. *Filtername* ist **Sysname**, hat keinen Standardwert.  
  
`[ @property = ] 'property'` Ist der Name des zu ändernden Eigenschaft. *Eigenschaft* ist **Sysname**, hat keinen Standardwert.  
  
`[ @value = ] 'value'` Ist der neue Wert für die angegebene Eigenschaft. *Wert*ist **nvarchar(1000)** , hat keinen Standardwert.  
  
 Diese Tabelle beschreibt die Eigenschaften von Artikeln und die Werte für diese Eigenschaften.  
  
|Eigenschaft|Wert|Description|  
|--------------|-----------|-----------------|  
|**filter_type**|**1**|Joinfilter.<br /><br /> Diese Option ist erforderlich, um [!INCLUDE[ssEW](../../includes/ssew-md.md)]-Abonnenten zu unterstützen.|  
||**2**|Logische Datensatzbeziehung.|  
||**3**|Ein Joinfilter ist ebenfalls eine logische Datensatzbeziehung.|  
|**filtername**||Name des Filters.|  
|**join_articlename**||Name des Join-Artikels.|  
|**join_filterclause**||Filterklausel|  
|**join_unique_key**|**true**|Der Join betrifft einen eindeutigen Schlüssel.|  
||**false**|Der Join betrifft nicht einen eindeutigen Schlüssel.|  
  
`[ @force_invalidate_snapshot = ] force_invalidate_snapshot` Bestätigt, dass die von dieser gespeicherten Prozedur ausgeführte Aktion eine vorhandene Momentaufnahme für ungültig erklären kann. *Force_invalidate_snapshot* ist eine **Bit**, hat den Standardwert **0**.  
  
 **0** gibt an, dass Änderungen am Mergeartikel bewirken nicht, die Momentaufnahme ungültig wird. Wenn die gespeicherte Prozedur erkennt, dass die Änderungen eine neue Momentaufnahme erfordern, tritt ein Fehler auf und es werden keine Änderungen vorgenommen.  
  
 **1** bedeutet, dass Änderungen am Mergeartikel die Momentaufnahme ungültig werden können, und es sind Abonnements vorhanden, die eine neue Momentaufnahme erfordern würden, können Sie über die Berechtigung für die vorhandene Momentaufnahme als veraltet zu markieren und eine neue Momentaufnahme zu generieren.  
  
`[ @force_reinit_subscription = ] force_reinit_subscription` Bestätigt, dass die von dieser gespeicherten Prozedur ausgeführte Aktion die erneute Initialisierung vorhandener Abonnements erfordern kann. *Force_reinit_subscription* ist eine **Bit** hat den Standardwert **0**.  
  
 **0** gibt an, dass Änderungen am Mergeartikel bewirken nicht, das Abonnement erneut initialisiert werden. Wenn die gespeicherte Prozedur erkennt, dass die Änderung die Neuinitialisierung vorhandener Abonnements erfordert, tritt ein Fehler auf, und es werden keine Änderungen durchgeführt.  
  
 **1** bedeutet, dass am Mergeartikel Änderungen führt dazu, dass vorhandene Abonnements erneut initialisiert werden, und erteilt die Berechtigung für die Initialisierung des Abonnements erfolgen.  
  
## <a name="return-code-values"></a>Rückgabecodewerte  
 **0** (Erfolg) oder **1** (Fehler)  
  
## <a name="remarks"></a>Hinweise  
 **Sp_changemergefilter** wird bei der Mergereplikation verwendet.  
  
 Das Ändern des Filters für einen Mergeartikel erfordert, dass eine vorhandene Momentaufnahme erneut erstellt wird. Dies erfolgt durch Festlegen der **@force_invalidate_snapshot** zu **1**. Wenn es Abonnements für diesen Artikel gibt, müssen die Abonnements erneut initialisiert werden. Dies erfolgt durch Festlegen der **@force_reinit_subscription** zu **1**.  
  
 Um logische Datensätze verwenden zu können, müssen die Veröffentlichung und die Artikel eine Reihe von Anforderungen erfüllen. Weitere Informationen finden Sie unter [Gruppieren von Änderungen an verknüpften Zeilen mithilfe von logischen Datensätzen](../../relational-databases/replication/merge/group-changes-to-related-rows-with-logical-records.md).  
  
## <a name="permissions"></a>Berechtigungen  
 Nur Mitglieder der der **Sysadmin** -Serverrolle sein oder **Db_owner** feste Datenbankrolle können ausführen **Sp_changemergefilter**.  
  
## <a name="see-also"></a>Siehe auch  
 [Ändern von Veröffentlichungs- und Artikeleigenschaften](../../relational-databases/replication/publish/change-publication-and-article-properties.md)   
 [sp_addmergefilter &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-addmergefilter-transact-sql.md)   
 [sp_dropmergefilter &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-dropmergefilter-transact-sql.md)   
 [sp_helpmergefilter &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-helpmergefilter-transact-sql.md)   
 [Gespeicherte Systemprozeduren &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
