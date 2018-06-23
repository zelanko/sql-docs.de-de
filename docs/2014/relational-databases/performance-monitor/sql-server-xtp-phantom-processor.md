---
title: XTP-Phantomprozessor | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dbe-cross-instance
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 0f691b3d-a8fd-4459-ad21-2cfc8574a8c0
caps.latest.revision: 4
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: bc489c0fc5be77e8dfaf2d2ea11a10515ec460e8
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/19/2018
ms.locfileid: "36061368"
---
# <a name="xtp-phantom-processor"></a>XTP-Phantomprozessor
  Das XTP-Leistungsobjekt "Phantomprozessor" enthält Leistungsindikatoren für das zur Phantomverarbeitung verwendete Subsystem der XTP-Engine. Diese Komponente ist dafür verantwortlich, Phantomzeilen in Transaktionen zu erkennen, die auf der SERIALIZABLE-Isolationsstufe ausgeführt werden.  
  
 Diese Tabelle beschreibt die **XTP-Phantomprozessor** Leistungsindikatoren.  
  
|Leistungsindikator|Description|  
|-------------|-----------------|  
|**Dusty-Corner-Scanwiederholungen/s (durch Phantom ausgegeben)**|Die durchschnittliche Anzahl von Scanwiederholungen aufgrund von Schreibkonflikten während Dusty-Corner-Sweep-Vorgängen, die pro Sekunde durch den Phantomprozessor ausgegeben werden. Dieser Leistungsindikator befindet sich auf einer sehr niedrigen Ebene und dient nicht der Verwendung durch Kunden.|  
|**Entfernte abgelaufene Phantomzeilen/s**|Die durchschnittliche Anzahl abgelaufener Zeilen, die pro Sekunde von Phantomscans entfernt werden.|  
|**Berührte abgelaufene Phantomzeilen/s**|Die durchschnittliche Anzahl abgelaufener Zeilen, die pro Sekunde von Phantomscans berührt werden.|  
|**Berührte ablaufende Phantomzeilen/s**|Die durchschnittliche Anzahl ablaufender Zeilen, die pro Sekunde von Phantomscans berührt werden.|  
|**Berührte Phantomzeilen/s**|Die durchschnittliche Anzahl von Zeilen, die pro Sekunde von Phantomscans berührt werden.|  
|**Gestartete Phantomscans/s**|Die durchschnittliche Anzahl der pro Sekunde gestarteten Phantomscans.|  
  
## <a name="see-also"></a>Siehe auch  
 [XTP &#40;In-Memory OLTP&#41; -Leistungsindikatoren](../../integration-services/performance/performance-counters.md)  
  
  