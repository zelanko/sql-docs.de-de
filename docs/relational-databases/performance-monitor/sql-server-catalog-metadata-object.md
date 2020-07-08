---
title: SQL Server:Catalog Metadata-Objekt | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: performance
ms.topic: conceptual
helpviewer_keywords:
- SQLServer:Catalog Metadata
ms.assetid: 665e63e6-4bd2-4091-92a5-327364db2f8d
author: julieMSFT
ms.author: jrasnick
ms.openlocfilehash: 5c8b74e6647422231f0ace765f57579bb3ea2b84
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/01/2020
ms.locfileid: "85656176"
---
# <a name="sql-server-catalog-metadata-object"></a>SQLServer:Catalog Metadata-Objekt
 [!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]
Das **SQLServer:Catalog Metadata** Leistungsobjekt enthält Leistungsindikatoren für Katalogmetadaten für SQL Server.

In der folgenden Tabelle sind die **Catalog Metadata** .


|**SQLServer Catalog Metadata-Leistungsindikatoren**|BESCHREIBUNG|  
|-------------|-----------------|  
|**Anzahl der Cacheeinträge**|Die Anzahl der Einträge im Katalogmetadaten-Cache.|
|**Anzahl der fixierten Cacheeinträge**|Anzahl der Einträge im Katalogmetadaten-Cache, die fixiert sind.|
|**Cachetrefferquote**|Quote zwischen den Treffern im Katalogmetadaten-Cache und den Suchvorgängen.|
|**Basis für Cachetrefferquote**|Nur zur internen Verwendung.|

Es gibt eine Instanz des Leistungsindikators für jede Datenbank.

## <a name="see-also"></a>Weitere Informationen  
[Überwachen der Ressourcenverwendung (Systemmonitor)](../../relational-databases/performance-monitor/monitor-resource-usage-system-monitor.md)
