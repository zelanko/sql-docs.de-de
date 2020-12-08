---
title: SQL Server:Catalog Metadata-Objekt | Microsoft-Dokumentation
description: Informationen zum „SQLServer:Catalog Metadata“-Leistungsobjekt, das Leistungsindikatoren für Katalogmetadaten für SQL Server bereitstellt.
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
author: WilliamDAssafMSFT
ms.author: wiassaf
ms.openlocfilehash: a02c8d6253df487ebf5c01c8658f448ec680022c
ms.sourcegitcommit: 0e0cd9347c029e0c7c9f3fe6d39985a6d3af967d
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 12/02/2020
ms.locfileid: "96505814"
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
