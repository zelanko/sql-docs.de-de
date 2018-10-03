---
title: Zusammenführen von Partitionen (Dialogfeld) (Analysis Services – mehrdimensionale Daten) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.sqlserverstudio.mergepartition.f1
ms.assetid: 1c94e250-ee18-4f98-b112-985f6346102a
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: c18ffdaa50c6ee48896f2d2e6e65db46c8fe3349
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/02/2018
ms.locfileid: "48117422"
---
# <a name="merge-partition-dialog-box-analysis-services---multidimensional-data"></a>Dialogfeld 'Mergepartition' (Analysis Services – Mehrdimensionale Daten)
  Mithilfe des Dialogfelds **Mergepartition** in **SQL Server Management Studio** können Sie Partitionen für eine Measuregruppe in einem Cube zusammenführen. Sie können das Dialogfeld **Mergepartition** anzeigen, indem Sie mit der rechten Maustaste auf den Ordner „Partitionen“ oder eine Partition im **Objekt-Explorer** klicken und aus dem Kontextmenü die Option **Partitionen zusammenführen** auswählen.  
  
## <a name="options"></a>Tastatur  
 **Server**  
 Wählen Sie den Namen der Analysis Services-Instanz aus, die die Zielpartition enthält.  
  
 **Name**  
 Wählen Sie den Namen einer vorhandenen Partition aus, die als Zielpartition verwendet werden soll.  
  
 **Ordner**  
 Zeigt den Namen des Ordners an, der die Zielpartition enthält, wenn die unter Name ausgewählte Partition nicht den Standardordner für die Analysis Services-Instanz verwendet.  
  
 **Quellpartitionen**  
 Zeigt ein Raster mit den Quellpartitionen an, die in der Zielpartition zusammengeführt werden können.  
  
> [!NOTE]  
>  Nur Partitionen in derselben Measuregruppe, die dasselbe Aggregationsdesign verwenden, können zusammengeführt werden.  
  
 Das Raster enthält die folgenden Spalten:  
  
|Spalte|Description|  
|------------|-----------------|  
|**Merge**|Wählen Sie diese Option aus, um die Quellpartitionen in der Zielpartition zusammenzuführen.|  
|**Partitionsname**|Zeigt den Namen der Quellpartition an.|  
|**Zuletzt verarbeitet**|Zeigt das Datum und die Uhrzeit der letzten Verarbeitung der Quellpartition an.|  
  
## <a name="see-also"></a>Siehe auch  
 [Partitionen &#40;Analysis Services – mehrdimensionale Daten&#41;](multidimensional-models-olap-logical-cube-objects/partitions-analysis-services-multidimensional-data.md)   
 [Zusammenführen von Partitionen in Analysis Services &#40;SSAS – mehrdimensional&#41;](multidimensional-models/merge-partitions-in-analysis-services-ssas-multidimensional.md)  
  
  
