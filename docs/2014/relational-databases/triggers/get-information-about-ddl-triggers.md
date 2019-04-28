---
title: Abrufen von Informationen zu DDL-Triggern | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
helpviewer_keywords:
- metadata [SQL Server], triggers
- status information [SQL Server], DDL triggers
- DDL triggers, metadata
ms.assetid: 462becea-292a-4b9e-bb98-533e89733911
author: rothja
ms.author: jroth
manager: craigg
ms.openlocfilehash: 8d5e59264036380f6c8b5c9e73df5a6700c4b1ef
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62698216"
---
# <a name="get-information-about-ddl-triggers"></a>Abrufen von Informationen zu DDL-Triggern
  Die in diesem Abschnitt aufgeführten Katalogsichten können zum Abrufen von Informationen zu DLL-Triggern verwendet werden.  
  
 **So rufen Sie Informationen zu Ereignissen oder Ereignisgruppen ab, bei denen ein DDL-Trigger ausgelöst werden kann**  
  
-   [sys.trigger_event_types &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-trigger-event-types-transact-sql)  
  
 **So zeigen Sie die Abhängigkeiten eines Triggers an**  
  
-   [sys.sql_expression_dependencies &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-sql-expression-dependencies-transact-sql)  
  
-   [sys.dm_sql_referenced_entities &#40;Transact-SQL&#41;](/sql/relational-databases/system-dynamic-management-views/sys-dm-sql-referenced-entities-transact-sql)  
  
-   [sys.dm_sql_referencing_entities &#40;Transact-SQL&#41;](/sql/relational-databases/system-dynamic-management-views/sys-dm-sql-referencing-entities-transact-sql)  
  
## <a name="database-scoped-ddl-triggers"></a>Datenbankbezogene DLL-Trigger  
 **So rufen Sie Informationen zu datenbankbezogenen Triggern ab**  
  
-   [sys.triggers &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-triggers-transact-sql)  
  
 **So rufen Sie Informationen zu Datenbankereignissen ab, die Trigger auslösen**  
  
-   [sys.trigger_events &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-trigger-events-transact-sql)  
  
 **So zeigen Sie die Definition eines datenbankbezogenen Triggers an**  
  
-   [sys.sql_modules &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-sql-modules-transact-sql)  
  
 **So rufen Sie Informationen zu auf CRL-Datenbanken bezogenen Trigger ab**  
  
-   [sys.assembly_modules &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-assembly-modules-transact-sql)  
  
## <a name="server-scoped-ddl-triggers"></a>Serverbezogene DLL-Trigger  
 **So rufen Sie Informationen zu serverbezogenen Triggern ab**  
  
-   [sys.server_triggers &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-server-triggers-transact-sql)  
  
 **So rufen Sie Informationen zu Serverereignissen ab, die Trigger auslösen**  
  
-   [sys.server_trigger_events &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-server-trigger-events-transact-sql)  
  
 **So zeigen Sie die Definition eines serverbezogenen Triggers an**  
  
-   [sys.server_sql_modules &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-server-sql-modules-transact-sql)  
  
 **So rufen Sie Informationen zu auf CRL-Server bezogenen Triggern ab**  
  
-   [sys.server_assembly_modules &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-server-assembly-modules-transact-sql)  
  
## <a name="see-also"></a>Siehe auch  
 [DDL-Trigger](../triggers/ddl-triggers.md)  
  
  
