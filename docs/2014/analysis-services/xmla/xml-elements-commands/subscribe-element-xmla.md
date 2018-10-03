---
title: Subscribe-Element (XMLA) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
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
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: cf88b3e4e2fd990ad786b8e505c908f96f53ce6e
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/02/2018
ms.locfileid: "48079340"
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
|Datentyp und -länge|None|  
|Standardwert|None|  
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
  
  
