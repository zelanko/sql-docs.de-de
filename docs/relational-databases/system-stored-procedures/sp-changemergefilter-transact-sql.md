---
title: sp_changemergefilter (Transact-SQL) | Microsoft-Dokumentation
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
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 5b5ea4ccea0f314e17cfa5dca8a4f3db6d2c9c1a
ms.sourcegitcommit: f7ac1976d4bfa224332edd9ef2f4377a4d55a2c9
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/02/2020
ms.locfileid: "85872500"
---
# <a name="sp_changemergefilter-transact-sql"></a>sp_changemergefilter (Transact-SQL)
[!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

  Ändert einige Mergefiltereigenschaften. Diese gespeicherte Prozedur wird auf dem Verleger für die Veröffentlichungs Datenbank ausgeführt.  
  
 ![Symbol für Themenlink](../../database-engine/configure-windows/media/topic-link.gif "Symbol für Themenlink") [Transact-SQL-Syntaxkonventionen](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
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
`[ @publication = ] 'publication'`Der Name der Veröffentlichung. *Publication* ist vom **Datentyp vom Datentyp sysname**und hat keinen Standardwert.  
  
`[ @article = ] 'article'`Der Name des Artikels. der *Artikel* ist vom **Datentyp vom Datentyp sysname**und hat keinen Standardwert.  
  
`[ @filtername = ] 'filtername'`Der aktuelle Name des Filters. *Filter Name* ist vom **Datentyp vom Datentyp sysname**und hat keinen Standardwert.  
  
`[ @property = ] 'property'`Der Name der Eigenschaft, die geändert werden soll. *Property* ist vom **Datentyp vom Datentyp sysname**und hat keinen Standardwert.  
  
`[ @value = ] 'value'`Der neue Wert für die angegebene Eigenschaft. der Wert ist vom Datentyp **nvarchar (1000)** und hat keinen Standard *Wert*.  
  
 Diese Tabelle beschreibt die Eigenschaften von Artikeln und die Werte für diese Eigenschaften.  
  
|Eigenschaft|Wert|Beschreibung|  
|--------------|-----------|-----------------|  
|**filter_type**|**1**|Joinfilter.<br /><br /> Diese Option ist erforderlich, um [!INCLUDE[ssEW](../../includes/ssew-md.md)]-Abonnenten zu unterstützen.|  
||**2**|Logische Datensatzbeziehung.|  
||**3**|Ein Joinfilter ist ebenfalls eine logische Datensatzbeziehung.|  
|**Filter Name**||Name des Filters.|  
|**join_articlename**||Name des Join-Artikels.|  
|**join_filterclause**||Filterklausel|  
|**join_unique_key**|**true**|Der Join betrifft einen eindeutigen Schlüssel.|  
||**false**|Der Join betrifft nicht einen eindeutigen Schlüssel.|  
  
`[ @force_invalidate_snapshot = ] force_invalidate_snapshot`Bestätigt, dass die von dieser gespeicherten Prozedur ausgeführte Aktion eine vorhandene Momentaufnahme für ungültig erklären kann. *force_invalidate_snapshot* ist ein **Bit**und hat den Standardwert **0**.  
  
 der Wert **0** gibt an, dass Änderungen am Mergeartikel nicht bewirken, dass die Momentaufnahme ungültig wird. Wenn die gespeicherte Prozedur erkennt, dass die Änderungen eine neue Momentaufnahme erfordern, tritt ein Fehler auf und es werden keine Änderungen vorgenommen.  
  
 **1** bedeutet, dass Änderungen am Mergeartikel bewirken können, dass die Momentaufnahme ungültig ist, und wenn Abonnements vorhanden sind, die eine neue Momentaufnahme erfordern, wird die Berechtigung erteilt, die vorhandene Momentaufnahme als veraltet zu markieren und eine neue Momentaufnahme zu generieren.  
  
`[ @force_reinit_subscription = ] force_reinit_subscription`Bestätigt, dass die von dieser gespeicherten Prozedur ausgeführte Aktion möglicherweise erfordert, dass vorhandene Abonnements erneut initialisiert werden. *force_reinit_subscription* ist ein **Bit** mit einem Standardwert von **0**.  
  
 der Wert **0** gibt an, dass Änderungen am Mergeartikel nicht bewirken, dass das Abonnement erneut initialisiert wird. Wenn die gespeicherte Prozedur erkennt, dass die Änderung die Neuinitialisierung vorhandener Abonnements erfordert, tritt ein Fehler auf, und es werden keine Änderungen durchgeführt.  
  
 **1** bedeutet, dass Änderungen am Mergeartikel bewirken, dass vorhandene Abonnements erneut initialisiert werden, und es wird die Berechtigung für die erneute Initialisierung des Abonnements erteilt.  
  
## <a name="return-code-values"></a>Rückgabecodewerte  
 **0** (Erfolg) oder **1** (Fehler)  
  
## <a name="remarks"></a>Hinweise  
 **sp_changemergefilter** wird bei der Mergereplikation verwendet.  
  
 Das Ändern des Filters für einen Mergeartikel erfordert, dass eine vorhandene Momentaufnahme erneut erstellt wird. Dies erfolgt durch Festlegen des ** \@ force_invalidate_snapshot** auf **1**. Wenn es Abonnements für diesen Artikel gibt, müssen die Abonnements erneut initialisiert werden. Dies erfolgt durch Festlegen des ** \@ force_reinit_subscription** auf **1**.  
  
 Um logische Datensätze verwenden zu können, müssen die Veröffentlichung und die Artikel eine Reihe von Anforderungen erfüllen. Weitere Informationen finden Sie unter [Gruppieren von Änderungen an verknüpften Zeilen mithilfe von logischen Datensätzen](../../relational-databases/replication/merge/group-changes-to-related-rows-with-logical-records.md).  
  
## <a name="permissions"></a>Berechtigungen  
 Nur Mitglieder der festen Server Rolle **sysadmin** oder der festen Daten Bank Rolle **db_owner** können **sp_changemergefilter**ausführen.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Ändern von Veröffentlichungs-und Artikeleigenschaften](../../relational-databases/replication/publish/change-publication-and-article-properties.md)   
 [sp_addmergefilter &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/sp-addmergefilter-transact-sql.md)   
 [sp_dropmergefilter &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/sp-dropmergefilter-transact-sql.md)   
 [sp_helpmergefilter &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/sp-helpmergefilter-transact-sql.md)   
 [Gespeicherte Systemprozeduren &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
