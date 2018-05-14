---
title: TableNotifications-Element (ASSL) | Microsoft Docs
ms.date: 05/03/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: assl
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: becc7005fa1a8d737344eefce0384a57013a19be
ms.sourcegitcommit: c12a7416d1996a3bcce3ebf4a3c9abe61b02fb9e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/10/2018
---
# <a name="tablenotifications-element-assl"></a>TableNotifications-Element (ASSL)
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]
  Enthält die Auflistung der [TableNotification](../../../analysis-services/scripting/objects/tablenotification-element-assl.md) Elemente, die Anmeldeinformationen für die [ProactiveCaching](../../../analysis-services/scripting/objects/proactivecaching-element-assl.md) Element zu Tabellen oder Sichten in einer Datenquelle, die geändert wurden.  
  
## <a name="syntax"></a>Syntax  
  
```xml  
  
<ProactiveCachingTablesBinding>  
   <TableNotifications>  
      <TableNotification>...</TableNotification>  
...</TableNotifications>  
</ProactiveCachingTablesBinding>  
```  
  
## <a name="element-characteristics"></a>Elementmerkmale  
  
|Merkmal|Beschreibung|  
|--------------------|-----------------|  
|Datentyp und -länge|Keine|  
|Standardwert|Keine|  
|Kardinalität|1-1: Erforderliches Element, das nur einmal auftritt.|  
  
## <a name="element-relationships"></a>Elementbeziehungen  
  
|Beziehung|Element|  
|------------------|-------------|  
|Übergeordnete Elemente|[ProactiveCachingTablesBinding](../../../analysis-services/scripting/data-type/proactivecachingtablesbinding-data-type-assl.md)|  
|Untergeordnete Elemente|[TableNotification](../../../analysis-services/scripting/objects/tablenotification-element-assl.md)|  
  
## <a name="remarks"></a>Hinweise  
 Das entsprechende Element im Objektmodell von Analysis Management Objects (AMO) ist <xref:Microsoft.AnalysisServices.TableNotificationCollection>.  
  
## <a name="see-also"></a>Siehe auch  
 [ProactiveCachingBinding-Datentyp &#40;ASSL&#41;](../../../analysis-services/scripting/data-type/proactivecachingbinding-data-type-assl.md)   
 [ProactiveCachingObjectNotificationBinding-Datentyp &#40;ASSL&#41;](../../../analysis-services/scripting/data-type/proactivecachingobjectnotificationbinding-data-type-assl.md)   
 [Schemaauflistungen & #40; ASSL & #41;](../../../analysis-services/scripting/collections/collections-assl.md)  
  
  
