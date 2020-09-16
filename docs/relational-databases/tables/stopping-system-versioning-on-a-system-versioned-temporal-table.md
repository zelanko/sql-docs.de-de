---
description: Beenden der Versionsverwaltung auf einer versionsverwalteten temporalen Tabelle
title: Beenden der Versionsverwaltung auf einer versionsverwalteten temporalen Tabelle | Microsoft Dokumentation
ms.custom: ''
ms.date: 04/28/2020
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: table-view-index
ms.topic: conceptual
ms.assetid: dddd707e-bfb1-44ff-937b-a84c5e5d1a94
author: markingmyname
ms.author: maghan
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: 2686ba2c5ac8e4db03f49a1d090ed8de1066b2c7
ms.sourcegitcommit: dd36d1cbe32cd5a65c6638e8f252b0bd8145e165
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 09/08/2020
ms.locfileid: "89550948"
---
# <a name="stopping-system-versioning-on-a-system-versioned-temporal-table"></a>Beenden der Versionsverwaltung in einer temporalen Tabelle mit Systemversionsverwaltung


[!INCLUDE [sqlserver2016-asdb-asdbmi](../../includes/applies-to-version/sqlserver2016-asdb-asdbmi.md)]


Möglicherweise möchten Sie die Versionsverwaltung Ihrer temporalen Tabelle vorübergehend oder dauerhaft beenden. Legen Sie zu diesem Zweck die **SYSTEM_VERSIONING** -Klausel, um **OFF**fest.

## <a name="setting-system_versioning--off"></a>Festlegen von SYSTEM_VERSIONING = OFF

Beenden Sie die Systemversionsverwaltung, wenn Sie bestimmte Wartungsvorgänge für eine temporale Tabelle ausführen möchten, oder wenn Sie eine Tabelle mit Versionsverwaltung nicht mehr benötigen. Das Ergebnis dieses Vorgangs sind zwei unabhängige Tabellen:

- Die aktuelle Tabelle mit der Fristdefinition

- Verlaufstabelle als normale Tabelle

### <a name="important-remarks"></a>Wichtige Hinweise

- Die Verlaufstabelle **beendet** die Aufnahme der Updates solange **SySTEM_VERSIONING = OFF** festgelegt ist.
- Bei einer **temporären Tabelle** tritt kein Datenverlust auf, wenn Sie **SYSTEM_VERSIONING = OFF** festlegen oder den Zeitraum für **SYSTEM_TIME** löschen.
- Wenn Sie **SYSTEM_VERSIONING = OFF** festlegen und den **SYSTEM_TIME** -Zeitraum nicht löschen, wird das System die Aktualisierung der Zeitraumspalten für jeden Einfüge- und Aktualisierungsvorgang fortsetzen. Löschungen in der aktuellen Tabelle sind endgültig.
- Löschen Sie den **SYSTEM_TIME** -Zeitraum, um die Zeitraumspalten vollständig zu entfernen.
- Wenn Sie **SYSTEM_VERSIONING = OFF**festlegen, können alle Benutzer, die über ausreichende Berechtigungen verfügen, das Schema und den Inhalt der Verlaufstabelle ändern oder die Verlaufstabelle sogar endgültig löschen.
- Sie können **SYSTEM_VERSIONING = OFF** nicht festlegen, wenn Sie mithilfe temporaler Abfrageerweiterungen andere Objekte mit SCHEMABINDING erstellt haben, z. B. durch Verweise auf **SYSTEM_TIME**. Diese Einschränkung verhindert, dass es bei diesen Objekten zu Fehlern kommt, wenn Sie **SYSTEM_VERSIONING = OFF** festlegen.

### <a name="permanently-remove-system_versioning"></a>Dauerhaftes Entfernen von SYSTEM_VERSIONING

In diesem Beispiel werden SYSTEM_VERSIONING und die Zeitraumspalten dauerhaft und vollständig entfernt. Das Entfernen der Zeitraumspalten ist optional.

```sql
ALTER TABLE dbo.Department SET (SYSTEM_VERSIONING = OFF);
/*Optionally, DROP PERIOD if you want to revert temporal table to a non-temporal*/
ALTER TABLE dbo.Department
DROP PERIOD FOR SYSTEM_TIME;
```

### <a name="temporarily-remove-system_versioning"></a>Vorübergehendes Entfernen von SYSTEM_VERSIONING

Dies ist die Liste der Vorgänge, für die die Systemversionsverwaltung auf **OFF**festgelegt werden muss:

- Entfernen unnötiger Daten aus dem Verlauf (**DELETE** oder **TRUNCATE**)
- Entfernen von Daten aus der aktuellen Tabelle ohne Versionsverwaltung (**DELETE**, **TRUNCATE**)
- Partition **SWITCH OUT** aus der aktuellen Tabelle
- Partition **SWITCH IN** in die Verlaufstabelle

In diesem Beispiel wird SYSTEM_VERSIONING vorübergehend beendet, um bestimmte Wartungsvorgänge zu erlauben. Wenn Sie Versionsverwaltung als Voraussetzung für die Tabellenwartung vorübergehend beenden, empfehlen wir nachdrücklich, dies für die Datenkonsistenz innerhalb einer Transaktion durchzuführen.

> [!NOTE]
> Wenn Sie die Systemversionsverwaltung wieder aktivieren, vergessen Sie nicht, das Argument HISTORY_TABLE anzugeben. Andernfalls wird eine neue Verlaufstabelle erstellt und der aktuellen Tabelle zugeordnet. Die ursprüngliche Verlaufstabelle existiert dann weiterhin als normale Tabelle, wird der aktuellen Tabelle aber nicht zugeordnet.

```sql
BEGIN TRAN
ALTER TABLE dbo.Department SET (SYSTEM_VERSIONING = OFF);
TRUNCATE TABLE [History].[DepartmentHistory]
WITH (PARTITIONS (1,2))
ALTER TABLE dbo.Department SET
(
SYSTEM_VERSIONING = ON (HISTORY_TABLE = History.DepartmentHistory)
);
COMMIT ;
```

## <a name="next-steps"></a>Nächste Schritte

- [Temporale Tabellen](../../relational-databases/tables/temporal-tables.md)
- [Erste Schritte mit temporalen Tabellen mit Systemversionsverwaltung](../../relational-databases/tables/getting-started-with-system-versioned-temporal-tables.md)
- [Verwalten der Beibehaltung von Verlaufsdaten in temporalen Tabellen mit Systemversionsverwaltung](../../relational-databases/tables/manage-retention-of-historical-data-in-system-versioned-temporal-tables.md)
- [Temporale Tabellen mit Systemversionsverwaltung und speicheroptimierten Tabellen](../../relational-databases/tables/system-versioned-temporal-tables-with-memory-optimized-tables.md)
- [Erstellen einer temporalen Tabelle mit Systemversionsverwaltung](../../relational-databases/tables/creating-a-system-versioned-temporal-table.md)
- [Ändern von Daten in einer temporalen Tabelle mit Systemversionsverwaltung](../../relational-databases/tables/modifying-data-in-a-system-versioned-temporal-table.md)
- [Abfragen von Daten in einer temporalen Tabelle mit Systemversionsverwaltung](../../relational-databases/tables/querying-data-in-a-system-versioned-temporal-table.md)
- [Ändern vom Schema einer versionsverwalteten temporalen Tabelle](../../relational-databases/tables/changing-the-schema-of-a-system-versioned-temporal-table.md)
