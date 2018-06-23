---
title: SQL Server Profiler - Spalten organisieren | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- sql12.pro.organize.columns.f1
ms.assetid: bf5674f4-da5e-43f9-aeb2-76ca37993790
caps.latest.revision: 8
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 69622d02bbe0eae497f7d6e463ea6d40eb6536cd
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/19/2018
ms.locfileid: "36159221"
---
# <a name="sql-server-profiler---organize-columns"></a>SQL Server Profiler - Spalten organisieren
  Verwenden Sie das Dialogfeld **Spalten organisieren** , um Datenspalten für das Gruppieren oder Aggregieren von Ereignissen auszuwählen, die in einer Ablaufverfolgung angezeigt werden. Dadurch können große Ablaufverfolgungsdateien und -tabellen einfacher gelesen und analysiert werden.  
  
 Durch das Aggregieren werden alle Ereignisse in der Ablaufverfolgung unter die jeweiligen Ereignisklassentypen verschoben und reduziert. Links neben dem Ereignisklassennamen wird ein Pluszeichen (**+**) angezeigt. Wenn Sie auf das Pluszeichen klicken, wird die Ereignisklasse expandiert, sodass alle Ereignisse dieses Typs angezeigt werden.  
  
 Mithilfe der Gruppierung werden alle Ereignisklassen eines bestimmten Typs im Ablaufverfolgungsfenster zusammengefasst angezeigt. Die Ereignisse werden jedoch nicht unter dem Ereignisklassentyp reduziert.  
  
 Wenn Sie Ereignisse in der Anzeige des Ablaufverfolgungsfensters gruppieren oder aggregieren, bleiben die dafür ausgewählten Spalten im Anzeigefenster fixiert, aber Sie können einen Bildlauf nach links oder rechts ausführen, um alle anderen Datenspalten anzuzeigen.  
  
 Um auf dieses Dialogfeld zuzugreifen, öffnen Sie eine vorhandene Ablaufverfolgungsdatei oder -tabelle, und klicken Sie auf im Menü **Datei** von [!INCLUDE[ssSqlProfiler](../includes/sssqlprofiler-md.md)] **Eigenschaften** . Klicken Sie im Dialogfeld **Ablaufverfolgungseigenschaften** auf die Registerkarte **Ereignisauswahl** , und dann auf **Spalten organisieren**. Sie können in der Registerkarte **Ereignisauswahl** auch auf **Spalten organisieren** klicken, wenn Sie eine neue Ablaufverfolgung erstellen.  
  
## <a name="options"></a>Tastatur  
 **Gruppen**  
 Verschieben Sie die Datenspaltennamen unter **Gruppen** , um Ereignisklassen im Ablaufverfolgungsfenster zu gruppieren oder aggregieren.  
  
 Um Ereignisse zu aggregieren, verschieben Sie eine Datenspalte in die **Gruppen**. Dadurch werden alle Ereignisse eines bestimmten Typs unter dem Namen des Ereignisklassentyps in der Anzeige im Ablaufverfolgungsfenster reduziert. Links neben dem Ereignisklassennamen wird ein Pluszeichen (**+**) angezeigt. Klicken Sie auf das Pluszeichen, um den Ereignisklassentyp zu expandieren und alle Ereignisse anzuzeigen. Sie können die Aggregierung bzw. Gruppierung ein- und ausschalten, indem Sie im Menü **Ansicht** auf **Aggregierte Ansicht** bzw. **Gruppierte Ansicht** klicken.  
  
 Um Ereignisse zu gruppieren, verschieben Sie mehrere Datenspalten in die **Gruppen**. Dadurch werden alle Ereignisse eines bestimmten Typs zusammen in der Anzeige des Ablaufverfolgungsfensters gruppiert, aber nicht unter dem Namen des jeweiligen Ereignisklassentyps reduziert. Sie können zwischen der gruppierten und der nicht gruppierten Ansicht wechseln, indem Sie im Menü Ansicht auf **Gruppierte Ansicht** klicken. Wenn mehr als eine Datenspalte in die **Gruppen**verschoben wird, ist die Option zum Wechseln in die **Aggregierte Ansicht** nicht verfügbar.  
  
 **Spalten**  
 Liste der Datenspalten, die für das Verschieben in **Gruppen**verfügbar sind. Klicken Sie auf das Pluszeichen (**+**) links neben **Spalten** , um die Liste zu erweitern.  
  
 **Nach oben**  
 Klicken Sie nach dem Auswählen einer Datenspalte auf **Nach oben** , um die Datenspalten nach oben in **Gruppen**zu verschieben. Sie können auch auf **Nach oben** klicken, um die Anzeige der Spalten im Ablaufverfolgungsfenster neu anzuordnen.  
  
 **Nach unten**  
 Klicken Sie nach dem Auswählen einer Datenspalte auf **Nach unten** , um die Datenspalten aus den **Gruppen**heraus zu verschieben. Sie können auch auf **Nach unten** klicken, um die Anzeige der Spalten im Ablaufverfolgungsfenster neu anzuordnen.  
  
## <a name="see-also"></a>Siehe auch  
 [Organisieren von in einer Ablaufverfolgung angezeigten Spalten &#40;SQL Server Profiler&#41;](../tools/sql-server-profiler/organize-columns-displayed-in-a-trace-sql-server-profiler.md)   
 [Erstellen einer Ablaufverfolgung &#40;SQL Server Profiler&#41;](../tools/sql-server-profiler/create-a-trace-sql-server-profiler.md)   
 [Erstellen einer Ablaufverfolgungsvorlage &#40;SQL Server Profiler&#41;](../tools/sql-server-profiler/create-a-trace-template-sql-server-profiler.md)   
 [Öffnen einer Ablaufverfolgungsdatei &#40;SQL Server Profiler&#41;](../tools/sql-server-profiler/open-a-trace-file-sql-server-profiler.md)   
 [Öffnen einer Ablaufverfolgungstabelle &#40;SQL Server Profiler&#41;](../tools/sql-server-profiler/open-a-trace-table-sql-server-profiler.md)  
  
  