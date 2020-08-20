---
description: sp_recompile (Transact-SQL)
title: sp_recompile (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/16/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_recompile_TSQL
- sp_recompile
dev_langs:
- TSQL
helpviewer_keywords:
- sp_recompile
ms.assetid: 6192ca87-febd-4075-8199-14b4fa609b8c
author: CarlRabeler
ms.author: carlrab
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: 6bbf1e6b85b3071e0029d1fd294a8147b79d64fb
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/17/2020
ms.locfileid: "88473894"
---
# <a name="sp_recompile-transact-sql"></a>sp_recompile (Transact-SQL)
[!INCLUDE [SQL Server SQL Database](../../includes/applies-to-version/sql-asdb.md)]

  Bewirkt, dass gespeicherte Prozeduren, Trigger und benutzerdefinierte Funktionen beim nächsten Ausführen erneut kompiliert werden. Dazu wird der vorhandene Plan aus dem Prozedurcache gelöscht, sodass beim nächsten Ausführen der Prozedur oder des Triggers das Erstellen eines neuen Plans erzwungen wird. In einer [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)]-Auflistung wird das Ereignis SP:CacheInsert anstelle des Ereignisses SP:Recompile protokolliert.  
  
 ![Symbol für Themenlink](../../database-engine/configure-windows/media/topic-link.gif "Symbol für Themenlink") [Transact-SQL-Syntaxkonventionen](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```sql  
  
sp_recompile [ @objname = ] 'object'  
```  
  
## <a name="arguments"></a>Argumente  
 [ @objname =] '*Object*'  
 Der qualifizierte oder nicht qualifizierte Name einer gespeicherten Prozedur, eines Triggers, einer Tabelle, einer Sicht oder einer benutzerdefinierten Funktion in der aktuellen Datenbank. Das *Objekt* ist vom Datentyp **nvarchar (776)** und hat keinen Standardwert. Wenn *Object* der Name einer gespeicherten Prozedur, eines Auslösers oder einer benutzerdefinierten Funktion ist, wird die gespeicherte Prozedur, der-Triggertyp oder die-Funktion beim nächsten Ausführen erneut kompiliert. Wenn *Object* der Name einer Tabelle oder Sicht ist, werden alle gespeicherten Prozeduren, Trigger oder benutzerdefinierten Funktionen, die auf die Tabelle oder Sicht verweisen, beim nächsten Ausführen erneut kompiliert.  
  
## <a name="return-code-values"></a>Rückgabecodewerte  
 0 (Erfolg) oder eine Zahl ungleich Null (Fehler)  
  
## <a name="remarks"></a>Bemerkungen  
 sp_recompile sucht nur in der aktuellen Datenbank nach einem Objekt.  
  
 Die Abfragen, die von gespeicherten Prozeduren, Triggern oder benutzerdefinierten Funktionen durchgeführt werden, werden nur bei der Prozedur- oder Triggerkompilierung optimiert. Wenn Sie Indizes bearbeiten oder andere Änderungen an der Datenbank vornehmen, die sich auf Statistiken beziehen, kann dies die Effizienz von gespeicherten Prozeduren, Triggern und benutzerdefinierten Funktionen beeinträchtigen. Durch das erneute Kompilieren der gespeicherten Prozeduren und Trigger, die auf eine Tabelle zugreifen, können solche Abfragen wieder optimiert werden.  
  
> [!NOTE]  
>  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] kompiliert gespeicherte Prozeduren, Trigger und benutzerdefinierten Funktionen automatisch neu, wenn dies von Vorteil ist.  
  
## <a name="permissions"></a>Berechtigungen  
 Erfordert die ALTER-Berechtigung für das angegebene Objekt.  
  
## <a name="examples"></a>Beispiele  
 Im folgenden Beispiel werden gespeicherte Prozeduren, Trigger und benutzerdefinierten Funktionen, die auf die `Customer`-Tabelle zugreifen, beim nächsten Ausführen erneut kompiliert.  
  
```  
USE AdventureWorks2012;  
GO  
EXEC sp_recompile N'Sales.Customer';  
GO  
```  
  
## <a name="see-also"></a>Weitere Informationen  
 [CREATE PROCEDURE &#40;Transact-SQL&#41;](../../t-sql/statements/create-procedure-transact-sql.md)   
 [CREATE TRIGGER &#40;Transact-SQL&#41;](../../t-sql/statements/create-trigger-transact-sql.md)   
 [Gespeicherte Systemprozeduren &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
