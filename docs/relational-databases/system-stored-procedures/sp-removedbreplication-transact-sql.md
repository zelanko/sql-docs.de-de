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
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 60004b81134b550761e65eba2ce38e155732c77f
ms.sourcegitcommit: 4d3896882c5930248a6e441937c50e8e027d29fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/05/2020
ms.locfileid: "82817333"
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
`[ @dbname = ] 'dbname'`Der Name der Datenbank. *dbname* ist vom Datentyp **sysname**. Der Standardwert ist NULL. Bei NULL wird die aktuelle Datenbank verwendet.  
  
`[ @type = ] type`Der Typ der Replikation, für den Datenbankobjekte entfernt werden. *type* ist vom Datentyp **nvarchar(5)** . Die folgenden Werte sind möglich:  
  
|||  
|-|-|  
|**tran**|Entfernt Transaktionsreplikations-Veröffentlichungsobjekte.|  
|**Merge**|Entfernt Mergereplikations-Veröffentlichungsobjekte.|  
|**both** (Standard)|Entfernt alle Replikationsveröffentlichungsobjekte.|  
  
## <a name="return-code-values"></a>Rückgabecodewerte  
 **0** (Erfolg) oder **1** (Fehler)  
  
## <a name="remarks"></a>Bemerkungen  
 **sp_removedbreplication** wird für alle Replikationstypen verwendet.  
  
 **sp_removedbreplication** ist hilfreich beim Wiederherstellen einer replizierten Datenbank, für die keine Replikationsobjekte wiederhergestellt werden müssen.  
  
 **sp_removedbreplication** kann nicht bei schreibgeschützten Datenbanken verwendet werden.  
  
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
  
  
