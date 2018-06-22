---
title: Cancel-Element (XMLA) | Microsoft Docs
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
- Cancel Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- microsoft.xml.analysis.cancel
- http://schemas.microsoft.com/analysisservices/2003/engine#Cancel
- urn:schemas-microsoft-com:xml-analysis#Cancel
helpviewer_keywords:
- Cancel command
ms.assetid: de4062c1-7434-44dc-9f01-29fcf78963bd
caps.latest.revision: 15
author: mgblythe
ms.author: mblythe
manager: mblythe
ms.openlocfilehash: cd0fdd50a1dcddb51d167ab76cd5408b631bb3ef
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/19/2018
ms.locfileid: "36150899"
---
# <a name="cancel-element-xmla"></a>Cancel-Element (XMLA)
  Bricht einen derzeit ausgeführten Befehl ab einem [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] Instanz.  
  
## <a name="syntax"></a>Syntax  
  
```xml  
  
<Command>  
   <Cancel>  
      <ConnectionID>...</ConnectionID>  
      <SessionID>...</SessionID>  
      <SPID>...</SPID>  
      <CancelAssociated>...</CancelAssociated>  
   </Cancel>  
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
|Untergeordnete Elemente|[CancelAssociated](../xml-elements-properties/cancelassociated-element-xmla.md), [ConnectionID](../xml-elements-properties/id-element-xmla.md), [SessionID](../xml-elements-properties/sessionid-element-xmla.md), [SPID](../xml-elements-properties/spid-element-xmla.md)|  
  
## <a name="remarks"></a>Hinweise  
 Die `Cancel` -Befehl bricht ab, die derzeit ausgeführten Befehle innerhalb des Kontexts einer Sitzung. Wenn die Clientanwendung keine Sitzung angefordert hat, ist es nicht möglich, einen Befehl abzubrechen.  
  
 Wenn die `Cancel` Befehl wird ausgeführt, während der Ausführung einer `Batch` Befehl, den gesamten `Batch` -Befehl abgebrochen. Wenn der `Batch`-Befehl transaktional war, wird für alle Befehle innerhalb des `Batch`-Befehls ein Rollback ausgeführt. Wenn die `Batch` -Befehl nicht transaktional war, nur für diejenigen Befehle innerhalb der `Batch` Befehls, die zum Zeitpunkt der Ausführung, der `Cancel` Befehl ausgeführt wurde zurückgesetzt. Befehle in eine nicht transaktionale `Batch` -Befehl, der bereits ausgeführt worden wäre nicht zurückgesetzt werden.  
  
 In der Regel die `Cancel` -Befehl verwendet, um auf der gerade aktiven Sitzung ausführende Befehle abzubrechen. In diesem Fall braucht keines der untergeordneten Elemente für den `Cancel`-Befehl angegeben zu werden. Der `Cancel`-Befehl kann außerdem vom Administrator verwendet werden, um Befehle abzubrechen, die nicht auf der derzeit aktiven Sitzung, sondern auf anderen Verbindungen oder Sitzungen ausgeführt werden. Mitglieder einer Rolle, die Administrator-Berechtigungen für eine bestimmte Datenbank besitzt, können Befehle für Verbindungen und Sitzungen abbrechen, die für diese Datenbank gelten; Serveradministratoren hingegen können Befehle für Verbindungen und Sitzungen für eine bestimmte Analysis Services-Instanz abbrechen.  
  
 Zum Abrufen von Informationen über derzeit aktive Verbindungen und Sitzungen einer [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]-Instanz können auf Anforderung die `Discover`-Methode bzw. die DISCOVER_CONNECTIONS- und DISCOVER_SESSIONS-Schemarowsets ausgeführt werden. Mitglieder einer Rolle, die Administrator-Berechtigungen für eine bestimmte Datenbank besitzt, können nur Sitzungen für eine bestimmte Datenbank zurückgeben, indem sie die Datenbank in der SESSION_CURRENT_DATABASE-Einschränkungsspalte des DISCOVER_SESSIONS-Schemarowsets angeben. Weitere Informationen zu den `Discover` -Methode finden Sie unter [Discover-Methode &#40;XMLA&#41;](../xml-elements-methods-discover.md).  
  
## <a name="see-also"></a>Siehe auch  
 [Batch-Element &#40;XMLA&#41;](batch-element-xmla.md)   
 [Befehle &#40;XMLA&#41;](xml-elements-commands.md)  
  
  