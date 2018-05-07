---
title: ClrAssembly-Datentyp (ASSL) | Microsoft Docs
ms.date: 05/03/2018
ms.prod: sql
ms.technology: analysis-services
ms.component: assl
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: d1c8b137cdcfd4cadb65fa5ffae195c2cf111d7e
ms.sourcegitcommit: f1caaa156db2b16e817e0a3884394e7b30fb642f
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/04/2018
---
# <a name="clrassembly-data-type-assl"></a>ClrAssembly-Datentyp (ASSL)
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]
  Definiert einen abgeleiteten Datentyp, der darstellt, der eine [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] Assembly zugeordnet eine [Datenbank](../../../analysis-services/scripting/objects/database-element-assl.md) oder [Server](../../../analysis-services/scripting/objects/server-element-assl.md) Element  
  
## <a name="syntax"></a>Syntax  
  
```xml  
  
<ClrAssembly>  
      <!-- The following elements extend Assembly -->  
   <Files>...</Files>  
      <PermissionSet>...</PermissionSet>  
</ClrAssembly>  
```  
  
## <a name="data-type-characteristics"></a>Datentypmerkmale  
  
|Merkmal|Beschreibung|  
|--------------------|-----------------|  
|Basisdatentypen|[Assembly](../../../analysis-services/scripting/objects/assembly-element-assl.md)|  
|Abgeleitete Datentypen|Keine|  
  
## <a name="data-type-relationships"></a>Datentypbeziehungen  
  
|Beziehung|Element|  
|------------------|-------------|  
|Übergeordnete Elemente|Keiner (abstrakter Typ)|  
|Untergeordnete Elemente|[Files](../../../analysis-services/scripting/collections/files-element-assl.md), [PermissionSet](../../../analysis-services/scripting/properties/permissionset-element-assl.md)|  
|Abgeleitete Elemente|See [Assembly](../../../analysis-services/scripting/objects/assembly-element-assl.md) ([Assemblies](../../../analysis-services/scripting/collections/assemblies-element-assl.md) -Auflistung von [Database](../../../analysis-services/scripting/objects/database-element-assl.md) oder [Server](../../../analysis-services/scripting/objects/server-element-assl.md))|  
  
## <a name="remarks"></a>Hinweise  
 Die **ClrAssembly** Element enthält die Dateien, die erforderlich sind, neu erstellen einer [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] Assembly verknüpft sind, entweder mit einer Instanz von [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] oder mit einer bestimmten Datenbank auf einer Instanz von [!INCLUDE[ssAS](../../../includes/ssas-md.md)], sowie die Berechtigungen zum Ausführen der Assembly erforderlich.  
  
 Das entsprechende Element im Objektmodell von Analysis Management Objects (AMO) ist <xref:Microsoft.AnalysisServices.ClrAssembly>.  
  
## <a name="see-also"></a>Siehe auch  
 [File-Element & #40; ASSL & #41;](../../../analysis-services/scripting/objects/file-element-assl.md)   
 [ClrAssemblyFile-Datentyp & #40; ASSL & #41;](../../../analysis-services/scripting/data-type/clrassemblyfile-data-type-assl.md)   
 [Data-Element & #40; ASSL & #41;](../../../analysis-services/scripting/objects/data-element-assl.md)   
 [DataBlock-Datentyp & #40; ASSL & #41;](../../../analysis-services/scripting/data-type/datablock-data-type-assl.md)   
 [Blocks-Element & #40; ASSL & #41;](../../../analysis-services/scripting/collections/blocks-element-assl.md)   
 [Block-Element & #40; ASSL & #41;](../../../analysis-services/scripting/objects/block-element-assl.md)   
 [ComAssembly-Datentyp & #40; ASSL & #41;](../../../analysis-services/scripting/data-type/comassembly-data-type-assl.md)   
 [Analysis Services Scripting Language-XML-Datentypen & #40; ASSL & #41;](../../../analysis-services/scripting/data-type/analysis-services-scripting-language-xml-data-types-assl.md)  
  
  
