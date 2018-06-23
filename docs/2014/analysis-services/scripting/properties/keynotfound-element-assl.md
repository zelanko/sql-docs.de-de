---
title: KeyNotFound-Element (ASSL) | Microsoft Docs
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
- KeyNotFound Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- KeyNotFound
helpviewer_keywords:
- KeyNotFound element
ms.assetid: 2a93bbfa-2409-4e94-8b68-926532895a4c
caps.latest.revision: 35
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: 545ae163b4dda53adb60f5300e7f8b75cf926d52
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/19/2018
ms.locfileid: "36159055"
---
# <a name="keynotfound-element-assl"></a>KeyNotFound-Element (ASSL)
  Gibt an, wie [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] reagiert, wenn einen Fehler der referenziellen Integrität festgestellt wird.  
  
## <a name="syntax"></a>Syntax  
  
```xml  
  
<ErrorConfiguration>  
   ...  
      <KeyNotFound>...</KeyNotFound>  
   ...  
</ErrorConfiguration>  
```  
  
## <a name="element-characteristics"></a>Elementmerkmale  
  
|Merkmal|Description|  
|--------------------|-----------------|  
|Datentyp und -länge|Zeichenfolge (Enumeration)|  
|Standardwert|*ReportAndContinue*|  
|Cardinality|0-1: Optionales Element, das nur einmal auftreten kann.|  
  
## <a name="element-relationships"></a>Elementbeziehungen  
  
|Beziehung|Element|  
|------------------|-------------|  
|Übergeordnetes Element|[ErrorConfiguration](../objects/errorconfiguration-element-assl.md)|  
|Untergeordnete Elemente|InclusionThresholdSetting|  
  
## <a name="remarks"></a>Hinweise  
 Fehler in der referenziellen Integrität treten auf, wenn ein Fremdschlüsselwert in einer abhängigen Tabelle keinen entsprechenden Eintrag in der übergeordneten Tabelle aufweist. Dieser Fehler tritt auf, wenn [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] verarbeitet eine Dimension, die in der die Faktentabelle verweist auf einen Fremdschlüsselwert, der in der Dimensionstabelle für diese Dimension nicht vorhanden ist oder wenn [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] der Dimension Main Tabelle für eine Partition verarbeitet ein Dimension, in der Partition enthalten ist, verweist auf ein Schlüssel-Wert, der nicht in weiteren zugeordneten Dimensionstabelle existiert. (Bei Dimensionen mit Über-/Unterordnungshierarchien und übergeordneten Attributen kann der Fehler auch dann auftreten, wenn die Dimensionshaupttabelle für eine Dimension, die in der Partition enthalten ist, auf einen Schlüsselwert verweist, der nicht in derselben Dimensionstabelle existiert.)  
  
 Der Wert dieses Elements ist auf eine der in der folgenden Tabelle aufgelisteten Zeichenfolgen beschränkt.  
  
|value|Description|  
|-----------|-----------------|  
|*IgnoreError*|Die Verarbeitung sollte den Fehler ignorieren und fortfahren.|  
|*ReportAndContinue*|Die Verarbeitung sollte den Fehler berichten und fortfahren.|  
|*ReportAndStop*|Die Verarbeitung sollte den Fehler berichten und anhalten.|  
  
 Die Enumeration, die den zulässigen Werten für entspricht `KeyNotFound` im Objekt Analysis Management Objects (AMO) Modell ist <xref:Microsoft.AnalysisServices.ErrorOption>.  
  
## <a name="see-also"></a>Siehe auch  
 [Eigenschaften &#40;ASSL&#41;](properties-assl.md)  
  
  