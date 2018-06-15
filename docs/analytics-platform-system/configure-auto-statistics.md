---
title: Statistiken automatisch (Analytics Platform System)
description: Beschreibt die automatische Statistikfunktion Analytics Platform System AU7 eingeführt.
author: mzaman1
manager: craigg
ms.prod: sql
ms.technology: data-warehouse
ms.topic: conceptual
ms.date: 04/24/2018
ms.author: murshedz
ms.reviewer: martinle
ms.openlocfilehash: 1c0f4623adad35ab874330b42aa54f6e1b91d961
ms.sourcegitcommit: fc3cd23685c6b9b6972d6a7bab2cc2fc5ebab5f2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/25/2018
ms.locfileid: "34550908"
---
# <a name="configure-auto-statistics"></a>Statistiken automatisch konfigurieren

Informationen Sie zum Konfigurieren von Parallel Data Warehouse Verwendung Statistiken automatisch für das Erstellen und Aktualisieren von Statistiken automatisch.  Diese Funktion verwenden, um Abfragepläne zu verbessern, und aus diesem Grund die abfrageleistung.

**Gilt für:** APS (beginnend mit AU7)

## <a name="what-are-statistics"></a>Was sind Statistiken?
Statistiken zur abfrageoptimierung sind Objekte, die statistische Informationen über die Verteilung der Werte in einer oder mehreren Spalten einer Tabelle enthalten. Der Abfrageoptimierer verwendet diese Statistiken, die Kardinalität geschätzt, oder führen die Anzahl von Zeilen in der Abfrage. Diese kardinalitätsschätzungen aktivieren den Abfrageoptimierer, einen hochwertigen Abfrageplan zu erstellen. Beispielsweise können in APS die abfrageleistung der MPP Abfrageoptimierer verwendet, die kardinalitätsschätzung um zufällige weitergeleitet oder repliziert die kleinere von zwei Tabellen in einer Join-Klausel und in diesem Fall verwendet werden sollen.  Weitere Informationen finden Sie unter [Statistiken](../relational-databases/statistics/statistics.md) und [DBCC SHOW_STATISTICS](../t-sql/database-console-commands/dbcc-show-statistics-transact-sql.md)

## <a name="what-are-auto-statistics"></a>Was sind Statistiken automatisch?
Statistiken automatisch sind Statistiken, die der Abfrageoptimierer erstellt und automatisch aktualisiert, um den Abfrageplan zu verbessern. Statistiken können nicht aktualisiert werden, nach lädt, eingefügt, aktualisiert und Löschvorgänge. Ohne automatische Statistiken müssen Sie führen Sie eigene Analysen, um zu verstehen, welche Spalten Statistiken benötigen, und wenn die Statistiken aktualisiert werden müssen.

Statistiken automatisch umfasst die folgenden drei Einstellungen: 

### <a name="autocreatestatistics"></a>AUTO_CREATE_STATISTICS
Wenn Statistikoption zum automatischen erstellen, AUTO_CREATE_STATISTICS auf ON festgelegt ist, erstellt der Abfrageoptimierer Statistiken für einzelne Spalten im Abfrageprädikat, nach Bedarf, um kardinalitätsschätzungen für den Abfrageplan zu verbessern. Diese Statistiken für einzelne Spalten werden für Spalten erstellt, die noch nicht über ein Histogramm in einem vorhandenen Statistikobjekt verfügen.

### <a name="autoupdatestatistics"></a>AUTO_UPDATE_STATISTICS 
Wenn die AUTO_UPDATE_STATISTICS-Option zur automatischen Aktualisierung von Statistiken aktiviert ist, stellt der Abfrageoptimierer fest, wann Statistiken veraltet sein könnten, und aktualisiert diese Statistiken, sobald sie von einer Abfrage verwendet werden. Statistiken sind veraltet, wenn die Vorgänge insert, update, löschen oder zusammenführen, ändern die Verteilung der Daten in der Tabelle oder indizierten Sicht. Der Abfrageoptimierer stellt fest, wann Statistiken veraltet sein könnten, indem er die Anzahl der Datenänderungen seit des letzten Statistikupdates ermittelt und sie mit einem Schwellenwert vergleicht. Der Schwellenwert basiert auf der Anzahl von Zeilen in der Tabelle oder indizierten Sicht.

