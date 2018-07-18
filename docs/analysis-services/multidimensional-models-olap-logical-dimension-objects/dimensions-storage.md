---
title: Dimension-Speicher | Microsoft Docs
ms.date: 05/02/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: olap
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 3d739bd19cd5be1f9b6167acbf104f569fc517ec
ms.sourcegitcommit: c12a7416d1996a3bcce3ebf4a3c9abe61b02fb9e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/10/2018
ms.locfileid: "34022797"
---
# <a name="dimensions---storage"></a>Dimensionen - Speicher
[!INCLUDE[ssas-appliesto-sqlas](../../includes/ssas-appliesto-sqlas.md)]
  Dimensionen in [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] unterstützen zwei Speichermodi:  
  
-   Relationale OLAP (ROLAP)  
  
-   Mehrdimensionale OLAP (MOLAP)  
  
 Durch den Speichermodus werden der Speicherort und die Form der Daten einer Dimension bestimmt. MOLAP ist der Standardspeichermodus für Dimensionen. **Verwandte Themen:**[Partition Speichermodi und Verarbeitung](../../analysis-services/multidimensional-models-olap-logical-cube-objects/partitions-partition-storage-modes-and-processing.md)  
  
## <a name="molap"></a>MOLAP  
 Daten für eine Dimension, die MOLAP verwendet, werden in einer mehrdimensionalen Struktur in einer Instanz von [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] gespeichert. Diese mehrdimensionale Struktur wird erstellt und aufgefüllt, wenn die Dimension verarbeitet wird. MOLAP-Dimensionen ermöglichen eine bessere Abfrageleistung als ROLAP-Dimensionen.  
  
## <a name="rolap"></a>ROLAP  
 Die Daten für eine Dimension, die ROLAP verwendet, werden eigentlich in den Tabellen gespeichert, die zum Definieren der Dimension verwendet werden. Der ROLAP-Speichermodus kann verwendet werden, um große Dimensionen ohne Kopieren großer Datenmengen zu unterstützen, allerdings zu Lasten der Abfrageleistung. Da die Dimension direkt von den Tabellen in der Datenquellensicht abhängt, die zum Definieren der Dimension verwendet wurden, unterstützt der ROLAP-Speichermodus auch Echtzeit-OLAP.  
  
> [!IMPORTANT]  
>  Wenn eine Dimension den ROLAP-Speichermodus verwendet und die Dimension in einen Cube eingeschlossen ist, der die MOLAP-Speicherung verwendet, muss auf jede Schemaänderung an der zugehörigen Quelltabelle die sofortige Verarbeitung des Cubes folgen. Erfolgt die Verarbeitung nicht, kann dies zu inkonsistenten Ergebnissen führen, wenn der Cube abgefragt wird. **Verwandtes Thema:**[Automatisieren von Analysis Services-Verwaltungsaufgaben mit SSIS](../../analysis-services/instances/automate-analysis-services-administrative-tasks-with-ssis.md).  
  
## <a name="see-also"></a>Siehe auch  
 [Partition Speichermodi und Verarbeitung](../../analysis-services/multidimensional-models-olap-logical-cube-objects/partitions-partition-storage-modes-and-processing.md)  
  
  
