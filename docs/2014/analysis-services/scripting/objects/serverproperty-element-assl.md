---
title: ServerProperty-Element (ASSL) | Microsoft Docs
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
- ServerProperty Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- SERVERPROPERTY
helpviewer_keywords:
- ServerProperty element
ms.assetid: f152a1b5-0972-40d8-907f-f131c2a108bb
caps.latest.revision: 37
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: 6cb62681b0c25c83d54076a67a37addc764102da
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/19/2018
ms.locfileid: "36048575"
---
# <a name="serverproperty-element-assl"></a>ServerProperty-Element (ASSL)
  Definiert eine zugeordnete Servereigenschaft eine [Server](server-element-assl.md) Element.  
  
## <a name="syntax"></a>Syntax  
  
```xml  
  
<ServerProperties>  
   <ServerProperty>  
      <Name>...</Name>  
      <Value>...</Value>  
            <RequiresRestart>...</RequiresRestart>  
            <PendingValue>...</PendingValue>  
      <DefaultValue>...</DefaultValue>  
      <DisplayFlag>...</DisplayFlag>  
   </ServerProperty>  
</ServerProperties>  
```  
  
## <a name="element-characteristics"></a>Elementmerkmale  
  
|Merkmal|Description|  
|--------------------|-----------------|  
|Datentyp und -länge|InclusionThresholdSetting|  
|Standardwert|InclusionThresholdSetting|  
|Cardinality|0-n: Optionales Element, das mehr als einmal auftreten kann.|  
  
## <a name="element-relationships"></a>Elementbeziehungen  
  
|Beziehung|Element|  
|------------------|-------------|  
|Übergeordnete Elemente|[ServerProperties](../collections/serverproperties-element-assl.md)|  
|Untergeordnete Elemente|["DefaultValue"](../properties/value-element-assl.md), [DisplayFlag](../properties/displayflag-element-assl.md), [Namen](../properties/name-element-assl.md), [PendingValue](../properties/pendingvalue-element-assl.md), [RequiresRestart](../properties/requiresrestart-element-assl.md), [Wert](../properties/value-element-assl.md)|  
  
## <a name="remarks"></a>Hinweise  
 Die `ServerProperty` -Element beschreibt die Daten und Metadaten einer Servereigenschaft, die mit einer Instanz des verknüpften [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]. Anders als Elemente, die in anderen Auflistungen in ASSL (Analysis Services Scripting Language) enthalten sind, verwendet das `ServerProperty`-Element zum Beschreiben von Servereigenschaften Name/Wert-Paare und keine explizit benannten Elemente. Die Name/Wert-Paare sorgen für Flexibilität und Erweiterbarkeit.  
  
 Das entsprechende Element im Objektmodell von Analysis Management Objects (AMO) ist <xref:Microsoft.AnalysisServices.ServerProperty>.  
  
## <a name="see-also"></a>Siehe auch  
 [Server-Element &#40;ASSL&#41;](server-element-assl.md)   
 [Objekte &#40;ASSL&#41;](objects-assl.md)  
  
  