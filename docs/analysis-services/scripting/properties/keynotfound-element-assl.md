---
title: KeyNotFound-Element (ASSL) | Microsoft Docs
ms.date: 5/8/2018
ms.prod: sql
ms.component: assl
ms.reviewer: owend
ms.technology: analysis-services
ms.topic: reference
author: minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: e90452cb0b40dac2ce285cf0058ed820bff9c0dd
ms.sourcegitcommit: 38f8824abb6760a9dc6953f10a6c91f97fa48432
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/10/2018
---
# <a name="keynotfound-element-assl"></a>KeyNotFound-Element (ASSL)
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]
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
 Fehler in der referenziellen Integrität treten auf, wenn ein Fremdschlüsselwert in einer abhängigen Tabelle keinen entsprechenden Eintrag in der übergeordneten Tabelle aufweist. Dieser Fehler tritt auf, wenn [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] verarbeitet eine Dimension, die in der die Faktentabelle verweist auf einen Fremdschlüsselwert, der in der Dimensionstabelle für diese Dimension nicht vorhanden ist oder wenn [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] der Dimension Main Tabelle für eine Partition verarbeitet ein Dimension, in der Partition enthalten ist, verweist auf ein Schlüssel-Wert, der nicht in weiteren zugeordneten Dimensionstabelle existiert. (Bei Dimensionen mit Über-/Unterordnungshierarchien und übergeordneten Attributen kann der Fehler auch dann auftreten, wenn die Dimensionshaupttabelle für eine Dimension, die in der Partition enthalten ist, auf einen Schlüsselwert verweist, der nicht in derselben Dimensionstabelle existiert.)  
  
 Der Wert dieses Elements ist auf eine der in der folgenden Tabelle aufgelisteten Zeichenfolgen beschränkt.  
  
|Wert|Description|  
|-----------|-----------------|  
|*IgnoreError*|Die Verarbeitung sollte den Fehler ignorieren und fortfahren.|  
|*ReportAndContinue*|Die Verarbeitung sollte den Fehler berichten und fortfahren.|  
|*ReportAndStop*|Die Verarbeitung sollte den Fehler berichten und anhalten.|  
  
 Die Enumeration, die den zulässigen Werten für entspricht **KeyNotFound** im Objekt Analysis Management Objects (AMO) Modell ist <xref:Microsoft.AnalysisServices.ErrorOption>.  
  
## <a name="see-also"></a>Siehe auch  
 [Datenbankeigenschaften & #40; ASSL & #41;](../../../analysis-services/scripting/properties/properties-assl.md)  
  
  
