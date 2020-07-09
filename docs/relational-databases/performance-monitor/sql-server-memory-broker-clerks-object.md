---
title: SQL Server, Speicherbrokerclerks (Objekt) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: performance
ms.topic: conceptual
helpviewer_keywords:
- SQLServer:Memory Broker Clerks
ms.assetid: 47b9c236-66a3-4c42-97ee-da5555bdc046
author: julieMSFT
ms.author: jrasnick
ms.openlocfilehash: 5a14877c98b4abb2487712cfed2bd744c20933d2
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/01/2020
ms.locfileid: "85775813"
---
# <a name="sql-server-memory-broker-clerks-object"></a>SQLServer, Speicherbrokerclerks (Objekt)
 [!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]
Das Leistungsobjekt **SQLServer: Speicherbrokerclerks** enthält Leistungsindikatoren für Statistiken zu Speicherbrokerclerks.

In der folgenden Tabelle werden die SQL Server-Leistungsobjekte für **Speicherbrokerclerks** beschrieben.

|**SQL Server-Speicherbrokerclerks (Leistungsindikatoren)**|BESCHREIBUNG|  
|-------------|-----------------|  
|**Interner Nutzen**|Der interne Wert des Arbeitsspeichers für eine unzureichende Eintragsanzahl (in ms pro Seite pro ms) multipliziert mit 10 Milliarden und auf eine ganze Zahl gekürzt.|
|**Größe des Speicherbrokerclerks**|Die Clerkgröße in Seiten.|
|**Periodische Entfernungsvorgänge (Seiten)**|Die Anzahl der durch den letzten periodischen Entfernungsvorgang aus dem Brokerclerk entfernten Seiten.|
|**Überlastungsentfernungsvorgänge (Seiten/Sekunde)**|Die Anzahl der Seiten pro Sekunde, die aufgrund unzureichenden Arbeitsspeichers aus dem Brokerclerk entfernt wurden.|
|**Simulationsnutzen**|Der Wert des Arbeitsspeichers für den Clerk (in ms pro Seite pro ms) multipliziert mit 10 Milliarden und auf eine ganze Zahl gekürzt.|
|**Simulationsgröße**|Die aktuelle Größe der Clerksimulation in Seiten.|

Es gibt eine Instanz des Indikators für den Pufferpool und für den Objektpool des Spaltenspeichers.

## <a name="see-also"></a>Weitere Informationen  
[Überwachen der Ressourcenverwendung (Systemmonitor)](../../relational-databases/performance-monitor/monitor-resource-usage-system-monitor.md)
