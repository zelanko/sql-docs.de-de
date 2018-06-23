---
title: Weisen Sie die Aggregation (Dialogfeld) (Analysis Services – mehrdimensionale Daten) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- sql12.asvs.sqlserverstudio.copyaggregationdesign.f1
ms.assetid: 50c26cb1-c294-4f17-8b9e-435fdbd4806d
caps.latest.revision: 18
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: 6aba2628057c8a26ba7ee8fd5262ad1e524baf1b
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/19/2018
ms.locfileid: "36056115"
---
# <a name="assign-aggregation-design-dialog-box-analysis-services---multidimensional-data"></a>Dialogfeld 'Aggregationsentwurf zuweisen' (Analysis Services - Mehrdimensionale Daten)
  Mithilfe des Dialogfelds **Aggregationsentwurf zuweisen** in [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] können Sie Aggregationsentwürfe einer oder mehreren Zielpartitionen zuweisen. Sie können das Dialogfeld **Aggregationsentwurf zuweisen** anzeigen, indem Sie mit der rechten Maustaste im **Objekt-Explorer** auf eine Partition oder einen Aggregationsentwurf klicken und **Aggregationsentwurf zuweisen**auswählen.  
  
## <a name="options"></a>Tastatur  
  
|Begriff|Definition|  
|----------|----------------|  
|**Aggregationsentwürfe**|Wählen Sie einen Aggregationsentwurf aus, um ihn einer oder mehreren Zielpartitionen zuzuweisen.|  
|**Zielpartitionen**|Wählen Sie die Partitionen aus, denen Sie den Aggregationsentwurf zuweisen möchten. Das folgende Raster wird verwendet, um Zielpartitionen anzugeben:<br /><br /> \<das Kontrollkästchen >: Aktivieren oder deaktivieren Sie das Kontrollkästchen im Spaltenheader, um alle aufgelisteten Partitionen als Zielpartitionen einzuschließen oder auszuschließen. Aktivieren oder deaktivieren Sie das Kontrollkästchen neben einer Partition, um diese Partition als Zielpartition einzuschließen oder auszuschließen.<br /><br /> **Partition**: Zeigt den Namen der Partition.<br /><br /> **Quelle**: Zeigt die Quelltabelle oder Abfrage für die Partition.<br /><br /> **Aggregationsentwurf**: Zeigt den Namen des vorhandenen Aggregationsentwurfs für die Partition.|  
|**Partitionen mit Aggregationsentwürfen ausblenden**|Wählen Sie diese Option aus, um nur die Partitionen anzuzeigen, denen keine Aggregationsentwürfe zugewiesen sind.|  
  
## <a name="see-also"></a>Siehe auch  
 [Aggregationen und Aggregationsentwürfe](multidimensional-models-olap-logical-cube-objects/aggregations-and-aggregation-designs.md)  
  
  