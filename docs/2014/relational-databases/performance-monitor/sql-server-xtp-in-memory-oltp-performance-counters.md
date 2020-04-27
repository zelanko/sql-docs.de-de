---
title: XTP-Leistungsindikatoren (in-Memory OLTP) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: performance
ms.topic: conceptual
ms.assetid: fe3cbaf4-65f4-44c5-acc6-7b735cda0c5d
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: 69b24c96e4833a45038bfcae20f0a5fecd0d2340
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/26/2020
ms.locfileid: "63151135"
---
# <a name="xtp-in-memory-oltp-performance-counters"></a>XTP (In-Memory OLTP)-Leistungsindikatoren
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] bietet Objekte und Leistungsindikatoren, die vom Systemmonitor zum Überwachen der In-Memory OLTP-Aktivität verwendet werden können.  
  
##  <a name="xtp-in-memory-oltp-performance-objects"></a><a name="SQLServerPOs"></a>XTP-Leistungs Objekte (in-Memory OLTP)  
 In der folgenden Tabelle werden [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Objekte beschrieben.  
  
|Leistungsobjekt|Beschreibung|  
|------------------------|-----------------|  
|[XTP-Cursor](../cursors.md)|Das XTP-Leistungsobjekt für Cursor enthält Leistungsindikatoren für interne Cursor der XTP-Engine. Cursor sind die Bausteine auf unterer Ebene, die die XTP-Engine zur Verarbeitung von [!INCLUDE[tsql](../../includes/tsql-md.md)]-Abfragen verwendet. Daher können Sie diese in der Regel nicht direkt steuern.|  
|[XTP Garbage Collection](sql-server-xtp-garbage-collection.md)|Das XTP-Leistungsobjekt für die Garbage Collection enthält Leistungsindikatoren für die Garbage Collection der XTP-Engine.|  
|[XTP-Phantomprozessor](sql-server-xtp-phantom-processor.md)|Das XTP-Leistungsobjekt "Phantomprozessor" enthält Leistungsindikatoren für das zur Phantomverarbeitung verwendete Subsystem der XTP-Engine. Diese Komponente ist dafür verantwortlich, Phantomzeilen in Transaktionen zu erkennen, die auf der SERIALIZABLE-Isolationsstufe ausgeführt werden.|  
|[XTP-Speicher](sql-server-xtp-storage.md)|Das Leistungsobjekt "XTP-Speicher" enthält Leistungsindikatoren für den XTP-Speicher in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].|  
|[XTP-Transaktionsprotokoll](sql-server-xtp-transaction-log.md)|Das XTP-Leistungsobjekt für Transaktionsprotokolle enthält Leistungsindikatoren für die XTP-Transaktionsprotokollierung in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].|  
|[XTP-Transaktionen](sql-server-xtp-transactions.md)|Das XTP-Leistungsobjekt für Transaktionen enthält Leistungsindikatoren für XTP-Engine-Transaktionen in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].|  
  
  
