---
title: Erstellen und Verwalten von Speicher für speicheroptimierte Objekte | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine-imoltp
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: 622aabe6-95c7-42cc-8768-ac2e679c5089
caps.latest.revision: 61
author: CarlRabeler
ms.author: carlrab
manager: craigg
ms.openlocfilehash: 324143732c9ae7830e1fb588cb0793795acb6f5f
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/02/2018
ms.locfileid: "37285236"
---
# <a name="creating-and-managing-storage-for-memory-optimized-objects"></a>Erstellen und Verwalten von Speicher für speicheroptimierte Objekte
  Die [!INCLUDE[hek_2](../../includes/hek-2-md.md)]-Engine ist in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]integriert, was es Ihnen ermöglicht, sowohl speicheroptimierte als auch (traditionelle) datenträgerbasierte Tabellen in der gleichen Datenbank zu haben. Jedoch unterscheidet sich die Speicherstruktur für speicheroptimierte Tabellen von der für datenträgerbasierte Tabellen.  
  
 Speicher für datenträgerbasierte Tabelle weisen die folgenden Schlüsselattribute auf:  
  
-   Einer Dateigruppe zugeordnet, und die Dateigruppe enthält eine oder mehrere Dateien.  
  
-   Jede Datei wird in Blöcke mit 8 Seiten unterteilt, und jede Seite hat eine Größe von 8.000 Byte.  
  
-   Ein Block kann über mehrere Tabellen gemeinsam genutzt werden, aber es gibt eine 1:1-Zuordnung zwischen der zugeordneten Seite und der Tabelle oder dem Index. Anders gesagt kann eine Tabelle keine Zeilen von zwei oder mehr Tabellen oder Indizes enthalten.  
  
-   Die Daten werden je nach Bedarf in den Arbeitsspeicher (der Pufferpool) verschoben, und die geänderten oder neu erstellten Seiten werden asynchron auf den Datenträger geschrieben, wobei hauptsächlich zufällige Ein- und Ausgaben generiert werden.  
  
 Speicher für speicheroptimierte Tabellen weisen die folgenden Schlüsselattribute auf:  
  
-   Alle speicheroptimierten Tabellen werden in eine Speicheroptimierte Dateigruppe zugeordnet werden. Diese Dateigruppe basiert auf Filestream-Dateigruppe.  
  
-   Es gibt keine Seiten und die Daten werden als Zeile dauerhaft gespeichert.  
  
-   Alle Änderungen an speicheroptimierten Tabellen werden durch Anfügevorgänge an aktive Dateien gespeichert. Sowohl das Lesen als auch das Schreiben an Dateien ist sequenziell.  
  
-   Eine Aktualisierung wird jedoch als Vorgang implementiert, der aus einer Löschung und einer Einfügung besteht. Die gelöschten Zeilen werden nicht sofort aus dem Speicher entfernt. Die gelöschten Zeilen werden durch einen im Hintergrund ausgeführten Prozess namens MERGE entfernt; dies geschieht basierend auf einer Richtlinie wie in [Dauerhaftigkeit für speicheroptimierte Tabellen](memory-optimized-tables.md)beschrieben.  
  
-   Im Gegensatz zum Speicher für datenträgerbasierten Tabellen wird der Speicher für speicheroptimierte Tabellen nicht komprimiert. Beim Migrieren einer komprimierten (ZEILE oder SEITE), datenträgerbasierten Tabelle zu einer speicheroptimierten Tabelle müssen Sie die Größenänderungen berücksichtigen.  
  
-   Eine speicheroptimierte Tabelle kann sowohl dauerhaft als auch nicht dauerhaft sein. Sie müssen nur zum Konfigurieren von Speicher für permanente Speicher – optimieren von Tabellen.  
  
 In diesem Abschnitt werden Prüfpunktdateipaare und weitere Aspekte der Speicherung von Daten in speicheroptimierten Tabellen beschrieben.  
  
 Themen in diesem Abschnitt:  
  
-   [Konfigurieren von Speicher für speicheroptimierte Tabellen](configuring-storage-for-memory-optimized-tables.md)  
  
-   [Die speicheroptimierte Dateigruppe](the-memory-optimized-filegroup.md)  
  
-   [Dauerhaftigkeit für speicheroptimierte Tabellen](memory-optimized-tables.md)  
  
-   [Prüfpunktvorgang für speicheroptimierte Tabellen](checkpoint-operation-for-memory-optimized-tables.md)  
  
-   [Definieren von Dauerhaftigkeit für speicheroptimierte Objekte](defining-durability-for-memory-optimized-objects.md)  
  
-   [Vergleichen des datenträgerbasierten Tabellenspeichers mit dem speicheroptimierten Tabellenspeicher](comparing-disk-based-table-storage-to-memory-optimized-table-storage.md)  
  
-   [Überwachung und Problembehandlung beim Zusammenführen von Daten-/Änderungsdateipaaren](../../database-engine/monitoring-and-troubleshooting-merge-for-data-and-delta-file-pairs.md)  
  
## <a name="see-also"></a>Siehe auch  
 [In-Memory-OLTP &#40;Arbeitsspeicheroptimierung&#41;](in-memory-oltp-in-memory-optimization.md)  
  
  
