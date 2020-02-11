---
title: Eigenschaften der Ablauf Verfolgungs Datei (Registerkarte Ereignis Auswahl) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
f1_keywords:
- sql12.pro.tracefileproperties.eventsselection.f1
helpviewer_keywords:
- Trace File Properties dialog box
ms.assetid: 158d442f-2225-4173-8545-fb1cf611b4d0
author: mashamsft
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 0a6c6da76bd89b4686791087e558ae1f329f57a3
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "66088803"
---
# <a name="trace-file-properties-events-selection-tab"></a>Eigenschaften der Ablaufverfolgungsdatei (Registerkarte Ereignisauswahl)
  Mithilfe der Registerkarte **Ereignisauswahl** im Dialogfeld **Eigenschaften der Ablaufverfolgungsvorlage** können Sie die Spalteneigenschaften der Ablaufverfolgung anzeigen oder Datenspalten aus der Ablaufverfolgung entfernen.  
  
 Öffnen Sie eine Ablaufverfolgungsdatei, um dieses Fenster anzuzeigen. Klicken Sie dann im Menü **Datei** auf **Eigenschaften**und dann auf die Registerkarte **Ereignisauswahl** .  
  
## <a name="options"></a>Tastatur  
 **Ereignis** Spalte  
 Zeigt verfolgte Ereignisse an, die nach Ereigniskategorien geordnet sind. Zunächst sind alle Ereignisse in der Ablaufverfolgung ausgewählt. Die Ereignisse können ausgewählt werden, indem das Kontrollkästchen oder eine Datenspalte für ein Ereignis aktiviert wird. Wenn das Ereigniskästchen aktiviert ist, werden alle für dieses Ereignis verfügbaren Datenspalten ausgewählt. Wenn die Datenspalte für ein Ereignis aktiviert ist, wird das Ereignis automatisch aktiviert und mit ihm alle weiteren erforderlichen Spalten. Wenn Sie eine Ablaufverfolgungsdatei oder -tabelle anzeigen, können Sie per Deaktivierung von Ereignissen oder Datenspalten die Menge der angezeigten Daten im Ablaufverfolgungsfenster zur besseren Übersicht reduzieren. Sie können auch Spaltenfilter ändern, um die Menge der sichtbaren Daten im Ablaufverfolgungsfenster zu reduzieren. Weitere Informationen zu Ereignisklassen finden Sie unter [Ereignisklassen in SQL Server – Referenz](../relational-databases/event-classes/sql-server-event-class-reference.md).  
  
 Datenspalten  
 Zeigt Datenspalten der Ablaufverfolgung an. Alle relevanten Datenspalten in der Ablaufverfolgung sind standardmäßig für jedes in die Verfolgung einbezogene Ereignis aktiviert.  
  
 Sie können Filter festlegen, indem Sie auf die Spaltenüberschrift klicken und die Filterkriterien eingeben. Gefilterte Datenspalten sind im Dialogfeld **Filter bearbeiten** links neben der Spaltenbezeichnung durch ein Filtersymbol gekennzeichnet.  
  
 **Alle Ereignisse anzeigen**  
 Zeigt alle verfügbaren Ereignisse an. Standardmäßig werden nur Zeilen im Raster **Ereignisauswahl** angezeigt, die ausgewählt sind. Deaktivieren Sie dieses Kontrollkästchen, um alle nicht ausgewählten Ereignisse im Raster **Ereignisauswahl** auszublenden. Wenn die Option **Alle Ereignisse anzeigen** aktiviert ist und Sie eine Ablaufverfolgungsdatei oder -tabelle anzeigen, werden alle aufgezeichneten Ereignisse in der Ablaufanzeige des Ablaufverfolgungsfensters angezeigt.  
  
 **Alle Spalten anzeigen**  
 Zeigt alle verfügbaren Datenspalten an. Standardmäßig werden nur ausgewählte Datenspalten angezeigt. Deaktivieren Sie dieses Kontrollkästchen, um alle nicht ausgewählten Datenspalten im Raster **Ereignisauswahl** auszublenden.  
  
 **Spalten Filter**  
 Öffnet das Dialogfeld **Filter bearbeiten** , durch das ein Filtersymbol auf der linken Seite des Spaltentitels für gefilterte Datenspalten angezeigt wird. Mithilfe des Dialogfelds **Filter bearbeiten** können Sie Datenspaltenfilter bearbeiten.  
  
 **Organisieren von Spalten**  
 Klicken Sie nach der Auswahl der zu verfolgenden **Ereignisse** und Datenspalten auf **Spalten organisieren**, um eine Reorganisation der Spalten im Raster des Fensters mit den Ablaufverfolgungsergebnissen zu erzwingen.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Angeben von Ereignissen und Datenspalten für eine Ablauf Verfolgungs Datei &#40;SQL Server Profiler&#41;](../tools/sql-server-profiler/specify-events-and-data-columns-for-a-trace-file-sql-server-profiler.md)   
 [Ereignisse in einer Ablauf Verfolgung &#40;SQL Server Profiler Filtern&#41;](../tools/sql-server-profiler/filter-events-in-a-trace-sql-server-profiler.md)   
 [Filter Informationen &#40;SQL Server Profiler anzeigen&#41;](../tools/sql-server-profiler/view-filter-information-sql-server-profiler.md)   
 [Ändern eines Filters &#40;SQL Server Profiler&#41;](../tools/sql-server-profiler/modify-a-filter-sql-server-profiler.md)   
 [SQL Server Profiler](../tools/sql-server-profiler/sql-server-profiler.md)   
 [Vorlagen und Berechtigungen in SQL Server Profiler](../tools/sql-server-profiler/sql-server-profiler-templates-and-permissions.md)  
  
  
