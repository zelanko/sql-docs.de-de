---
title: SQL Server XTP-Phantomprozessor | Microsoft-Dokumentation
description: Hier lernen Sie das SQL Server-XTP-Leistungsobjekt „Phantomprozessor“ kennen, das Leistungsindikatoren für das zur Phantomverarbeitung verwendete Subsystem der XTP-Engine enthält.
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: performance
ms.topic: conceptual
ms.assetid: 0f691b3d-a8fd-4459-ad21-2cfc8574a8c0
author: WilliamDAssafMSFT
ms.author: wiassaf
ms.openlocfilehash: c0547f8f93b548e7dcf51271e7c796bad52f46ad
ms.sourcegitcommit: 0e0cd9347c029e0c7c9f3fe6d39985a6d3af967d
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 12/02/2020
ms.locfileid: "96505471"
---
# <a name="sql-server-xtp-phantom-processor"></a>SQL Server XTP-Phantomprozessor
 [!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

  Das SQL Server-XTP-Leistungsobjekt „Phantomprozessor“ enthält Leistungsindikatoren, die sich auf den für das zur Phantomverarbeitung verwendete Subsystem der XTP-Engine beziehen. Diese Komponente ist dafür verantwortlich, Phantomzeilen in Transaktionen zu erkennen, die auf der SERIALIZABLE-Isolationsstufe ausgeführt werden sowie Einschränkungsvalidierung in Parallelitätsszenarios.  
  
 In dieser Tabelle werden die Leistungsindikatoren für **SQL Server-XTP-Phantomprozessor** beschrieben.  
  
|Leistungsindikator|BESCHREIBUNG|  
|-------------|-----------------|  
|**Dusty-Corner-Scanwiederholungen/s (durch Phantom ausgegeben)**|Die durchschnittliche Anzahl von Scanwiederholungen aufgrund von Schreibkonflikten während Dusty-Corner-Sweep-Vorgängen, die pro Sekunde durch den Phantomprozessor ausgegeben werden. Dieser Leistungsindikator befindet sich auf einer sehr niedrigen Ebene und dient nicht der Verwendung durch Kunden.|  
|**Entfernte abgelaufene Phantomzeilen/s**|Die durchschnittliche Anzahl abgelaufener Zeilen, die pro Sekunde von Phantomscans entfernt werden.|  
|**Berührte abgelaufene Phantomzeilen/s**|Die durchschnittliche Anzahl abgelaufener Zeilen, die pro Sekunde von Phantomscans berührt werden.|  
|**Berührte ablaufende Phantomzeilen/s**|Die durchschnittliche Anzahl ablaufender Zeilen, die pro Sekunde von Phantomscans berührt werden.|  
|**Berührte Phantomzeilen/s**|Die durchschnittliche Anzahl von Zeilen, die pro Sekunde von Phantomscans berührt werden.|  
|**Gestartete Phantomscans/s**|Die durchschnittliche Anzahl der pro Sekunde gestarteten Phantomscans.|  
  
## <a name="see-also"></a>Weitere Informationen  
 [Leistungsindikatoren für SQL Server XTP &#40;In-Memory-OLTP&#41;](../../relational-databases/performance-monitor/sql-server-xtp-in-memory-oltp-performance-counters.md)  
  
  
