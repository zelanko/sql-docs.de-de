---
title: Partitionierung mit temporalen Tabellen | Microsoft-Dokumentation
ms.custom: ''
ms.date: 04/26/2016
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: table-view-index
ms.topic: conceptual
ms.assetid: 313714b8-4ad1-4c14-93a3-7f628a334a51
author: CarlRabeler
ms.author: carlrab
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: fc76e2a2aaee2d3bc8474c8cec06b7ee85a31971
ms.sourcegitcommit: b57d98e9b2444348f95c83a24b8eea0e6c9da58d
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/21/2020
ms.locfileid: "86555885"
---
# <a name="partitioning-with-temporal-tables"></a>Partitionierung mit temporalen Tabellen

[!INCLUDE [sqlserver2016-asdb-asdbmi](../../includes/applies-to-version/sqlserver2016-asdb-asdbmi.md)]

Sie können die Partitionierung unabhängig voneinander für die aktuelle und die Verlaufstabelle verwenden. Ohne Systemversionsverwaltung können mittels Partitionierung jedoch keine Dateninhalte geändert werden.

> [!NOTE]
> Die Partitionierung ist eine Funktion der Enterprise Edition von SQL Server 2016 vor dem Service Pack 1 und früheren Versionen. Sämtliche Editionen von SQL Server 2016 Service Pack 1 und spätere Versionen unterstützen die Partitionierung.

- **Aktuelle Tabelle:**

  - **SWITCH IN** für die aktuelle Tabelle kann zum Laden und Abfragen von Daten verwendet werden, solange **SYSTEM_VERSIONING** mit **ON**
  - **SWITCH OUT** ist nicht zulässig, wenn **SYSTEM_VERSIONING** mit **ON**

- **Verlaufstabelle:**

  - **SWITCH OUT** kann über die Verlaufstabelle ausgeführt werden, solange **SYSTEM_VERSIONING** aktiviert ist ( **ON** ), um Teile der Verlaufsdaten zu löschen, die nicht mehr relevant sind.
  - **SWITCH IN** ist nicht zulässig, solange **SYSTEM_VERSIONING** aktiviert ist ( **ON** ), da es die Konsistenz temporaler Daten beeinträchtigen kann.

## <a name="next-steps"></a>Nächste Schritte

- [Temporale Tabellen](../../relational-databases/tables/temporal-tables.md)
- [Erste Schritte mit temporalen Tabellen mit Systemversionsverwaltung](../../relational-databases/tables/getting-started-with-system-versioned-temporal-tables.md)
- [Systemkonsistenzprüfungen von temporalen Tabellen](../../relational-databases/tables/temporal-table-system-consistency-checks.md)
- [Überlegungen und Einschränkungen zu temporalen Tabellen](../../relational-databases/tables/temporal-table-considerations-and-limitations.md)
- [Sicherheit bei temporale Tabellen](../../relational-databases/tables/temporal-table-security.md)
- [Verwalten der Beibehaltung von Verlaufsdaten in temporalen Tabellen mit Systemversionsverwaltung](../../relational-databases/tables/manage-retention-of-historical-data-in-system-versioned-temporal-tables.md)
- [Temporale Tabellen mit Systemversionsverwaltung und speicheroptimierten Tabellen](../../relational-databases/tables/system-versioned-temporal-tables-with-memory-optimized-tables.md)
- [Metadatenansichten und Funktionen für temporale Tabellen](../../relational-databases/tables/temporal-table-metadata-views-and-functions.md)
