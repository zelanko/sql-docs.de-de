---
title: SQL Server, Wartestatistik-Objekt | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dbe-cross-instance
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Wait Statistics object
- SQLServer:Wait Statistics
ms.assetid: cb7f917d-4291-4115-9b78-ee7692ebbb2d
caps.latest.revision: 14
author: craigg-msft
ms.author: craigg
manager: jhubbard
ms.openlocfilehash: e9c8678351661af55eb04dde5dfea656bab23dd5
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/19/2018
ms.locfileid: "36046427"
---
# <a name="sql-server-wait-statistics-object"></a>SQL Server, Wartestatistik-Objekt
  Das **SQLServer:Wartestatistik** -Leistungsobjekt enthält Leistungsindikatoren mit Informationen zum Wartestatus.  
  
 In der folgenden Tabelle werden die im Wartestatistik-Objekt enthaltenen Leistungsindikatoren aufgelistet.  
  
|Leistungsindikatoren des SQLServer:Wartestatistik-Objekts|Description|  
|-----------------------------------------|-----------------|  
|**Sperrenwartevorgänge**|Statistik für Prozesse, die auf eine Sperre warten|  
|**Protokollpuffer-Wartevorgänge**|Statistik für Prozesse, die auf die Verfügbarkeit des Protokollpuffers warten|  
|**Wartevorgänge für Schreiben des Protokolls**|Statistik für Prozesse, die darauf warten, dass der Protokollpuffer geschrieben wird|  
|**Speicherzuweisungs-Wartevorgänge**|Statistik für Prozesse, die auf die Verfügbarkeit einer Speicherzuweisung warten|  
|**Netzwerk-E/A-Wartevorgänge**|Statistik für Wartevorgänge bezüglich Netzwerk-E/A|  
|**Nichtseiten-Latchwartevorgänge**|Statistik für Nichtseitenlatches|  
|**Seiten-E/A-Latchwartevorgänge**|Statistik für Seiten-E/A-Latches|  
|**Seitenlatch-Wartevorgänge**|Statistik für Seitenlatches, ohne E/A-Latches|  
|**Thread-sichere Speicherobjekt-Wartevorgänge**|Statistik für Prozesse, die auf Thread-sichere Speicherzuordnungen warten|  
|**Transaktionsbesitzer-Wartevorgänge**|Statistik für Prozesse, die den Zugriff auf Transaktionen synchronisieren|  
|**Warten auf den Arbeitsthread**|Statistik für Prozesse, die auf die Verfügbarkeit des Arbeitsthreads warten|  
|**Wartevorgänge für Arbeitsbereichssynchronisierung**|Statistik für Prozesse, die den Zugriff auf den Arbeitsbereich synchronisieren|  
  
 Jeder Leistungsindikator in dem Objekt enthält die folgenden Instanzen:  
  
|Element|Description|  
|----------|-----------------|  
|**Durchschnittliche Wartezeit (ms)**|Durchschnittliche Zeit für den ausgewählten Wartetyp|  
|**Kumulierte Wartezeit (ms) pro Sekunde**|Aggregierte Wartezeit für den ausgewählten Typ pro Sekunde|  
|**Aktuell ausgeführte Wartevorgänge**|Anzahl der Prozesse, die zurzeit auf den folgenden Typ warten|  
|**Gestartete Wartevorgänge pro Sekunde**|Anzahl der pro Sekunde gestarteten Wartevorgänge des ausgewählten Wartetyps|  
  
## <a name="see-also"></a>Siehe auch  
 [Überwachen der Ressourcenverwendung &#40;Systemmonitor&#41;](monitor-resource-usage-system-monitor.md)  
  
  