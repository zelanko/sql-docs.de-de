---
title: Klassifizierung ", Registerkarte" Matrix "(Mininggenauigkeitsdiagrammsicht) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.dm.miningmodeleditor.accuracychart.confusionmatrix.f1
ms.assetid: 85d5a047-d656-41e0-8a31-400271c2a620
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: ca3471a96a2ad171255f488b255deee55f73e2e0
ms.sourcegitcommit: f40fa47619512a9a9c3e3258fda3242c76c008e6
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/23/2019
ms.locfileid: "66087949"
---
# <a name="classification-matrix-tab-mining-accuracy-chart-view"></a>Klassifikationsmatrix (Registerkarte, Mininggenauigkeitsdiagramm-Sicht)
  Die Registerkarte **Klassifikationsmatrix** zeigt eine Klassifikationsmatrix für jedes im Modellraster auf der Registerkarte **Spaltenzuordnung** ausgewählte Modell an. Die Klassifikationsmatrix ist nur verfügbar, wenn die vorhersagbare Spalte, die auf der Registerkarte **Spaltenzuordnung** ausgewählt wurde, nicht kontinuierlich ist. Eine ausführlichere Beschreibung der Registerkarte **Klassifikationsmatrix** finden Sie unter [Testing and Validation &#40;Data Mining&#41;](data-mining/testing-and-validation-data-mining.md).  
  
## <a name="options"></a>Optionen  
 **Kopieren**  
 Kopiert den Inhalt jeder Klassifikationsmatrix in die Zwischenablage.  
  
 **Anzahl der \<Modell > auf \< vorhersagbare Spalte >**  
 Zeigt eine Klassifikationsmatrix für jedes Miningmodell in der Miningstruktur an. Diese Matrix enthält die folgenden Spalten:  
  
|Wert|Description|  
|-----------|-----------------|  
|**Vorhergesagt**|Enthält eine Zeile für jeden Status der vorhersagbaren Spalte.|  
|**\<Status > (tatsächlich)**|Eine Spalte für jeden Status in der vorhersagbaren Spalte. Wenn sich der Status der Zeile und der Spalte entsprechen, stellt die Zelle die tatsächliche Anzahl der Vorkommen des Status in der Datenbank dar. Wenn sich die Status nicht entsprechen, stellt die Zelle den Fehler der Vorhersage dar.|  
  
## <a name="see-also"></a>Siehe auch  
 [Mining-Genauigkeitsdiagramm-Designer &#40;Datamining&#41;](mining-accuracy-chart-designer-data-mining.md)   
 [Tests und Überprüfung miningmodelltasks und Anweisungen &#40;Datamining&#41;](data-mining/testing-and-validation-tasks-and-how-tos-data-mining.md)   
 [Tests und Überprüfung &#40;Data Mining&#41;](data-mining/testing-and-validation-data-mining.md)  
  
  
