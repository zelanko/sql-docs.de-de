---
title: Type-Element (ClrAssemblyFile) (ASSL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.topic: reference
api_name:
- Type Element (ClrAssemblyFile)
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- TYPE
helpviewer_keywords:
- Type element
ms.assetid: ab9e1e2c-ab06-4cd1-b007-16d738dc5604
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 7f5f52857fd9e87541e07ee03ffd36a7b24a4e96
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/02/2018
ms.locfileid: "48140380"
---
# <a name="type-element-clrassemblyfile-assl"></a>Type-Element (ClrAssemblyFile) (ASSL)
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
|Standardwert|None|  
|Cardinality|1-1: Erforderliches Element, das nur einmal auftritt.|  
  
## <a name="element-relationships"></a>Elementbeziehungen  
  
|Beziehung|Element|  
|------------------|-------------|  
|Übergeordnetes Element|[Clrassemblyfile-Objekts](../data-type/clrassemblyfile-data-type-assl.md)|  
|Untergeordnete Elemente|None|  
  
## <a name="remarks"></a>Hinweise  
 Der Wert dieses Elements ist auf eine der folgenden Zeichenfolgen beschränkt:  
  
|value|Description|  
|-----------|-----------------|  
|*Main*|Die angegebene Datei ist die Hauptdatei in der Assembly.|  
|*Abhängige*|Die angegebene Datei ist eine abhängige Datei in der Assembly.|  
|*Debuggen*|Die angegebene Datei enthält Debuginformationen.|  
  
 Die Enumeration, die den zulässigen Werten für entspricht `Type` im Objekt Analysis Management Objects (AMO) Modell ist <xref:Microsoft.AnalysisServices.ClrAssemblyFileType>.  
  
 Das Element, das dem übergeordneten entspricht `Type` im Objekt Analysis Management Objects (AMO) Modell ist <xref:Microsoft.AnalysisServices.ClrAssemblyFile>.  
  
## <a name="see-also"></a>Siehe auch  
 [File Element &#40;ASSL&#41;](../objects/file-element-assl.md)   
 [Dateien Element &#40;ASSL&#41;](../collections/files-element-assl.md)   
 [ClrAssembly-Datentyp &#40;ASSL&#41;](../data-type/assembly-data-type-assl.md)   
 [Assembly-Element &#40;ASSL&#41;](../objects/assembly-element-assl.md)   
 [Assemblies-Element &#40;ASSL&#41;](../collections/assemblies-element-assl.md)   
 [Eigenschaften &#40;ASSL&#41;](properties-assl.md)  
  
  
