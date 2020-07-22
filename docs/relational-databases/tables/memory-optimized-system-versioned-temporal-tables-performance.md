---
title: Systemleistung bei speicheroptimierten temporären Tabellen mit Systemversionsverwaltung | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/28/2016
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: table-view-index
ms.topic: conceptual
ms.assetid: 2e110984-7703-4806-a24b-b41e8c3018c6
author: CarlRabeler
ms.author: carlrab
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: bdb3feaead360c65760cb4e6ae996990c1d6bba9
ms.sourcegitcommit: b57d98e9b2444348f95c83a24b8eea0e6c9da58d
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/21/2020
ms.locfileid: "86552628"
---
# <a name="memory-optimized-system-versioned-temporal-tables-performance"></a>Systemleistung bei speicheroptimierten temporären Tabellen mit Systemversionsverwaltung

[!INCLUDE [sqlserver2016-asdb-asdbmi](../../includes/applies-to-version/sqlserver2016-asdb-asdbmi.md)]

Dieses Thema behandelt einige Überlegungen zur Systemleistung bei der Verwendung von speicheroptimierten Tabellen mit Systemversionsverwaltung.

- Wenn Sie einer vorhandenen, nicht-temporalen Tabelle Systemversionsverwaltung hinzufügen, ergeben sich Leistungsauswirkungen auf Aktualisierungs- und Löschvorgänge, da die Verlaufstabelle automatisch aktualisiert wird.
- Jeder Aktualisierungs- und Löschvorgang wird in einer internen speicheroptimierten Verlaufstabelle aufgezeichnet. Sie bemerken möglicherweise also einen unerwarteten Speicherverbrauch, wenn Ihre Arbeitsauslastung diese beiden Vorgänge im hohen Maße verwendet. Aus diesem Grund empfehlen wir Ihnen Folgendes:

  - Führen Sie keine massiven Löschvorgänge in der aktuellen Tabelle aus. So erhöhen Sie den verfügbaren RAM, indem Sie den Speicherplatz bereinigen. Ziehen Sie in Betracht, die Daten in mehreren Batches zu löschen und zusätzlich die Datenleerung manuell anzustoßen (mithilfe von [sp_xtp_flush_temporal_history](../../relational-databases/system-stored-procedures/temporal-table-sp-xtp-flush-temporal-history.md)oder wenn **SYSTEM_VERSIONING = OFF**gilt).
  - Führen Sie keine großen Tabellenaktualisierungen auf einmal durch, dies kann zu einem Speicherverbrauch führen, der doppelt so hoch wie für die Aktualisierung einer nicht-temporalen, speicheroptimierten Tabelle ist. Doppelter Speicherverbrauch ist temporär, da der Datenleerungstask regelmäßig ausgeführt wird, um den Speicherverbrauch interner Stagingtabellen in projizierten Grenzen in stabilen Zustand (ca. 10 % des Speicherverbrauchs der aktuellen temporalen Tabelle) zu halten. Sie sollten massive Aktualisierungen in mehreren Batches durchführen, oder während **SYSTEM_VERSIONING = OFF**, wie bei der Verwendung von Aktualisierungen zum Festlegen der Standardwerte für neu hinzugefügte Spalten.

- Der Zeitraum der Aktivierung der Datenleerung ist nicht konfigurierbar, jedoch können Sie den Prozess durch den Aufruf von [sp_xtp_flush_temporal_history](../../relational-databases/system-stored-procedures/temporal-table-sp-xtp-flush-temporal-history.md)gilt).
- Sie sollten als Speicheroption für datenträgerbasierte Verlaufstabellen einen gruppierten Columnstore verwenden, insbesondere dann, wenn Sie beabsichtigen, Analyseabfragen für Verlaufsdaten auszuführen, die Aggregat- oder Windowingfunktionen verwenden. In diesem Fall ist ein gruppierter Columnstore eine optimale Lösung für die Verlaufstabelle, da dieser gute Datenkomprimierung bietet und sich „einfügefreundlich“ verhält, was der Generierung von Verlaufsdaten entspricht.

## <a name="see-also"></a>Weitere Informationen

- [Temporale Tabellen mit Systemversionsverwaltung und speicheroptimierten Tabellen](../../relational-databases/tables/system-versioned-temporal-tables-with-memory-optimized-tables.md)
- [Erstellen einer speicheroptimierten temporalen Tabelle mit Systemversionsverwaltung](../../relational-databases/tables/creating-a-memory-optimized-system-versioned-temporal-table.md)
- [Verwenden von speicheroptimierten temporalen Tabellen mit Systemversionsverwaltung](../../relational-databases/tables/working-with-memory-optimized-system-versioned-temporal-tables.md)
- [Überwachung von speicheroptimierten temporalen Tabellen mit Systemversionsverwaltung](../../relational-databases/tables/monitoring-memory-optimized-system-versioned-temporal-tables.md)
- [Temporale Tabellen](../../relational-databases/tables/temporal-tables.md)
- [Systemkonsistenzprüfungen von temporalen Tabellen](../../relational-databases/tables/temporal-table-system-consistency-checks.md)
- [Verwalten der Beibehaltung von Verlaufsdaten in temporalen Tabellen mit Systemversionsverwaltung](../../relational-databases/tables/manage-retention-of-historical-data-in-system-versioned-temporal-tables.md)
- [Metadatenansichten und Funktionen für temporale Tabellen](../../relational-databases/tables/temporal-table-metadata-views-and-functions.md)
