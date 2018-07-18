---
title: DataBlock-Datentyp (ASSL) | Microsoft Docs
ms.date: 05/03/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: assl
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 656ed967d0e306668203abd46a4b2525655e0f61
ms.sourcegitcommit: c12a7416d1996a3bcce3ebf4a3c9abe61b02fb9e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/10/2018
ms.locfileid: "34032041"
---
# <a name="datablock-data-type-assl"></a>DataBlock-Datentyp (ASSL)
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]
  Definiert einen Grunddatentyp, der eine Auflistung von Datenblöcken darstellt, die verwendet werden, um binäre Inhalte des [ClrAssemblyFile](../../../analysis-services/scripting/data-type/clrassemblyfile-data-type-assl.md) -Elements zu speichern.  
  
## <a name="syntax"></a>Syntax  
  
```xml  
  
<DataBlock>  
   <Blocks>...</Blocks>  
</DataBlock>  
```  
  
## <a name="data-type-characteristics"></a>Datentypmerkmale  
  
|Merkmal|Beschreibung|  
|--------------------|-----------------|  
|Basisdatentypen|Keine|  
|Abgeleitete Datentypen|Keine|  
  
## <a name="data-type-relationships"></a>Datentypbeziehungen  
  
|Beziehung|Element|  
|------------------|-------------|  
|Übergeordnete Elemente|Keine|  
|Untergeordnete Elemente|[Blöcke](../../../analysis-services/scripting/collections/blocks-element-assl.md)|  
|Abgeleitete Elemente|[Data](../../../analysis-services/scripting/objects/data-element-assl.md) -Element des [ClrAssemblyFile](../../../analysis-services/scripting/data-type/clrassemblyfile-data-type-assl.md) -Typs ([Files](../../../analysis-services/scripting/collections/files-element-assl.md) -Auflistung des [ClrAssembly](../../../analysis-services/scripting/data-type/clrassembly-data-type-assl.md) -Typs)|  
  
## <a name="see-also"></a>Siehe auch  
 [Assembly-Element & #40; ASSL & #41;](../../../analysis-services/scripting/objects/assembly-element-assl.md)   
 [File-Element & #40; ASSL & #41;](../../../analysis-services/scripting/objects/file-element-assl.md)   
 [Block-Element & #40; ASSL & #41;](../../../analysis-services/scripting/objects/block-element-assl.md)   
 [Analysis Services Scripting Language-XML-Datentypen & #40; ASSL & #41;](../../../analysis-services/scripting/data-type/analysis-services-scripting-language-xml-data-types-assl.md)  
  
  
