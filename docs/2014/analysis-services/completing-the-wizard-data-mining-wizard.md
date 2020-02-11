---
title: Assistenten abschließen (Data Mining-Assistent) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.dm.dmwizard.finish.f1
ms.assetid: 6aef1548-35eb-42fd-ae87-63650a79eda1
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 95b1e9822296e26a187b333140ea89c47cb05466
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "66087711"
---
# <a name="completing-the-wizard-data-mining-wizard"></a>Abschließen des Assistenten (Data Mining-Assistent)
  Überprüfen Sie mithilfe der Seite **Assistenten abschließen** die Miningstruktur, die beim Beenden des Assistenten angelegt wird. Sie können auch den Namen der Miningstruktur festlegen.  
  
 Wenn Sie festgelegt haben, dass ein zugeordnetes Miningmodell erstellt werden soll, können Sie auch den Namen des zugeordneten Miningmodells festlegen und Drillthrough für das Miningmodell aktivieren.  
  
> [!NOTE]  
>  Diese Seite ändert sich je nachdem, ob Sie **Aus vorhandener relationaler Datenbank oder vorhandenem Data Warehouse** oder **Aus vorhandenem Cube** auf der Seite **Definitionsmethode auswählen** des Assistenten ausgewählt haben.  
  
 **Weitere Informationen:** [Data Mining-Assistent &#40;Analysis Services Data Mining&#41;](data-mining/data-mining-wizard-analysis-services-data-mining.md), [Data Mining-Designer](data-mining/data-mining-designer.md), [Erstellen einer relationalen Mining Struktur](data-mining/create-a-relational-mining-structure.md)  
  
## <a name="options"></a>Tastatur  
 **Miningstrukturname**  
 Geben Sie den Namen der Miningstruktur ein, der vom **Data Mining-Assistenten**definiert wurde.  
  
 **Miningmodellname**  
 Geben Sie den Namen des Miningmodells ein, das vom **Data Mining-Assistenten**definiert wurde.  
  
 **Drillthrough zulassen**  
 Wählen Sie diese Option aus, damit Drillthroughfunktionen im neuen Miningmodell unterstützt werden, falls Sie ein neues Modell erstellt haben.  
  
> [!NOTE]  
>  Standardmäßig ist Drillthrough in der Miningstruktur aktiviert.  
  
 Weitere Informationen zu Drillthroughoptionen finden Sie unter [Drillthroughabfragen &#40;Data Mining&#41;](data-mining/drillthrough-queries-data-mining.md).  
  
 **Vorschau**  
 Zeigt die zu erstellende Miningstruktur an.  
  
 **Mining Modell Dimension erstellen**  
 Wählen Sie diese Option aus, um basierend auf dem zu erstellenden Miningmodell eine Dimension zu erstellen. Geben Sie, nachdem Sie diese Option ausgewählt haben, den Namen der zu erstellenden Dimension ein. Durch das Auswählen dieser Option wird die Option **Cube mithilfe der Miningmodelldimension erstellen**ausgewählt.  
  
> [!NOTE]  
>  Diese Option ist verfügbar, wenn Sie **Aus vorhandenem Cube** auf der Seite **Definitionsmethode auswählen** des Assistenten ausgewählt haben.  
  
 **Cube mithilfe der Mining Modell Dimension erstellen**  
 Wählen Sie diese Option aus, um basierend auf dem zu erstellenden Miningmodell einen Cube zu erstellen. Geben Sie, nachdem Sie diese Option ausgewählt haben, den Namen des zu erstellenden Cubes ein.  
  
> [!NOTE]  
>  Diese Option ist verfügbar, wenn Sie **Aus vorhandenem Cube** auf der Seite **Definitionsmethode auswählen** sowie **Miningmodelldimension erstellen** auf der aktuellen Seite des Assistenten ausgewählt haben.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Data Mining-Assistent (F1-Hilfe &#40;Analysis Services-Data Mining-&#41;](data-mining-wizard-f1-help-analysis-services-data-mining.md)   
 [Wählen Sie die Datenquellen Sicht &#40;Data Mining-Assistenten aus&#41;](select-data-source-view-data-mining-wizard.md)   
 [Geben Sie den Data Mining-Assistenten für Trainingsdaten &#40;an&#41;](specify-the-training-data-data-mining-wizard.md)  
  
  
