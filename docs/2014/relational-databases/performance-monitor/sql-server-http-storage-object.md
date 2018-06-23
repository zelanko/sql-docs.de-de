---
title: SQL Server, HTTP_STORAGE_OBJECT | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dbe-cross-instance
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: ae849f79-c581-42a5-a5cc-0a9ebea171b9
caps.latest.revision: 4
author: craigg-msft
ms.author: craigg
manager: jhubbard
ms.openlocfilehash: 84ba27202f0a1d95810d80d474b9db91dfa4201a
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/19/2018
ms.locfileid: "36162021"
---
# <a name="sql-server-httpstorageobject"></a>SQL Server, HTTP_STORAGE_OBJECT
  Das **SQLServer:HTTP_STORAGE_OBJECT** -Leistungsobjekt umfasst Leistungsindikatoren, mit denen das Microsoft Azure-Speicherkonto überwacht wird. Mit [SQL Server-Datendateien in Windows Azure](../databases/sql-server-data-files-in-microsoft-azure.md) -Feature können Sie Datenbankdateien in Windows Azure-Speicher-Blobs speichern. Dieses Leistungsobjekt behandelt jedes Windows Azure-Speicherkonto als getrenntes Laufwerk.  
  
|Indikatorname|Description|  
|------------------|-----------------|  
|**Gelesene Bytes/s**|Die bei Lesevorgängen pro Sekunde aus dem HTTP-Speicher übertragene Datenmenge.|  
|**Geschriebene Bytes/s**|Die bei Schreibvorgängen pro Sekunde aus dem HTTP-Speicher übertragene Datenmenge.|  
|**Gesamtanzahl Bytes/s**|Die bei Lese- oder Schreibvorgängen pro Sekunde aus dem HTTP-Speicher übertragene Datenmenge.|  
|**Lesevorgänge/s**|Die Anzahl der Lesevorgänge im HTTP-Speicher pro Sekunde.|  
|**Schreibvorgänge/s**|Die Anzahl der Schreibvorgänge im HTTP-Speicher pro Sekunde.|  
|**Übertragungen/s**|Die Anzahl der Lese- und Schreibvorgänge im HTTP-Speicher pro Sekunde.|  
|**Mittlere Bytes/Lesevorgang**|Die durchschnittliche Anzahl von Bytes, die pro Lesevorgang aus dem HTTP-Speicher übertragen wurde.|  
|**Mittlere Bytes/Schreibvorgang**|Die durchschnittliche Anzahl von Bytes, die pro Schreibvorgang aus dem HTTP-Speicher übertragen wurde.|  
|**Mittlere Bytes/Übertragung**|Die durchschnittliche Anzahl von Bytes, die während Lese- oder Schreibvorgängen aus dem HTTP-Speicher übertragen wurde.|  
|**Durchschn. Mikrosekunden/Lesevorgang**|Die durchschnittliche Anzahl von Mikrosekunden, die ein Lesevorgang aus dem HTTP-Speicher dauert.|  
|**Durchschn. Mikrosekunden/Schreibvorgang**|Die durchschnittliche Anzahl von Mikrosekunden, die ein Schreibvorgang in den HTTP-Speicher dauert.|  
|**Durchschn. Mikrosekunden/Übertragung**|Die durchschnittliche Anzahl von Mikrosekunden, die eine Übertragung in den HTTP-Speicher dauert.|  
|**Ausstehende HTTP-Speicher-E/A-Vorgänge**|Die Gesamtanzahl ausstehender E/A-Vorgänge für einen HTTP-Speicher.|  
|**Wiederholungen für HTTP-Speicher-E/A-Vorgänge/s**|Die Anzahl der an den HTTP-Speicher pro Sekunde gesendeten Wiederholungsanforderungen.|  
  
## <a name="see-also"></a>Siehe auch  
 [Überwachen der Ressourcenverwendung &#40;Systemmonitor&#41;](monitor-resource-usage-system-monitor.md)  
  
  