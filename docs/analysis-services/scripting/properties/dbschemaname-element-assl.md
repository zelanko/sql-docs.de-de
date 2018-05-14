---
title: DbSchemaName-Element (ASSL) | Microsoft Docs
ms.date: 05/08/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: assl
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: b12e49ea8f0533a578eceb059862b044a5725111
ms.sourcegitcommit: c12a7416d1996a3bcce3ebf4a3c9abe61b02fb9e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/10/2018
---
# <a name="dbschemaname-element-assl"></a>DbSchemaName-Element (ASSL)
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]
  Enthält den Namen des Schemas verwendet, die für das übergeordnete Element in die Tabelle identifiziert durch die [DbTableName](../../../analysis-services/scripting/properties/dbtablename-element-assl.md) Element.  
  
## <a name="syntax"></a>Syntax  
  
```xml  
  
<TableBinding> <!-- or TableNotification -->  
   ...  
   <DbSchemaName>...</DbSchemaName>  
   ...  
</TableBinding>  
```  
  
## <a name="element-characteristics"></a>Elementmerkmale  
  
|Merkmal|Beschreibung|  
|--------------------|-----------------|  
|Datentyp und -länge|String|  
|Standardwert|Keine|  
|Kardinalität|0-1: Optionales Element, das nur einmal auftreten kann.|  
  
## <a name="element-relationships"></a>Elementbeziehungen  
  
|Beziehung|Element|  
|------------------|-------------|  
|Übergeordnetes Element|[TableBinding](../../../analysis-services/scripting/data-type/tablebinding-data-type-assl.md), [TableNotification](../../../analysis-services/scripting/objects/tablenotification-element-assl.md)|  
|Untergeordnete Elemente|Keine|  
  
## <a name="remarks"></a>Hinweise  
 Die Elemente, die den übergeordneten Elementen von entsprechen **DbSchemaName** im Objektmodell von Analysis Management Objects (AMO) sind <xref:Microsoft.AnalysisServices.TableBinding> und <xref:Microsoft.AnalysisServices.TableNotification>.  
  
## <a name="see-also"></a>Siehe auch  
 [Datenbankeigenschaften & #40; ASSL & #41;](../../../analysis-services/scripting/properties/properties-assl.md)  
  
  
