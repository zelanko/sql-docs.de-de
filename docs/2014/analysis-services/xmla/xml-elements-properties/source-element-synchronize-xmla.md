---
title: Source-Element (Synchronize) (XMLA) | Microsoft Docs
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
- Source Element (Synchronize)
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- urn:schemas-microsoft-com:xml-analysis#Source
- http://schemas.microsoft.com/analysisservices/2003/engine#Source
- microsoft.xml.analysis.source
helpviewer_keywords:
- Source element
ms.assetid: 0a857f91-771f-4c5e-8bf7-4bf17442d4df
caps.latest.revision: 11
author: mgblythe
ms.author: mblythe
manager: mblythe
ms.openlocfilehash: 5341a6c993c6053dbe6716dcfcd5155f81a4ae0c
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/19/2018
ms.locfileid: "36160978"
---
# <a name="source-element-synchronize-xmla"></a>Source-Element (Synchronize) (XMLA)
  Stellt eine Quelldatenbank dar, von der während eines [Synchronize](../xml-elements-commands/synchronize-element-xmla.md) -Befehls eine Zieldatenbank synchronisiert werden soll.  
  
## <a name="syntax"></a>Syntax  
  
```xml  
  
<Synchronize>  
   <Source>  
      <Object>...</Object>  
      <ConnectionString>...</ConnectionString>  
   </Source>  
</Synchronize>  
```  
  
## <a name="element-characteristics"></a>Elementmerkmale  
  
|Merkmal|Description|  
|--------------------|-----------------|  
|Datentyp und -länge|InclusionThresholdSetting|  
|Standardwert|InclusionThresholdSetting|  
|Cardinality|1-1: Erforderliches Element, das nur einmal auftritt.|  
  
## <a name="element-relationships"></a>Elementbeziehungen  
  
|Beziehung|Element|  
|------------------|-------------|  
|Übergeordnete Elemente|[Synchronisieren](../xml-elements-commands/synchronize-element-xmla.md)|  
|Untergeordnete Elemente|[ConnectionString](connectionstring-element-xmla.md), [Object](object-element-xmla.md)|  
  
## <a name="remarks"></a>Hinweise  
 Die `Synchronize` Befehl verwendet das `Source` Element, um eine Verbindung mit herstellen und Identifizierung der Datenbank auf einer Instanz von [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] mit der die Zieldatenbank synchronisiert.  
  
## <a name="see-also"></a>Siehe auch  
 [Eigenschaften &#40;XMLA&#41;](xml-elements-properties.md)  
  
  