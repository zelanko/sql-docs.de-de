---
title: Detach-Element | Microsoft Docs
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
helpviewer_keywords:
- Detach command
ms.assetid: adbc7920-2a4a-4842-9e6f-37006fa19ff8
caps.latest.revision: 10
author: mgblythe
ms.author: mblythe
manager: mblythe
ms.openlocfilehash: e63bad3a6bbedc847307530cfa7a7afcd4138263
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/19/2018
ms.locfileid: "36148178"
---
# <a name="detach-element"></a>Detach-Element
  Trennt eine [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] -Datenbank von der aktuellen Serverinstanz.  
  
## <a name="syntax"></a>Syntax  
  
```xml  
  
<Command>  
   <Detach>  
      <Object>...</Object>  
      <Password>...</Password>  
   </Detach>  
</Command>  
  
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
|Übergeordnete Elemente|[Befehl](../xml-elements-properties/command-element-xmla.md)|  
|Untergeordnete Elemente|[Objekt](../xml-elements-properties/object-element-xmla.md)<br /><br /> [Kennwort](../xml-elements-properties/password-element-xmla.md)|  
  
## <a name="see-also"></a>Siehe auch  
 <xref:Microsoft.AnalysisServices.Database.Detach%2A>   
 [Attach-Element](attach-element.md)   
 [Anfügen und Trennen von Analysis Services-Datenbanken](../../multidimensional-models/attach-and-detach-analysis-services-databases.md)   
 [Verschieben einer Analysis Services-Datenbank](../../multidimensional-models/move-an-analysis-services-database.md)   
 [Datenbank-ReadWriteModes](../../multidimensional-models/database-readwritemodes.md)   
 [Umschalten Sie in einer Analysis Services-Datenbank zwischen Schreib-und Lesemodus](../../multidimensional-models/switch-an-analysis-services-database-between-readonly-and-readwrite-modes.md)  
  
  