### <a name="autoupdatestatisticsasync"></a>AUTO_UPDATE_STATISTICS_ASYNC
Mit der AUTO_UPDATE_STATISTICS_ASYNC-Option für die asynchrone Statistikaktualisierung wird festgelegt, ob der Abfrageoptimierer die synchrone oder asynchrone Statistikaktualisierung verwendet. Option für das asynchrone statistikupdate ist standardmäßig für APS, und der Abfrageoptimierer Statistiken asynchron aktualisiert. Die AUTO_UPDATE_STATISTICS_ASYNC-Option gilt für statistikobjekte, die für Indizes, einzelne Spalten in Abfrageprädikaten und die Statistiken, die mit der CREATE STATISTICS-Anweisung erstellt.

## <a name="configuration-settings-for-system-administrators"></a>Konfigurationseinstellungen für Systemadministratoren
Nach dem Upgrade auf APS AU7, ist die Statistiken automatisch standardmäßig aktiviert. Der Systemadministrator kann aktivieren oder deaktivieren Sie automatische Statistik mit der [Funktionsschalter](appliance-feature-switch.md) Option im Appliance Konfigurations-Manager.  Nach der Aktivierung können Benutzer die Einstellungen der Treiberstatistik pro Datenbank ändern.
Ändern alle Werte der Feature-Switch erfordert einen Neustart des Diensts auf APS.

## <a name="change-auto-statistics-settings-on-a-database"></a>Ändern der Einstellungen der automatischen Statistik für eine Datenbank
Wenn Statistiken automatisch vom Systemadministrator aktiviert ist, können Sie [ALTER DATABASE (Parallel Data Warehouse)](/sql/t-sql/statements/alter-database-parallel-data-warehouse) so ändern Sie die Einstellungen der Treiberstatistik in einer Datenbank. Wenn automatische Statistik Feature-Switch vom Systemadministrator aktiviert ist, müssen alle neuen Datenbanken, die nach dem Upgrade auf AU7 erstellt Statistiken für automatisch aktiviert. Automatische Statistik deaktiviert haben alle Datenbanken, die vor dem Upgrade auf AU7 vorhanden waren. Im folgenden Beispiel wird die Statistiken auf der vorhandenen Datenbank MyPDW automatisch.

```sql
ALTER DATABASE myPDW SET AUTO_CREATE_STATISTICS ON
ALTER DATABASE myPDW SET AUTO_UPDATE_STATISTICS ON 
ALTER DATABASE myPDW SET AUTO_UPDATE_STATISTICS_ASYNC ON
```
 
AUTO_UPDATE STATISTICS_ASYNC Option funktioniert nur, wenn AUTO_UPDATE_STATISTICS auf ON festgelegt ist.  Aus diesem Grund Statistiken werden nicht aktualisiert, wenn AUTO_UPDATE_STATISTICS auf OFF festgelegt ist und AUTO_UPDATE_STATISTICS_ASYNC ist ON. 

### <a name="error-messages"></a>Fehlermeldungen
Sie können die Fehlermeldung "Diese Option wird in PDW nicht unterstützt".  Dieser Fehler tritt auf, wenn der Systemadministrator hat keine Statistiken automatisch aktiviert, und Sie versuchen, eine von "Auto" die Optionen für Ausführungsstatistiken unter ALTER DATABASE festgelegt. 

### <a name="limitations-and-restrictions"></a>Einschränkungen
Statistiken automatisch funktioniert nicht in externen Tabellen. 

### <a name="check-the-current-values"></a>Überprüfen Sie die aktuellen Werte
Die folgende Abfrage gibt die aktuellen Werte von den Einstellungen der automatischen Statistik für alle Datenbanken zurück.

```sql
SELECT NAME
    , IS_AUTO_CREATE_STATS_ON 
    , IS_AUTO_UPDATE_STATS_ON
    , IS_AUTO_UPDATE_STATS_ASYNC_ON
FROM
    sys.databases;
```

Ein Rückgabewert von 1 bedeutet, dass die Einstellung ist, und 0 bedeutet, dass die Einstellung deaktiviert ist. 

## <a name="next-steps"></a>Nächste Schritte
Wie Ihre Abfragen durchführen, finden Sie unter [aktive Abfragen Überwachung](monitoring-active-queries.md)
