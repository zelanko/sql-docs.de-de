---
title: ServerMode-Element | Microsoft Docs
ms.date: 05/08/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: xmla
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 21e9344ef945311b3af07398e6e927482718f5ff
ms.sourcegitcommit: 808d23a654ef03ea16db1aa23edab496b73e5072
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/04/2018
ms.locfileid: "34576262"
---
# <a name="servermode-element"></a>ServerMode-Element
[!INCLUDE[ssas-appliesto-sqlas-aas](../../../includes/ssas-appliesto-sqlas-aas.md)]
  Das **ServerMode** -Serverelement gibt den Modus an, in dem der Server arbeitet.  
  
## <a name="syntax"></a>Syntax  
  
```xml  
  
<Server>  
...  
   <ddl300:ServerMode>...</ddl300:ServerMode>  
...  
</Server>  
```  
  
## <a name="element-characteristics"></a>Elementmerkmale  
  
|Merkmal|Description|  
|--------------------|-----------------|  
|Datentyp und -länge|Zeichenfolge (Enumeration)|  
|Standardwert|(none)|  
|Cardinality|0-1: Optionales Element, das nur einmal auftreten kann.|  
  
## <a name="element-relationships"></a>Elementbeziehungen  
  
|Beziehung|Element|  
|------------------|-------------|  
|Übergeordnete Elemente|[Server](../../../analysis-services/scripting/objects/server-element-assl.md)|  
|Untergeordnete Elemente|InclusionThresholdSetting|  
  
## <a name="remarks"></a>Hinweise  
 Der Server arbeitet in einem der folgenden beiden Modi:  
  
|value|Description|  
|-----------|-----------------|  
|*Mehrdimensionale*|Mehrdimensionaler und Data Mining-Modus|  
|*Tabellarische*|Tabellenmodus|  
|*SharePoint*|SharePoint-Modus|  
  
## <a name="see-also"></a>Siehe auch
 [Server](../../../analysis-services/scripting/objects/server-element-assl.md)  
  
  
