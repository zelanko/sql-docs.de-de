---
description: IsTestCase (DMX)
title: IsTestCase (DMX) | Microsoft-Dokumentation
ms.date: 06/07/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: dmx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: c0bc9e4ffe7da1f81bbd246e9cbfa7398bfec50e
ms.sourcegitcommit: c7f40918dc3ecdb0ed2ef5c237a3996cb4cd268d
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/05/2020
ms.locfileid: "91726145"
---
# <a name="istestcase-dmx"></a>IsTestCase (DMX)
[!INCLUDE[ssas](../includes/applies-to-version/ssas.md)]

  Gibt an, ob ein Fall als Testfall für ein bestimmtes Data Mining-Modell oder eine bestimmte Data Mining-Struktur verwendet wird.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
IsTestCase()  
```  
  
## <a name="result-type"></a>Ergebnistyp  
 Gibt " **true** " zurück, wenn der Fall ein Teil des Test Datasets ist. andernfalls **false**.  
  
## <a name="remarks"></a>Bemerkungen  
 Wenn Sie eine Miningstruktur und ein damit verknüpftes Miningmodell mit dem Data Mining-Assistenten erstellen, werden standardmäßig 30 Prozent der Fälle zur Verwendung als Testdataset zurückgehalten. Die übrigen Fälle werden zum Trainieren des Data Mining-Modells verwendet. Dasselbe Testdataset kann mit allen Modellen verwendet werden, die auf der Struktur basieren. Wenn Sie das Miningmodell jedoch mithilfe von DMX erstellen, werden standardmäßig alle Daten zum Trainieren des Modells verwendet, und es wird kein Testsatz erstellt. Um die Erstellung eines Test Datasets zu aktivieren, müssen Sie die Parameter der WITH HOLDOUT-Klausel festlegen.  
  
 Sie können ermitteln, ob ein Testsatz für eine bestimmte Miningstruktur erstellt wurde, indem Sie den Wert der Eigenschaften von <xref:Microsoft.AnalysisServices.MiningStructure.HoldoutMaxCases%2A> und <xref:Microsoft.AnalysisServices.MiningStructure.HoldoutMaxPercent%2A> anzeigen.  
  
> [!NOTE]  
>  Drillthrough muss für das Modell aktiviert sein, wenn Sie die IsTrainingCase-Funktion oder die IsTestCase-Funktion verwenden möchten, um Details zu den Fällen in einem bestimmten Modell zurückzugeben. Weitere Informationen finden Sie unter [Aktivieren von Drillthrough für ein Miningmodell](/analysis-services/data-mining/enable-drillthrough-for-a-mining-model).  
  
 Verwenden Sie die [IsTrainingCase-Funktion &#40;DMX-&#41;](../dmx/istrainingcase-dmx.md), um die Fälle zurückzugeben, die Teil des Trainings Datasets sind.  
  
## <a name="examples"></a>Beispiele  
 Im folgenden Beispiel wird die `Targeted Mailing` Mining Struktur verwendet, die im Lernprogramm zu [Data Mining-Grundlagen](/previous-versions/sql/sql-server-2016/ms167167(v=sql.130))erstellt wird. Die Abfrage gibt alle Fälle der Struktur zurück, die für Tests verwendet werden.  
  
```  
SELECT *  
FROM [Targeted Mailing].CASES  
WHERE IsTestCase()  
```  
  
 Weitere Informationen zum Abfragen von Fällen, die in Data Mining verwendet werden, finden [Sie unter Select from &#60;Model&#62;. Fälle &#40;DMX-&#41;](../dmx/select-from-model-cases-dmx.md) und [Wählen aus &#60;Struktur&#62;. Fälle](../dmx/select-from-structure-cases.md).  
  
## <a name="see-also"></a>Weitere Informationen  
 [Funktionen &#40;DMX-&#41;](../dmx/functions-dmx.md)   
 [Data Mining-Abfragen](/analysis-services/data-mining/data-mining-queries)   
 [Trainings- und Testdatasets](/analysis-services/data-mining/training-and-testing-data-sets)  
  
