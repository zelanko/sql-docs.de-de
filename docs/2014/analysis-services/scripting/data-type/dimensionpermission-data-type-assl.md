---
title: DimensionPermission-Datentyp (ASSL) | Microsoft Docs
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
- DimensionPermission Data Type
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
helpviewer_keywords:
- DimensionPermission data type
ms.assetid: 066405ff-903f-467a-b0d5-e58653952c52
caps.latest.revision: 17
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: 1c614d2fd30f7bd3b831c571cc4d3de0cf26e365
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/19/2018
ms.locfileid: "36059002"
---
# <a name="dimensionpermission-data-type-assl"></a>DimensionPermission-Datentyp (ASSL)
  Definiert einen abgeleiteten Datentyp, der die einer Datenbankdimension zugewiesenen Berechtigungen darstellt.  
  
## <a name="syntax"></a>Syntax  
  
```xml  
  
<DimensionPermission>  
   <!-- The following elements extend Permission -->  
   <AttributePermissions>...</AttributePermissions>  
   <AllowedRowsExpression>...</AllowedRowsExpression>  
</DimensionPermission>  
```  
  
## <a name="data-type-characteristics"></a>Datentypmerkmale  
  
|Merkmal|Description|  
|--------------------|-----------------|  
|Basisdatentypen|[Berechtigung](permission-data-type-assl.md)|  
|Abgeleitete Datentypen|InclusionThresholdSetting|  
  
## <a name="data-type-relationships"></a>Datentypbeziehungen  
  
|Beziehung|Element|  
|------------------|-------------|  
|Übergeordnete Elemente|InclusionThresholdSetting|  
|Untergeordnete Elemente|[AttributePermissions](../collections/attributepermissions-element-assl.md), [AllowedRowsExpression](../collections/attributepermissions-element-assl.md)|  
|Abgeleitete Elemente|[DimensionPermission](../objects/dimensionpermission-element-assl.md)|  
  
## <a name="remarks"></a>Hinweise  
 Diesem Element sind unter dem DeploymentMode-Wert 2 (tabellarischer Servermodus) die folgenden Überprüfungen zugeordnet:  
  
-   Das*AttributePermission* -Attribut muss leer sein, andernfalls tritt ein Fehler auf.  
  
 Dieses Element verfügt über die folgenden Überprüfungen unter dem DeploymentMode-Wert 0 (OLAP).  
  
-   Das*AllowedRowsExpression* -Attribut muss leer sein, andernfalls tritt ein Fehler auf.  
  
 Das entsprechende Element im Objektmodell von Analysis Management Objects (AMO) ist <xref:Microsoft.AnalysisServices.DimensionPermission>.  
  
## <a name="see-also"></a>Siehe auch  
 [Analysis Services Scripting Language-XML-Datentypen &#40;ASSL&#41;](analysis-services-scripting-language-xml-data-types-assl.md)  
  
  