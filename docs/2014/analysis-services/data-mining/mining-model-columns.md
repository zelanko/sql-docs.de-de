---
title: Mining Modell Spalten | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- columns [data mining], mining model columns
- columns [data mining]
- REGRESSOR column
- columns [data mining], modeling flags
- modeling flags [data mining]
- MODEL_EXISTENCE_ONLY column
- usage property [data mining]
ms.assetid: fab47643-5bfd-424e-a0f7-69e665db6bab
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: f99a2dc218543faa4d862fa7520c1618ec307ba7
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "66083709"
---
# <a name="mining-model-columns"></a>Miningmodellspalten
  Ein Data Mining-Modell wendet einen Miningmodellalgorithmus für die Daten an, welcher durch eine Miningstruktur dargestellt wird. Wie die Miningstruktur enthält das Miningmodell Spalten. Ein Miningmodell ist in der Miningstruktur enthalten und erbt alle Werte der Eigenschaften, die von der Miningstruktur definiert werden. Das Modell kann alle Spalten aus der Miningstruktur oder nur eine Teilmenge der Spalten verwenden.  
  
 Sie können für eine Miningmodellspalte zwei weitere Informationen definieren: Verwendung und Modellierungsflags.  
  
-   Die **Verwendung** ist eine Eigenschaft, die definiert, wie das Modell die Spalte verwendet. Spalten können als Eingabespalten, Schlüsselspalten oder vorhersagbare Spalten verwendet werden.  
  
-   **Modellierungsflags** bieten dem Algorithmus zusätzliche Informationen zu den in der Fall Tabelle definierten Daten, sodass der Algorithmus ein genaueres Modell erstellen kann. Modellierungsflags können programmgesteuert in der Sprache Data Mining-Erweiterungen (DMX) oder in **mit dem** Data Mining-Designer [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]definiert werden.  
  
 In der folgenden Liste werden die Modellierungsflags beschrieben, die Sie für eine Miningmodellspalte definieren können.  
  
 `MODEL_EXISTENCE_ONLY`  
 Gibt an, dass das Vorhandensein der Attributs wichtiger ist als die Werte in der Attributspalte. Stellen Sie sich z. B. eine Falltabelle mit einer Bestellelementenliste vor, die einem bestimmten Kunden zugeordnet ist. Die Tabellendaten enthalten für jedes Element Produkttyp, Bezeichner und Kosten. Für die Modellierung kann die Tatsache, dass der Kunde einen bestimmtes Bestellelement erworben hat, wichtiger sein als die Kosten des Bestellelements selbst. In diesem Fall sollte die Cost-Spalte mit `MODEL_EXISTENCE_ONLY` gekennzeichnet werden.  
  
 `REGRESSOR`  
 Zeigt an, dass der Algorithmus die angegebene Spalte in der Regressionsformel von Regressionsalgorithmen verwenden kann. Dieses Flag wird von den Algorithmen [!INCLUDE[msCoName](../../includes/msconame-md.md)] Decision Trees und [!INCLUDE[msCoName](../../includes/msconame-md.md)] Time Series unterstützt.  
  
 Weitere Informationen zum Festlegen der Verwendungseigenschaft und zum programmgesteuerten Definieren des Modellierungsflags mit DMX finden Sie unter [CREATE MINING MODEL &#40;DMX&#41;](/sql/dmx/create-mining-model-dmx). Weitere Informationen zum Festlegen der Verwendungseigenschaft und zum Definieren des Modellierungsflags in [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]finden Sie unter [Verschieben von Data Mining-Objekten](moving-data-mining-objects.md).  
  
## <a name="see-also"></a>Weitere Informationen  
 [Data Mining-Algorithmen &#40;Analysis Services Data Mining-&#41;](data-mining-algorithms-analysis-services-data-mining.md)   
 [Mining Strukturen &#40;Analysis Services Data Mining-&#41;](mining-structures-analysis-services-data-mining.md)   
 [Ändern der Eigenschaften eines Mining Modells](change-the-properties-of-a-mining-model.md)   
 [Ausschließen einer Spalte aus einem Mining Modell](exclude-a-column-from-a-mining-model.md)   
 [Miningstrukturspalten](mining-structure-columns.md)  
  
  
