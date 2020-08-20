---
description: Wählen Sie aus dem &lt; Modell aus &gt; . DIMENSION_CONTENT (DMX)
title: Wählen Sie aus dem &lt; Modell aus &gt; . DIMENSION_CONTENT (DMX) | Microsoft-Dokumentation
ms.date: 06/07/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: dmx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: e3d7bbfcce023ce994f71a5897a1cbf4b0095419
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/17/2020
ms.locfileid: "88472006"
---
# <a name="select-from-ltmodelgtdimension_content-dmx"></a>Wählen Sie aus dem &lt; Modell aus &gt; . DIMENSION_CONTENT (DMX)
[!INCLUDE[ssas](../includes/applies-to-version/ssas.md)]

  Ein Miningmodell kann als Dimension in einem OLAP-Cube verwendet werden, wobei jeder Knoten im Modell als Element der Dimension dargestellt wird. **Die Select from-Option \<model> . DIMENSION_CONTENT** -Anweisung gibt den Inhalt des Modells zurück, der sich auf seine Verwendung als Dimension bezieht.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
SELECT [FLATTENED] [TOP <n>] <expression list> FROM <model>.Dimension_CONTENT   
[WHERE <condition expression>]  
[ORDER BY <expression> [DESC|ASC]]  
```  
  
## <a name="arguments"></a>Argumente  
 *n*  
 Optional. Eine ganze Zahl, die angibt, wie viele Zeilen zurückgegeben werden sollen.  
  
 *Ausdrucks Liste*  
 Eine durch Trennzeichen getrennte Liste mit Bezeichnern, die aus dem Schemarowset des Inhalts abgeleitet wurden.  
  
 *model*  
 Ein Modellbezeichner.  
  
 *Bedingungs Ausdruck*  
 Optional. Eine Bedingung, die die Werte einschränkt, die für die Spaltenliste zurückgegeben werden.  
  
 *expression*  
 Optional. Ein Ausdruck, der einen Skalarwert zurückgibt.  
  
## <a name="remarks"></a>Bemerkungen  
 Algorithmusanbieter definieren, welcher Inhalt zurückgegeben wird und wie dieser aufgebaut ist. Beispielsweise kann der Anbieter die Anzahl von Knoten begrenzen, die im Dimensionsinhalt beschrieben werden.  
  
 In der folgenden Tabelle sind die Spalten, die für den Dimensionsinhalt abgefragt werden können, sowie für jede Spalte die Funktion aufgeführt, die sie als Data Mining-Dimension hat.  
  
|CONTENT-Rowsetspalte|Funktion in einer Data Mining-Dimension|  
|---------------------------|---------------------------------------|  
|ATTRIBUTE_NAME|Member-Eigenschaft.|  
|NODE_NAME|Member-Eigenschaft.|  
|NODE_UNIQUE_NAME|Schlüssel Attribut.|  
|NODE_TYPE|Member-Eigenschaft.|  
|NODE_CAPTION|CaptionColumn für das **Schlüssel** Attribut.|  
|CHILDREN_CARDINALITY|Member-Eigenschaft.|  
|PARENT_UNIQUE_NAME|Relatedattribute für das **Schlüssel** Attribut ("Element Attribute" in der über-/unterordnungshierarchie).|  
|NODE_DESCRIPTION|Member-Eigenschaft.|  
|NODE_RULE|Member-Eigenschaft.|  
|MARGINAL_RULE|Member-Eigenschaft.|  
|NODE_PROBABILITY|Member-Eigenschaft.|  
|MARGINAL_PROBABILITY|Member-Eigenschaft.|  
|NODE_SUPPORT|Member-Eigenschaft.|  
  
## <a name="examples"></a>Beispiele  
  
### <a name="description"></a>BESCHREIBUNG  
 In diesem Beispiel werden alle Spalten aus dem Inhalt des `[TM Decision Tree]`-Modells ausgewählt, die sich auf die Verwendung des Modells als Dimension beziehen.  
  
### <a name="code"></a>Code  
  
```  
SELECT *   
FROM [TM Decision Tree].Dimension_Content  
```  
  
## <a name="see-also"></a>Weitere Informationen  
 [Wählen Sie &#40;DMX-&#41;](../dmx/select-dmx.md)   
 [Data Mining-Erweiterungen &#40;DMX-&#41; Daten Definitions Anweisungen](../dmx/dmx-statements-data-definition.md)   
 [Data Mining-Erweiterungen &#40;DMX-&#41; Daten Bearbeitungsanweisungen](../dmx/dmx-statements-data-manipulation.md)   
 [Data Mining-Erweiterungen &#40;DMX&#41; – Anweisungsreferenz](../dmx/data-mining-extensions-dmx-statements.md)  
  
  
