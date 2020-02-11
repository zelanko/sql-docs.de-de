---
title: Remote Partitionen | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: reference
helpviewer_keywords:
- storage [Analysis Services], partitions
- archiving remote partitions [Analysis Services]
- partitions [Analysis Services], remote
- restoring remote partitions [Analysis Services]
- backing up remote partitions [Analysis Services]
- partitions [Analysis Services], storage
- storing data [Analysis Services], partitions
- MasterDataSourceID property
- remote partitions [Analysis Services]
ms.assetid: 63f5d9f5-c6b6-4ceb-94fe-7b6c396d10bb
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: d092c33c8c350dc19b749fd3b31ccf1b8c73eac6
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "62727339"
---
# <a name="remote-partitions"></a>Remotepartitionen
  Die Daten einer Remote Partition werden in einer anderen Instanz von Microsoft [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] gespeichert als die Instanz, die die Definitionen (Metadaten) der Partition und des übergeordneten Cubes enthält. Eine Remotepartition wird auf derselben Instanz von [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] verwaltet, auf der die Partition und der übergeordnete Cube definiert sind.  
  
> [!NOTE]  
>  Zum Speichern einer Remote Partition muss auf dem Computer eine Instanz von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] installiert sein, und es muss dieselbe Service Pack Ebene wie die Instanz, auf der die Partition definiert wurde, ausgeführt werden. Remotepartitionen auf Instanzen einer früheren Version von [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] werden nicht unterstützt.  
  
 Wenn Remotepartitionen in einer Measuregruppe enthalten sind, wird die Arbeitsspeicher- und CPU-Nutzung des Cubes auf alle Partitionen in der Measuregruppe verteilt. Wenn beispielsweise eine Remotepartition verarbeitet wird (entweder allein oder als Teil der Verarbeitung des übergeordneten Cubes), erfolgt ein großer Teil der Arbeitsspeicher- und CPU-Nutzung für diese Partition auf der Remoteinstanz von [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)].  
  
> [!NOTE]  
>  Ein Cube, der Remotepartitionen enthält, kann Dimensionen mit aktiviertem Schreibzugriff enthalten. Dies kann sich jedoch auf die Leistung für diesen Cube auswirken. Weitere Informationen zu Dimensionen mit aktiviertem Schreibzugriff finden Sie unter [Dimensionen mit aktiviertem Schreib](../multidimensional-models-olap-logical-dimension-objects/write-enabled-dimensions.md)Zugriff.  
  
## <a name="storage-modes-for-remote-partitions"></a>Speichermodi für Remotepartitionen  
 Remotepartitionen können alle Speichertypen verwenden, die von lokalen Partitionen verwendet werden: mehrdimensionale OLAP (MOLAP), hybride OLAP (HOLAP) oder relationale OLAP (ROLAP). Remotepartitionen können zudem die proaktive Zwischenspeicherung verwenden. Die folgenden Daten werden in Abhängigkeit vom Speichermodus einer Remotepartition auf der Remoteinstanz von [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] gespeichert.  
  
|||  
|-|-|  
|Speichertyp|Data|  
|MOLAP|Die Aggregationen einer Partition sowie eine Kopie der Quelldaten der Partition|  
|HOLAP|Die Aggregationen von Partitionen|  
|ROLAP|Keine Partitionsdaten|  
  
 Wenn eine Measuregruppe mehrere MOLAP- oder HOLAP-Partitionen enthält, die auf mehreren Instanzen von [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] gespeichert sind, verteilt der Cube die Daten in den Measuregruppendaten auf diese Instanzen von [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)].  
  
## <a name="merging-remote-partitions"></a>Zusammenführen von Remotepartitionen  
 Remotepartitionen können nur mit anderen Remotepartitionen zusammengeführt werden, die auf der gleichen Remoteinstanz von [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] gespeichert sind. Weitere Informationen zum Zusammenführen von Partitionen finden Sie unter zusammen [führen von Partitionen in Analysis Services &#40;SSAS-Multidimensional&#41;](../multidimensional-models/merge-partitions-in-analysis-services-ssas-multidimensional.md).  
  
## <a name="archiving-and-restoring-remote-partitions"></a>Archivieren und Wiederherstellen von Remotepartitionen  
 Daten in Remotepartitionen können archiviert oder wiederhergestellt werden, wenn die Datenbank, in der die Remotepartition gespeichert ist, archiviert oder wiederhergestellt wird. Wenn Sie eine Datenbank ohne Wiederherstellung einer Remotepartition wiederherstellen, müssen Sie die Remotepartition verarbeiten, bevor Sie die Daten in der Partition verwenden können. Weitere Informationen zum Archivieren und Wiederherstellen von Datenbanken finden Sie unter [Sichern und Wiederherstellen von Analysis Services Datenbanken](../multidimensional-models/backup-and-restore-of-analysis-services-databases.md).  
  
## <a name="see-also"></a>Weitere Informationen  
 [Erstellen und Verwalten einer Remote Partition &#40;Analysis Services&#41;](../multidimensional-models/create-and-manage-a-remote-partition-analysis-services.md)   
 [Verarbeiten von Analysis Services Objekten](../multidimensional-models/processing-analysis-services-objects.md)  
  
  
