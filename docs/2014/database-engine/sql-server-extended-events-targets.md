---
title: Ziele für erweiterte Ereignisse von SQLServer | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- targets [SQL Server extended events]
- extended events [SQL Server], targets
ms.assetid: e281684c-40d1-4cf9-a0d4-7ea1ecffa384
caps.latest.revision: 50
author: mashamsft
ms.author: mathoma
manager: craigg
ms.openlocfilehash: ba3ea863b35142c65b2e5f38789f888d603b6977
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/02/2018
ms.locfileid: "37160981"
---
# <a name="sql-server-extended-events-targets"></a>SQL Server Extended Events Targets
  [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Ziele für erweiterte Ereignisse sind Ereignisconsumer. Ziele können in eine Datei schreiben, Ereignisdaten in einem Arbeitsspeicherpuffer speichern oder Ereignisdaten aggregieren. Ziele können Daten synchron oder asynchron verarbeiten.  
  
 Durch das Design von Extended Events wird sichergestellt, dass Ziele garantiert nur einmal pro Sitzung Ereignisse empfangen.  
  
 Erweiterte Ereignisse stellen die folgenden Ziele zur Verwendung in einer Sitzung mit erweiterten Ereignissen bereit:  
  
-   [Ereigniszähler](../../2014/database-engine/event-counter-target.md)  
  
     Zählt alle angegebenen Ereignisse, die während einer Sitzung für erweiterte Ereignisse auftreten. Wird eingesetzt, um Informationen über Merkmale der Arbeitsauslastung ohne den Aufwand einer vollständigen Ereignisauflistung zu sammeln. Dies ist ein synchrones Ziel.  
  
-   [Ereignisdatei](../../2014/database-engine/event-file-target.md)  
  
     Wird eingesetzt, um die Ereignissitzungsausgabe aus vollständigen Speicherpuffern auf die Festplatte zu schreiben. Dies ist ein asynchrones Ziel.  
  
-   [Ereignispaarbildung](../../2014/database-engine/event-pairing-target.md)  
  
     Viele Arten von Ereignissen treten paarweise auf, wie z. B. Anforderungen zur Einrichtung und Aufhebung einer Sperre. Ereignispaarbildung wird eingesetzt, um zu bestimmen, wann ein spezifisches, kombiniertes Ereignis nicht als Paar auftritt. Dies ist ein asynchrones Ziel.  
  
-   [Ereignisablaufverfolgung für Windows (ETW)](../relational-databases/extended-events/event-tracing-for-windows-target.md)  
  
     Wird eingesetzt, um [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] -Ereignisse mit Ereignisdaten von Anwendungen oder des Windows-Betriebssystems zu korrelieren. Dies ist ein synchrones Ziel.  
  
-   [Histogramm](../../2014/database-engine/histogram-target.md)  
  
     Dient dazu, die Häufigkeit eines bestimmten Ereignisses auf Grundlage einer bestimmten Ereignisspalte oder Aktion zu zählen. Dies ist ein asynchrones Ziel.  
  
-   [Ringpuffer](../../2014/database-engine/ring-buffer-target.md)  
  
     Wird verwendet, um die Ereignisdaten auf Basis der FIFO-Reihenfolge (First-In-First-Out) oder auf Basis der ereignisbezogenen FIFO-Reihenfolge im Speicher zu behalten. Dies ist ein asynchrones Ziel.  
  
## <a name="see-also"></a>Siehe auch  
 [Erweiterte Ereignisse](../relational-databases/extended-events/extended-events.md)   
 [SQLServer-Pakete für erweiterte Ereignisse](../relational-databases/extended-events/sql-server-extended-events-packages.md)   
 [SQL Server Extended Events Sessions](../relational-databases/extended-events/sql-server-extended-events-sessions.md)   
 
  [Engine für erweiterte Ereignisse von SQL Server](../relational-databases/extended-events/sql-server-extended-events-engine.md)  
  
  
