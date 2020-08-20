---
description: sp_dropmergearticle (Transact-SQL)
title: sp_dropmergearticle (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 05/02/2016
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- sp_dropmergearticle
- sp_dropmergearticle_TSQL
helpviewer_keywords:
- sp_dropmergearticle
ms.assetid: 5ef1fbf7-c03d-4488-9ab2-64aae296fa4f
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 77762c318d06d1a9c872405a9965e7b018f3eb85
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/17/2020
ms.locfileid: "88464318"
---
# <a name="sp_dropmergearticle-transact-sql"></a>sp_dropmergearticle (Transact-SQL)
[!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

  Entfernt einen Artikel aus einer Mergeveröffentlichung. Diese gespeicherte Prozedur wird auf dem Verleger für die Veröffentlichungs Datenbank ausgeführt.  
  
 ![Symbol für Themenlink](../../database-engine/configure-windows/media/topic-link.gif "Symbol für Themenlink") [Transact-SQL-Syntaxkonventionen](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```  
  
sp_dropmergearticle [ @publication= ] 'publication'  
        , [ @article= ] 'article'   
    [ , [ @ignore_distributor= ] ignore_distributor   
    [ , [ @reserved= ] reserved   
    [ , [ @force_invalidate_snapshot= ] force_invalidate_snapshot ]  
    [ , [ @force_reinit_subscription = ] force_reinit_subscription ]  
    [ , [ @ignore_merge_metadata = ] ignore_merge_metadata ]  
```  
  
## <a name="arguments"></a>Argumente  
`[ @publication = ] 'publication'` Der Name der Veröffentlichung, aus der ein Artikel gelöscht werden soll. *Publication*ist vom **Datentyp vom Datentyp sysname**und hat keinen Standardwert.  
  
`[ @article = ] 'article'` Der Name des Artikels, der aus der angegebenen Veröffentlichung gelöscht werden soll. der *Artikel*ist vom **Datentyp vom Datentyp sysname**und hat keinen Standardwert. Wenn **alle**, werden alle vorhandenen Artikel in der angegebenen Mergeveröffentlichung entfernt. Auch wenn der *Artikel* voll **ständig**ist, muss die Veröffentlichung getrennt vom Artikel abgelegt werden.  
  
`[ @ignore_distributor = ] ignore_distributor` Gibt an, ob diese gespeicherte Prozedur ausgeführt wird, ohne eine Verbindung mit dem Verteiler herzustellen. *ignore_distributor* ist vom Typ **Bit**. der Standardwert ist **0**.  
  
`[ @reserved = ] reserved` Ist für die zukünftige Verwendung reserviert. *reserved* ist vom Datentyp **nvarchar (20)** und hat den Standardwert NULL.  
  
`[ @force_invalidate_snapshot = ] force_invalidate_snapshot` Aktiviert oder deaktiviert die Möglichkeit, eine Momentaufnahme für ungültig zu erklären. *force_invalidate_snapshot* ist ein **Bit**und hat den Standardwert **0**.  
  
 der Wert **0** gibt an, dass Änderungen am Mergeartikel nicht bewirken, dass die Momentaufnahme ungültig wird.  
  
 **1** bedeutet, dass Änderungen am Mergeartikel bewirken können, dass die Momentaufnahme ungültig wird. wenn dies der Fall ist, wird mit dem Wert **1** die Berechtigung zum Auftreten der neuen Momentaufnahme erteilt.  
  
`[ @force_reinit_subscription = ] force_reinit_subscription` Bestätigt, dass das Löschen des Artikels erfordert, dass vorhandene Abonnements erneut initialisiert werden. *force_reinit_subscription* ist ein **Bit**, der Standardwert ist **0**.  
  
 der Wert **0** gibt an, dass das Löschen des Artikels nicht dazu führt, dass das Abonnement erneut initialisiert wird.  
  
 **1** bedeutet, dass das Löschen des Artikels dazu führt, dass vorhandene Abonnements erneut initialisiert werden, und die Berechtigung zur erneuten Initialisierung des Abonnements erteilt.  
  
`[ @ignore_merge_metadata = ] ignore_merge_metadata` Nur interne Verwendung.  
  
## <a name="return-code-values"></a>Rückgabecodewerte  
 **0** (Erfolg) oder **1** (Fehler)  
  
## <a name="remarks"></a>Bemerkungen  
 **sp_dropmergearticle** wird bei der Mergereplikation verwendet. Weitere Informationen zum [Löschen von Artikeln finden Sie unter Hinzufügen und Löschen von Artikeln aus vorhandenen Veröffentlichungen](../../relational-databases/replication/publish/add-articles-to-and-drop-articles-from-existing-publications.md).  
  
 Durch das Ausführen **sp_dropmergearticle** zum Löschen eines Artikels aus einer Veröffentlichung wird das Objekt nicht aus der Veröffentlichungs Datenbank oder dem entsprechenden Objekt aus der Abonnement Datenbank entfernt. Verwenden Sie `DROP <object>`, um diese Objekte bei Bedarf manuell zu entfernen.  
  
## <a name="permissions"></a>Berechtigungen  
 Nur Mitglieder der festen Server Rolle **sysadmin** oder der festen Daten Bank Rolle **db_owner** können **sp_dropmergearticle**ausführen.  
  
## <a name="example"></a>Beispiel  
  
```sql  
DECLARE @publication AS sysname;  
DECLARE @article1 AS sysname;  
DECLARE @article2 AS sysname;  
SET @publication = N'AdvWorksSalesOrdersMerge';  
SET @article1 = N'SalesOrderDetail';   
SET @article2 = N'SalesOrderHeader';   
  
-- Remove articles from a merge publication.  
USE [AdventureWorks]  
EXEC sp_dropmergearticle   
  @publication = @publication,   
  @article = @article1,  
  @force_invalidate_snapshot = 1;  
EXEC sp_dropmergearticle   
  @publication = @publication,   
  @article = @article2,  
  @force_invalidate_snapshot = 1;  
GO  
```  
  
```sql  
DECLARE @publication AS sysname;  
DECLARE @table1 AS sysname;  
DECLARE @table2 AS sysname;  
DECLARE @table3 AS sysname;  
DECLARE @salesschema AS sysname;  
DECLARE @hrschema AS sysname;  
DECLARE @filterclause AS nvarchar(1000);  
SET @publication = N'AdvWorksSalesOrdersMerge';   
SET @table1 = N'Employee';   
SET @table2 = N'SalesOrderHeader';   
SET @table3 = N'SalesOrderDetail';   
SET @salesschema = N'Sales';  
SET @hrschema = N'HumanResources';  
SET @filterclause = N'Employee.LoginID = HOST_NAME()';  
  
-- Drop the merge join filter between SalesOrderHeader and SalesOrderDetail.  
EXEC sp_dropmergefilter   
  @publication = @publication,   
  @article = @table3,   
  @filtername = N'SalesOrderDetail_SalesOrderHeader',   
  @force_invalidate_snapshot = 1,   
  @force_reinit_subscription = 1;  
  
-- Drops the merge join filter between Employee and SalesOrderHeader.  
EXEC sp_dropmergefilter   
  @publication = @publication,   
  @article = @table2,   
  @filtername = N'SalesOrderHeader_Employee',   
  @force_invalidate_snapshot = 1,   
  @force_reinit_subscription = 1;  
  
-- Drops the article for the SalesOrderDetail table.  
EXEC sp_dropmergearticle   
  @publication = @publication,   
  @article = @table3,  
  @force_invalidate_snapshot = 1,   
  @force_reinit_subscription = 1;  
  
-- Drops the article for the SalesOrderHeader table.  
EXEC sp_dropmergearticle   
  @publication = @publication,   
  @article = @table2,   
  @force_invalidate_snapshot = 1,   
  @force_reinit_subscription = 1;  
  
-- Drops the article for the Employee table.  
EXEC sp_dropmergearticle   
  @publication = @publication,   
  @article = @table1,  
  @force_invalidate_snapshot = 1,   
  @force_reinit_subscription = 1;  
GO  
```  
  
## <a name="see-also"></a>Weitere Informationen  
 [Löschen eines Artikels](../../relational-databases/replication/publish/delete-an-article.md)   
 [Hinzufügen und Löschen von Artikeln aus vorhandenen Veröffentlichungen](../../relational-databases/replication/publish/add-articles-to-and-drop-articles-from-existing-publications.md)   
 [sp_addmergearticle &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/sp-addmergearticle-transact-sql.md)   
 [sp_changemergearticle &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/sp-changemergearticle-transact-sql.md)   
 [sp_helpmergearticle &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-helpmergearticle-transact-sql.md)   
 [Gespeicherte Automatisierungsprozeduren &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/replication-stored-procedures-transact-sql.md)  
  
  
