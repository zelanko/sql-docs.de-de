---
title: Automatische Statistiken (Analytics Platform System)
description: Beschreibt Statistiken-Funktion automatisch in Analytics Platform System AU7 eingeführt.
author: mzaman1
manager: craigg
ms.prod: sql
ms.technology: data-warehouse
ms.topic: conceptual
ms.date: 06/27/2018
ms.author: murshedz
ms.reviewer: martinle
monikerRange: '>= aps-pdw-2016-au7 || = sqlallproducts-allversions'
ms.openlocfilehash: e48d40d78c25431fd6e5592dacfa410723b31f82
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "63057063"
---
# <a name="configure-auto-statistics"></a>Statistiken automatisch konfigurieren

Informationen Sie zum Konfigurieren von Parallel Data Warehouse, um Statistiken automatisch für das Erstellen und Aktualisieren von Statistiken automatisch verwenden.  Verwenden Sie diese Funktion, um Abfragepläne zu verbessern, und aus diesem Grund die verbessern Sie abfrageleistung zu.

**Gilt für:** APS (beginnend mit 2016-AU7)

## <a name="what-are-statistics"></a>Was sind Statistiken?
Statistiken zur abfrageoptimierung sind Objekte, die statistische Informationen über die Verteilung der Werte in einer oder mehreren Spalten einer Tabelle enthalten. Die Abfrageoptimierer verwendet diese Statistiken, um die Kardinalität geschätzt, oder die Anzahl von Zeilen in der Abfrage führen. Diese kardinalitätsschätzungen ermöglichen den Abfrageoptimierer, einen hochwertigen Abfrageplan zu erstellen. Als Beispiel, in der APS abfrageleistung die MPP Abfrage der Abfrageoptimierer verwendet, die Kardinalität geschätzt wird, um auszuwählen, die zufällige oder replizieren die kleinere von zwei Tabellen, die in einer Join-Klausel und auf diese Weise verwendet.  Weitere Informationen finden Sie unter [Statistiken](../relational-databases/statistics/statistics.md) und [DBCC SHOW_STATISTICS](../t-sql/database-console-commands/dbcc-show-statistics-transact-sql.md)

## <a name="what-are-auto-statistics"></a>Was sind Statistiken automatisch?
Statistiken automatisch sind Statistiken, die die Abfrageoptimierer erstellt und wird automatisch aktualisiert, um den Abfrageplan zu verbessern. Statistiken können veralten nach Ladevorgängen, eingefügt, aktualisiert und Löschvorgänge. Ohne automatische Statistiken müssen Sie eine eigene Analyse, um zu verstehen, welche Spalten Statistiken benötigen, und wenn die Statistiken aktualisiert werden müssen.

Statistiken automatisch umfasst die folgenden drei Einstellungen: 

### <a name="autocreatestatistics"></a>AUTO_CREATE_STATISTICS
Ist die Option AUTO_CREATE_STATISTICS zum automatischen Erstellen von Statistiken aktiviert, erstellt der Abfrageoptimierer nach Bedarf Statistiken für einzelne Spalten im Abfrageprädikat, um Kardinalitätsschätzungen für den Abfrageplan zu verbessern. Diese Statistiken für einzelne Spalten werden für Spalten erstellt, die noch nicht über ein Histogramm in einem vorhandenen Statistikobjekt verfügen.

### <a name="autoupdatestatistics"></a>AUTO_UPDATE_STATISTICS 
Wenn die AUTO_UPDATE_STATISTICS-Option zur automatischen Aktualisierung von Statistiken aktiviert ist, stellt der Abfrageoptimierer fest, wann Statistiken veraltet sein könnten, und aktualisiert diese Statistiken, sobald sie von einer Abfrage verwendet werden. Statistiken sind veraltet, wenn die Datenverteilung in der Tabelle oder indizierten Sicht durch die Vorgänge INSERT, UPDATE, DELETE oder MERGE geändert wurde. Der Abfrageoptimierer stellt fest, wann Statistiken veraltet sein könnten, indem er die Anzahl der Datenänderungen seit des letzten Statistikupdates ermittelt und sie mit einem Schwellenwert vergleicht. Der Schwellenwert basiert auf der Anzahl von Zeilen in der Tabelle oder indizierten Sicht.

