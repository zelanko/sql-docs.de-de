---
title: ComAssembly-Datentyp (ASSL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.topic: reference
api_name:
- ComAssembly Data Type
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- ComAssembly
helpviewer_keywords:
- ComAssembly data type
ms.assetid: 23c0f4b3-b6ac-4ec8-9254-74d2f84f5244
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 9cf05a673de90310563cdc5264f61e2da0952450
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/02/2018
ms.locfileid: "48133450"
---
# <a name="comassembly-data-type-assl"></a>ComAssembly-Datentyp (ASSL)
  Definiert einen abgeleiteten Datentyp, der eine COM-Bibliothek im Zusammenhang mit darstellt, der eine [Server](../objects/server-element-assl.md) oder [Datenbank](../objects/database-element-assl.md) Element.  
  
> [!IMPORTANT]  
>  COM-Assemblys können ein Sicherheitsrisiko darstellen. Aufgrund dieses Risikos und anderer Überlegungen wurden COM-Assemblys in [!INCLUDE[ssASversion10](../../../includes/ssasversion10-md.md)]als veraltet markiert. COM-Assemblys werden in zukünftigen Versionen möglicherweise nicht mehr unterstützt.  
  
## <a name="syntax"></a>Syntax  
  
```xml  
  
<ComAssembly>  
      <!-- The following elements extend Assembly -->  
   <Source>...</Source>  
</ComAssembly>  
```  
  
## <a name="data-type-characteristics"></a>Datentypmerkmale  
  
|Merkmal|Description|  
|--------------------|-----------------|  
|Basisdatentypen|[Assembly](../objects/assembly-element-assl.md)|  
|Abgeleitete Datentypen|None|  
  
## <a name="data-type-relationships"></a>Datentypbeziehungen  
  
|Beziehung|Element|  
|------------------|-------------|  
|Übergeordnete Elemente|None|  
|Untergeordnete Elemente|[Quelle](../properties/source-element-comassembly-assl.md)|  
|Abgeleitete Elemente|Finden Sie unter [Assembly](../objects/assembly-element-assl.md) ([Assemblys](../collections/assemblies-element-assl.md) Auflistung von [Datenbank](../objects/database-element-assl.md) oder [Server](../objects/server-element-assl.md))|  
  
## <a name="remarks"></a>Hinweise  
 Die `ComAssembly` Element enthält einen Verweis (den vollqualifizierten Dateinamen oder den Programmbezeichner) auf eine COM-Bibliothek im Zusammenhang mit einer Instanz von [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] oder mit einer bestimmten Datenbank auf einer Instanz von [!INCLUDE[ssAS](../../../includes/ssas-md.md)].  
  
 Das entsprechende Element im Analysis Management Objects (AMO)-Objektmodell ist <xref:Microsoft.AnalysisServices.ComAssembly>.  
  
## <a name="see-also"></a>Siehe auch  
 [ClrAssembly-Datentyp &#40;ASSL&#41;](assembly-data-type-assl.md)   
 [Analysis Services Scripting Language-XML-Datentypen &#40;ASSL&#41;](analysis-services-scripting-language-xml-data-types-assl.md)  
  
  
