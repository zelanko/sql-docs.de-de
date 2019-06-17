---
title: Stretch Database, die erweiterte gespeicherte Prozeduren (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.reviewer: ''
ms.technology: stored-procedures
ms.topic: language-reference
dev_langs:
- TSQL
helpviewer_keywords:
- Stretch Database, stored procedures
ms.assetid: bda29952-4b8b-4295-ab78-f24dcb0b03c6
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: 5acbd4a14de04df412d71fb4ec8fd7d40e8fb7a8
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "65979987"
---
# <a name="stretch-database-extended-stored-procedures-transact-sql"></a>Stretch Database, die erweiterte gespeicherte Prozeduren (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2016-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2016-xxxx-xxxx-xxx-md.md)]

 Dieser Abschnitt beschreibt die erweiterten gespeicherten Prozeduren, die im Zusammenhang mit Stretch Database.  
  
## <a name="in-this-section"></a>In diesem Abschnitt  
[Sys. sp_rda_deauthorize_db](../../relational-databases/system-stored-procedures/sys-sp-rda-deauthorize-db-transact-sql.md) entfernt die authentifizierte Verbindung zwischen einer lokalen Stretch-aktivierte Datenbank und Azure-Remotedatenbank.

[sp_rda_get_rpo_duration](../../relational-databases/system-stored-procedures/sys-sp-rda-get-rpo-duration-transact-sql.md) Ruft die Anzahl von Stunden für migrierte Daten, die von SQL Server beibehalten in eine Stagingtabelle, um sicherzustellen, eine vollständige Wiederherstellung von Azure-Remotedatenbank, wenn eine Wiederherstellung erforderlich ist.
  
 [Sys. sp_rda_reauthorize_db](../../relational-databases/system-stored-procedures/sys-sp-rda-reauthorize-db-transact-sql.md) die authentifizierte Verbindung zwischen einer lokalen Datenbank für Stretch aktiviert und die remote-Datenbank wiederhergestellt.
  
 [sys.sp_rda_reconcile_batch](../../relational-databases/system-stored-procedures/sys-sp-rda-reconcile-batch-transact-sql.md)  
 Gleicht die Batch-ID, die in der Stretch-aktivierten SQL Server-Tabelle für die am häufigsten vor kurzem migrierten Daten gespeichert werden, mit der Batch-ID im Azure-Remotetabelle gespeichert. 
 
[sp_rda_reconcile_columns](../../relational-databases/system-stored-procedures/sys-sp-rda-reconcile-columns-transact-sql.md) gleicht im Azure-Remotetabelle Spalten den Spalten in Stretch-aktivierten SQL Server-Tabelle.
 
 [Sys.sp_rda_reconcile_indexes](../../relational-databases/system-stored-procedures/sys-sp-rda-reconcile-indexes-transact-sql.md) Warteschlangen eine Schemaaufgabe an, wenn Sie Indizes in der Remotetabelle abstimmen möchten.
 
 [sp_rda_set_query_mode](../../relational-databases/system-stored-procedures/sys-sp-rda-set-query-mode-transact-sql.md) gibt an, ob Abfragen an der aktuellen aktivierter Funktion Stretch-Datenbank und die Tabellen sowohl lokale als auch Daten (Standard) oder nur lokale Daten zurückgeben.
 
 [Sys. sp_rda_set_rpo_duration](../../relational-databases/system-stored-procedures/sys-sp-rda-set-rpo-duration-transact-sql.md) wird die Anzahl von Stunden für migrierte Daten, die von SQL Server beibehalten in eine Stagingtabelle, um sicherzustellen, eine vollständige Wiederherstellung von Azure-Remotedatenbank, wenn eine Wiederherstellung erforderlich ist.
 
 [Sys.sp_rda_test_connection](../../relational-databases/system-stored-procedures/sys-sp-rda-test-connection-transact-sql.md) testet die Verbindung von SQL Server mit der Azure-Remoteserver und meldet Probleme, die die Migration von Daten verhindern können.
 
## <a name="see-also"></a>Siehe auch  
 [Stretch Database](../../sql-server/stretch-database/stretch-database.md)  
  
  
