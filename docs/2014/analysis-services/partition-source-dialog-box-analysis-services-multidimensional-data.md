---
title: Partitions-Datenquelle (Dialogfeld) (Analysis Services – mehrdimensionale Daten) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.partitionsourcedialog.f1
ms.assetid: c414dabe-9bad-49b7-9a3c-dfca87fef92b
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 2102d28a61a99ed9ed6786dd8f2dee196066045c
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "66072148"
---
# <a name="partition-source-dialog-box-analysis-services---multidimensional-data"></a>Dialogfeld 'Partitionsquelle' (Analysis Services – Mehrdimensionale Daten)
  Mithilfe des Dialogfelds **Partitionsquelle** in [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] können Sie die Quelle der Faktentabellendaten für eine Partition angeben. Das Dialogfeld **Partitionsquelle** können Sie wie folgt aufrufen:  
  
-   Klicken Sie im Cube-Designer auf der Registerkarte **Partitionen** auf die Schaltfläche **...** einer Zelle des Rasters **Partitionen** einer im Bereich **Measuregruppen** ausgewählten Measuregruppe.  
  
-   Klicken Sie in **im Fenster** Eigenschaften **auf die Schaltfläche** ... **eines Eigenschaftswerts** Quelle **eines** Partition [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]-Objekts.  
  
## <a name="options"></a>Optionen  
  
|Option|Definition|  
|------------|----------------|  
|**Typ der datenbankbindung**|Wählen Sie den Bindungstyp für die Quelle der angegebenen Partition aus. Die folgenden Optionen stehen zur Verfügung:<br /><br /> **Tabellenbindung:** Wählen Sie diese Option aus, um den Bereich mit **Tabellenbindungsdetails** anzuzeigen und um anzugeben, dass die Partition an die Inhalte einer Tabelle in einer Datenquelle oder einer Datenquellensicht gebunden ist. Weitere Informationen zum Bereich mit **Tabellenbindungsdetails** finden Sie unter [Tabellenbindungsdetails &#40;Dialogfeld „Partitionsquelle“, Analysis Services – mehrdimensionale Daten&#41;](table-binding-partition-source-dialog-analysis-services-multidimensional-data.md).<br /><br /> **Detail:** Wählen Sie diese Option aus, um den Bereich für **Abfragebindungsdetails** anzuzeigen und anzugeben, dass die Partition an die Inhalte einer Abfrage gebunden ist, die für eine Datenquelle ausgeführt wurde. Weitere Informationen zum Bereich mit **Abfragebindungsdetails** finden Sie unter [Abfragebindungsdetails &#40;Dialogfeld „Partitionsquelle“, Analysis Services – mehrdimensionale Daten&#41;](query-binding-partition-source-dialog-analysis-services-multidimensional-data.md).|  
|**Detail**|Zeigt abhängig vom Wert der Option **Bindungstyp** entweder die Details im Dialogfeld **Tabellenbindung** oder **Abfragebindung** an.|  
  
## <a name="see-also"></a>Siehe auch  
 [Partitionen &#40;Cube-Designer&#41; &#40;Analysis Services – mehrdimensionale Daten&#41;](partitions-cube-designer-analysis-services-multidimensional-data.md)   
 [Analysis Services-Designer und-Dialogfelder &#40;mehrdimensionale Daten&#41;](analysis-services-designers-and-dialog-boxes-multidimensional-data.md)  
  
  
