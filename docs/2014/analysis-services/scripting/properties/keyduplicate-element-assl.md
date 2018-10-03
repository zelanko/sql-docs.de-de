---
title: KeyDuplicate-Element (ASSL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.topic: reference
api_name:
- KeyDuplicate Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- KeyDuplicate
helpviewer_keywords:
- KeyDuplicate element
ms.assetid: d7000b8b-e81f-4401-8738-00c2e0f73a59
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: c4ca2e06d39607acf92dc820bc08cfe53f938bed
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/02/2018
ms.locfileid: "48055294"
---
# <a name="keyduplicate-element-assl"></a>KeyDuplicate-Element (ASSL)
  Bestimmt, wie [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] einen während der Verarbeitung festgestellten Fehler aufgrund doppelter Schlüssel behandelt.  
  
## <a name="syntax"></a>Syntax  
  
```xml  
  
<ErrorConfiguration>  
   ...  
      <KeyDuplicate>...</KeyDuplicate>  
   ...  
</ErrorConfiguration>  
```  
  
## <a name="element-characteristics"></a>Elementmerkmale  
  
|Merkmal|Description|  
|--------------------|-----------------|  
|Datentyp und -länge|Zeichenfolge (Enumeration)|  
|Standardwert|*IgnoreError*|  
|Cardinality|0-1: Optionales Element, das nur einmal auftreten kann.|  
  
## <a name="element-relationships"></a>Elementbeziehungen  
  
|Beziehung|Element|  
|------------------|-------------|  
|Übergeordnetes Element|[ErrorConfiguration](../objects/errorconfiguration-element-assl.md)|  
|Untergeordnete Elemente|None|  
  
## <a name="remarks"></a>Hinweise  
 Fehler aufgrund von doppelten Schlüsseln werden nur während der Dimensionsverarbeitung generiert, wenn ein Attributschlüssel mehr als einmal auftaucht. Da Attributschlüssel eindeutig sein müssen [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] verwirft die doppelten Datensätze. Fehler aufgrund von doppelten Schlüsseln deuten normalerweise auf einen Schwachpunkt im Design der Dimension und insbesondere in den Beziehungen zwischen Attributen hin.  
  
 Der Wert dieses Elements ist auf eine der in der folgenden Tabelle aufgelisteten Zeichenfolgen beschränkt.  
  
|value|Description|  
|-----------|-----------------|  
|*IgnoreError*|Die Verarbeitung sollte den Fehler ignorieren und fortfahren.|  
|*ReportAndContinue*|Die Verarbeitung sollte den Fehler berichten und fortfahren.|  
|*ReportAndStop*|Die Verarbeitung sollte den Fehler berichten und anhalten.|  
  
 Die Enumeration, die den zulässigen Werten für entspricht `KeyDuplicate` im Objekt Analysis Management Objects (AMO) Modell ist <xref:Microsoft.AnalysisServices.ErrorOption>.  
  
## <a name="see-also"></a>Siehe auch  
 [Eigenschaften &#40;ASSL&#41;](properties-assl.md)  
  
  
