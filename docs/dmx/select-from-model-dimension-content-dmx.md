---
title: SELECT FROM &lt;Modell&gt;. DIMENSION_CONTENT (DMX) | Microsoft-Dokumentation
ms.date: 06/07/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: dmx
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: 7fac89454cd31c1334e41d4c2367143f31476e20
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "67928369"
---
# <a name="select-from-ltmodelgtdimensioncontent-dmx"></a>SELECT FROM &lt;Modell&gt;. DIMENSION_CONTENT (DMX)
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  Ein Miningmodell kann als Dimension in einem OLAP-Cube verwendet werden, wobei jeder Knoten im Modell als Element der Dimension dargestellt wird. **SELECT FROM \<Modell >. Dimension_CONTENT** -Anweisung gibt den Inhalt des Modells, die sich für dessen Verwendung als Dimension beziehen.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
SELECT [FLATTENED] [TOP <n>] <expression list> FROM <model>.Dimension_CONTENT   
[WHERE <condition expression>]  
[ORDER BY <expression> [DESC|ASC]]  
```  
  
## <a name="arguments"></a>Argumente  
 *n*  
 Dies ist optional. Eine ganze Zahl, die angibt, wie viele Zeilen zurückgegeben werden sollen.  
  
 *Liste mit Ausdrücken*  
 Eine durch Trennzeichen getrennte Liste mit Bezeichnern, die aus dem Schemarowset des Inhalts abgeleitet wurden.  
  
 *model*  
 Ein Modellbezeichner.  
  
 *Bedingungsausdruck*  
 Dies ist optional. Eine Bedingung, die die Werte einschränkt, die für die Spaltenliste zurückgegeben werden.  
  
 *expression*  
 Optional. Ein Ausdruck, der einen Skalarwert zurückgibt.  
  
## <a name="remarks"></a>Hinweise  
 Algorithmusanbieter definieren, welcher Inhalt zurückgegeben wird und wie dieser aufgebaut ist. Beispielsweise kann der Anbieter die Anzahl von Knoten begrenzen, die im Dimensionsinhalt beschrieben werden.  
  
 In der folgenden Tabelle sind die Spalten, die für den Dimensionsinhalt abgefragt werden können, sowie für jede Spalte die Funktion aufgeführt, die sie als Data Mining-Dimension hat.  
  
|CONTENT-Rowsetspalte|Funktion in einer Data Mining-Dimension|  
|---------------------------|---------------------------------------|  
|ATTRIBUTE_NAME|Member-Eigenschaft.|  
|NODE_NAME|Member-Eigenschaft.|  
|NODE_UNIQUE_NAME|Key-Attribut.|  
|NODE_TYPE|Member-Eigenschaft.|  
|NODE_CAPTION|CaptionColumn für **Schlüssel** Attribut.|  
|CHILDREN_CARDINALITY|Member-Eigenschaft.|  
|PARENT_UNIQUE_NAME|Zugeordnetes Attribut für **Schlüssel** Attribut (ParentAttribute in über-/ unterordnungshierarchie).|  
|NODE_DESCRIPTION|Member-Eigenschaft.|  
|NODE_RULE|Member-Eigenschaft.|  
|MARGINAL_RULE|Member-Eigenschaft.|  
|NODE_PROBABILITY|Member-Eigenschaft.|  
|MARGINAL_PROBABILITY|Member-Eigenschaft.|  
|NODE_SUPPORT|Member-Eigenschaft.|  
  
## <a name="examples"></a>Beispiele  
  
### <a name="description"></a>Beschreibung  
 In diesem Beispiel werden alle Spalten aus dem Inhalt des `[TM Decision Tree]`-Modells ausgewählt, die sich auf die Verwendung des Modells als Dimension beziehen.  
  
### <a name="code"></a>Code  
  
```  
SELECT *   
FROM [TM Decision Tree].Dimension_Content  
```  
  
## <a name="see-also"></a>Siehe auch  
 [SELECT &#40;DMX&#41;](../dmx/select-dmx.md)   
 [Datamining-Erweiterungen &#40;DMX&#41; Datendefinitionsanweisungen](../dmx/dmx-statements-data-definition.md)   
 [Datamining-Erweiterungen &#40;DMX&#41; -Datenbearbeitungsanweisungen](../dmx/dmx-statements-data-manipulation.md)   
 [Data Mining-Erweiterungen &#40;DMX&#41; – Anweisungsreferenz](../dmx/data-mining-extensions-dmx-statements.md)  
  
  
