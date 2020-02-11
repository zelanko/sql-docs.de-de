---
title: Erweiterte gespeicherte Prozeduren (Transact-SQL)
titleSuffix: SQL Server Stretch Database
ms.custom: seo-dt-2019
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
ms.openlocfilehash: d82b6cb9049bf5a41cfb987a55bb6d5a7147c9bd
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "74119272"
---
# <a name="stretch-database-extended-stored-procedures-transact-sql"></a>Stretch Database erweiterter gespeicherter Prozeduren (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2016-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2016-xxxx-xxxx-xxx-md.md)]

 In diesem Abschnitt werden die erweiterten gespeicherten Prozeduren beschrieben, die mit Stretch Database verknüpft sind.  
  
## <a name="in-this-section"></a>In diesem Abschnitt  
[sys. sp_rda_deauthorize_db](../../relational-databases/system-stored-procedures/sys-sp-rda-deauthorize-db-transact-sql.md) Entfernt die authentifizierte Verbindung zwischen einer lokalen Stretch-aktivierten Datenbank und der Azure-Remote Datenbank.

[sys. sp_rda_get_rpo_duration](../../relational-databases/system-stored-procedures/sys-sp-rda-get-rpo-duration-transact-sql.md) Ruft die Anzahl der Stunden der migrierten Daten ab, die SQL Server in einer Stagingtabelle beibehält, um eine vollständige Wiederherstellung der Azure-Remote Datenbank zu gewährleisten, wenn eine Wiederherstellung erforderlich ist.
  
 [sys. sp_rda_reauthorize_db](../../relational-databases/system-stored-procedures/sys-sp-rda-reauthorize-db-transact-sql.md) Stellt die authentifizierte Verbindung zwischen einer lokalen Datenbank, die für Stretch aktiviert ist, und der Remote Datenbank wieder her.
  
 [sys.sp_rda_reconcile_batch](../../relational-databases/system-stored-procedures/sys-sp-rda-reconcile-batch-transact-sql.md)  
 Gibt die Batch-ID, die in der Stretch-aktivierten SQL Server Tabelle gespeichert ist, für die zuletzt migrierten Daten mit der in der Azure-Remote Tabelle gespeicherten Batch-ID aus. 
 
[sys. sp_rda_reconcile_columns](../../relational-databases/system-stored-procedures/sys-sp-rda-reconcile-columns-transact-sql.md) Gibt die Spalten in der Azure-Remote Tabelle mit den Spalten in der Stretch-aktivierten SQL Server Tabelle aus.
 
 [sys. sp_rda_reconcile_indexes](../../relational-databases/system-stored-procedures/sys-sp-rda-reconcile-indexes-transact-sql.md) Fügt eine Schema Aufgabe in die Warteschlange ein, um Indizes für die Remote Tabelle abzustimmen.
 
 [sys. sp_rda_set_query_mode](../../relational-databases/system-stored-procedures/sys-sp-rda-set-query-mode-transact-sql.md) Gibt an, ob Abfragen für die aktuelle Stretch-aktivierte Datenbank und Ihre Tabellen sowohl lokale als auch Remote Daten (Standard) oder lokale Daten zurückgeben.
 
 [sys. sp_rda_set_rpo_duration](../../relational-databases/system-stored-procedures/sys-sp-rda-set-rpo-duration-transact-sql.md) Legt die Anzahl von Stunden für migrierte Daten fest, die SQL Server in einer Stagingtabelle beibehalten werden, um eine vollständige Wiederherstellung der Azure-Remote Datenbank zu gewährleisten, wenn eine Wiederherstellung erforderlich ist.
 
 [sys. sp_rda_test_connection](../../relational-databases/system-stored-procedures/sys-sp-rda-test-connection-transact-sql.md) Testet die Verbindung von SQL Server mit dem Azure-Remote Server und meldet Probleme, die eine Datenmigration verhindern können.
 
## <a name="see-also"></a>Weitere Informationen  
 [Stretch Database](../../sql-server/stretch-database/stretch-database.md)  
  
  
