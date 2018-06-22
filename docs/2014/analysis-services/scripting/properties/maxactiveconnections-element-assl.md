---
title: MaxActiveConnections-Element (ASSL) | Microsoft Docs
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
- MaxActiveConnections Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
helpviewer_keywords:
- MaxActiveConnections element
ms.assetid: 0dc5b64d-061d-409f-95c0-4c63f87f5ee4
caps.latest.revision: 11
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: df2dafc69a97d1beb954100413761c07878881d4
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/19/2018
ms.locfileid: "36049050"
---
# <a name="maxactiveconnections-element-assl"></a>MaxActiveConnections-Element (ASSL)
  Enthält die maximale Anzahl gleichzeitiger Verbindungen zulässig, die von einem Element, das von abgeleitet ist die [DataSource](../data-type/datasource-data-type-assl.md) -Datentyp.  
  
## <a name="syntax"></a>Syntax  
  
```xml  
  
<DataSource>  
   ...  
   <MaxActiveConnections>...</MaxActiveConnections>  
   ...  
</DataSource>  
```  
  
## <a name="element-characteristics"></a>Elementmerkmale  
  
|Merkmal|Description|  
|--------------------|-----------------|  
|Datentyp und -länge|Integer|  
|Standardwert|`10`|  
|Cardinality|0-1: Optionales Element, das nur einmal auftreten kann.|  
  
## <a name="element-relationships"></a>Elementbeziehungen  
  
|Beziehung|Element|  
|------------------|-------------|  
|Übergeordnetes Element|[DataSource](../data-type/datasource-data-type-assl.md)|  
|Untergeordnete Elemente|InclusionThresholdSetting|  
  
## <a name="remarks"></a>Hinweise  
 Wenn der Wert für dieses Element auf null gesetzt wird, wird die maximal zulässige Anzahl gleichzeitiger Verbindungen von der Daten-Cartridge bestimmt, die für den Zugriff auf die Datenquelle verwendet wird. Wenn der Wert für dieses Element negativ ist, ist die maximal zulässige Anzahl gleichzeitiger Verbindungen unbegrenzt.  
  
## <a name="see-also"></a>Siehe auch  
 [Eigenschaften &#40;ASSL&#41;](properties-assl.md)  
  
  