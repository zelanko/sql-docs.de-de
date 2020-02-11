---
title: Verarbeitungs-und Speicherorte (Partitions-Assistent) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.partitionwizard.specifyprocessingandstorage.f1
ms.assetid: dda2dc57-923d-4db9-93a7-38e95770f3df
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 73340613b14c8f0e90340b589c8b97bad7cd5599
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "66070651"
---
# <a name="processing-and-storage-locations-partition-wizard"></a>Speicherorte zum Verarbeiten und Speichern (Partitions-Assistent)
  Mithilfe der Seite **Speicherorte zum Verarbeiten und Speichern** können Sie die [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] -Instanz des Cubes angeben, der die Partition besitzt, sowie die [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] -Instanz, die die Daten für die Partition speichert. Sie können eine Partition als Remotepartition definieren, indem Sie entweder eine [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] -Remoteinstanz oder einen vom Standardspeicherort abweichenden Speicherort angeben. Weitere Informationen zu Remotepartitionen finden Sie unter [Remotepartitionen](multidimensional-models-olap-logical-cube-objects/partitions-remote-partitions.md).  
  
## <a name="processing-location-options"></a>Verarbeitungsstandort (Optionen)  
 **Aktuelle Serverinstanz**  
 Macht die aktuelle [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] -Instanz für die Verarbeitung der Partition verantwortlich.  
  
 **Remotedatenquelle für SQL Server Analysis Services**  
 Macht eine [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] -Remoteinstanz für die Verarbeitung dieser Partition verantwortlich.  
  
 Wählen Sie aus der Dropdownliste die Datenquelle aus, die die für die Verarbeitung der Partition verantwortliche [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] -Remoteinstanz darstellt.  
  
> [!NOTE]  
>  Wenn Sie eine Datenquelle auswählen, in der die Eigenschaft der `Initial Catalog`-Verbindungszeichenfolge nicht auf eine gültige [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]-Datenbank festgelegt ist, oder wenn die in der Eigenschaft der `Initial Catalog`-Verbindungszeichenfolge angegebene Datenbank keine Remotepartitionen unterstützt (d. h. die `MasterDatasourceID`-Eigenschaft der angegebenen Datenbank ist nicht auf einen gültigen Wert festgelegt), tritt ein Fehler auf.  
  
 **Neu**  
 Erstellt eine neue Datenquelle, die die für die Verarbeitung der Partition verantwortliche [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] -Remoteinstanz darstellt.  
  
## <a name="storage-location-options"></a>Speicherort (Optionen)  
 **Standardmäßiger Serverstandort**  
 Legt den Datenordner der aktuellen [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] -Instanz als Speicherort der Aggregations- und Indizierungsdaten für die Partition fest.  
  
 **Angegebener Ordner**  
 Gibt den Speicherort der Aggregations- und Indizierungsdaten für die Partition an.  
  
 **...**  
 Zeigt das Dialogfeld **Nach Remoteordner suchen** an, in dem Sie einen Ordner für **Angegebener Ordner**auswählen können.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Partitions-Assistent (F1-Hilfe &#40;Analysis Services-mehrdimensionalen Daten&#41;](partition-wizard-f1-help-analysis-services-multidimensional-data.md)   
 [Partitionen &#40;Analysis Services Mehrdimensionale Daten&#41;](multidimensional-models-olap-logical-cube-objects/partitions-analysis-services-multidimensional-data.md)   
 [Dialog Feld "Remote Ordner suchen" &#40;Analysis Services Mehrdimensionale Daten&#41;](browse-for-remote-folder-dialog-box-analysis-services-multidimensional-data.md)  
  
  
