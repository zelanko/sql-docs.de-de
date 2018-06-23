---
title: LName-Element (XMLA) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
api_name:
- LName Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- urn:schemas-microsoft-com:xml-analysis#LName
- http://schemas.microsoft.com/analysisservices/2003/engine#LName
- microsoft.xml.analysis.lname
helpviewer_keywords:
- LName element
ms.assetid: 2c8c2fa9-cb2d-44ea-b253-5e6ff61f1b66
caps.latest.revision: 14
author: mgblythe
ms.author: mblythe
manager: mblythe
ms.openlocfilehash: aa8dbe634d876527cc23112e96740c5ebcbf9cb7
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/19/2018
ms.locfileid: "36150428"
---
# <a name="lname-element-xmla"></a>LName-Element (XMLA)
  Enthält Informationen über die eindeutige Ebenennamen für das übergeordnete [HierarchyInfo](hierarchyinfo-element-xmla.md) - oder [Member](member-element-xmla.md) -Element.  
  
## <a name="syntax"></a>Syntax  
  
```xml  
  
<HierarchyInfo> <!-- or Member -->  
   ...  
   <LName>...</LName>  
   ...  
</HierarchyInfo>  
```  
  
## <a name="element-characteristics"></a>Elementmerkmale  
  
|Merkmal|Description|  
|--------------------|-----------------|  
|Datentyp und -länge|Zeichenfolge|  
|Standardwert|InclusionThresholdSetting|  
|Cardinality|1-1: Erforderliches Element, das nur einmal auftritt.|  
  
## <a name="element-relationships"></a>Elementbeziehungen  
  
|Beziehung|Element|  
|------------------|-------------|  
|Übergeordnete Elemente|[HierarchyInfo](hierarchyinfo-element-xmla.md), [Member](member-element-xmla.md)|  
|Untergeordnete Elemente|InclusionThresholdSetting|  
  
## <a name="remarks"></a>Hinweise  
 Bei `HierarchyInfo`-Elementen enthält dieses Element den Namen der Eigenschaft, die die eindeutigen Ebenennamen der Hierarchie bereitstellt. Der Wert entspricht der LEVEL_UNIQUE_NAME-Eigenschaft, die in der OLE DB-Spezifikation für OLAP für Achsen-Rowsets definiert ist.  
  
 Für `Member` Elemente, die dieses Element enthält den eindeutigen Namen der Ebene in der Hierarchie, die durch das übergeordnete Element dargestellten Elements enthält `Member` Element.  
  
## <a name="see-also"></a>Siehe auch  
 [Eigenschaften &#40;XMLA&#41;](xml-elements-properties.md)  
  
  