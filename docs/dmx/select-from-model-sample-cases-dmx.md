---
title: SELECT FROM &lt;Modell&gt;. SAMPLE_CASES (DMX) | Microsoft-Dokumentation
ms.date: 06/07/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: dmx
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: e0838c688b0518bf1fc7ed6c5d65c3ef03d0a7aa
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "67928311"
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
 Dies ist optional. Eine ganze Zahl, die angibt, wie viele Zeilen zurückgegeben werden sollen.  
  
 *Liste mit Ausdrücken*  
 Eine durch Trennzeichen getrennte Liste mit Bezeichnern verbundener Spalten.  
  
 *model*  
 Ein Modellbezeichner.  
  
 *Liste der Bedingungen*  
 Optional. Bedingungen, die die Werte einschränken, die für die Spaltenliste zurückgegeben werden.  
  
 *expression*  
 Optional. Ein Ausdruck, der einen Skalarwert zurückgibt.  
  
## <a name="remarks"></a>Hinweise  
 Beispielfälle können generiert werden und sind in den Trainingsdaten möglicherweise nicht tatsächlich vorhanden. Der zurückgegebene Fall ist repräsentativ für den angegebenen Inhaltsknoten.  
  
 Obwohl die [!INCLUDE[msCoName](../includes/msconame-md.md)] Sequence Clustering-Algorithmus ist die einzige [!INCLUDE[msCoName](../includes/msconame-md.md)] Algorithmus, der unterstützt die Verwendung von SELECT FROM \<Modell >. SAMPLE_CASES, möglicherweise von Drittanbietern von Algorithmen auch unterstützt.  
  
## <a name="examples"></a>Beispiele  
 Im folgenden Beispiel werden Beispielfälle zurückgegeben, mit denen das Target Mail-Miningmodell trainiert wird. Mithilfe der [IsInNode &#40;DMX&#41; ](../dmx/isinnode-dmx.md) Funktion in der **, in denen** Klausel nur Fälle zurückgegeben, die dem Knoten '000000003' zugeordnet sind. Die Knotenzeichenfolge ist in der NODE_UNIQUE_NAME-Spalte des Schemarowsets zu finden.  
  
```  
Select * from [Sequence Clustering].SAMPLE_Cases  
WHERE IsInNode('000000003')  
```  
  
## <a name="see-also"></a>Siehe auch  
 [SELECT &#40;DMX&#41;](../dmx/select-dmx.md)   
 [Datamining-Erweiterungen &#40;DMX&#41; Datendefinitionsanweisungen](../dmx/dmx-statements-data-definition.md)   
 [Datamining-Erweiterungen &#40;DMX&#41; -Datenbearbeitungsanweisungen](../dmx/dmx-statements-data-manipulation.md)   
 [Data Mining-Erweiterungen &#40;DMX&#41; – Anweisungsreferenz](../dmx/data-mining-extensions-dmx-statements.md)  
  
  
