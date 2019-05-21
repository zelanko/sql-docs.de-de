---
title: SQL Server XTP-Phantomprozessor | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: performance
ms.topic: conceptual
ms.assetid: 0f691b3d-a8fd-4459-ad21-2cfc8574a8c0
author: julieMSFT
ms.author: jrasnick
manager: craigg
ms.openlocfilehash: df34bbcfee578a36fc10e18a47ad4861aae4d8ff
ms.sourcegitcommit: 0c1d552b3256e1bd995e3c49e0561589c52c21bf
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 12/14/2018
ms.locfileid: "53380271"
---
# <a name="sql-server-xtp-phantom-processor"></a>SQL Server XTP-Phantomprozessor
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

  Das SQL Server-XTP-Leistungsobjekt „Phantomprozessor“ enthält Leistungsindikatoren, die sich auf den für das zur Phantomverarbeitung verwendete Subsystem der XTP-Engine beziehen. Diese Komponente ist dafür verantwortlich, Phantomzeilen in Transaktionen zu erkennen, die auf der SERIALIZABLE-Isolationsstufe ausgeführt werden sowie Einschränkungsvalidierung in Parallelitätsszenarios.  
  
 In dieser Tabelle werden die Leistungsindikatoren für **SQL Server-XTP-Phantomprozessor** beschrieben.  
  
|Leistungsindikator|Beschreibung|  
|-------------|-----------------|  
|**Dusty-Corner-Scanwiederholungen/s (durch Phantom ausgegeben)**|Die durchschnittliche Anzahl von Scanwiederholungen aufgrund von Schreibkonflikten während Dusty-Corner-Sweep-Vorgängen, die pro Sekunde durch den Phantomprozessor ausgegeben werden. Dieser Leistungsindikator befindet sich auf einer sehr niedrigen Ebene und dient nicht der Verwendung durch Kunden.|  
|**Entfernte abgelaufene Phantomzeilen/s**|Die durchschnittliche Anzahl abgelaufener Zeilen, die pro Sekunde von Phantomscans entfernt werden.|  
|**Berührte abgelaufene Phantomzeilen/s**|Die durchschnittliche Anzahl abgelaufener Zeilen, die pro Sekunde von Phantomscans berührt werden.|  
|**Berührte ablaufende Phantomzeilen/s**|Die durchschnittliche Anzahl ablaufender Zeilen, die pro Sekunde von Phantomscans berührt werden.|  
|**Berührte Phantomzeilen/s**|Die durchschnittliche Anzahl von Zeilen, die pro Sekunde von Phantomscans berührt werden.|  
|**Gestartete Phantomscans/s**|Die durchschnittliche Anzahl der pro Sekunde gestarteten Phantomscans.|  
  
## <a name="see-also"></a>Weitere Informationen  
 [Leistungsindikatoren für SQL Server XTP &#40;In-Memory OLTP&#41;](../../relational-databases/performance-monitor/sql-server-xtp-in-memory-oltp-performance-counters.md)  
  
  
