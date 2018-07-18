---
title: Type-Element (ClrAssemblyFile) (ASSL) | Microsoft-Dokumentation
ms.date: 5/8/2018
ms.prod: sql
ms.custom: assl
ms.reviewer: owend
ms.technology: analysis-services
ms.topic: reference
author: minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: a4cf5d0a1ef4fd627dd10d0b73ca1520980484fe
ms.sourcegitcommit: e77197ec6935e15e2260a7a44587e8054745d5c2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/11/2018
ms.locfileid: "37990302"
---
# <a name="type-element-clrassemblyfile-assl"></a>Type-Element (ClrAssemblyFile) (ASSL)
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]
  Gibt den Dateityp von einer der Dateien, die zu gehören eine [!INCLUDE[msCoName](../../../includes/msconame-md.md)] .NET Framework-Assembly.  
  
## <a name="syntax"></a>Syntax  
  
```xml  
  
<ClrAssemblyFile>  
      ...  
      <Type>...</Type>  
   ...  
</ClrAssemblyFile>  
```  
  
## <a name="element-characteristics"></a>Elementmerkmale  
  
|Merkmal|Description|  
|--------------------|-----------------|  
|Datentyp und -länge|Zeichenfolge (Enumeration)|  
|Standardwert|InclusionThresholdSetting|  
|Cardinality|1-1: Erforderliches Element, das nur einmal auftritt.|  
  
## <a name="element-relationships"></a>Elementbeziehungen  
  
|Beziehung|Element|  
|------------------|-------------|  
|Übergeordnetes Element|[Clrassemblyfile-Objekts](../../../analysis-services/scripting/data-type/clrassemblyfile-data-type-assl.md)|  
|Untergeordnete Elemente|InclusionThresholdSetting|  
  
## <a name="remarks"></a>Hinweise  
 Der Wert dieses Elements ist auf eine der folgenden Zeichenfolgen beschränkt:  
  
|value|Description|  
|-----------|-----------------|  
|*Main*|Die angegebene Datei ist die Hauptdatei in der Assembly.|  
|*Abhängige*|Die angegebene Datei ist eine abhängige Datei in der Assembly.|  
|*Debuggen*|Die angegebene Datei enthält Debuginformationen.|  
  
 Die Enumeration, die den zulässigen Werten für entspricht **Typ** im Objekt Analysis Management Objects (AMO) Modell ist <xref:Microsoft.AnalysisServices.ClrAssemblyFileType>.  
  
 Das Element, das dem übergeordneten entspricht **Typ** im Objekt Analysis Management Objects (AMO) Modell ist <xref:Microsoft.AnalysisServices.ClrAssemblyFile>.  
  
## <a name="see-also"></a>Siehe auch  
 [File Element &#40;ASSL&#41;](../../../analysis-services/scripting/objects/file-element-assl.md)   
 [Dateien Element &#40;ASSL&#41;](../../../analysis-services/scripting/collections/files-element-assl.md)   
 [ClrAssembly-Datentyp &#40;ASSL&#41;](../../../analysis-services/scripting/data-type/clrassembly-data-type-assl.md)   
 [Assembly-Element &#40;ASSL&#41;](../../../analysis-services/scripting/objects/assembly-element-assl.md)   
 [Assemblies-Element &#40;ASSL&#41;](../../../analysis-services/scripting/collections/assemblies-element-assl.md)   
 [Eigenschaften &#40;ASSL&#41;](../../../analysis-services/scripting/properties/properties-assl.md)  
  
  
