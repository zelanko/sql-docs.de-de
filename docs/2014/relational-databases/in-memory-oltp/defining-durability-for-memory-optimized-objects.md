---
title: Definieren von Dauerhaftigkeit für speicheroptimierte Objekte | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: in-memory-oltp
ms.topic: conceptual
ms.assetid: 0fe85fbf-8e8d-4983-96fd-d04b3c7d6d65
author: CarlRabeler
ms.author: carlrab
manager: craigg
ms.openlocfilehash: ecf171c8c50e1f7ce1e7cdc9e86cd27ac6fe558b
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "63161992"
---
# <a name="defining-durability-for-memory-optimized-objects"></a>Definieren von Dauerhaftigkeit für speicheroptimierte Objekte
  In-Memory OLTP gewährleistet vollständige Atomarität, Konsistenz, Isolation und Dauerhaftigkeit (ACID-Eigenschaften). Dauerhaftigkeit im Kontext von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] und speicheroptimierten Tabellen bietet folgende Garantien:  
  
 Dauerhaftigkeit von Transaktionen  
 Wenn Sie ein Commit für eine vollständig dauerhafte Transaktion ausführen, die DDL- oder DML-Änderungen an einer speicheroptimierten Tabelle vorgenommen hat, werden die Änderungen, die an einer dauerhaften speicheroptimierten Tabelle vorgenommen wurden, dauerhaft gespeichert.  
  
 Wenn Sie für eine verzögert dauerhafte Transaktion ein Commit in einer speicheroptimierte Tabelle ausführen, wird die Transaktion erst dauerhaft, nachdem das Transaktionsprotokoll im Arbeitsspeicher auf dem Datenträger gespeichert wurde.  
  
 Dauerhaftigkeit bei Neustarts  
 Wenn [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] nach einem Systemabsturz oder einem geplanten Herunterfahren neu gestartet wird, werden die speicheroptimierten Tabellen erneut instanziiert, um den Status der Tabellen vor dem Herunterfahren oder Systemabsturz wiederherzustellen.  
  
 Dauerhaftigkeit bei Medienfehlern  
 Wenn sich auf einem fehlerhaften oder beschädigten Datenträger eine oder mehrere persistente Kopien von dauerhaften speicheroptimierten Objekten befinden, werden durch die Sicherungs- und Wiederherstellungsfunktion von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] speicheroptimierte Tabellen auf dem neuen Medium wiederhergestellt.  
  
 Es gibt zwei Dauerhaftigkeitsoptionen für speicheroptimierte Tabellen:  
  
 SCHEMA_ONLY (nichtdauerhafte Tabelle)  
 Diese Option stellt die Dauerhaftigkeit des Tabellenschemas einschließlich Indizes sicher. Wenn [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] neu gestartet wird, wird die nichtdauerhafte Tabelle neu erstellt, aber ohne Daten gestartet. (Dies steht im Gegensatz zu einer Tabelle in tempdb, bei der sowohl die Tabelle als auch die Daten beim Neustart verloren gehen.) Ein typisches Szenario zum Erstellen einer nichtdauerhaften Tabelle besteht darin, kurzlebige Daten wie eine Stagingtabelle für einen ETL-Vorgang zu speichern. Durch SCHEMA_ONLY-Dauerhaftigkeit werden Transaktionsprotokollierung und -prüfpunkt vermieden, was zu einer erheblichen Reduzierung von E/A-Vorgängen führen kann.  
  
 SCHEMA_AND_DATA (dauerhafte Tabelle)  
 Diese Option gewährleistet Dauerhaftigkeit für Schema und Daten. Der Grad der Datendauerhaftigkeit ist abhängig davon, ob Sie ein Commit für eine Transaktion mit vollständiger oder verzögerter Dauerhaftigkeit ausführen. Vollständig dauerhafte Transaktionen bieten die gleiche Dauerhaftigkeitsgarantie für Daten und Schemas – ähnlich einer datenträgerbasierten Tabelle. Verzögerte Dauerhaftigkeit verbessert die Leistung, kann aber im Falle eines Serverabsturzes oder Failovers zu Datenverlusten führen. (Weitere Informationen zur verzögerten Dauerhaftigkeit finden Sie unter [Steuern der Transaktionsdauerhaftigkeit](../logs/control-transaction-durability.md).)  
  
 Das Schema der speicheroptimierten Tabelle wird – ähnlich datenträgerbasierten Tabellen – in der primären Dateigruppe einer Datenbank dauerhaft gespeichert.  
  
 Daten in dauerhaften speicheroptimierten Tabellen werden in Daten-/Änderungsdateipaaren gespeichert.  
  
 Die in speicheroptimierten Tabellen definierten Indizes werden nur in Metadaten, aber nicht im Speicher beibehalten. Indexstrukturen werden während des Ladevorgangs speicheroptimierter Tabellen generiert.  
  
 Zeilen werden entweder explizit durch eine DELETE-Anweisung oder indirekt durch eine UPDATE-Anweisung gelöscht. Ein UPDATE-Vorgang setzt sich aus einer Löschung und einer Einfügung zusammen. Wenn eine Zeile gelöscht wird, wird keine Änderung an einer Datendatei vorgenommen. An die entsprechende Änderungsdatei wird jedoch eine neue Zeile angefügt, die die gelöschte Zeile identifiziert.  
  
 Während der Wiederherstellung liest die In-Memory-OLTP-Engine Daten- und Änderungsdateien zum Laden in den physischen Speicher. Die Ladezeit wird bestimmt durch:  
  
-   Die zu ladende Datenmenge.  
  
-   Sequenzielle E/A-Bandbreite.  
  
-   Grad der Parallelität, bestimmt anhand der Anzahl der Dateicontainer und Prozessorkerne.  
  
-   Die Anzahl von Protokolldatensätzen im aktiven Teil des Protokolls, die wiederholt werden müssen.  
  
## <a name="see-also"></a>Siehe auch  
 [Erstellen und Verwalten von Speicher für speicheroptimierte Objekte](creating-and-managing-storage-for-memory-optimized-objects.md)  
  
  
