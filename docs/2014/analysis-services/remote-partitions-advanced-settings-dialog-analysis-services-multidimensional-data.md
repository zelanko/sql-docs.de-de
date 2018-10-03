---
title: Remotepartitionen - Erweiterte Einstellungen (Dialogfeld) (Analysis Services – mehrdimensionale Daten) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.sqlserverstudio.advancedrestoresettings.f1
ms.assetid: a03bb7e1-efaf-47c8-b0ee-f3e4438311cb
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 7677776bb1adf21d3234f770a9e2941edfa70ed0
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/02/2018
ms.locfileid: "48074930"
---
# <a name="remote-partitions---advanced-settings-dialog-box-analysis-services---multidimensional-data"></a>Dialogfeld 'Remote-Partitionen – Erweiterte Einstellungen' (Analysis Services – Mehrdimensionale Daten)
  Mithilfe des Dialogfelds **Remotepartitionen – Erweiterte Einstellungen** in [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] können Sie erweiterte Einstellungen bearbeiten, z.B. die Verbindungszeichenfolge der Datenquelle, die die [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]-Remotedatenbank zur Wartung von Remotepartitionen darstellt. Dagegen wird zum Wiederherstellen von Remotepartitionen aus einer Remotesicherungsdatei in eine [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]-Datenbank das Dialogfeld **Datenbank wiederherstellen** verwendet. Sie können das Dialogfeld **Remotepartitionen – Erweiterte Einstellungen** über die Seite **Partitionen** des Dialogfelds **Datenbank wiederherstellen** anzeigen, indem Sie nach dem Auswählen der Option**Remotepartitionen wiederherstellen**für eine Remotepartition auf die Schaltfläche mit den Auslassungspunkten ( **...** ) klicken.  
  
## <a name="options"></a>Tastatur  
  
|Begriff|Definition|  
|----------|----------------|  
|**Datenquellenname**|Zeigt den Namen der Datenquelle an, die die [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]-Remotedatenbank zur Verwaltung der aufgeführten Remotepartitionen darstellt.|  
|**Sicherungsdatei**|Zeigt den Namen der Remotesicherungsdatei an, die die wiederherzustellenden Daten für die aufgeführten Remotepartitionen enthält.<br /><br /> Hinweis: Wenn in eine remotesicherungsdatei angegeben wurde, wird keine Sicherungsdatei angezeigt der **Sicherungsdatei** Spalte auf die **Partitionen** auf der Seite die **Restore Database** Dialogfeld.|  
|**Verbindungszeichenfolge**|Zeigt die Verbindungszeichenfolge für die unter **Datenquellenname**angezeigte Datenquelle an.|  
|**Bearbeiten**|Klicken Sie auf diese Option, um das Dialogfeld **Datenlinkeigenschaften** anzuzeigen und die Eigenschaften der Verbindungszeichenfolge zu bearbeiten.|  
|**Partitionsliste**|Wählen Sie diese Option aus, um verschiedene Speicherorte anzugeben, an welchen Remotepartitionen wiederhergestellt werden. Beachten Sie, dass Sie den Wiederherstellungsordner einer Remotepartition nur ändern können, wenn für die Remotepartition im Cube ein anderer als der Standardspeicherort angegeben wurde. Mithilfe des folgenden bei Auswahl dieser Option aktivierten Rasters können Sie für jede Remotepartition einen Wiederherstellungsordner angeben:<br /><br /> **Cube**: Zeigt den Namen des Cubes, der die jeweilige Remotepartition enthalten.<br /><br /> **MeasureGroup**: Zeigt den Namen der Measuregruppe, die die Remotepartition enthält.<br /><br /> **Partition**: Zeigt den Namen der Remotepartition.<br /><br /> **Größe (MB)**: Zeigt die Größe der Remotepartition in Megabytes an.<br /><br /> **Ursprünglicher Ordner**: Zeigt den Namen des ursprünglichen Ordners, in dem die Remotepartition gespeichert wurde.<br /><br /> **Wiederherstellungsordner**: Geben Sie den Namen des wiederherstellungsordners für die Remotepartition ein, oder klicken Sie auf die Schaltfläche mit den Auslassungspunkten (**...** ) zum Anzeigen der **nach Remoteordner suchen** Dialogfeld und wählen Sie den Pfad des Ordners zu verwenden. Weitere Informationen zum Dialogfeld **Nach Remoteordner suchen** finden Sie unter [Dialogfeld „Nach Remoteordner suchen“ &#40;Analysis Services – Mehrdimensionale Daten&#41;](browse-for-remote-folder-dialog-box-analysis-services-multidimensional-data.md).|  
  
## <a name="see-also"></a>Siehe auch  
 [Analysis Services-Designer und-Dialogfelder &#40;mehrdimensionale Daten&#41;](analysis-services-designers-and-dialog-boxes-multidimensional-data.md)   
 [Partitionen &#40;Dialogfeld Datenbank wiederherstellen&#41; &#40;Analysis Services – mehrdimensionale Daten&#41;](partitions-restore-database-dialog-box-analysis-services-multidimensional-data.md)   
 [Sichern und Wiederherstellen von Analysis Services-Datenbanken](multidimensional-models/backup-and-restore-of-analysis-services-databases.md)  
  
  
