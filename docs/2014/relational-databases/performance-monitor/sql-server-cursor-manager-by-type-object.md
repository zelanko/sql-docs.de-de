---
title: SQL Server, Cursor-Manager nach Typ-Objekt | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dbe-cross-instance
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- Cursor Manager by Type object
- SQLServer:Cursor Manager by Type
ms.assetid: d67fbd8a-7554-4a16-96f1-d9ee857a95e3
caps.latest.revision: 13
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: cab113ccef644267056edcc898412ba90fbc68c1
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/02/2018
ms.locfileid: "37322340"
---
# <a name="sql-server-cursor-manager-by-type-object"></a>SQL Server, Cursor-Manager nach Typ-Objekt
  Das **SQLServer:Cursor-Manager nach Typ** -Objekt stellt Leistungsindikatoren zum Überwachen von Cursorn bereit, die nach dem Typ gruppiert sind.  
  
 Diese Tabelle beschreibt die Leistungsindikatoren des **SQLServer:Cursor-Manager nach Typ** -Objekts von SQL Server.  
  
|Leistungsindikatoren des SQLServer:Cursor-Manager nach Typ-Objekts|Description|  
|-------------------------------------|-----------------|  
|**Aktive Cursor**|Anzahl der aktiven Cursor.|  
|**Cachetrefferquote**|Das Verhältnis zwischen Cachetreffern und -suchvorgängen.|  
|**Anzahl der zwischengespeicherten Cursor**|Anzahl der Cursor eines bestimmten Typs im Cache.|  
|**Verwendungszähler für zwischengespeicherte Cursor/Sekunde**|Häufigkeit, mit der jeder Typ eines zwischengespeicherten Cursors verwendet wurde.|  
|**Cursorspeicherauslastung**|Größe des Speicherplatzes, der durch Cursor belegt wird (KB).|  
|**Cursoranforderungen/Sekunde**|Anzahl der SQL-Cursoranforderungen, die vom Server empfangen wurden.|  
|**Cursor-Arbeitstabellenverwendung**|Anzahl der Arbeitstabellen, die von Cursorn verwendet werden.|  
|**Anzahl der aktiven Cursorpläne.**|Anzahl der Cursorpläne.|  
  
 Jeder Leistungsindikator in dem Objekt enthält die folgenden Instanzen:  
  
|Cursor-Manager-Instanz|Description|  
|-----------------------------|-----------------|  
|**_Total**|Informationen für alle Cursor.|  
|**API Cursor**|Nur die API-Cursor-Informationen.|  
|**TSQL Global Cursor**|Nur die globalen [!INCLUDE[tsql](../../includes/tsql-md.md)] -Cursorinformationen.|  
|**TSQL Local Cursor**|Nur die lokalen [!INCLUDE[tsql](../../includes/tsql-md.md)] -Cursorinformationen.|  
  
## <a name="see-also"></a>Siehe auch  
 [Überwachen der Ressourcenverwendung &#40;Systemmonitor&#41;](monitor-resource-usage-system-monitor.md)  
  
  
