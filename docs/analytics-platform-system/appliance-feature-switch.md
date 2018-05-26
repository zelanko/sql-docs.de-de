---
title: Feature-Switch (Analytics Platform System)
description: Zeigt Informationen zu den zwei funktionsschalter, die in Analytics Platform System AU7 eingeführt werden.
author: mzaman1
manager: craigg
ms.prod: sql
ms.technology: data-warehouse
ms.topic: conceptual
ms.date: 04/24/2018
ms.author: murshedz
ms.reviewer: martinle
ms.openlocfilehash: e384a252584fed0e7543a7a4000fc9a70f6533e7
ms.sourcegitcommit: fc3cd23685c6b9b6972d6a7bab2cc2fc5ebab5f2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/25/2018
---
#<a name="appliance-feature-switch"></a>Appliance-Feature-Switch
Die **Funktionsschalter** Seite Informationen zu den zwei funktionsschalter, die eingeführt werden in Analytics Platform System AU7 angezeigt. Verwenden Sie diese Seite zu aktualisieren oder zu aktivieren/deaktivieren von Funktionen und Einstellungen in Analytics Platform System. Ändern von Werten für Funktion Switch erfordert einen Neustart des Diensts.

![Appliance-Funktionsschalter DWConig](media/feature-switch/SQL_Server_PDW_DWConfig_feature_switch.png "DWConig Appliance Feature-Switch") 

##<a name="autostatsenabled-switch"></a>AutoStatsEnabled Switch
Steuert die automatische Statistikfunktion an. Dieses Feature-Switch wird festgelegt wird standardmäßig nach dem Upgrade auf AU7 "true". Eine Datenbank erstellt, die nach dem Upgrade wird die automatische Erstellung und asynchronen Aktualisieren von Statistiken erben. Bei vorhandenen Datenbanken können Datenbankadministratoren können Statistiken mit automatisch aktivieren [alter Database] (/ sql/t-sql/statements/alter-database-parallel-data-warehouse). Weitere Informationen zu Statistiken finden Sie unter [Statistiken](../relational-databases/statistics/statistics.md).

##<a name="dmsprocessstopmessagetimeoutinseconds-switch"></a>DmsProcessStopMessageTimeoutInSeconds Switch
Steuert die Zeit, die Daten Bewegung Service (DMS) wartet auf einem ausgelasteten System synchronisiert werden soll, wenn eine Abfrage, die im Zusammenhang mit der datenverschiebung abgebrochen wird. Aktualisieren auf AU7 wird standardmäßig dieser Wert auf 900 Sekunden (15 Minuten). Der gültige Bereich ist 0 bis 3600 Sekunden.
