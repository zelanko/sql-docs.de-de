---
title: SELECT FROM &lt;Modell&gt;. SAMPLE_CASES (DMX) | Microsoft Docs
ms.date: 06/07/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: dmx
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: f4443f05fbee790f5f1d266f451e1105b9c00197
ms.sourcegitcommit: 8f0faa342df0476884c3238e36ae3d9634151f87
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/07/2018
ms.locfileid: "34841523"
---
# <a name="select-from-ltmodelgtsamplecases-dmx"></a>SELECT FROM &lt;Modell&gt;. SAMPLE_CASES (DMX)
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  Gibt Beispielfälle zurück, die repräsentativ für die Fälle sind, die zum Trainieren des Data Mining-Modells verwendet werden.  
  
 Damit Sie diese Anweisung verwenden können, müssen Sie Drillthrough aktivieren, wenn Sie das Miningmodell erstellen. Weitere Informationen zum Aktivieren von Drillthrough finden Sie unter [CREATE MINING MODEL &#40;DMX&#41;](../dmx/create-mining-model-dmx.md), [SELECT INTO &#40;DMX&#41;](../dmx/select-into-dmx.md), und [ALTER MINING STRUCTURE &#40;DMX&#41;](../dmx/alter-mining-structure-dmx.md).  
  
## <a name="syntax"></a>Syntax  
  
```  
  
SELECT [FLATTENED] [TOP <n>] <expression list> FROM <model>.SAMPLE_CASES  
[WHERE <condition list>] ORDER BY <expression> [DESC|ASC]]  
```  
  
## <a name="arguments"></a>Argumente  
 *n*  
 Optional. Eine ganze Zahl, die angibt, wie viele Zeilen zurückgegeben werden sollen.  
  
 *Liste der Ausdrücke*  
 Eine durch Trennzeichen getrennte Liste mit Bezeichnern verbundener Spalten.  
  
 *model*  
 Ein Modellbezeichner.  
  
 *Liste der Bedingungen*  
 Optional. Bedingungen, die die Werte einschränken, die für die Spaltenliste zurückgegeben werden.  
  
 *expression*  
 Optional. Ein Ausdruck, der einen Skalarwert zurückgibt.  
  
## <a name="remarks"></a>Hinweise  
 Beispielfälle können generiert werden und sind in den Trainingsdaten möglicherweise nicht tatsächlich vorhanden. Der zurückgegebene Fall ist repräsentativ für den angegebenen Inhaltsknoten.  
  
 Obwohl die [!INCLUDE[msCoName](../includes/msconame-md.md)] Sequence Clustering-Algorithmus ist der einzige [!INCLUDE[msCoName](../includes/msconame-md.md)] Algorithmus, der unterstützt die Verwendung von SELECT FROM \<Modell >. SAMPLE_CASES, möglicherweise drittanbieteralgorithmen ebenfalls unterstützt.  
  
## <a name="examples"></a>Beispiele  
 Im folgenden Beispiel werden Beispielfälle zurückgegeben, mit denen das Target Mail-Miningmodell trainiert wird. Mithilfe der [IsInNode &#40;DMX&#41; ](../dmx/isinnode-dmx.md) -Funktion in der **, in denen** -Klausel nur Fälle zurückgegeben, die den Knoten '000000003' zugeordnet sind. Die Knotenzeichenfolge ist in der NODE_UNIQUE_NAME-Spalte des Schemarowsets zu finden.  
  
```  
Select * from [Sequence Clustering].SAMPLE_Cases  
WHERE IsInNode('000000003')  
```  
  
## <a name="see-also"></a>Siehe auch  
 [WÄHLEN SIE &AMP;#40;DMX&AMP;#41;](../dmx/select-dmx.md)   
 [Datamining-Erweiterungen &#40;DMX&#41; -Datendefinitionsanweisungen](../dmx/dmx-statements-data-definition.md)   
 [Datamining-Erweiterungen &#40;DMX&#41; -Datenbearbeitungsanweisungen](../dmx/dmx-statements-data-manipulation.md)   
 [Data Mining-Erweiterungen &#40;DMX&#41; – Anweisungsreferenz](../dmx/data-mining-extensions-dmx-statements.md)  
  
  
