---
title: NullKeyConvertedToUnknown-Element (ASSL) | Microsoft-Dokumentation
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
- NullKeyConvertedToUnknown Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- NullKeyConvertedToUnknown
helpviewer_keywords:
- NullKeyConvertedToUnknown element
ms.assetid: 1a6cde33-01ba-4095-b464-16d1ad3c6905
caps.latest.revision: 37
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: cebeef3421533b429a38f6c5696780cb008eca69
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/02/2018
ms.locfileid: "37316920"
---
# <a name="nullkeyconvertedtounknown-element-assl"></a>NullKeyConvertedToUnknown-Element (ASSL)
  Gibt die Aktion an, die beim Auftreten eines NULL-Konvertierungsfehlers ergriffen werden soll.  
  
## <a name="syntax"></a>Syntax  
  
```xml  
  
<ErrorConfiguration>  
   ...  
      <NullKeyConvertedToUnknown>...</NullKeyConvertedToUnknown>  
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
|Untergeordnete Elemente|InclusionThresholdSetting|  
  
## <a name="remarks"></a>Hinweise  
 NULL-Konvertierungsfehler treten auf, wenn ein Nullwert in einer Schlüsselspalte vorkommt und als `Unknown`-Element interpretiert wird. Dieser Fehler tritt jedoch nur, wenn die [NullProcessing](nullprocessing-element-assl.md) -Element für die [DataItem](../data-type/dataitem-data-type-assl.md) Vorgänger des der `ErrorConfiguration` übergeordnetes Element festgelegt ist, um *UnknownMember*.  
  
 Der Wert dieses Elements ist auf eine der in der folgenden Tabelle aufgelisteten Zeichenfolgen beschränkt.  
  
|value|Description|  
|-----------|-----------------|  
|*IgnoreError*|Die Verarbeitung ignoriert den Fehler und setzt die Verarbeitung fort.|  
|*ReportAndContinue*|Die Verarbeitung meldet den Fehler und setzt die Verarbeitung fort.|  
|*ReportAndStop*|Die Verarbeitung meldet den Fehler und beendet die Verarbeitung.|  
  
 Die Enumeration, die den zulässigen Werten für entspricht `NullKeyConvertedToUnknown` im Objekt Analysis Management Objects (AMO) Modell ist <xref:Microsoft.AnalysisServices.ErrorOption>.  
  
## <a name="see-also"></a>Siehe auch  
 [ErrorConfiguration-Element &#40;ASSL&#41;](../objects/errorconfiguration-element-assl.md)   
 [Eigenschaften &#40;ASSL&#41;](properties-assl.md)  
  
  
