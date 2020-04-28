---
title: Funktions Wechsel
description: Zeigt Informationen zu den zwei Funktions Switches an, die in Analytics Platform System AU7 eingeführt wurden.
author: mzaman1
ms.prod: sql
ms.technology: data-warehouse
ms.topic: conceptual
ms.date: 06/27/2018
ms.author: murshedz
ms.reviewer: martinle
monikerRange: '>= aps-pdw-2016-au7 || = sqlallproducts-allversions'
ms.openlocfilehash: 8642f27a329da8819acf0ab99a648c4979ed40d0
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/27/2020
ms.locfileid: "74401455"
---
# <a name="appliance-feature-switches"></a>Geräte Funktions Schalter

Auf der Seite " **Funktions Wechsel** " werden Informationen zu den Funktions Schaltern angezeigt, die in Analytics Platform System AU7 und höher eingeführt werden. Verwenden Sie diese Konfigurationsseite, um Features und Einstellungen in Analytics Platform System zu aktualisieren oder zu aktivieren bzw. zu deaktivieren.

> [!NOTE]
> Änderungen an Funktions switchwerten erfordern einen Neustart des Dienstanbieter.

![Funktions Schalter der dwconfig-Appliance](media/feature-switch/SQL_Server_PDW_DWConfig_feature_switch.png "Funktions Schalter der dwconfig-Appliance")

## <a name="autostatsenabled"></a>Autostatus Abled

Steuert die Funktion zur automatischen Statistik. Dieser Funktions Wechsel wird standardmäßig nach dem Upgrade auf AU7 auf true festgelegt. Jede Datenbank, die nach dem Upgrade erstellt wird, erbt die automatische Erstellung und das asynchrone Update der Statistiken. Bei vorhandenen Datenbanken können Datenbankadministratoren automatische Statistiken mit [ALTER DATABASE (Parallel Data Warehouse)](../t-sql/statements/alter-database-transact-sql.md?tabs=sqlpdw)aktivieren. Weitere Informationen zu Statistiken finden Sie unter [Statistics](../relational-databases/statistics/statistics.md).

## <a name="maxdopforinsertqueries"></a>Maxdopforinsertqueries

Ermöglicht das Auswählen von MAXDOP-Einstellungen größer als 1 für INSERT/SELECT-Vorgänge. Optionen für diese Einstellung sind 0, 1, 2 und 4. der Standardwert ist 1.

## <a name="optimizecommonsubexpressions"></a>Optimizecommonsubexausdrucks

Verbessert die Abfrageleistung, da die Daten Verschiebung für einen allgemeinen Teil Ausdruck im SQL-Abfrageoptimierer eliminiert wird. Ausführliche Erläuterungen zu diesem Feature finden Sie [hier](common-sub-expression-elimination.md).

## <a name="usecatalogqueries"></a>Usecatalogqueries

Die Verwendung von Katalog Objekten für einige Metadatenaufrufe anstelle der Verwendung von SMO hat eine Leistungsverbesserung gezeigt. Standardmäßig auf true festgelegt ist, steuert dieser Switch dieses Verhalten.

## <a name="dmsprocessstopmessagetimeoutinseconds"></a>Dmsprocessstopmessagetimeoutinseconds

Steuert, wie lange der Daten Verschiebungs Dienst (DMS) auf ein ausgelasteter System synchronisiert, wenn eine Abfrage mit Daten Verschiebungen abgebrochen wird. Wenn Sie auf AU7 aktualisieren, wird dieser Wert standardmäßig auf 900 Sekunden (15 Minuten) festgelegt. Der gültige Bereich ist 0-3600 Sekunden.
