---
title: Systemtabellen (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/15/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
dev_langs:
- TSQL
helpviewer_keywords:
- status information [SQL Server]
- tables [SQL Server], system tables
- information retrieval [SQL Server]
- status information [SQL Server], system tables
- system information [SQL Server]
- system tables [SQL Server]
- system tables [SQL Server], about system tables
- system tables [SQL Server], retrieving information from
- retrieving system table information
ms.assetid: 56b8ad51-930c-4e5c-8d99-8c939d5b70ac
author: stevestein
ms.author: sstein
ms.openlocfilehash: 98f9a51b2248a1d218e9cbed576dc41bf64c91b5
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "68029617"
---
# <a name="system-tables-transact-sql"></a>Systemtabellen (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  In den Themen in diesem Abschnitt werden die Systemtabellen in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] beschrieben.  
  
 Die Systemtabellen sollten von keinem Benutzer direkt geändert werden. Versuchen Sie z. B. nicht, Systemtabellen mit den Anweisungen DELETE, UPDATE oder INSERT oder benutzerdefinierten Triggern zu ändern.  
  
 Das Verweisen auf dokumentierte Spalten in Systemtabellen ist zulässig. Viele der Spalten in Systemtabellen sind jedoch nicht dokumentiert. Anwendungen sollten nicht so geschrieben werden, dass sie undokumentierte Spalten direkt abfragen. Zum Abrufen von Informationen aus den Systemtabellen sollten Anwendungen vielmehr die folgenden Komponenten verwenden:  
  
-   Gespeicherte Systemprozeduren  
  
-   [!INCLUDE[tsql](../../includes/tsql-md.md)]-Anweisungen und -Funktionen  
  
-   [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Management Objects (SMO)  
  
-   Replikationsverwaltungsobjekte (RMO)  
  
-   Datenbank-API-Katalogfunktionen  
  
 Die Komponenten bilden eine veröffentlichte API zum Abrufen von Systeminformationen von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. [!INCLUDE[msCoName](../../includes/msconame-md.md)] erhält die Kompatibilität dieser Komponenten von Version zu Version aufrecht. Das Format der Systemtabellen hängt von der internen Architektur von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ab und kann sich von Version zu Version ändern. Daher müssen Anwendungen, die direkt auf die undokumentierten Spalten der Systemtabellen zugreifen, möglicherweise geändert werden, bevor sie auf eine spätere Version von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] zugreifen können.  
  
## <a name="in-this-section"></a>In diesem Abschnitt  
 Die Themen im Zusammenhang mit Systemtabellen sind nach den folgenden Funktionen unterteilt:  
  
|||  
|-|-|  
|[Sichern und Wiederherstellen von Tabellen &#40;Transact-SQL&#41;](../../relational-databases/system-tables/backup-and-restore-tables-transact-sql.md)|[Protokollversandtabellen &#40;Transact-SQL&#41;](../../relational-databases/system-tables/log-shipping-tables-transact-sql.md)|  
|[Ändern Sie die Data Capture-Tabellen &#40;Transact-SQL&#41;](../../relational-databases/system-tables/change-data-capture-tables-transact-sql.md)|[Replikationstabellen &#40;Transact-SQL&#41;](../../relational-databases/system-tables/replication-tables-transact-sql.md)|  
|[Datenbank-Wartungsplantabellen &#40;Transact-SQL&#41;](../../relational-databases/system-tables/database-maintenance-plan-tables-transact-sql.md)|[SQL Server-Agent-Tabellen &#40;Transact-SQL&#41;](../../relational-databases/system-tables/sql-server-agent-tables-transact-sql.md)|  
|[SQLServer, die erweiterte Ereignistabelle &#40;Transact-SQL&#41;](https://msdn.microsoft.com/library/6d52ff03-f5aa-4f0f-8c98-9b49dc76f94e)|[Sys.sysoledbusers &#40;Transact-SQL&#41;](../../relational-databases/system-compatibility-views/sys-sysoledbusers-transact-sql.md)|  
|[Integration Services-Tabellen &#40;Transact-SQL&#41;](../../relational-databases/system-tables/integration-services-tables-transact-sql.md)|[systranschemas &#40;Transact-SQL&#41;](../../relational-databases/system-views/systranschemas-transact-sql.md)|  
  
## <a name="see-also"></a>Siehe auch  
 [Kompatibilitätssichten &#40;Transact-SQL&#41;](~/relational-databases/system-compatibility-views/system-compatibility-views-transact-sql.md)   
 [Katalogsichten &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/catalog-views-transact-sql.md)  
  
  
