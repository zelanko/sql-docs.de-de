---
title: IsTestCase (DMX) | Microsoft-Dokumentation
ms.date: 06/07/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: dmx
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: eefb9269a3eb0dc7a6b95e84accb4c68c6737a13
ms.sourcegitcommit: e77197ec6935e15e2260a7a44587e8054745d5c2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/11/2018
ms.locfileid: "38063950"
---
# <a name="istestcase-dmx"></a>IsTestCase (DMX)
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  Gibt an, ob ein Fall als Testfall für ein bestimmtes Data Mining-Modell oder eine bestimmte Data Mining-Struktur verwendet wird.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
IsTestCase()  
```  
  
## <a name="result-type"></a>Ergebnistyp  
 Gibt **"true"** ist der Fall ein Teil des testdatasets; andernfalls **"false"**.  
  
## <a name="remarks"></a>Hinweise  
 Wenn Sie eine Miningstruktur und ein damit verknüpftes Miningmodell mit dem Data Mining-Assistenten erstellen, werden standardmäßig 30 Prozent der Fälle zur Verwendung als Testdataset zurückgehalten. Die übrigen Fälle werden zum Trainieren des Data Mining-Modells verwendet. Dasselbe Testdataset kann mit allen Modellen verwendet werden, die auf der Struktur basieren. Wenn Sie das Miningmodell jedoch mithilfe von DMX erstellen, werden standardmäßig alle Daten zum Trainieren des Modells verwendet, und es wird kein Testsatz erstellt. Um ein testdataset erstellt werden kann, müssen Sie die Parameter der WITH HOLDOUT-Klausel festlegen.  
  
 Sie können ermitteln, ob ein Testsatz für eine bestimmte Miningstruktur erstellt wurde, indem Sie den Wert der Eigenschaften von <xref:Microsoft.AnalysisServices.MiningStructure.HoldoutMaxCases%2A> und <xref:Microsoft.AnalysisServices.MiningStructure.HoldoutMaxPercent%2A> anzeigen.  
  
> [!NOTE]  
>  Für das Modell muss Drillthrough aktiviert werden, wenn die IsTrainingCase oder IsTestCase-Funktion zu verwenden, um Details zu den Fällen in einem bestimmten Modell zurückgegeben werden sollen. Weitere Informationen finden Sie unter [Aktivieren von Drillthrough für ein Miningmodell](../analysis-services/data-mining/enable-drillthrough-for-a-mining-model.md).  
  
 Um Fälle zurückzugeben, die Teil des trainingsdatasets sind, verwenden Sie die Funktion [IsTrainingCase &#40;DMX&#41;](../dmx/istrainingcase-dmx.md).  
  
## <a name="examples"></a>Beispiele  
 Im folgenden Beispiel wird die `Targeted Mailing` Mining-Struktur, die in erstellt haben, wird die [Lernprogramm zu Data Mining](http://msdn.microsoft.com/library/6602edb6-d160-43fb-83c8-9df5dddfeb9c). Die Abfrage gibt alle Fälle der Struktur zurück, die für Tests verwendet werden.  
  
```  
SELECT *  
FROM [Targeted Mailing].CASES  
WHERE IsTestCase()  
```  
  
 Weitere Informationen zum Abfragen von Fällen im Datamining verwendet wird, finden Sie unter [SELECT FROM &#60;Modell&#62;. Fällen &#40;DMX&#41; ](../dmx/select-from-model-cases-dmx.md) und [SELECT FROM &#60;Struktur&#62;. Fällen](../dmx/select-from-structure-cases.md).  
  
## <a name="see-also"></a>Siehe auch  
 [Funktionen &#40;DMX&#41;](../dmx/functions-dmx.md)   
 [Datamining-Abfragen](../analysis-services/data-mining/data-mining-queries.md)   
 [Trainings- und Testdatasets](../analysis-services/data-mining/training-and-testing-data-sets.md)  
  
  
