---
title: Eigenschaften der Ablauf Verfolgungs Vorlage (Registerkarte Ereignis Auswahl) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
f1_keywords:
- sql12.pro.tracetemplateproperties.eventsselection.f1
helpviewer_keywords:
- Trace Template Properties dialog box
ms.assetid: 5b202457-ab42-4902-8012-7f3f40aa09f5
author: mashamsft
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 8d86515646236916a9c651c7fa02923b88b995cd
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/26/2020
ms.locfileid: "66089544"
---
# <a name="trace-template-properties-events-selection-tab"></a>Eigenschaften der Ablaufverfolgungsvorlage (Registerkarte Ereignisauswahl)
  Die Registerkarte **Ereignisauswahl** im Dialogfeld **Eigenschaften der Ablaufverfolgungsvorlage** wird zum Anzeigen, Bearbeiten und Angeben von Ereignisklassen und Datenspalten verwendet, die in eine [!INCLUDE[ssSqlProfiler](../includes/sssqlprofiler-md.md)] -Ablaufverfolgungsvorlage eingeschlossen werden sollen.  
  
## <a name="options"></a>Optionen  
 Spalte**Ereignisse**  
 Geben Sie die Ereignisse an, für die eine Ablaufverfolgung ausgeführt werden soll, indem Sie das betreffende Kontrollkästchen in der Ereignisspalte aktivieren bzw. deaktivieren. Die Ereignisse sind nach Ereigniskategorien angeordnet.  
  
 Wenn Sie auf der Registerkarte **Allgemein** die Option **Neue Vorlage auf vorhandener basieren** auswählen, werden die Ereignisse der angegebenen Vorlage entsprechend automatisch ausgewählt. Weitere Informationen zu Ereignisklassen finden Sie unter [Ereignisklassen in SQL Server – Referenz](../relational-databases/event-classes/sql-server-event-class-reference.md).  
  
 Datenspalten  
 Geben Sie die Datenspalten an, für die eine Ablaufverfolgung ausgeführt werden soll, indem Sie das Kontrollkästchen für das Ereignis und die benötigte Datenspalte aktivieren. Die relevanten Ereignisspalten werden standardmäßig für die einzelnen in die Ablaufverfolgung eingeschlossenen Ereignisse aktiviert, sofern das Kontrollkästchen des entsprechenden Ereignisses aktiviert ist. Wenn Sie auf der Registerkarte **Allgemein** die Option **Neue Vorlage auf vorhandener basieren** aktiviert haben, werden die Datenspalten und Filter der angegebenen Vorlage entsprechend automatisch ausgewählt.  
  
 Sie können Filter festlegen, indem Sie auf die Spaltenüberschrift klicken und die Filterkriterien eingeben. Gefilterte Datenspalten sind im Dialogfeld **Filter bearbeiten** links neben der Spaltenbezeichnung durch ein Filtersymbol gekennzeichnet.  
  
 **Alle Ereignisse anzeigen**  
 Zeigt alle verfügbaren Ereignisse an. Diese Option ist standardmäßig aktiviert, wenn Sie eine neue Vorlage erstellen, die nicht auf einer vorhandenen Vorlage basiert. Deaktivieren Sie diese Option, um alle nicht ausgewählten Ereignisse im Raster **Ereignisauswahl** auszublenden.  
  
 **Alle Spalten anzeigen**  
 Zeigt alle verfügbaren Datenspalten an. Diese Option ist standardmäßig aktiviert, wenn Sie eine neue Vorlage erstellen, die nicht auf einer vorhandenen Vorlage basiert. Deaktivieren Sie diese Option, um alle nicht ausgewählten Datenspalten im Raster **Ereignisauswahl** auszublenden.  
  
 **Spaltenfilter**  
 Öffnet das Dialogfeld **Filter bearbeiten**, in dem links neben der Datenspaltenbezeichnung ein Filtersymbol angezeigt wird. Mithilfe des Dialogfelds **Filter bearbeiten** können Sie Datenspaltenfilter bearbeiten.  
  
 **Spalten organisieren**  
 Ändert die Reihenfolge der Spalten in der Ablaufverfolgung und gruppiert die Ergebnisse in einer oder mehreren Spalten.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Angeben von Ereignissen und Datenspalten für eine Ablauf Verfolgungs Datei &#40;SQL Server Profiler&#41;](../tools/sql-server-profiler/specify-events-and-data-columns-for-a-trace-file-sql-server-profiler.md)   
 [Organisieren der in einer Ablauf Verfolgung angezeigten Spalten &#40;SQL Server Profiler&#41;](../tools/sql-server-profiler/organize-columns-displayed-in-a-trace-sql-server-profiler.md)   
 [Ereignisse in einer Ablauf Verfolgung &#40;SQL Server Profiler Filtern&#41;](../tools/sql-server-profiler/filter-events-in-a-trace-sql-server-profiler.md)   
 [Filter Informationen &#40;SQL Server Profiler anzeigen&#41;](../tools/sql-server-profiler/view-filter-information-sql-server-profiler.md)   
 [Ändern eines Filters &#40;SQL Server Profiler&#41;](../tools/sql-server-profiler/modify-a-filter-sql-server-profiler.md)   
 [SQL Server Profiler Vorlagen und Berechtigungen](../tools/sql-server-profiler/sql-server-profiler-templates-and-permissions.md)   
 [SQL Server Profiler](../tools/sql-server-profiler/sql-server-profiler.md)  
  
  
