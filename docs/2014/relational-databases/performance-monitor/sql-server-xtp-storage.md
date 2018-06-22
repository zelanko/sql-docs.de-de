---
title: XTP-Speicher | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dbe-cross-instance
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 4070580b-880d-4f4c-abcc-626a4fe0c9a2
caps.latest.revision: 3
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 897a3a2e9e3cc592281be87593aa6356ce474c56
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/19/2018
ms.locfileid: "36148350"
---
# <a name="xtp-storage"></a>XTP-Speicher
  Das Leistungsobjekt "XTP-Speicher" enthält Leistungsindikatoren für XTP-Speicher in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
 Diese Tabelle beschreibt die **XTP-Speicher** Leistungsindikatoren.  
  
|Leistungsindikator|Description|  
|-------------|-----------------|  
|**Geschlossene Prüfpunkte**|Die Anzahl der vom Online-Agent geschlossenen Prüfpunkte.|  
|**Verarbeitete Prüfpunkte**|Die Anzahl der vom Offline-Prüfpunktthread verarbeiteten Prüfpunkte.|  
|**Abgeschlossene Kernzusammenführungen**|Die Anzahl der vom Zusammenführungsarbeitsthread abgeschlossenen Kernzusammenführungen. Diese Zusammenführungen müssen noch installiert werden.|  
|**Auswertungen der Zusammenführungsrichtlinie**|Die Anzahl der Auswertungen für die Zusammenführungsrichtlinie, seit der Server gestartet wurde.|  
|**Ausstehende Zusammenführungsanforderungen**|Die Anzahl der ausstehenden Zusammenführungsanforderungen, seit der Server gestartet wurde.|  
|**Abgebrochene Zusammenführungen**|Die Anzahl der aufgrund eines Fehlers abgebrochenen Zusammenführungen.|  
|**Installierte Zusammenführungen**|Die Anzahl der erfolgreich installierten Zusammenführungen.|  
|**Gesamtanzahl zusammengeführter Dateien**|Die Gesamtanzahl der zusammengeführten Quelldateien. Diese Anzahl kann verwendet werden, um die durchschnittliche Anzahl von Quelldateien in der Zusammenführung zu ermitteln.|  
  
## <a name="see-also"></a>Siehe auch  
 [XTP &#40;In-Memory OLTP&#41; -Leistungsindikatoren](../../integration-services/performance/performance-counters.md)  
  
  