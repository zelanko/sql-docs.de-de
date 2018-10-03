---
title: CubeDimensionPermission-Datentyp (ASSL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.topic: reference
api_name:
- CubeDimensionPermission Data Type
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- CubeDimensionPermission
helpviewer_keywords:
- CubeDimensionPermission data type
ms.assetid: d9d39859-5f33-48bc-a402-0071755918de
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 6b3eddc79ab599ec57001a33ed5163acec44ac6d
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/02/2018
ms.locfileid: "48099360"
---
# <a name="cubedimensionpermission-data-type-assl"></a>CubeDimensionPermission-Datentyp (ASSL)
  Definiert einen Grunddatentyp, der die Berechtigungen einer einzelnen Rolle in einer bestimmten Dimension in einem Cube darstellt.  
  
## <a name="syntax"></a>Syntax  
  
```xml  
  
<CubeDimensionPermission>  
   <CubeDimensionID>...</CubeDimensionID>  
   <Description>...</Description>  
   <Read>...</Read>  
   <Write>...</Write>  
   <AttributePermissions>...</AttributePermissions>  
   <Annotations>...</Annotations>  
</CubeDimensionPermission>  
```  
  
## <a name="data-type-characteristics"></a>Datentypmerkmale  
  
|Merkmal|Description|  
|--------------------|-----------------|  
|Basisdatentypen|None|  
|Abgeleitete Datentypen|None|  
  
## <a name="data-type-relationships"></a>Datentypbeziehungen  
  
|Beziehung|Element|  
|------------------|-------------|  
|Übergeordnete Elemente|None|  
|Untergeordnete Elemente|[Anmerkungen](../collections/annotations-element-assl.md), [AttributePermissions](../collections/attributepermissions-element-assl.md), [CubeDimensionID](../properties/id-element-assl.md), [Beschreibung](../properties/description-element-assl.md), [lesen](../properties/read-element-assl.md), [ Schreiben](../properties/write-element-assl.md)|  
|Abgeleitete Elemente|[DimensionPermission](../objects/dimensionpermission-element-assl.md) ([DimensionPermissions](../collections/dimensionpermissions-element-assl.md) Auflistung von [Dimension](../objects/dimension-element-assl.md) oder [CubePermission](../objects/cubepermission-element-assl.md))|  
  
## <a name="remarks"></a>Hinweise  
 Das entsprechende Element im Analysis Management Objects (AMO)-Objektmodell ist <xref:Microsoft.AnalysisServices.CubeDimensionPermission>.  
  
## <a name="see-also"></a>Siehe auch  
 [Analysis Services Scripting Language-XML-Datentypen &#40;ASSL&#41;](analysis-services-scripting-language-xml-data-types-assl.md)  
  
  
