---
title: Cell-Element (MDDataSet) (XMLA) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.topic: reference
api_name:
- Cell Element (MDDataSet)
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- microsoft.xml.analysis.cell
- http://schemas.microsoft.com/analysisservices/2003/engine#Cell
- urn:schemas-microsoft-com:xml-analysis#Cell
helpviewer_keywords:
- Cell element
ms.assetid: c4ea08a4-f653-4ade-be07-b91eb5b1ef32
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 7c422fdd13c03a2ab3c5a9cd58ce4cca1d22c5d6
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/02/2018
ms.locfileid: "48091670"
---
# <a name="cell-element-mddataset-xmla"></a>Cell-Element (MDDataSet) (XMLA)
  Enthält Informationen über eine einzelne Zelle, die von einem übergeordneten Element enthaltenen [CellData](celldata-element-xmla.md) Element.  
  
## <a name="syntax"></a>Syntax  
  
```xml  
  
<CellData>  
   <Cell CellOrdinal="unsignedInt">  
      <!-- Zero or more cell property values -->  
      <!-- or -->  
      <Error>...</Error>  
   </Cell>  
</CellData>  
```  
  
## <a name="element-characteristics"></a>Elementmerkmale  
  
|Merkmal|Description|  
|--------------------|-----------------|  
|Datentyp und -länge|None|  
|Standardwert|None|  
|Cardinality|0-n: Optionales Element, das mehr als einmal auftreten kann.|  
  
## <a name="element-relationships"></a>Elementbeziehungen  
  
|Beziehung|Element|  
|------------------|-------------|  
|Übergeordnete Elemente|[CellData](celldata-element-xmla.md)|  
|Untergeordnete Elemente|NULL oder mehr zelleigenschaftswerte oder [Fehler](error-element-xmla.md)|  
  
## <a name="attributes"></a>Attribute  
  
|attribute|Description|  
|---------------|-----------------|  
|CellOrdinal|Erforderliche `unsignedInt` Attribut. Die Ordnungsposition der Zelle innerhalb des mehrdimensionalen Datasets.|  
  
## <a name="remarks"></a>Hinweise  
 Im übergeordneten `root`-Element folgt auf das `Axes`-Element das `CellData`-Element, eine Auflistung von `Cell`-Elementen, die die Zelleneigenschaftswerte für jede im mehrdimensionalen Dataset verwendete Zelle enthalten. Das `Cell`-Element enthält das `CellOrdinal`-Attribut, das die nullbasierte Ordnungszahl der Zelle innerhalb des mehrdimensionalen Datasets angibt, und ein Element für jeden Zelleneigenschaftswert, der der Zelle zugeordnet ist. Jeder Zelleneigenschaftswert im `Cell`-Element wird durch ein separates XML-Element definiert. Der Wert der Zelleneigenschaft entspricht den Daten, die im XML-Element enthalten sind, und der Name der Zelleneigenschaft (laut Definition im `CellInfo`-Element des übergeordneten Stammelements) entspricht dem Namen des XML-Elements.  
  
 Die folgende Syntax beschreibt einen Zelleneigenschaftswert:  
  
```  
<CellProperty xsi:type="string">value</CellProperty>  
```  
  
 Der Datentyp eines Zelleneigenschaftswerts wird nur für die VALUE-Zelleneigenschaft angegeben. Die Datentypen anderer Zelleneigenschaften werden durch die Zelleneigenschaftsdefinition im `CellInfo`-Element bestimmt. Ein Zelleneigenschaftswert kann ausgeschlossen werden, wenn ein Standardwert für eine Zelleneigenschaft angegeben wurde (durch Einschluss eines `Default`-Elements als Zelleneigenschaftsdefinition, die im `CellInfo`-Element enthalten ist) oder wenn kein Standardwert angegeben wurde und der Wert der Zelleneigenschaft Null ist.  
  
## <a name="cell-property-errors"></a>Zelleneigenschaftsfehler  
 Wenn aufgrund eines Fehlers, der auf der Instanz von [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] auftritt (z. B. ein Berechnungsfehler, der eine Rückgabe des Werts für eine bestimmte Zelle verhindert) keine Zelleneigenschaft zurückgegeben werden kann, ersetzt ein `Error`-Element die Inhalte der fraglichen Zelleneigenschaft. Das folgende XML-Beispiel beschreibt einen Zelleneigenschaftsfehler:  
  
```  
<Cell CellOrdinal="0">  
   <Value xsi:type="xsd:double">  
      <Error>  
         <ErrorCode>2148497527</ErrorCode>  
         <Description>Unknown error</Description>  
      </Error>  
   </Value>  
</Cell>  
```  
  
