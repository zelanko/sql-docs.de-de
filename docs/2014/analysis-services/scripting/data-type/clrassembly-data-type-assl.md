---
title: ClrAssembly-Datentyp (ASSL) | Microsoft Docs
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
- ClrAssembly Data Type
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- ClrAssembly
helpviewer_keywords:
- ClrAssembly data type
ms.assetid: 3f5dc5a1-ebd6-41b8-ac04-91d4de137eb4
caps.latest.revision: 44
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: e17992a5d15113ec0de5dd75978f932cb83d11c8
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/19/2018
ms.locfileid: "36057287"
---
# <a name="clrassembly-data-type-assl"></a>ClrAssembly-Datentyp (ASSL)
  Definiert einen abgeleiteten Datentyp, der darstellt, der eine [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] Assembly zugeordnet eine [Datenbank](../objects/database-element-assl.md) oder [Server](../objects/server-element-assl.md) Element  
  
## <a name="syntax"></a>Syntax  
  
```xml  
  
<ClrAssembly>  
      <!-- The following elements extend Assembly -->  
   <Files>...</Files>  
      <PermissionSet>...</PermissionSet>  
</ClrAssembly>  
```  
  
## <a name="data-type-characteristics"></a>Datentypmerkmale  
  
|Merkmal|Description|  
|--------------------|-----------------|  
|Basisdatentypen|[Assembly](../objects/assembly-element-assl.md)|  
|Abgeleitete Datentypen|InclusionThresholdSetting|  
  
## <a name="data-type-relationships"></a>Datentypbeziehungen  
  
|Beziehung|Element|  
|------------------|-------------|  
|Übergeordnete Elemente|Keiner (abstrakter Typ)|  
|Untergeordnete Elemente|[Dateien](../collections/files-element-assl.md), [PermissionSet](../properties/permissionset-element-assl.md)|  
|Abgeleitete Elemente|Finden Sie unter [Assembly](../objects/assembly-element-assl.md) ([Assemblys](../collections/assemblies-element-assl.md) Auflistung von [Datenbank](../objects/database-element-assl.md) oder [Server](../objects/server-element-assl.md))|  
  
## <a name="remarks"></a>Hinweise  
 Die `ClrAssembly` Element enthält die Dateien, die erforderlich sind, neu erstellen einer [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] Assembly verknüpft sind, entweder mit einer Instanz von [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] oder mit einer bestimmten Datenbank auf einer Instanz von [!INCLUDE[ssAS](../../../includes/ssas-md.md)], als auch die Berechtigungen zum Ausführen der Assembly erforderlich.  
  
 Das entsprechende Element im Objektmodell von Analysis Management Objects (AMO) ist <xref:Microsoft.AnalysisServices.ClrAssembly>.  
  
## <a name="see-also"></a>Siehe auch  
 [Datei Element &#40;ASSL&#41;](../objects/file-element-assl.md)   
 [ClrAssemblyFile-Datentyp &#40;ASSL&#41;](clrassemblyfile-data-type-assl.md)   
 [Datenelement &#40;ASSL&#41;](../objects/data-element-assl.md)   
 [DataBlock-Datentyp &#40;ASSL&#41;](datablock-data-type-assl.md)   
 [Element blockiert &#40;ASSL&#41;](../collections/blocks-element-assl.md)   
 [Element sperren &#40;ASSL&#41;](../objects/block-element-assl.md)   
 [ComAssembly-Datentyp &#40;ASSL&#41;](assembly-data-type-assl.md)   
 [Analysis Services Scripting Language-XML-Datentypen &#40;ASSL&#41;](analysis-services-scripting-language-xml-data-types-assl.md)  
  
  