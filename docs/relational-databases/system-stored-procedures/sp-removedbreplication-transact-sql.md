---
title: sp_removedbreplication (T-SQL)
description: Beschreibt die sp_removedbreplication gespeicherte Prozedur, die zum Entfernen aller Replikations Objekte in der Veröffentlichungs Datenbank für SQL Server Replikation verwendet wird.
ms.custom: seo-lt-2019
ms.date: 03/04/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- sp_removedbreplication
- sp_removedbreplication_TSQL
helpviewer_keywords:
- sp_removedbreplication
ms.assetid: cb98d571-d1eb-467b-91f7-a6e091009672
author: stevestein
ms.author: sstein
ms.openlocfilehash: c7da3db641d6e0b9aa53d570a7d0cf9bdc731477
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "75322248"
---
# <a name="sp_removedbreplication-transact-sql"></a>sp_removedbreplication (Transact-SQL)
[!INCLUDE[appliesto-ss-asdbmi-xxxx-xxx-md](../../includes/appliesto-ss-asdbmi-xxxx-xxx-md.md)]

  Diese gespeicherte Prozedur entfernt alle Replikationsobjekte aus der Veröffentlichungsdatenbank auf der Verlegerinstanz von SQL Server oder aus der Abonnementdatenbank auf der Abonnenteninstanz von SQL Server. Führen Sie sie in der entsprechenden Datenbank aus, oder geben Sie bei Ausführung im Kontext einer anderen Datenbank auf derselben Instanz die Datenbank an, aus der die Replikationsobjekte entfernt werden sollen. Diese Prozedur entfernt keine Objekte von anderen Datenbanken, wie z. B. der Verteilungsdatenbank.  
  
> [!NOTE]  
>  Die Prozedur sollte nur verwendet werden, wenn bei anderen Methoden zum Entfernen von Replikationsobjekten Fehler aufgetreten sind.  
  
 ![Symbol für Themenlink](../../database-engine/configure-windows/media/topic-link.gif "Symbol für Themenlink") [Transact-SQL-Syntaxkonventionen](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```  
  
sp_removedbreplication [ [ @dbname = ] 'dbname' ]  
    [ , [ @type = ] type ]   
```  
  
## <a name="arguments"></a>Argumente  
`[ @dbname = ] 'dbname'`Der Name der Datenbank. *dbname* ist vom **Datentyp vom Datentyp sysname**und hat den Standardwert NULL. Bei NULL wird die aktuelle Datenbank verwendet.  
  
`[ @type = ] type`Der Typ der Replikation, für den Datenbankobjekte entfernt werden. *Type ist vom Datentyp* **nvarchar (5)** . die folgenden Werte sind möglich:  
  
|||  
|-|-|  
|**Bahnhöfen**|Entfernt Transaktionsreplikations-Veröffentlichungsobjekte.|  
|**Merge**|Entfernt Mergereplikations-Veröffentlichungsobjekte.|  
|**beides** (Standard)|Entfernt alle Replikationsveröffentlichungsobjekte.|  
  
## <a name="return-code-values"></a>Rückgabecodewerte  
 **0** (Erfolg) oder **1** (Fehler)  
  
## <a name="remarks"></a>Bemerkungen  
 **sp_removedbreplication** wird bei allen Replikations Typen verwendet.  
  
 **sp_removedbreplication** ist nützlich, wenn eine replizierte Datenbank wieder hergestellt wird, für die keine Replikations Objekte wieder hergestellt werden müssen.  
  
 **sp_removedbreplication** kann nicht für eine Datenbank verwendet werden, die als schreibgeschützt gekennzeichnet ist.  
  
## <a name="example"></a>Beispiel  
 [!code-sql[HowTo#sp_removedbreplication](../../relational-databases/replication/codesnippet/tsql/sp-removedbreplication-t_1.sql)]  
  
## <a name="permissions"></a>Berechtigungen  
 Nur Mitglieder der festen Serverrolle **sysadmin** können **sp_removedbreplication**ausführen.  
  
## <a name="example"></a>Beispiel  
  
```  
-- Remove replication objects from the subscription database on MYSUB.  
DECLARE @subscriptionDB AS sysname  
SET @subscriptionDB = N'AdventureWorksReplica'  
  
-- Remove replication objects from a subscription database (if necessary).  
USE master  
EXEC sp_removedbreplication @subscriptionDB  
GO  
  
```  
  
## <a name="see-also"></a>Weitere Informationen  
 [Veröffentlichung und Verteilung deaktivieren](../../relational-databases/replication/disable-publishing-and-distribution.md)   
 [Gespeicherte Systemprozeduren &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
