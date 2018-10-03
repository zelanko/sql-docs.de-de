---
title: DbTableName-Element (XMLA) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.topic: reference
api_name:
- DbTableName Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- http://schemas.microsoft.com/analysisservices/2003/engine#DbTableName
- microsoft.xml.analysis.dbtablename
- urn:schemas-microsoft-com:xml-analysis#DbTableName
helpviewer_keywords:
- DbTableName element
ms.assetid: 0ffda645-2a88-4f42-8929-9d7385c19a74
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 81caaee312e7c6978dbd66fec666aaa37b6efe3b
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/02/2018
ms.locfileid: "48056820"
---
# <a name="dbtablename-element-xmla"></a>DbTableName-Element (XMLA)
  Enthält den Namen der Tabelle verwendet wird, durch das übergeordnete [TableNotification](tablenotification-element-xmla.md) Element.  
  
## <a name="syntax"></a>Syntax  
  
```xml  
  
<TableNotification>  
   ...  
   <DbTableName>...</DbTableName>  
   ...  
</TableNotification>  
```  
  
## <a name="element-characteristics"></a>Elementmerkmale  
  
|Merkmal|Description|  
|--------------------|-----------------|  
|Datentyp und -länge|Zeichenfolge|  
|Standardwert|None|  
|Cardinality|0-1: Optionales Element, das nur einmal auftreten kann.|  
  
## <a name="element-relationships"></a>Elementbeziehungen  
  
|Beziehung|Element|  
|------------------|-------------|  
|Übergeordnete Elemente|[TableNotification](tablenotification-element-xmla.md)|  
|Untergeordnete Elemente|None|  
  
## <a name="remarks"></a>Hinweise  
  
## <a name="see-also"></a>Siehe auch  
 [DbSchemaName-Element &#40;XMLA&#41;](name-element-xmla.md)   
 [Eigenschaften &#40;XMLA&#41;](xml-elements-properties.md)  
  
  
