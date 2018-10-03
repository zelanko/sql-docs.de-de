---
title: Klassifizierte Spalten [Datamining] | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
ms.topic: conceptual
helpviewer_keywords:
- content types [data mining]
- STDEV column
- VARIANCE column
- PROBABLILITY column
- PROBABILITY_STDEV column
- columns [data mining], classified
- classified columns [data mining]
- PROBABILITY_VARIANCE column
- SUPPORT column
ms.assetid: 68bf3b78-dc12-497c-898f-b43a45646123
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: d4a0fc7a0eeb0cabd07a38f77d5024aac0eaebb8
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/02/2018
ms.locfileid: "48193750"
---
# <a name="classified-columns-data-mining"></a>Klassifizierte Spalten [Data Mining]
  Wenn Sie eine klassifizierte Spalte definieren, erstellen Sie eine Beziehung zwischen der aktuellen Spalte und eine andere Spalte in der Miningstruktur. Die Daten in der Miningstrukturspalte, die Sie als klassifizierte Spalte festlegen, enthält Kategorieinformationen zur Beschreibung der Werte in einer anderen Spalte der Miningstruktur.  
  
 Angenommen, Sie verfügen über zwei Spalten mit numerischen Daten: die Spalte [Jährliche Käufe] enthält die gesamten jährlichen Käufe pro Kunde für ein bestimmtes Kalenderjahr, und die andere Spalte [Standardabweichungen] enthält die Standardabweichungen für diese Werte. In diesem Fall könnten Sie die Spalte [Jährliche Käufe] als klassifizierte Spalte festlegen, und das Modell wäre in der Lage, diese Beziehung in der Analyse zu verwenden.  
  
> [!NOTE]  
>  Von den in [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] bereitgestellten Algorithmen werden klassifizierte Spalten nicht unterstützt. Diese Funktion wird für die Erstellung benutzerdefinierter Algorithmen bereitgestellt.  
  
## <a name="defining-a-classified-column"></a>Definieren einer klassifizierten Spalte  
 Der Datentyp für eine klassifizierte Spalte muss entweder `Long` oder `Double`.  
  
 In der folgenden Liste werden die Inhaltstypen beschrieben, die [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] für klassifizierte Spalten unterstützt.  
  
 **PROBABILITY**  
 Der Wert in der Spalte entspricht der Wahrscheinlichkeit des zugeordneten Wertes und ist eine Zahl zwischen 0 und 1.  
  
 **VARIANCE**  
 Der Wert in der Spalte entspricht der Varianz des zugeordneten Wertes.  
  
 **STDEV**  
 Der Wert in der Spalte entspricht der Standardabweichung des zugeordneten Wertes.  
  
 **PROBABILITY_VARIANCE**  
 Der Wert in der Spalte entspricht der Varianz der Wahrscheinlichkeit des zugeordneten Wertes.  
  
 **PROBABILITY_STDEV**  
 Der Wert in der Spalte entspricht der Standardabweichung der Wahrscheinlichkeit des zugeordneten Wertes.  
  
 **Alias**  
 Der Wert in der Spalte entspricht der Gewichtung oder dem Fallreplikationsfaktor des zugeordneten Wertes.  
  
## <a name="see-also"></a>Siehe auch  
 [Inhaltstypen &#40;Datamining&#41;](content-types-data-mining.md)   
 [Miningstrukturen &#40;Analysis Services – Datamining&#41;](mining-structures-analysis-services-data-mining.md)   
 [Datentypen &#40;Datamining&#41;](data-types-data-mining.md)  
  
  