## <a name="calculating-cell-ordinal-values"></a>Berechnen der Ordinalwerte der Zelle  
 Der Achsenverweis für eine Zelle kann auf Grundlage eines `CellOrdinal`-Attributwerts berechnet werden. Grundsätzlich werden Zellen in einem Dataset nummeriert, als wäre das Dataset eine *p*-, eindimensionales Array, in denen *p* ist die Anzahl der Achsen. Die Zellen werden in zeilengerichteter Reihenfolge adressiert.  
  
 Hier wird angenommen, dass eine Anforderung vier Measures auf den Spalten und einen Crossjoin mit zwei Status mit vier Quartalen auf den Zeilen anfordert. Im Folgenden Dataset-Ergebnis ist die `CellOrdinal`-Eigenschaft des Datasetergebnisses, die fett gedruckt ist, der Satz {9, 10, 11, 13, 14, 15, 17, 18, 19}. Dies ist der Satz, da die Zellen in zeilengerichteter Reihenfolge nummeriert sind (Anfang mit einer `CellOrdinal` von 0 für die Zelle links oben).  
  
|Status|Quarter|Unit Sales|Store-Cost|Store-Sales|Sales-Count|  
|-----------|-------------|----------------|----------------|-----------------|-----------------|  
|California|Q1|16890|14431.09|36175.2|5498|  
||IM 2. QUARTAL|18052|15332.02|38396.75|5915|  
||3. QUARTAL|18370|**15672.83**|**39394.05**|**6014**|  
||Q4|21436|**18094.5**|**45201.84**|**7015**|  
|Oregon|Q1|19287|**16081.07**|**40170.29**|**6184**|  
||IM 2. QUARTAL|15079|12678.96|31772.88|4799|  
||3. QUARTAL|16940|14273.78|35880.46|5432|  
||Q4|16353|13738.68|34453.44|5196|  
|Washington|Q1|30114|25240.08|63282.86|9906|  
||IM 2. QUARTAL|29479|24953.25|62496.64|9654|  
||3. QUARTAL|30538|25958.26|64997.38|10007|  
||Q4|34235|29172.72|73016.34|11217|  
  
 Wenn die in der Abbildung gezeigte Formel angewendet wird, hat die Achse k = 0 Uk = 4 Elemente und die Achse k = 1 Uk = 8 Tupel. P = 2 ist die Gesamtzahl der Achsen in der Abfrage. Wenn man die Zelle mit dem Inhalt {Kalifornien, Q3, Speicherkosten} als S0 nimmt, ist die ursprüngliche Summe i = 0 bis 1. Für i = 0 ist die Tupelordinalzahl auf Achse 0 auf {Speicherkosten} 1. Für i = 1 ist die Tupelordinalzahl von {CA, Q3} 2.  
  
 Für die ich = 0 Ei = 1, für ich = 0 die Summe wird 1 * 1 = 1 und für die ich = 1, die Summe ist 2 (tupelordinalzahl) Mal 4 (der Wert von Ei berechnet als 1 \* 4), oder 8. Die Summe von 1 + 8 ist dann 9, die Zellenordinalzahl für diese Zelle.  
  
## <a name="example"></a>Beispiel  
 Das folgende Beispiel zeigt daher die Struktur des `Cell`-Elements, einschließlich der VALUE-, FORMATTED_VALUE- und FORMAT_STRING-Zelleneigenschaftswerte jeder Zelle.  
  
```  
<CellData>  
   <Cell CellOrdinal="0">  
      <Value xsi:type="xsd:double">16890</Value>  
      <FmtValue>16,890.00</FmtValue>  
      <FormatString>Standard</FormatString>  
   </Cell>  
   <Cell CellOrdinal="1">  
      <Value xsi:type="xsd:int">50</Value>  
      <FmtValue>50</FmtValue>  
      <FormatString>Standard</FormatString>  
   </Cell>  
   <Cell CellOrdinal="2">  
      <Value xsi:type="xsd:double">36175.2</Value>  
      <FmtValue>$36,175.20</FmtValue>  
      <FormatString>Currency</FormatString>  
   </Cell>  
</CellData>  
```  
  
## <a name="see-also"></a>Siehe auch  
 [MDDataSet-Datentyp &#40;XMLA&#41;](../xml-data-types/mddataset-data-type-xmla.md)   
 [Eigenschaften &#40;XMLA&#41;](xml-elements-properties.md)  
  
  
