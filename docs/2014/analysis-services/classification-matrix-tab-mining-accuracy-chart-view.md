---
title: Klassifizierung ", Registerkarte" Matrix "(Mininggenauigkeitsdiagrammsicht) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
ms.tgt_pltfrm: ''
ms.topic: conceptual
f1_keywords:
- sql12.dm.miningmodeleditor.accuracychart.confusionmatrix.f1
ms.assetid: 85d5a047-d656-41e0-8a31-400271c2a620
caps.latest.revision: 22
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 58df3c6d14edb8bfddbd53db0c110475d2a983bd
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/02/2018
ms.locfileid: "37251512"
---
# <a name="classification-matrix-tab-mining-accuracy-chart-view"></a>Klassifikationsmatrix (Registerkarte, Mininggenauigkeitsdiagramm-Sicht)
  Die Registerkarte **Klassifikationsmatrix** zeigt eine Klassifikationsmatrix für jedes im Modellraster auf der Registerkarte **Spaltenzuordnung** ausgewählte Modell an. Die Klassifikationsmatrix ist nur verfügbar, wenn die vorhersagbare Spalte, die auf der Registerkarte **Spaltenzuordnung** ausgewählt wurde, nicht kontinuierlich ist. Eine ausführlichere Beschreibung der Registerkarte **Klassifikationsmatrix** finden Sie unter [Testing and Validation &#40;Data Mining&#41;](data-mining/testing-and-validation-data-mining.md).  
  
## <a name="options"></a>Tastatur  
 **Kopieren**  
 Kopiert den Inhalt jeder Klassifikationsmatrix in die Zwischenablage.  
  
 **Anzahl der \<Modell > auf \< vorhersagbare Spalte >**  
 Zeigt eine Klassifikationsmatrix für jedes Miningmodell in der Miningstruktur an. Diese Matrix enthält die folgenden Spalten:  
  
|value|Description|  
|-----------|-----------------|  
|**Vorhergesagt**|Enthält eine Zeile für jeden Status der vorhersagbaren Spalte.|  
|**\<Status > (tatsächlich)**|Eine Spalte für jeden Status in der vorhersagbaren Spalte. Wenn sich der Status der Zeile und der Spalte entsprechen, stellt die Zelle die tatsächliche Anzahl der Vorkommen des Status in der Datenbank dar. Wenn sich die Status nicht entsprechen, stellt die Zelle den Fehler der Vorhersage dar.|  
  
## <a name="see-also"></a>Siehe auch  
 [Mining-Genauigkeitsdiagramm-Designer &#40;Datamining&#41;](mining-accuracy-chart-designer-data-mining.md)   
 [Tests und Überprüfung miningmodelltasks und Anweisungen &#40;Datamining&#41;](data-mining/testing-and-validation-tasks-and-how-tos-data-mining.md)   
 [Tests und Überprüfung &#40;Datamining&#41;](data-mining/testing-and-validation-data-mining.md)  
  
  
