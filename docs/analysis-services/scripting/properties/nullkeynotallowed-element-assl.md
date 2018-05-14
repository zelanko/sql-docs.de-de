---
title: NullKeyNotAllowed-Element (ASSL) | Microsoft Docs
ms.date: 5/8/2018
ms.prod: sql
ms.custom: assl
ms.reviewer: owend
ms.technology: analysis-services
ms.topic: reference
author: minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: 0a7d499729efa4e9079fb01c864faf1f2a21f75d
ms.sourcegitcommit: c12a7416d1996a3bcce3ebf4a3c9abe61b02fb9e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/10/2018
---
# <a name="nullkeynotallowed-element-assl"></a>NullKeyNotAllowed-Element (ASSL)
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]
  Bestimmt, wie die [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] -Verarbeitungsmodul einen null-Schlüsselfehler während der Verarbeitung auftreten.  
  
## <a name="syntax"></a>Syntax  
  
```xml  
  
<ErrorConfiguration>  
   ...  
   <NullKeyNotAllowed>...</NullKeyNotAllowed>  
   ...  
</ErrorConfiguration>  
```  
  
## <a name="element-characteristics"></a>Elementmerkmale  
  
|Merkmal|Beschreibung|  
|--------------------|-----------------|  
|Datentyp und -länge|Zeichenfolge (Enumeration)|  
|Standardwert|*ReportAndContinue*|  
|Kardinalität|0-1: Optionales Element, das nur einmal auftreten kann.|  
  
## <a name="element-relationships"></a>Elementbeziehungen  
  
|Beziehung|Element|  
|------------------|-------------|  
|Übergeordnetes Element|[ErrorConfiguration](../../../analysis-services/scripting/objects/errorconfiguration-element-assl.md)|  
|Untergeordnete Elemente|Keine|  
  
## <a name="remarks"></a>Hinweise  
 NULL-Schlüsselfehler treten auf, wenn ein NULL-Wert in einer Schlüsselspalte auftritt, in der NULL-Werte nicht zulässig sind, wodurch ein Verwerfen des Datensatzes während der Verarbeitung erzwungen wird. Dieser Fehler tritt jedoch nur, wenn die [NullProcessing](../../../analysis-services/scripting/properties/nullprocessing-element-assl.md) -Element für die **DataItem** Vorgänger des der **ErrorConfiguration** übergeordnetes Element festgelegt ist, um  *Fehler*.  
  
 Der Wert dieses Elements ist auf eine der in der folgenden Tabelle aufgelisteten Zeichenfolgen beschränkt.  
  
|Wert|Description|  
|-----------|-----------------|  
|*IgnoreError*|Die Verarbeitung ignoriert den Fehler und setzt die Verarbeitung fort.|  
|*ReportAndContinue*|Die Verarbeitung meldet den Fehler und setzt die Verarbeitung fort.|  
|*ReportAndStop*|Die Verarbeitung meldet den Fehler und beendet die Verarbeitung.|  
  
 Die Enumeration, die den zulässigen Werten für entspricht **NullKeyNotAllowed** im Objekt Analysis Management Objects (AMO) Modell ist <xref:Microsoft.AnalysisServices.ErrorOption>.  
  
## <a name="see-also"></a>Siehe auch  
 [ErrorConfiguration-Element &#40;ASSL&#41;](../../../analysis-services/scripting/objects/errorconfiguration-element-assl.md)  
  
  
