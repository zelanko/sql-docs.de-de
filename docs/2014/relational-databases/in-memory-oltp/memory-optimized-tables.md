---
title: Speicheroptimierte Tabellen | Microsoft-Dokumentation
ms.custom: ''
ms.date: 10/27/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: in-memory-oltp
ms.topic: conceptual
ms.assetid: 14dddf81-b502-49dc-a6b6-d18b1ae32d2b
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 9123bf89f75fce68a6edd8ba1becd141821fe326
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "63158751"
---
# <a name="memory-optimized-tables"></a>Speicheroptimierte Tabellen
  Mit[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] In-Memory OLTP wird die Leistung von OLTP-Anwendungen durch effiziente, speicheroptimierte Datenzugriffe, systeminterne Kompilierung der Geschäftslogik sowie sperr- und latchfreie Algorithmen verbessert. Die In-Memory OLTP-Funktion enthält speicheroptimierte Tabellen und Tabellentypen sowie systeminterne Kompilierung von gespeicherten [!INCLUDE[tsql](../../includes/tsql-md.md)] -Prozeduren für effizienten Zugriff auf diese Tabellen.  
  
 Weitere Informationen zu speicheroptimierten Tabellen finden Sie unter:  
  
-   [Einführung in speicheroptimierte Tabellen](memory-optimized-tables.md)  
  
     Erläutert, was speicheroptimierte Tabellen sind, und stellt Informationen über die Dauerhaftigkeit von Daten, den Zugriff auf Daten in speicheroptimierten Tabellen und die Leistung sowie Skalierbarkeit bereit.  
  
-   [Systeminterne Kompilierung von Tabellen und gespeicherten Prozeduren](../in-memory-oltp/natively-compiled-stored-procedures.md)  
  
     Erläutert, wie speicheroptimierte Tabellen und systemintern kompilierten gespeicherten Prozeduren in DLLs kompiliert werden, und stellt Sicherheitsüberlegungen in diesem Zusammenhang dar.  
  
-   [Ändern von speicheroptimierten Tabellen](altering-memory-optimized-tables.md)  
  
     Richtlinien für die Aktualisierung von speicheroptimierten Tabellen (einschließlich dem Ändern von Tabellenspalten, Indizes und bucket_count).  
  
-   [Grundlegendes zu Transaktionen in speicheroptimierten Tabellen](../../database-engine/understanding-transactions-on-memory-optimized-tables.md)  
  
     Dieser Abschnitt enthält mehrere Themen in Bezug auf die Durchführung von Transaktionen in speicheroptimierten Tabellen, einschließlich Transaktionsisolationsstufen und containerübergreifenden Transaktionen.  
  
-   [Anwendungsmuster zur Partitionierung von speicheroptimierten Tabellen](application-pattern-for-partitioning-memory-optimized-tables.md)  
  
     Detailliertes Codebeispiel, das darstellt, wie partitionierte Tabellen bei der Verwendung von speicheroptimierten Tabellen emuliert werden.  
  
-   [Statistiken für speicheroptimierte Tabellen](statistics-for-memory-optimized-tables.md)  
  
     Erläutert, wie Statistiken für speicheroptimierte Tabellen kompiliert werden und wie diese Statistiken gepflegt und manuell aktualisiert werden.  
  
-   [Sortierungen und Codepages](../../database-engine/collations-and-code-pages.md)  
  
     Erläutert die Einschränkungen für unterstützte Sortierungen und Codeseiten für speicheroptimierte Tabellen.  
  
-   [Tabellen- und Zeilengröße in speicheroptimierten Tabellen](table-and-row-size-in-memory-optimized-tables.md)  
  
     Erläutert den Grenzwert von 8.060 Byte in den Zeilen speicheroptimierter Tabellen, und gibt ein Beispiel für die Berechnung von Tabellen- und Zeilengrößen an.  
  
-   [Anleitung zur Abfrageverarbeitung für speicheroptimierte Tabellen](a-guide-to-query-processing-for-memory-optimized-tables.md)  
  
     Gibt eine Übersicht über die Abfrageverarbeitung für speicheroptimierte Tabellen und systemintern kompilierte gespeicherte Prozeduren.  
  
## <a name="see-also"></a>Weitere Informationen  
 [In-Memory-OLTP &#40;Arbeitsspeicheroptimierung&#41;](in-memory-oltp-in-memory-optimization.md)  
  
  