### <a name="autoupdatestatisticsasync"></a>AUTO_UPDATE_STATISTICS_ASYNC
Mit der AUTO_UPDATE_STATISTICS_ASYNC-Option für die asynchrone Statistikaktualisierung wird festgelegt, ob der Abfrageoptimierer die synchrone oder asynchrone Statistikaktualisierung verwendet. Für Zugriffspunkte die Option für das asynchrone statistikupdate ist standardmäßig aus, und der Abfrageoptimierer Statistiken asynchron aktualisiert. Die Option AUTO_UPDATE_STATISTICS_ASYNC gilt für Statistikobjekte, die für Indizes, einzelne Spalten in Abfrageprädikaten und mit der CREATE STATISTICS-Anweisung generierte Statistiken erstellt wurden.

## <a name="configuration-settings-for-system-administrators"></a>Konfigurationseinstellungen für Systemadministratoren
Nach dem Upgrade der Zugriffspunkte AU7 – ist die Statistiken automatisch standardmäßig aktiviert. Der Systemadministrator kann aktivieren oder deaktivieren Sie automatische Statistiken mit der [Featureschalter](appliance-feature-switch.md) Option in der Appliance Configuration Manager.  Nach der Aktivierung können Benutzer die statistikeinstellungen pro Datenbank ändern.
Ändern alle Werte der Feature-Switch erfordert einen Neustart des Diensts für Zugriffspunkte.

## <a name="change-auto-statistics-settings-on-a-database"></a>Ändern der Einstellungen für automatische Statistiken für eine Datenbank
Wenn Statistiken automatisch vom Systemadministrator aktiviert ist, können Sie [ALTER DATABASE (Parallel Data Warehouse)](../t-sql/statements/alter-database-transact-sql.md?tabs=sqlpdw) die statistikeinstellungen für eine Datenbank zu ändern. Wenn vom Systemadministrator automatische Statistiken featureschalter aktiviert ist, müssen alle neuen Datenbanken, die nach dem Upgrade auf AU7 erstellt Statistiken für automatisch aktiviert. Haben alle Datenbanken, die vor dem Upgrade auf AU7 vorhanden waren automatische Statistik deaktiviert. Im folgenden Beispiel wird die Statistiken auf der vorhandenen Datenbank MyPDW automatisch.

```sql
ALTER DATABASE myPDW SET AUTO_CREATE_STATISTICS ON
ALTER DATABASE myPDW SET AUTO_UPDATE_STATISTICS ON 
ALTER DATABASE myPDW SET AUTO_UPDATE_STATISTICS_ASYNC ON
```
 
AUTO_UPDATE STATISTICS_ASYNC Option funktioniert nur auf, wenn AUTO_UPDATE_STATISTICS auf ON festgelegt ist.  Aus diesem Grund Statistiken werden nicht aktualisiert, wenn AUTO_UPDATE_STATISTICS auf OFF festgelegt ist und AUTO_UPDATE_STATISTICS_ASYNC ist ON. 

### <a name="error-messages"></a>Fehlermeldungen
Sie können die Fehlermeldung "Diese Option wird in PDW nicht unterstützt".  Dieser Fehler tritt auf, wenn der Systemadministrator hat keine Statistiken automatisch aktiviert, und Sie versuchen, eine automatisch in der ALTER DATABASE-Optionen für Ausführungsstatistiken festlegen. 

### <a name="limitations-and-restrictions"></a>Einschränkungen
Statistiken automatisch funktioniert nicht für externe Tabellen. 

### <a name="check-the-current-values"></a>Überprüfen Sie die aktuellen Werte
Die folgende Abfrage gibt die aktuellen Werte der Einstellungen für die automatische Statistiken für alle Datenbanken.

```sql
SELECT NAME
    , IS_AUTO_CREATE_STATS_ON 
    , IS_AUTO_UPDATE_STATS_ON
    , IS_AUTO_UPDATE_STATS_ASYNC_ON
FROM
    sys.databases;
```

Ein Rückgabewert 1 bedeutet, dass die Einstellung ist, und 0 bedeutet, dass diese Einstellung deaktiviert ist. 

## <a name="next-steps"></a>Nächste Schritte
Leistung von Abfragen finden Sie unter [überwachen aktiver Abfragen](monitoring-active-queries.md)
