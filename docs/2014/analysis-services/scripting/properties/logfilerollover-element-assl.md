---
title: LogFileRollover-Element (ASSL) | Microsoft Docs
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
- LogFileRollover Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- LogFileRollover
helpviewer_keywords:
- LogFileRollover element
ms.assetid: 5484e167-b891-431a-bbae-946ea6eb4a3c
caps.latest.revision: 34
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: 4ecaf972c701175d388ab71fa61d94de1c6f2cad
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/19/2018
ms.locfileid: "36048142"
---
# <a name="logfilerollover-element-assl"></a>LogFileRollover-Element (ASSL)
  Gibt an, ob die Protokollierung [Ablaufverfolgung](../objects/trace-element-assl.md) -Ausgabe an eine neue Datei, oder beenden, wenn die maximale Protokolldateigröße, sollte angegeben werden, [LogFileSize](logfilesize-element-assl.md) erreicht ist.  
  
## <a name="syntax"></a>Syntax  
  
```xml  
  
<Trace>  
   ...  
   <LogFileRollover>...</LogFileRollover>  
   ...  
</Trace>  
```  
  
## <a name="element-characteristics"></a>Elementmerkmale  
  
|Merkmal|Description|  
|--------------------|-----------------|  
|Datentyp und -länge|Boolean|  
|Standardwert|False|  
|Cardinality|0-1: Optionales Element, das nur einmal auftreten kann.|  
  
## <a name="element-relationships"></a>Elementbeziehungen  
  
|Beziehung|Element|  
|------------------|-------------|  
|Übergeordnetes Element|[Ablaufverfolgung](../objects/trace-element-assl.md)|  
|Untergeordnete Elemente|InclusionThresholdSetting|  
  
## <a name="remarks"></a>Hinweise  
 Ist der Wert des `LogFileRollover`-Elements auf "True" festgelegt, wird eine neue Datei begonnen, wenn die Größe der Protokolldatei den Wert übersteigt, der im `LogFileSize`-Element des übergeordneten `Trace`-Elements angegeben ist. Anderenfalls wird die Protokollierung beendet.  
  
 Das Element, das das übergeordnete Element des entspricht `LogFileRollover` im Objekt Analysis Management Objects (AMO) Modell ist <xref:Microsoft.AnalysisServices.Trace>.  
  
## <a name="see-also"></a>Siehe auch  
 [Verfolgt Element &#40;ASSL&#41;](../collections/traces-element-assl.md)   
 [Eigenschaften &#40;ASSL&#41;](properties-assl.md)  
  
  