---
title: Debuggen des Datenflusses | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- progress reporting [Integration Services]
- data viewers [Integration Services]
- data flow [Integration Services], debugging
- debugging [Integration Services], data flow
- counting rows
ms.assetid: 1c574f1b-54f7-4c05-8e42-8620e2c1df0f
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: fdfaeeb9e8dafe82a1312593df2dd128635b8365
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "62766193"
---
# <a name="debugging-data-flow"></a>Debuggen des Datenflusses
  [!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] und der [!INCLUDE[ssIS](../../includes/ssis-md.md)] -Designer enthalten Funktionen und Tools, mit denen Sie die Datenflüsse in einem [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] -Paket behandeln können.  
  
-   
  [!INCLUDE[ssIS](../../includes/ssis-md.md)] -Designer stellt Daten-Viewer bereit.  
  
-   
  [!INCLUDE[ssIS](../../includes/ssis-md.md)] -Designer und [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] -Transformationen stellen die Zeilenanzahl bereit.  
  
-   
  [!INCLUDE[ssIS](../../includes/ssis-md.md)] -Designer stellt zur Laufzeit Fortschrittsberichte bereit.  
  
## <a name="data-viewers"></a>Daten-Viewer  
 Daten-Viewer zeigen Daten zwischen zwei Komponenten in einem Datenfluss an. Mit Daten-Viewern können Daten angezeigt werden, wenn die Daten von einer Datenquelle extrahiert werden und an einen Datenfluss weitergegeben werden, vor und nach dem Update der Daten durch eine Transformation sowie vor dem Laden der Daten in das Ziel.  
  
 Um die Daten anzuzeigen, fügen Sie dem Pfad, der zwei Datenflusskomponenten verbindet, Daten-Viewer hinzu. Durch die Möglichkeit, Daten zwischen Datenflusskomponenten anzuzeigen, können Sie auf einfache Weise unerwartete Datenwerte identifizieren, die Änderung von Spaltenwerten durch eine Transformation anzeigen sowie die Ursache für einen Fehler bei einer Transformation ermitteln. Beispielsweise kann es sein, dass bei einer Suche in einer Verweistabelle ein Fehler auftritt. Um dieses Problem zu beseitigen, können Sie eine Transformation hinzufügen, die Standarddaten für leere Spalten bereitstellt.  
  
 Ein Daten-Viewer kann Daten in einem Raster anzeigen. Bei einem Raster wählen Sie die Spalten aus, die angezeigt werden sollen. Die Werte für die ausgewählten Spalten werden im Tabellenformat angezeigt.  
  
 Sie können auch mehrere Daten-Viewer in einen Pfad einschließen. Daten können in unterschiedlichen Formaten angezeigt werden (erstellen Sie z.B. eine Diagrammansicht und eine Rasteransicht der Daten). Außerdem können Sie unterschiedliche Daten-Viewer für verschiedene Datenspalten erstellen.  
  
 Wenn Sie einem Pfad einen Daten-Viewer hinzufügen, fügt der [!INCLUDE[ssIS](../../includes/ssis-md.md)] -Designer der Entwurfsoberfläche der Registerkarte **Datenfluss** neben dem Pfad ein Daten-Viewer-Symbol hinzu. Transformationen mit mehreren Ausgaben, wie z. B. die Transformation für bedingtes Teilen, können in jedem Pfad einen Daten-Viewer enthalten.  
  
 Zur Laufzeit wird ein **Daten-Viewer** -Fenster geöffnet, in dem die vom Daten-Viewer-Format definierten Informationen angezeigt werden. Beispielsweise zeigt ein Daten-Viewer, der das Rasterformat verwendet, Daten für die ausgewählten Spalten, die Anzahl von an die Datenflusskomponente übergebenen Ausgabezeilen sowie die Anzahl dargestellter Zeilen an. Die Informationen werden pufferweise angezeigt und, ein Puffer kann, abhängig von der Zeilenbreite im Datenfluss, mehr oder weniger Zeilen enthalten.  
  
 Im Dialogfeld **Daten-Viewer** können Sie die Daten in die Zwischenablage kopieren, alle Daten aus der Tabelle löschen, den Daten-Viewer neu konfigurieren, den Datenfluss fortsetzen und den Daten-Viewer anfügen oder trennen.  
  
#### <a name="to-add-a-data-viewer"></a>So fügen Sie einen Daten-Viewer hinzu  
  
-   [Hinzufügen eines Daten-Viewers zu einem Datenfluss](../add-a-data-viewer-to-a-data-flow.md)  
  
## <a name="row-counts"></a>Zeilenanzahl  
 Die Anzahl von Zeilen, die über einen Pfad verschoben wurden, werden in der Entwurfsoberfläche der Registerkarte **Datenfluss** in [!INCLUDE[ssIS](../../includes/ssis-md.md)] neben dem Pfad angezeigt. Dieser Wert wird regelmäßig aktualisiert, während die Daten über den Pfad verschoben werden.  
  
 Sie können dem Datenfluss auch eine Transformation für Zeilenanzahl hinzufügen, um die endgültige Zeilenanzahl in einer Variablen aufzuzeichnen. Weitere Informationen finden Sie unter [Row Count Transformation](../data-flow/transformations/row-count-transformation.md).  
  
## <a name="progress-reporting"></a>Fortschrittsberichte  
 Wenn Sie ein Paket ausführen, stellt der [!INCLUDE[ssIS](../../includes/ssis-md.md)] -Designer den Fortschritt in der Entwurfsoberfläche der Registerkarte **Datenfluss** dar, indem jede Datenflusskomponente in der entsprechenden Statusfarbe dargestellt wird. Wenn eine Komponente mit der Arbeit beginnt, wird die Farbe von keiner Farbe in gelb geändert. Wenn die Komponente erfolgreich abgeschlossen ist, wird sie in grün geändert. Rot bedeutet, dass bei der Komponente ein Fehler aufgetreten ist.  
  
 In der folgenden Tabelle wird die Farbcodierung beschrieben.  
  
|Color|BESCHREIBUNG|  
|-----------|-----------------|  
|Keine Farbe|Wartet auf den Aufruf durch die Datenfluss-Engine.|  
|Gelb|Führt eine Transformation aus, extrahiert Daten oder lädt Daten.|  
|Grün|Wurde erfolgreich ausgeführt.|  
|red|Wurde mit Fehlern ausgeführt.|  
  
## <a name="see-also"></a>Weitere Informationen  
 [Tools zur Problembehandlung für die Paketentwicklung](troubleshooting-tools-for-package-development.md)  
  
  
