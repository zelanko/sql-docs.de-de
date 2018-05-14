---
title: Cancel-Element (XMLA) | Microsoft Docs
ms.date: 05/08/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: xmla
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: e8c4f015d5a606d67cb4c6b5f0519875db58b416
ms.sourcegitcommit: c12a7416d1996a3bcce3ebf4a3c9abe61b02fb9e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/10/2018
---
# <a name="cancel-element-xmla"></a>Cancel-Element (XMLA)
[!INCLUDE[ssas-appliesto-sqlas-aas](../../../includes/ssas-appliesto-sqlas-aas.md)]
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
  
|Merkmal|Beschreibung|  
|--------------------|-----------------|  
|Datentyp und -länge|Keine|  
|Standardwert|Keine|  
|Kardinalität|0-n: Optionales Element, das mehr als einmal auftreten kann.|  
  
## <a name="element-relationships"></a>Elementbeziehungen  
  
|Beziehung|Element|  
|------------------|-------------|  
|Übergeordnete Elemente|[Befehl](../../../analysis-services/xmla/xml-elements-properties/command-element-xmla.md)|  
|Untergeordnete Elemente|[CancelAssociated](../../../analysis-services/xmla/xml-elements-properties/cancelassociated-element-xmla.md), [ConnectionID](../../../analysis-services/xmla/xml-elements-properties/connectionid-element-xmla.md), [SessionID](../../../analysis-services/xmla/xml-elements-properties/sessionid-element-xmla.md), [SPID](../../../analysis-services/xmla/xml-elements-properties/spid-element-xmla.md)|  
  
## <a name="remarks"></a>Hinweise  
 Der **Cancel** -Befehl bricht die Befehle ab, die derzeit im Rahmen einer Sitzung ausgeführt werden. Wenn die Clientanwendung keine Sitzung angefordert hat, ist es nicht möglich, einen Befehl abzubrechen.  
  
 Wenn der **Cancel** -Befehl während der Ausführung eines **Batch** -Befehls ausgeführt wird, wird der komplette **Batch** -Befehl abgebrochen. Wenn der **Batch** -Befehl transaktional war, wird für alle Befehle innerhalb des **Batch** -Befehls ein Rollback ausgeführt. Wenn der **Batch** -Befehl nicht transaktional war, wird nur für diejenigen Befehle innerhalb des **Batch** -Befehls, die zur Zeit der Ausführung des **Cancel** -Befehls ausgeführt wurden, ein Rollback durchgeführt. Für Befehle in einem nicht transaktionalen **Batch** -Befehl, der bereits ausgeführt worden ist, würde kein Rollback ausgeführt werden.  
  
 In der Regel wird der **Cancel** -Befehl verwendet, um auf der gerade aktiven Sitzung ausführende Befehle abzubrechen. In diesem Fall braucht keines der untergeordneten Elemente für den **Cancel** -Befehl angegeben zu werden. Der **Cancel** -Befehl kann außerdem vom Administrator verwendet werden, um Befehle abzubrechen, die nicht auf der derzeit aktiven Sitzung, sondern auf anderen Verbindungen oder Sitzungen ausgeführt werden. Mitglieder einer Rolle, die Administrator-Berechtigungen für eine bestimmte Datenbank besitzt, können Befehle für Verbindungen und Sitzungen abbrechen, die für diese Datenbank gelten; Serveradministratoren hingegen können Befehle für Verbindungen und Sitzungen für eine bestimmte Analysis Services-Instanz abbrechen.  
  
 Zum Abrufen von Informationen zu aktuellen Verbindungen und Sitzungen für eine [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] -Instanz, die **Discover** -Methode kann ausgeführt werden, bzw. die DISCOVER_CONNECTIONS- und DISCOVER_SESSIONS-Schemarowsets an. Mitglieder einer Rolle, die Administrator-Berechtigungen für eine bestimmte Datenbank besitzt, können nur Sitzungen für eine bestimmte Datenbank zurückgeben, indem sie die Datenbank in der SESSION_CURRENT_DATABASE-Einschränkungsspalte des DISCOVER_SESSIONS-Schemarowsets angeben. Weitere Informationen zu den **Discover** -Methode finden Sie unter [Discover-Methode &#40;XMLA&#41;](../../../analysis-services/xmla/xml-elements-methods-discover.md).  
  
## <a name="see-also"></a>Siehe auch  
 [Batch-Element & #40; XMLA & #41;](../../../analysis-services/xmla/xml-elements-commands/batch-element-xmla.md)   
 [Befehle & #40; XMLA & #41;](../../../analysis-services/xmla/xml-elements-commands/xml-elements-commands.md)  
  
  
