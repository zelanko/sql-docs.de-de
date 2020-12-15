---
title: Automatische Statistik
description: Beschreibt die Funktion "Automatische Statistik" in Analytics Platform System AU7.
author: mzaman1
ms.prod: sql
ms.technology: data-warehouse
ms.topic: conceptual
ms.date: 06/27/2018
ms.author: murshedz
ms.reviewer: martinle
ms.custom: seo-dt-2019
monikerRange: '>= aps-pdw-2016-au7'
ms.openlocfilehash: fc204c5c4fd37ef4621c4376142662b7a9164ade
ms.sourcegitcommit: 1a544cf4dd2720b124c3697d1e62ae7741db757c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/14/2020
ms.locfileid: "97420187"
---
# <a name="configure-auto-statistics"></a>Automatische Statistik konfigurieren

Erfahren Sie, wie Sie parallele Data Warehouse konfigurieren, um automatische Statistiken zum automatischen Erstellen und Aktualisieren von Statistiken zu verwenden.  Verwenden Sie diese Funktion, um Abfrage Pläne zu verbessern und so die Abfrageleistung zu verbessern.

**Gilt für:** APS (beginnend mit 2016-AU7)

## <a name="what-are-statistics"></a>Was sind Statistiken?
Statistiken zur Abfrageoptimierung sind Objekte, die statistische Informationen über die Verteilung von Werten in einer oder mehreren Spalten einer Tabelle enthalten. Der Abfrageoptimierer verwendet diese Statistiken, um die Kardinalität oder Anzahl von Zeilen im Abfrageergebnis zu schätzen. Diese Kardinalitätsschätzungen ermöglichen es dem Abfrageoptimierer, einen hochwertigen Abfrageplan zu erstellen. Beispielsweise verwendet der MPP-Abfrageoptimierer in APS Kardinalitätsschätzungen, um die kleinere von zwei Tabellen, die in einer Join-Klausel verwendet werden, zu mischen oder zu replizieren und dadurch die Abfrageleistung zu verbessern.  Weitere Informationen finden Sie unter [Statistiken](../relational-databases/statistics/statistics.md) und [DBCC SHOW_STATISTICS](../t-sql/database-console-commands/dbcc-show-statistics-transact-sql.md)

## <a name="what-are-auto-statistics"></a>Was sind automatische Statistiken?
Die automatische Statistik ist eine Statistik, die der Abfrageoptimierer erstellt und automatisch aktualisiert, um den Abfrageplan zu verbessern. Statistiken können nach Lade-, Einfügungs-, Aktualisierungs-und Lösch Vorgängen veraltet sein. Ohne automatische Statistik müssen Sie eine eigene Analyse durchführen, um zu verstehen, welche Spalten Statistiken benötigen und wann die Statistiken aktualisiert werden müssen.

Die automatische Statistik umfasst die folgenden drei Einstellungen: 

### <a name="auto_create_statistics"></a>AUTO_CREATE_STATISTICS
Ist die Option AUTO_CREATE_STATISTICS zum automatischen Erstellen von Statistiken aktiviert, erstellt der Abfrageoptimierer nach Bedarf Statistiken für einzelne Spalten im Abfrageprädikat, um Kardinalitätsschätzungen für den Abfrageplan zu verbessern. Diese Statistiken für einzelne Spalten werden für Spalten erstellt, die noch nicht über ein Histogramm in einem vorhandenen Statistikobjekt verfügen.

### <a name="auto_update_statistics"></a>AUTO_UPDATE_STATISTICS 
Wenn die AUTO_UPDATE_STATISTICS-Option zur automatischen Aktualisierung von Statistiken aktiviert ist, stellt der Abfrageoptimierer fest, wann Statistiken veraltet sein könnten, und aktualisiert diese Statistiken, sobald sie von einer Abfrage verwendet werden. Statistiken sind veraltet, wenn die Datenverteilung in der Tabelle oder indizierten Sicht durch die Vorgänge INSERT, UPDATE, DELETE oder MERGE geändert wurde. Der Abfrageoptimierer stellt fest, wann Statistiken veraltet sein könnten, indem er die Anzahl der Datenänderungen seit des letzten Statistikupdates ermittelt und sie mit einem Schwellenwert vergleicht. Der Schwellenwert basiert auf der Anzahl von Zeilen in der Tabelle oder indizierten Sicht.

