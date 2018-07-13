---
title: Filtern von Ereignissen anhand der Ereignisstartzeit (SQL Server Profiler) | Microsoft-Dokumentation
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
- event start times [SQL Server]
- filters [SQL Server], traces
- traces [SQL Server], filters
- traces [SQL Server], events
ms.assetid: e965579e-d006-41a3-89ec-cfd5398c67d2
caps.latest.revision: 25
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: f72628b01609d055971bcf6446f5afcb0879776d
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/02/2018
ms.locfileid: "37204540"
---
# <a name="filter-events-based-on-the-event-start-time-sql-server-profiler"></a>Filtern von Ereignissen nach Ereignisstartzeit (SQL Server Profiler)
  In diesem Thema wird beschrieben, wie Sie mithilfe von [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)]Ablaufverfolgungsereignisse basierend auf der Ereignisstartzeit filtern.  
  
### <a name="to-filter-an-event-based-on-the-event-start-time"></a>So filtern Sie ein Ereignis basierend auf der Ereignisstartzeit  
  
1.  Klicken Sie im Menü **Datei** auf **Neue Ablaufverfolgung**, und stellen Sie dann eine Verbindung mit einer Instanz von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]her.  
  
     Das Dialogfeld **Ablaufverfolgungseigenschaften**wird angezeigt.  
  
    > [!NOTE]  
    >  Bei der Auswahl von **Ablaufverfolgung sofort nach dem Herstellen der Verbindung starten**wird das Dialogfeld **Ablaufverfolgungseigenschaften**nicht angezeigt. Stattdessen beginnt die Ablaufverfolgung. Um diese Einstellung zu deaktivieren, klicken Sie im Menü **Extras**auf **Optionen**, und deaktivieren Sie das Kontrollkästchen **Ablaufverfolgung sofort nach dem Herstellen der Verbindung starten** .  
  
2.  Geben Sie im Feld **Ablaufverfolgungsname** einen Namen für die Ablaufverfolgung ein.  
  
3.  Geben Sie im Feld **Vorlage verwenden**eine Ablaufverfolgungsvorlage aus.  
  
4.  Geben Sie optional ein Ziel für die Ablaufverfolgungsergebnisse an.  
  
5.  Klicken Sie im Menü **Ereignisauswahl**auf die Spaltenüberschrift **StartTime** . Sie können auch mit der rechten Maustaste auf die Spaltenüberschrift klicken und dann auf **Spaltenfilter bearbeiten** klicken, um das Dialogfeld **Filter bearbeiten** zu starten.  
  
6.  Erweitern Sie **größer als** oder **kleiner als**, und geben Sie dann eine `datetime` Wert im Feld, das unterhalb des Vergleichsoperators angezeigt wird.  
  
## <a name="see-also"></a>Siehe auch  
 [SQL Server Profiler](sql-server-profiler.md)  
  
  
