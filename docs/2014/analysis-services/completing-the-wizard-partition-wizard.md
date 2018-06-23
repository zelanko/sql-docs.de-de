---
title: Assistenten abschließen (Partitions-Assistent) | Microsoft Docs
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
- sql12.asvs.partitionwizard.finish.f1
ms.assetid: 68a4dd5d-94d9-4a02-be31-949a6da0ef51
caps.latest.revision: 23
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: 77c297c3deb6cc63e972b695c7d02c1f5b937713
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/19/2018
ms.locfileid: "36161690"
---
# <a name="completing-the-wizard-partition-wizard"></a>Assistenten abschließen (Partitions-Assistent)
  Mithilfe der Seite **Assistenten abschließen** können Sie der Partition einen Namen zuweisen, den Aggregationsentwurf für die Partition definieren und optional die Partition nach dem Abschließen des Partitions-Assistenten bereitstellen und verarbeiten.  
  
## <a name="options"></a>Tastatur  
 **Name**  
 Geben Sie den Namen für die neue Partition ein. Wenn Sie mit mehreren Tabellen arbeiten, geben Sie den Präfix ein, der mit dem Tabellennamen kombiniert wird, um den Partitionsnamen zu bilden.  
  
 **Aggregationsoptionen festlegen**  
 Gibt die Aggregationsoption für die Partition an.  
  
 In der folgenden Tabelle sind die verfügbaren Aggregationsoptionen aufgelistet.  
  
|Option|Description|  
|------------|-----------------|  
|**Aggregationen für die Partition jetzt entwerfen**|Entwirft Aggregationen für die neue Partition, nachdem der Partitions-Assistent die neue Partition erstellt hat. Bei Auswahl dieser Option wird der Aggregationsentwurfs-Assistent gestartet, nachdem Sie im Partitions-Assistenten auf **Fertig stellen** geklickt haben. Weitere Informationen zum Aggregationsentwurfs-Assistenten finden Sie unter [Aggregationsentwurfs-Assistent (F1-Hilfe)](aggregation-design-wizard-f1-help.md).|  
|**Aggregationen später entwerfen**|Erstellt die Partition, ohne gleichzeitig Aggregationen zu entwerfen.|  
|**Aggregationsentwurf aus einer vorhandenen Partition kopieren**|Kopiert den Aggregationsentwurf aus einer vorhandenen Partition der Measuregruppe in die neue Partition. Wenn Sie auf diese Option klicken, ist auch die Option **Kopieren von** verfügbar. Wählen Sie mithilfe der Option **Kopieren von** die Partition aus, aus der der Aggregationsentwurf kopiert werden soll.<br /><br /> Beachten Sie, dass die gleichen Struktur und Aggregation Tabellenentwurf Partitionen, die später möglicherweise zusammengeführt werden müssen. Wenn Sie die neue Partition mit einer vorhandenen Partition in der Measuregruppe zusammenführen möchten, sollten Sie den Aggregationsentwurf der vorhandenen Partition in die neue Partition kopieren.|  
  
 **Jetzt bereitstellen und verarbeiten**  
 Wählen Sie diese Option aus, um die Partition auf der [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]-Instanz, die auf der Seite **Speicherorte zum Verarbeiten und Speichern** angegebenen ist, bereitzustellen und zu verarbeiten. Wenn Sie auf dieser Seite auf **Fertig stellen** klicken, führt der Assistent die Bereitstellung und Verarbeitung der Partition aus.  
  
## <a name="see-also"></a>Siehe auch  
 [Partitionen &#40;Analysis Services – mehrdimensionale Daten&#41;](multidimensional-models-olap-logical-cube-objects/partitions-analysis-services-multidimensional-data.md)  
  
  