---
title: Leistungsindikatoren für XTP (In-Memory OLTP) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
ms.assetid: fe3cbaf4-65f4-44c5-acc6-7b735cda0c5d
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: 2362807e8e033fbc55e75a08d9dec80bf3782e03
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/02/2018
ms.locfileid: "48084050"
---
# <a name="xtp-in-memory-oltp-performance-counters"></a>XTP (In-Memory OLTP)-Leistungsindikatoren
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] bietet Objekte und Leistungsindikatoren, die vom Systemmonitor zum Überwachen der In-Memory OLTP-Aktivität verwendet werden können.  
  
##  <a name="SQLServerPOs"></a> XTP (In-Memory-OLTP)-Leistungsobjekte  
 In der folgenden Tabelle werden [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Objekte beschrieben.  
  
|Leistungsobjekt|Description|  
|------------------------|-----------------|  
|[XTP-Cursor](../cursors.md)|Das XTP-Leistungsobjekt für Cursor enthält Leistungsindikatoren für interne Cursor der XTP-Engine. Cursor sind die Bausteine auf unterer Ebene der XTP-Engine verwendet zum Verarbeiten [!INCLUDE[tsql](../../includes/tsql-md.md)] Abfragen. Daher können Sie diese in der Regel nicht direkt steuern.|  
|[XTP Garbage Collection](sql-server-xtp-garbage-collection.md)|Das XTP-Leistungsobjekt für die Garbage Collection enthält Leistungsindikatoren für die Garbage Collection der XTP-Engine.|  
|[XTP-Phantomprozessor](sql-server-xtp-phantom-processor.md)|Das XTP-Leistungsobjekt "Phantomprozessor" enthält Leistungsindikatoren für das zur Phantomverarbeitung verwendete Subsystem der XTP-Engine. Diese Komponente ist dafür verantwortlich, Phantomzeilen in Transaktionen zu erkennen, die auf der SERIALIZABLE-Isolationsstufe ausgeführt werden.|  
|[XTP-Speicher](sql-server-xtp-storage.md)|Das XTP-Speicher-Leistungsobjekt enthält Leistungsindikatoren für XTP-Speicher in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].|  
|[XTP-Transaktionsprotokoll](sql-server-xtp-transaction-log.md)|Das XTP-Transaktionsprotokoll-Leistungsobjekt enthält Leistungsindikatoren für XTP-transaktionsprotokollierung in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].|  
|[XTP-Transaktionen](sql-server-xtp-transactions.md)|Das Leistungsobjekt "XTP-Transaktionen" enthält Leistungsindikatoren für XTP-modultransaktionen in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].|  
  
  
