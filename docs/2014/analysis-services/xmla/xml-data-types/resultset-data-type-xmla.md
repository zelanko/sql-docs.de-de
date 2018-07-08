---
title: Resultset-Datentyp (XMLA) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
api_name:
- Resultset Data Type
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- http://schemas.microsoft.com/analysisservices/2003/engine#Resultset
- urn:schemas-microsoft-com:xml-analysis#Resultset
- Resultset
helpviewer_keywords:
- Resultset data type
ms.assetid: 45e7d7d6-1f89-4dc8-b39d-9270ea2db541
caps.latest.revision: 30
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 4d4e95d3e2b85971271cff4b1365b44e5a30ba0c
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/02/2018
ms.locfileid: "37155071"
---
# <a name="resultset-data-type-xmla"></a>Resultset-Datentyp (XMLA)
  Definiert einen abstrakten Grunddatentyp, der vom zurückgegebenen Daten darstellt. ein [Discover](../xml-elements-methods-discover.md) oder [Execute](../xml-elements-methods-execute.md) Methodenaufruf.  
  
 **Namespace** urn:schemas-microsoft-com:xml-analysis:resultset  
  
## <a name="syntax"></a>Syntax  
  
```xml  
  
<Resultset>  
   <Exception>...</Exception>  
   <Messages>...</Messages>  
</Resultset>  
```  
  
## <a name="data-type-characteristics"></a>Datentypmerkmale  
  
|Merkmal|Description|  
|--------------------|-----------------|  
|Basisdatentypen|InclusionThresholdSetting|  
|Abgeleitete Datentypen|[MDDataSet](mddataset-data-type-xmla.md), [Olapxmla_EmptyResult](emptyresult-data-type-xmla.md), [Rowset](rowset-data-type-xmla.md)|  
  
## <a name="data-type-relationships"></a>Datentypbeziehungen  
  
|Beziehung|Element|  
|------------------|-------------|  
|Übergeordnete Elemente|InclusionThresholdSetting|  
|Untergeordnete Elemente|[Ausnahme](../xml-elements-properties/exception-element-xmla.md), [Nachrichten](../xml-elements-properties/messages-element-xmla.md)|  
|Abgeleitete Elemente|InclusionThresholdSetting|  
  
## <a name="remarks"></a>Hinweise  
 Der `Resultset`-Datentyp ist ein selbstbeschreibendes XML-Ergebnis, das, abhängig vom Typ der zurückzugebenden Informationen sowohl ein Schema als auch Daten enthalten kann.  
  
## <a name="see-also"></a>Siehe auch  
 [XML-Datentypen &#40;XMLA&#41;](xml-data-types-xmla.md)  
  
  
