---
title: sp_helpstats (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_helpstats
- sp_helpstats_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sp_helpstats
ms.assetid: 00ab3cfd-2736-4fc0-b1b2-16dd49fb2fe5
author: stevestein
ms.author: sstein
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: fba09255204b796a5134e8b8098e650430b7de63
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/27/2020
ms.locfileid: "68048404"
---
# <a name="sp_helpstats-transact-sql"></a>sp_helpstats (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  Gibt statistische Informationen zu Spalten und Indizes der angegebenen Tabelle zurück.  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepNextAvoid](../../includes/ssnotedepnextavoid-md.md)]Fragen Sie die Katalog Sichten [sys. stats](../../relational-databases/system-catalog-views/sys-stats-transact-sql.md) und [sys. stats_columns](../../relational-databases/system-catalog-views/sys-stats-columns-transact-sql.md) ab, um Informationen zu Statistiken zu erhalten.  
  
 ![Symbol für Themenlink](../../database-engine/configure-windows/media/topic-link.gif "Symbol für Themenlink") [Transact-SQL-Syntaxkonventionen](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```  
  
sp_helpstats[ @objname = ] 'object_name'   
     [ , [ @results = ] 'value' ]  
```  
  
## <a name="arguments"></a>Argumente  
`[ @objname = ] 'object_name'`Gibt die Tabelle an, für die Statistik Informationen bereitgestellt werden sollen. *object_name* ist vom Datentyp **nvarchar (520)** und darf nicht NULL sein. Es kann ein ein- oder zweiteiliger Name angegeben werden.  
  
`[ @results = ] 'value'`Gibt den Umfang der bereitgestellten Informationen an. Gültige Einträge sind **alle** und **Statistiken**. **Alle** listet Statistiken für alle Indizes und auch Spalten auf, für die Statistiken erstellt wurden. **Statistiken listet nur Statistiken** auf, die keinem Index zugeordnet sind. der Wert ist vom Datentyp **nvarchar (5)** und hat den Standard *Wert* stats.  
  
## <a name="return-code-values"></a>Rückgabecodewerte  
 „0“ (erfolgreich) oder „1“ (fehlerhaft)  
  
## <a name="result-sets"></a>Resultsets  
 In der folgenden Tabelle werden die Spalten des Resultsets beschrieben:  
  
|Spaltenname|BESCHREIBUNG|  
|-----------------|-----------------|  
|**statistics_name**|Der Name der Statistik. Gibt " **vom Datentyp sysname** " zurück und kann nicht NULL sein.|  
|**statistics_keys**|Die Schlüssel, auf denen die Statistik basiert. Gibt **nvarchar (2078)** zurück und darf nicht NULL sein.|  
  
## <a name="remarks"></a>Bemerkungen  
 Verwenden Sie DBCC SHOW_STATISTICS, um detaillierte statistische Informationen zu einem bestimmten Index oder einer bestimmten Statistik anzuzeigen. Weitere Informationen finden Sie unter [DBCC SHOW_STATISTICS &#40;Transact-SQL&#41;](../../t-sql/database-console-commands/dbcc-show-statistics-transact-sql.md) und [sp_helpindex &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/sp-helpindex-transact-sql.md).  
  
## <a name="permissions"></a>Berechtigungen  
 Erfordert die Mitgliedschaft in der **public** -Rolle.  
  
## <a name="examples"></a>Beispiele  
 Durch Ausführen von `sp_createstats` werden einspaltige Statistiken für alle in Frage kommenden Spalten aller Benutzertabellen in der [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)]-Datenbank erstellt. Anschließend wird `sp_helpstats` ausgeführt, um die für die `Customer`-Tabelle erstellten Statistiken zu ermitteln.  
  
```  
USE AdventureWorks2012;  
GO  
EXEC sp_createstats;  
GO  
EXEC sp_helpstats   
@objname = 'Sales.Customer',  
@results = 'ALL';  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
 `statistics_name               statistics_keys`  
  
 `----------------------------  ----------------`  
  
 `_WA_Sys_00000003_22AA2996     AccountNumber`  
  
 `AK_Customer_AccountNumber     AccountNumber`  
  
 `AK_Customer_rowguid           rowguid`  
  
 `CustomerType                  CustomerType`  
  
 `IX_Customer_TerritoryID       TerritoryID`  
  
 `ModifiedDate                  ModifiedDate`  
  
 `PK_Customer_CustomerID        CustomerID`  
  
## <a name="see-also"></a>Weitere Informationen  
 [Gespeicherte System Prozeduren &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)   
 [Datenbank-Engine gespeicherter Prozeduren &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/database-engine-stored-procedures-transact-sql.md)  
  
  
