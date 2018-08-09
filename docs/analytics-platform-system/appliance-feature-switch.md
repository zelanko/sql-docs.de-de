---
title: Feature-Switch (Analytics Platform System)
description: Zeigt Informationen zu den zwei Features, die in Analytics Platform System AU7 eingeführt werden.
author: mzaman1
manager: craigg
ms.prod: sql
ms.technology: data-warehouse
ms.topic: conceptual
ms.date: 06/27/2018
ms.author: murshedz
ms.reviewer: martinle
monikerRange: '>= aps-pdw-2016-au7 || = sqlallproducts-allversions'
ms.openlocfilehash: d9657b1433b0647d7165cb427da6333c0a325583
ms.sourcegitcommit: 0cda14b1151d9bce1253d96dea038c038484f07a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/08/2018
ms.locfileid: "39400923"
---
#<a name="appliance-feature-switch"></a>Appliance-Feature-Switch
Die **Featureschalter** Seite werden Informationen zu den zwei Features, die eingeführt werden in Analytics Platform System 2016-AU7 angezeigt. Mithilfe dieser Seite zu aktualisieren oder zu aktivieren/deaktivieren Features und Einstellungen in Analytics Platform System. Ändern von Werten der Feature-Switch erfordert einen Neustart des Diensts.

![Appliance-Feature-Switch DWConig](media/feature-switch/SQL_Server_PDW_DWConfig_feature_switch.png "DWConig Appliance-Feature-Switch") 

##<a name="autostatsenabled-switch"></a>AutoStatsEnabled Switch
Steuert das statistikfeature automatisch. Dieses Feature-Switch nastaven NA hodnotu True, wird standardmäßig nach dem Upgrade auf AU7. Alle nach dem Upgrade erstellte Datenbank übernimmt die automatische Erstellung und asynchronen Aktualisieren von Statistiken. Datenbankadministratoren können für vorhandene Datenbanken automatisch Statistiken mit [ALTER DATABASE (Parallel Data Warehouse)](../t-sql/statements/alter-database-transact-sql.md?tabs=sqlpdw). Weitere Informationen zu Statistiken finden Sie unter [Statistiken](../relational-databases/statistics/statistics.md).

##<a name="dmsprocessstopmessagetimeoutinseconds-switch"></a>DmsProcessStopMessageTimeoutInSeconds Switch
Steuert die Zeit, die Data Movement Service (DMS) wartet auf einem ausgelasteten System synchronisiert werden soll, wenn eine Abfrage, die im Zusammenhang mit der datenverschiebung abgebrochen wird. Aktualisieren auf AU7 wird standardmäßig dieser Wert auf 900 Sekunden (15 Minuten). Der gültige Bereich ist 0 bis 3.600 Sekunden.
