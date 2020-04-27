---
title: Dialog Feld "Remote Partitionen-Erweiterte Einstellungen" (Analysis Services Mehrdimensionale Daten) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.sqlserverstudio.advancedrestoresettings.f1
ms.assetid: a03bb7e1-efaf-47c8-b0ee-f3e4438311cb
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 1ca3f12ff53c4291d8bbe7c8eb97ce8e47172ea3
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/26/2020
ms.locfileid: "66070382"
---
# <a name="remote-partitions---advanced-settings-dialog-box-analysis-services---multidimensional-data"></a>Dialogfeld 'Remote-Partitionen – Erweiterte Einstellungen' (Analysis Services – Mehrdimensionale Daten)
  Mithilfe des Dialogfelds **Remotepartitionen – Erweiterte Einstellungen** in [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] können Sie erweiterte Einstellungen bearbeiten, z.B. die Verbindungszeichenfolge der Datenquelle, die die [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] -Remotedatenbank zur Wartung von Remotepartitionen darstellt. Dagegen wird zum Wiederherstellen von Remotepartitionen aus einer Remotesicherungsdatei in eine [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] -Datenbank das Dialogfeld **Datenbank wiederherstellen** verwendet. Sie können das Dialogfeld **Remotepartitionen – Erweiterte Einstellungen** über die Seite **Partitionen** des Dialogfelds **Datenbank wiederherstellen** anzeigen, indem Sie nach dem Auswählen der Option**Remotepartitionen wiederherstellen**für eine Remotepartition auf die Schaltfläche mit den Auslassungspunkten ( **...** ) klicken.  
  
## <a name="options"></a>Optionen  
  
|Begriff|Definition|  
|----------|----------------|  
|**Datenquellen Name**|Zeigt den Namen der Datenquelle an, die die [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] -Remotedatenbank zur Verwaltung der aufgeführten Remotepartitionen darstellt.|  
|**Sicherungsdatei**|Zeigt den Namen der Remotesicherungsdatei an, die die wiederherzustellenden Daten für die aufgeführten Remotepartitionen enthält.<br /><br /> Hinweis: Es wird keine Sicherungsdatei angezeigt, wenn in der Spalte **Sicherungsdatei** auf der Seite **Partitionen** des Dialog Felds **Datenbank wiederherstellen** eine Remote Sicherungsdatei angegeben wurde.|  
|**Verbindungszeichenfolge**|Zeigt die Verbindungszeichenfolge für die unter **Datenquellenname**angezeigte Datenquelle an.|  
|**Bearbeiten**|Klicken Sie auf diese Option, um das Dialogfeld **Datenlinkeigenschaften** anzuzeigen und die Eigenschaften der Verbindungszeichenfolge zu bearbeiten.|  
|**Liste der Partitionen**|Wählen Sie diese Option aus, um verschiedene Speicherorte anzugeben, an welchen Remotepartitionen wiederhergestellt werden. Beachten Sie, dass Sie den Wiederherstellungsordner einer Remotepartition nur ändern können, wenn für die Remotepartition im Cube ein anderer als der Standardspeicherort angegeben wurde. Mithilfe des folgenden bei Auswahl dieser Option aktivierten Rasters können Sie für jede Remotepartition einen Wiederherstellungsordner angeben:<br /><br /> **Cube**: zeigt den Namen des Cubes an, der die Remote Partition enthält.<br /><br /> **Measregroup**: zeigt den Namen der Measure-Gruppe an, die die Remote Partition enthält.<br /><br /> **Partition**: zeigt den Namen der Remote Partition an.<br /><br /> **Size (MB)**: zeigt die Größe der Remote Partition in Megabyte an.<br /><br /> **Ursprünglicher Ordner**: zeigt den Namen des ursprünglichen Ordners an, in dem die Remote Partition gespeichert wurde.<br /><br /> **Wiederherstellungs Ordner**: Geben Sie den Namen des Wiederherstellungs Ordners für die Remote Partition ein, oder klicken Sie auf die Schaltfläche mit den Auslassungs Punkten (**...**), um das Dialogfeld **nach Remote Ordner suchen** anzuzeigen und den Pfad des zu verwendenden Ordners auszuwählen. Weitere Informationen zum Dialogfeld **Nach Remoteordner suchen** finden Sie unter [Dialogfeld „Nach Remoteordner suchen“ &#40;Analysis Services – Mehrdimensionale Daten&#41;](browse-for-remote-folder-dialog-box-analysis-services-multidimensional-data.md).|  
  
## <a name="see-also"></a>Weitere Informationen  
 [Analysis Services Designer und Dialog Felder &#40;Mehrdimensionale Daten&#41;](analysis-services-designers-and-dialog-boxes-multidimensional-data.md)   
 [Partitionen &#40;Dialog Feld Datenbank wiederherstellen&#41; &#40;Analysis Services Mehrdimensionale Daten&#41;](partitions-restore-database-dialog-box-analysis-services-multidimensional-data.md)   
 [Sichern und Wiederherstellen von Analysis Services-Datenbanken](multidimensional-models/backup-and-restore-of-analysis-services-databases.md)  
  
  
