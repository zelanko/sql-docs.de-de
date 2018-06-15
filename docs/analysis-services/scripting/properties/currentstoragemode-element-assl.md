---
title: CurrentStorageMode-Element (ASSL) | Microsoft Docs
ms.date: 05/08/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: assl
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: fd14d8a08253a85ff0cd14a33036806a4b008e53
ms.sourcegitcommit: c12a7416d1996a3bcce3ebf4a3c9abe61b02fb9e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/10/2018
ms.locfileid: "34032391"
---
# <a name="currentstoragemode-element-assl"></a>CurrentStorageMode-Element (ASSL)
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]
  Bestimmt den aktuellen Speichermodus für das übergeordnete Element.  
  
## <a name="syntax"></a>Syntax  
  
```xml  
  
<Dimension> <!-- or Partition -->  
   <CurrentStorageMode>...</CurrentStorageMode>  
</Dimension>  
```  
  
## <a name="element-characteristics"></a>Elementmerkmale  
  
|Merkmal|Beschreibung|  
|--------------------|-----------------|  
|Datentyp und -länge|Zeichenfolge (Enumeration)|  
|Standardwert|*ROLAP*|  
|Kardinalität|0-1: Optionales Element, das nur einmal auftreten kann.|  
  
## <a name="element-relationships"></a>Elementbeziehungen  
  
|Beziehung|Element|  
|------------------|-------------|  
|Übergeordnetes Element|[Dimension](../../../analysis-services/scripting/objects/dimension-element-assl.md), [Partition](../../../analysis-services/scripting/objects/partition-element-assl.md)|  
|Untergeordnete Elemente|Keine|  
  
## <a name="remarks"></a>Hinweise  
 Das **CurrentStorageMode** -Element gibt den Speichermodus an, der derzeit für proaktives Zwischenspeichern verwendet wird, und gilt für alle Attribute des übergeordneten Elements.  
  
 Der Wert dieses Elements ist auf eine der in der folgenden Tabelle aufgelisteten Zeichenfolgen beschränkt.  
  
|Wert|Description|  
|-----------|-----------------|  
|*MOLAP*|Das übergeordnete Element verwendet die mehrdimensionale OLAP (MOLAP)-Speicherung.|  
|*ROLAP*|Das übergeordnete Element verwendet die relationale OLAP (ROLAP)-Speicherung.|  
|*HOLAP*|Das übergeordnete Element verwendet die hybride OLAP (HOLAP)-Speicherung.<br /><br /> Hinweis: Dieser Wert ist nur gültig für [Partition](../../../analysis-services/scripting/objects/partition-element-assl.md) übergeordneten Elementen.|  
  
 Die Enumeration, die den zulässigen Werten entspricht **CurrentStorageMode** im Objekt Analysis Management Objects (AMO) Modell ist <xref:Microsoft.AnalysisServices.StorageMode>.  
  
## <a name="see-also"></a>Siehe auch  
 [Datenbankeigenschaften & #40; ASSL & #41;](../../../analysis-services/scripting/properties/properties-assl.md)  
  
  
