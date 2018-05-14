---
title: ProcessingQuery-Element (ASSL) | Microsoft Docs
ms.date: 5/8/2018
ms.prod: sql
ms.custom: assl
ms.reviewer: owend
ms.technology: analysis-services
ms.topic: reference
author: minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: ff294d15e56f23721cd87f1934298e9fea756328
ms.sourcegitcommit: c12a7416d1996a3bcce3ebf4a3c9abe61b02fb9e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/10/2018
---
# <a name="processingquery-element-assl"></a>ProcessingQuery-Element (ASSL)
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]
  Enthält den parametrisierten Text der Abfrage, die für eine Benachrichtigung über den inkrementellen Verarbeitungsstatus ausgeführt werden muss.  
  
## <a name="syntax"></a>Syntax  
  
```xml  
  
<IncrementalProcessingNotification>  
   ...  
   <ProcessingQuery>...</ProcessingQuery>  
   ...  
</IncrementalProcessingNotification>  
```  
  
## <a name="element-characteristics"></a>Elementmerkmale  
  
|Merkmal|Beschreibung|  
|--------------------|-----------------|  
|Datentyp und -länge|String|  
|Standardwert|Keine|  
|Kardinalität|1-1: Erforderliches Element, das nur einmal auftritt.|  
  
## <a name="element-relationships"></a>Elementbeziehungen  
  
|Beziehung|Element|  
|------------------|-------------|  
|Übergeordnetes Element|[IncrementalProcessingNotification](../../../analysis-services/scripting/objects/incrementalprocessingnotification-element-assl.md)|  
|Untergeordnete Elemente|Keine|  
  
## <a name="remarks"></a>Hinweise  
 Die Tabelle in der [DataSourceView](../../../analysis-services/scripting/objects/datasourceview-element-assl.md) , verweist der **ProcessingQuery** wird durch das gleichgeordnete Element identifiziert [TableID](../../../analysis-services/scripting/properties/tableid-element-assl.md).  
  
 Das Element, das das übergeordnete Element des entspricht **ProcessingQuery** im Objekt Analysis Management Objects (AMO) Modell ist <xref:Microsoft.AnalysisServices.IncrementalProcessingNotification>.  
  
## <a name="see-also"></a>Siehe auch  
 [Datenbankeigenschaften & #40; ASSL & #41;](../../../analysis-services/scripting/properties/properties-assl.md)  
  
  
