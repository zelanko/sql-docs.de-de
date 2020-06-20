---
title: Filtern von Ereignissen anhand der Ereignisendzeit (SQL Server Profiler) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: profiler
ms.topic: conceptual
helpviewer_keywords:
- event end times [SQL Server]
- filters [SQL Server], traces
- traces [SQL Server], filters
- traces [SQL Server], events
ms.assetid: 74628f9e-2d39-496a-a443-0a3887db223d
author: stevestein
ms.author: sstein
ms.openlocfilehash: b7ccb13828235b690bad83e3791b945d8584d5e1
ms.sourcegitcommit: 57f1d15c67113bbadd40861b886d6929aacd3467
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/18/2020
ms.locfileid: "85054385"
---
# <a name="filter-events-based-on-the-event-end-time-sql-server-profiler"></a>Filtern von Ereignissen anhand der Ereignisendzeit (SQL Server Profiler)
  In diesem Thema wird beschrieben, wie Sie mithilfe von [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)]Ablaufverfolgungsereignisse basierend auf der Beendigungszeit des Ereignisses filtern.  
  
### <a name="to-filter-events-based-on-the-event-end-time"></a>So filtern Sie Ereignisse, die auf der Beendigungszeit des Ereignisses basieren  
  
1.  Klicken Sie im Menü **Datei** auf **Neue Ablaufverfolgung**, und stellen Sie dann eine Verbindung mit einer Instanz von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]her.  
  
     Das Dialogfeld **Ablaufverfolgungseigenschaften**wird angezeigt.  
  
    > [!NOTE]  
    >  Bei der Auswahl von **Ablaufverfolgung sofort nach dem Herstellen der Verbindung starten**wird das Dialogfeld **Ablaufverfolgungseigenschaften**nicht angezeigt. Stattdessen beginnt die Ablaufverfolgung. Um diese Einstellung zu deaktivieren, klicken Sie im Menü **Extras**auf **Optionen**, und deaktivieren Sie das Kontrollkästchen **Ablaufverfolgung sofort nach dem Herstellen der Verbindung starten** .  
  
2.  Stellen Sie im Dialogfeld **Ablaufverfolgungseigenschaften** sicher, dass die Registerkarte **Allgemein** ausgewählt ist, und geben Sie in das Textfeld **Ablaufverfolgungsname** einen Namen ein.  
  
3.  Wählen Sie in der Liste **Vorlage verwenden**eine Nachverfolgungsvorlage aus.  
  
4.  Sie können optional eine Zieldatei oder Zieltabelle angeben, in der die Ablaufverfolgungsergebnisse gespeichert werden.  
  
5.  Klicken Sie auf der Registerkarte **Ereignisauswahl**auf die **EndTime** Datenspalte, um das Dialogfeld **Filter bearbeiten** zu öffnen. Sie können auch mit der rechten Maustaste auf die Spaltenüberschrift klicken und **Spaltenfilter bearbeiten**auswählen.  
  
6.  Erweitern Sie **größer als** oder **kleiner als**, und geben Sie einen `datetime` Wert in das Feld ein, das unterhalb des Vergleichs Operators angezeigt wird.  
  
## <a name="see-also"></a>Weitere Informationen  
 [SQL Server Profiler](sql-server-profiler.md)   
 [SQL Server Profiler](sql-server-profiler.md)  
  
  
