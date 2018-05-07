---
title: ServerProperty-Element (ASSL) | Microsoft Docs
ms.date: 05/03/2018
ms.prod: sql
ms.technology: analysis-services
ms.component: assl
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: fd8d5ff3afbb85b2f087e4476dc81777b524deca
ms.sourcegitcommit: f1caaa156db2b16e817e0a3884394e7b30fb642f
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/04/2018
---
# <a name="serverproperty-element-assl"></a>ServerProperty-Element (ASSL)
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]
  Definiert eine zugeordnete Servereigenschaft eine [Server](../../../analysis-services/scripting/objects/server-element-assl.md) Element.  
  
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
  
|Merkmal|Beschreibung|  
|--------------------|-----------------|  
|Datentyp und -länge|Keine|  
|Standardwert|Keine|  
|Kardinalität|0-n: Optionales Element, das mehr als einmal auftreten kann.|  
  
## <a name="element-relationships"></a>Elementbeziehungen  
  
|Beziehung|Element|  
|------------------|-------------|  
|Übergeordnete Elemente|[ServerProperties](../../../analysis-services/scripting/collections/serverproperties-element-assl.md)|  
|Untergeordnete Elemente|["DefaultValue"](../../../analysis-services/scripting/properties/defaultvalue-element-assl.md), [DisplayFlag](../../../analysis-services/scripting/properties/displayflag-element-assl.md), [Namen](../../../analysis-services/scripting/properties/name-element-assl.md), [PendingValue](../../../analysis-services/scripting/properties/pendingvalue-element-assl.md), [RequiresRestart](../../../analysis-services/scripting/properties/requiresrestart-element-assl.md), [Wert](../../../analysis-services/scripting/properties/value-element-assl.md)|  
  
## <a name="remarks"></a>Hinweise  
 Die **ServerProperty** -Element beschreibt die Daten und Metadaten einer Servereigenschaft, die mit einer Instanz des verknüpften [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]. Anders als Elemente, die in anderen Auflistungen in ASSL (Analysis Services Scripting Language) enthalten sind, verwendet das **ServerProperty** -Element zum Beschreiben von Servereigenschaften Name/Wert-Paare und keine explizit benannten Elemente. Die Name/Wert-Paare sorgen für Flexibilität und Erweiterbarkeit.  
  
 Das entsprechende Element im Objektmodell von Analysis Management Objects (AMO) ist <xref:Microsoft.AnalysisServices.ServerProperty>.  
  
## <a name="see-also"></a>Siehe auch  
 [Server-Element & #40; ASSL & #41;](../../../analysis-services/scripting/objects/server-element-assl.md)   
 [Objekte & #40; ASSL & #41;](../../../analysis-services/scripting/objects/objects-assl.md)  
  
  
