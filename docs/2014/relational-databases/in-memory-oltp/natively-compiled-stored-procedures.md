---
title: Systemintern kompilierte gespeicherte Prozeduren | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: in-memory-oltp
ms.topic: conceptual
helpviewer_keywords:
- natively compiled stored procedures
ms.assetid: d5ed432c-10c5-4e4f-883c-ef4d1fa32366
author: CarlRabeler
ms.author: carlrab
manager: craigg
ms.openlocfilehash: e9bdc0c104b212f3c26389c1792b6b617634a12a
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/02/2018
ms.locfileid: "48150561"
---
# <a name="natively-compiled-stored-procedures"></a>Systemintern kompilierte gespeicherte Prozeduren
  Systemintern kompilierte gespeicherte Prozeduren sind gespeicherte [!INCLUDE[tsql](../../includes/tsql-md.md)] -Prozeduren, die in systemeigenen Code kompiliert werden und auf speicheroptimierte Tabellen zugreifen. Systemintern kompilierte gespeicherte Prozeduren ermöglichen die effiziente Ausführung der Abfragen und Geschäftslogik in der gespeicherten Prozedur. Ausführliche Informationen zur systeminternen Kompilierung finden Sie unter [Native Compilation of Tables and Stored Procedures](native-compilation-of-tables-and-stored-procedures.md). Weitere Informationen zum Migrieren von datenträgerbasierten gespeicherten Prozeduren zu nativ kompilierten gespeicherten Prozeduren finden Sie unter [Migrationsprobleme bei nativ kompilierten gespeicherten Prozeduren](migration-issues-for-natively-compiled-stored-procedures.md).  
  
> [!NOTE]  
>  Ein Unterschied zwischen interpretierten (datenträgerbasierten) gespeicherten Prozeduren und systemintern kompilierten gespeicherten Prozeduren besteht darin, dass eine interpretierte gespeicherte Prozedur bei der ersten Ausführung kompiliert wird, während eine systemintern kompilierte gespeicherte Prozedur bei der Erstellung kompiliert wird. Bei systemintern kompilierten gespeicherten Prozeduren können viele Fehlerbedingungen (arithmetischer Überlauf, Typkonvertierung und bestimmte Bedingungen bei Division durch null) bei der Erstellung festgestellt werden, die zu einem Fehler bei der Erstellung der systemintern kompilierten gespeicherten Prozedur führen. Bei interpretierten gespeicherten Prozeduren führen diese Fehlerbedingungen in der Regel zu keinem Fehler, wenn die gespeicherte Prozedur erstellt wird, sondern bei jeder Ausführung.  
  
 Themen in diesem Abschnitt:  
  
-   [Erstellen systemintern kompilierter gespeicherter Prozeduren](creating-natively-compiled-stored-procedures.md)  
  
-   [ATOMIC-Blöcke](atomic-blocks-in-native-procedures.md)  
  
-   [Unterstützte Konstrukte in nativ kompilierten gespeicherten Prozeduren](supported-features-for-natively-compiled-t-sql-modules.md)  
  
-   [Verwenden von TRY...CATCH in nativ kompilierten gespeicherten Prozeduren](../../database-engine/using-try-catch-in-natively-compiled-stored-procedures.md)  
  
-   [Unterstützte Konstrukte für nativ kompilierte gespeicherte Prozeduren](supported-ddl-for-natively-compiled-t-sql-modules.md)  
  
-   [Nativ kompilierte gespeicherte Prozeduren und deren Ausführung mit SET-Optionen](natively-compiled-stored-procedures-and-execution-set-options.md)  
  
-   [Bewährte Vorgehensweisen für den Aufruf von systemintern kompilierten gespeicherten Prozeduren](best-practices-for-calling-natively-compiled-stored-procedures.md)  
  
-   [Überwachen der Leistung von systemintern kompilierten gespeicherten Prozeduren](monitoring-performance-of-natively-compiled-stored-procedures.md)  
  
-   [Aufrufen von systemintern kompilierten gespeicherten Prozeduren über Datenzugriffsanwendungen](calling-natively-compiled-stored-procedures-from-data-access-applications.md)  
  
## <a name="see-also"></a>Siehe auch  
 [Speicheroptimierte Tabellen](memory-optimized-tables.md)  
  
  
