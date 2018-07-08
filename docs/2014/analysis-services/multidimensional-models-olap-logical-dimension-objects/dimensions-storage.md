---
title: Dimension-Speicher | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- dimensions [Analysis Services], storage
- storing data [Analysis Services]
- storage [Analysis Services], dimensions
- relational OLAP
- multidimensional OLAP
- MOLAP
- storing data [Analysis Services], dimensions
- ROLAP
ms.assetid: 8d74b932-2174-4e1f-8414-636455880b6a
caps.latest.revision: 30
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 6462ebf90b7783260f7027d82b26be117ea0b5ce
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/02/2018
ms.locfileid: "37153111"
---
# <a name="dimension-storage"></a>Speichern von Dimensionen
  Dimensionen in [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] unterstützen zwei Speichermodi:  
  
-   Relationale OLAP (ROLAP)  
  
-   Mehrdimensionale OLAP (MOLAP)  
  
 Durch den Speichermodus werden der Speicherort und die Form der Daten einer Dimension bestimmt. MOLAP ist der Standardspeichermodus für Dimensionen. **Verwandte Themen:**[Partition Speichermodi und Verarbeitung](../multidimensional-models-olap-logical-cube-objects/partitions-partition-storage-modes-and-processing.md)  
  
## <a name="molap"></a>MOLAP  
 Daten für eine Dimension, die MOLAP verwendet, werden in einer mehrdimensionalen Struktur in einer Instanz von [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] gespeichert. Diese mehrdimensionale Struktur wird erstellt und aufgefüllt, wenn die Dimension verarbeitet wird. MOLAP-Dimensionen ermöglichen eine bessere Abfrageleistung als ROLAP-Dimensionen.  
  
## <a name="rolap"></a>ROLAP  
 Die Daten für eine Dimension, die ROLAP verwendet, werden eigentlich in den Tabellen gespeichert, die zum Definieren der Dimension verwendet werden. Der ROLAP-Speichermodus kann verwendet werden, um große Dimensionen ohne Kopieren großer Datenmengen zu unterstützen, allerdings zu Lasten der Abfrageleistung. Da die Dimension direkt von den Tabellen in der Datenquellensicht abhängt, die zum Definieren der Dimension verwendet wurden, unterstützt der ROLAP-Speichermodus auch Echtzeit-OLAP.  
  
> [!IMPORTANT]  
>  Wenn eine Dimension den ROLAP-Speichermodus verwendet und die Dimension in einen Cube eingeschlossen ist, der die MOLAP-Speicherung verwendet, muss auf jede Schemaänderung an der zugehörigen Quelltabelle die sofortige Verarbeitung des Cubes folgen. Erfolgt die Verarbeitung nicht, kann dies zu inkonsistenten Ergebnissen führen, wenn der Cube abgefragt wird. **Verwandtes Thema:**[Automatisieren von Analysis Services-Verwaltungsaufgaben mit SSIS](../instances/automate-analysis-services-administrative-tasks-with-ssis.md).  
  
## <a name="see-also"></a>Siehe auch  
 [Speichermodi und Verarbeitung von Partitionen](../multidimensional-models-olap-logical-cube-objects/partitions-partition-storage-modes-and-processing.md)  
  
  