### <a name="auto_update_statistics_async"></a>AUTO_UPDATE_STATISTICS_ASYNC
Mit der AUTO_UPDATE_STATISTICS_ASYNC-Option für die asynchrone Statistikaktualisierung wird festgelegt, ob der Abfrageoptimierer die synchrone oder asynchrone Statistikaktualisierung verwendet. Für APS ist die Option für die asynchrone Statistik Aktualisierung standardmäßig aktiviert, und der Abfrageoptimierer aktualisiert Statistiken asynchron. Die Option AUTO_UPDATE_STATISTICS_ASYNC gilt für Statistikobjekte, die für Indizes, einzelne Spalten in Abfrageprädikaten und mit der CREATE STATISTICS-Anweisung generierte Statistiken erstellt wurden.

## <a name="configuration-settings-for-system-administrators"></a>Konfigurationseinstellungen für System Administratoren
Nach dem Upgrade auf APS AU7 ist die automatische Statistik standardmäßig aktiviert. Der Systemadministrator kann die automatische Statistik mit der Option " [Feature Switch](appliance-feature-switch.md) " in der Appliance Configuration Manager aktivieren oder deaktivieren.  Sobald die Benutzer aktiviert sind, können Sie die Statistik Einstellungen pro Datenbank ändern.
Zum Ändern von Funktions switchwerten ist ein Neustart des Dienstanbieter für APS erforderlich.

## <a name="change-auto-statistics-settings-on-a-database"></a>Ändern der Einstellungen für die automatische Statistik in einer Datenbank
Wenn die automatische Statistik vom Systemadministrator aktiviert wird, können Sie [ALTER DATABASE (Parallel Data Warehouse)](../t-sql/statements/alter-database-transact-sql.md?tabs=sqlpdw) verwenden, um die Statistik Einstellungen für eine Datenbank zu ändern. Wenn der Systemadministrator die Funktion "Automatische Statistik Funktion" aktiviert, werden für alle neuen Datenbanken, die nach dem Upgrade auf AU7 erstellt werden, automatische Statistiken aktiviert. Für alle Datenbanken, die vor dem Upgrade auf AU7 vorhanden waren, ist die automatische Statistik deaktiviert. Im folgenden Beispiel wird die automatische Statistik in der vorhandenen Datenbank mypdw aktiviert.

```sql
ALTER DATABASE myPDW SET AUTO_CREATE_STATISTICS ON
ALTER DATABASE myPDW SET AUTO_UPDATE_STATISTICS ON 
ALTER DATABASE myPDW SET AUTO_UPDATE_STATISTICS_ASYNC ON
```
 
AUTO_UPDATE STATISTICS_ASYNC Option funktioniert nur, wenn AUTO_UPDATE_STATISTICS aktiviert ist.  Aus diesem Grund werden Statistiken nicht aktualisiert, wenn AUTO_UPDATE_STATISTICS deaktiviert ist und AUTO_UPDATE_STATISTICS_ASYNC auf on. 

### <a name="error-messages"></a>Fehlermeldungen
Sie erhalten die Fehlermeldung "diese Option wird in PDW nicht unterstützt".  Dieser Fehler tritt auf, wenn der Systemadministrator die automatische Statistik nicht aktiviert hat und Sie versuchen, die Optionen für die automatische Statistik in ALTER DATABASE festzulegen. 

### <a name="limitations-and-restrictions"></a>Einschränkungen
Automatische Statistiken können nicht für externe Tabellen verwendet werden. 

### <a name="check-the-current-values"></a>Überprüfen der aktuellen Werte
Die folgende Abfrage gibt die aktuellen Werte der Einstellungen für die automatische Statistik für alle Datenbanken zurück.

```sql
SELECT NAME
    , IS_AUTO_CREATE_STATS_ON 
    , IS_AUTO_UPDATE_STATS_ON
    , IS_AUTO_UPDATE_STATS_ASYNC_ON
FROM
    sys.databases;
```

Der Rückgabewert 1 bedeutet, dass die Einstellung auf ON festgelegt ist, und 0 bedeutet, dass die Einstellung auf OFF festgelegt ist. 

## <a name="next-steps"></a>Nächste Schritte
Informationen zur Leistung Ihrer Abfragen finden Sie unter über [Wachen aktiver Abfragen](monitoring-active-queries.md) .
