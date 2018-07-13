---
title: Subscribe-Element (XMLA) | Microsoft-Dokumentation
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
- Subscribe Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- urn:schemas-microsoft-com:xml-analysis#Subscribe
- microsoft.xml.analysis.subscribe
- http://schemas.microsoft.com/analysisservices/2003/engine#Subscribe
helpviewer_keywords:
- Subscribe command
ms.assetid: aad50dd7-44d4-4d83-a973-187f9aed35ec
caps.latest.revision: 14
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 97b473820ee809f5a606e8bb9f30be6e315a2801
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/02/2018
ms.locfileid: "37247260"
---
# <a name="subscribe-element-xmla"></a>Subscribe-Element (XMLA)
  Abonniert eine Ablaufverfolgung und gibt ein Rowset, das die Ablaufverfolgungsereignisse einer [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] Instanz.  
  
## <a name="syntax"></a>Syntax  
  
```xml  
  
<Command>  
   <Subscribe>  
      <Object>...</Object>  
   </Subscribe>  
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
|Untergeordnete Elemente|[Objekt](../xml-elements-properties/object-element-xmla.md)|  
  
## <a name="remarks"></a>Hinweise  
 Die `Subscribe` -Befehl abonniert und wiedergibt ein Rowset einer bestimmten Ablaufverfolgung auf einer [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] Instanz. Wenn ein anderes Objekt als eine Ablaufverfolgung, in angegeben ist der `Object` -Element, ein Fehler auftritt.  
  
 Wenn das `Object`-Element nicht angegeben wird, wird eine Sitzungsablaufverfolgung definiert und auf der [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]-Instanz abonniert. Die Sitzungsablaufverfolgung gibt einen festen Satz von Ablaufverfolgungsereignissen der aktuellen Sitzung zurück.  
  
 Der Rowset-Datenstrom, der von diesem Befehl zurückgegeben wird beendet, wenn die Clientanwendung die Verbindung mit schließt die [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] -Instanz oder, wenn die Sitzung auf dem die `Subscribe` Befehl ausgeführt wird wird beendet.  
  
## <a name="see-also"></a>Siehe auch  
 [Befehle &#40;XMLA&#41;](xml-elements-commands.md)  
  
  
