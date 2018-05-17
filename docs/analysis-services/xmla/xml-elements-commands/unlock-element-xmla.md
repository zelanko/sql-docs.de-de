---
title: Unlock-Element (XMLA) | Microsoft Docs
ms.date: 05/08/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: xmla
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfilee"
ms.openlocfilehash: eb9cced037ab7fcf7072e6db56cb645333a02311
ms.sourcegitcommit: c12a7416d1996a3bcce3ebf4a3c9abe61b02fb9e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/10/2018
---
# <a name="unlock-element-xmla"></a>Unlock-Element (XMLA)
[!INCLUDE[ssas-appliesto-sqlas-aas](../../../includes/ssas-appliesto-sqlas-aas.md)]
  Entsperrt eine bestimmte Sperre auf einer [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] Instanz.  
  
## <a name="syntax"></a>Syntax  
  
```xml  
  
<Command>  
   <Unlock>  
      <ID>...</ID>  
   </Unlock>  
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
|Untergeordnete Elemente|[ID](../../../analysis-services/xmla/xml-elements-properties/id-element-xmla.md)|  
  
## <a name="remarks"></a>Hinweise  
 Der Befehl **Unlock** entfernt eine innerhalb des Kontexts der gerade aktiven Transaktion begründete Sperre. Nur Datenbankadministratoren oder Serveradministratoren können explizit einen **Unlock** -Befehl ausgeben.  
  
 Alle Sperren werden im Kontext der aktuellen Transaktion abgehalten. Wenn die aktuelle Transaktion ausgeführt oder für diese ein Rollback durchgeführt wird, werden alle Sperren, die innerhalb der Transaktion definiert sind, automatisch aufgehoben.  
  
## <a name="see-also"></a>Siehe auch  
 [Element sperren &#40;XMLA&#41;](../../../analysis-services/xmla/xml-elements-commands/lock-element-xmla.md)   
 [Befehle & #40; XMLA & #41;](../../../analysis-services/xmla/xml-elements-commands/xml-elements-commands.md)  
  
  
