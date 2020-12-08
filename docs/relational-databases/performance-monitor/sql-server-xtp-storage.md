---
title: SQL Server-XTP-Speicher | Microsoft-Dokumentation
description: Hier lernen Sie das Leistungsobjekt „SQL Server-XTP-Speicher“ kennen, das Leistungsindikatoren enthält, die sich auf die Speicherung auf Datenträger für In-Memory-OLTP in SQL Server beziehen.
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: performance
ms.topic: conceptual
ms.assetid: 4070580b-880d-4f4c-abcc-626a4fe0c9a2
author: WilliamDAssafMSFT
ms.author: wiassaf
ms.openlocfilehash: a12431a679ddbe4f47697b181c81ed3b7b3f08f3
ms.sourcegitcommit: 0e0cd9347c029e0c7c9f3fe6d39985a6d3af967d
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 12/02/2020
ms.locfileid: "96505464"
---
# <a name="sql-server-xtp-storage"></a>SQL Server-XTP-Speicher
 [!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

  Das Leistungsobjekt „SQL Server-XTP-Speicher“ enthält Leistungsindikatoren, die sich auf die Speicherung auf Datenträger für In-Memory-OLTP in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]beziehen.  
  
 In dieser Tabelle werden die Leistungsindikatoren von **SQL Server-XTP-Speicher** beschrieben.  
  
|Leistungsindikator|BESCHREIBUNG|  
|-------------|-----------------|  
|**Geschlossene Prüfpunkte**|Die Anzahl der vom Online-Agent geschlossenen Prüfpunkte.|  
|**Verarbeitete Prüfpunkte**|Die Anzahl der vom Offline-Prüfpunktthread verarbeiteten Prüfpunkte.|  
|**Abgeschlossene Kernzusammenführungen**|Die Anzahl der vom Zusammenführungsarbeitsthread abgeschlossenen Kernzusammenführungen. Diese Zusammenführungen müssen noch installiert werden.|  
|**Auswertungen der Zusammenführungsrichtlinie**|Die Anzahl der Auswertungen für die Zusammenführungsrichtlinie, seit der Server gestartet wurde.|  
|**Ausstehende Zusammenführungsanforderungen**|Die Anzahl der ausstehenden Zusammenführungsanforderungen, seit der Server gestartet wurde.|  
|**Abgebrochene Zusammenführungen**|Die Anzahl der aufgrund eines Fehlers abgebrochenen Zusammenführungen.|  
|**Installierte Zusammenführungen**|Die Anzahl der erfolgreich installierten Zusammenführungen.|  
|**Gesamtanzahl zusammengeführter Dateien**|Die Gesamtanzahl der zusammengeführten Quelldateien. Diese Anzahl kann verwendet werden, um die durchschnittliche Anzahl von Quelldateien in der Zusammenführung zu ermitteln.|  
  
## <a name="see-also"></a>Weitere Informationen  
 [Leistungsindikatoren für SQL Server XTP &#40;In-Memory-OLTP&#41;](../../relational-databases/performance-monitor/sql-server-xtp-in-memory-oltp-performance-counters.md)  
  
  
