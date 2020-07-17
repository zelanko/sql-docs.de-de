---
title: Migrieren von Triggern | Microsoft-Dokumentation
description: Hier erfahren Sie mehr über speicheroptimierte Tabellen und DDL-Trigger, die bei den Anweisungen CREATE, ALTER, DROP, GRANT, DENY, REVOKE oder UPDATE STATISTICS in einer SQL Server-Instanz ausgelöst werden.
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: in-memory-oltp
ms.topic: conceptual
ms.assetid: ad5385c5-5a50-40ca-a319-97d5606b8511
author: MightyPen
ms.author: genemi
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: 7457f974820d1438d2e6d0293d31562c8c5f6a64
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/01/2020
ms.locfileid: "85722472"
---
# <a name="migrating-triggers"></a>Migrieren von Triggern
[!INCLUDE [SQL Server Azure SQL Database](../../includes/applies-to-version/sql-asdb.md)]

  In diesem Thema werden DDL-Trigger und speicheroptimierte Tabellen erläutert.  
  
 DML-Trigger werden für speicheroptimierte Tabellen unterstützt, aber nur mit dem Triggerereignis FOR | AFTER. Ein Beispiel finden Sie unter [Implementieren von UPDATE mit FROM oder Unterabfragen](../../relational-databases/in-memory-oltp/implementing-update-with-from-or-subqueries.md). 
  
 LOGON-Trigger sind Trigger zum Auslösen von LOGON-Ereignissen. LOGON-Trigger wirken sich nicht auf speicheroptimierte Tabellen aus.  
  
## <a name="ddl-triggers"></a>DDL-Trigger  
 DDL-Trigger sind Trigger, die ausgelöst werden, wenn eine CREATE-, ALTER-, DROP-, GRANT-, DENY-, REVOKE- oder UPDATE STATISTICS-Anweisung für die Datenbank oder den Server ausgeführt wird, für die oder den sie definiert wurde.  
  
 Sie können keine speicheroptimierten Tabellen erstellen, wenn die Datenbank oder der Server über mindestens einen DDL-Trigger verfügt, der für CREATE_TABLE oder eine beliebige Ereignisgruppe definiert wurde, in der das Ereignis enthalten ist. Sie können keine speicheroptimierte Tabelle löschen, wenn die Datenbank oder der Server über mindestens einen DDL-Trigger verfügt, der für DROP_TABLE oder eine beliebige Ereignisgruppe definiert wurde, in der das Ereignis enthalten ist.  
  
 Systemintern kompilierte gespeicherte Prozeduren können nicht erstellt werden, wenn mindestens ein DDL-Trigger für CREATE_PROCEDURE, DROP_PROCEDURE oder eine beliebige Ereignisgruppe definiert wurde, in der diese Ereignisse enthalten sind.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Migrieren zu In-Memory OLTP](../../relational-databases/in-memory-oltp/migrating-to-in-memory-oltp.md)  
  
  
