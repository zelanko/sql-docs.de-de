---
title: Sperren-Element (XMLA) | Microsoft Docs
ms.date: 05/08/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: xmla
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: a6524c4454eca42a771b2c3c87c2a6513804f720
ms.sourcegitcommit: 808d23a654ef03ea16db1aa23edab496b73e5072
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/04/2018
ms.locfileid: "34575242"
---
# <a name="lock-element-xmla"></a>Lock-Element (XMLA)
[!INCLUDE[ssas-appliesto-sqlas-aas](../../../includes/ssas-appliesto-sqlas-aas.md)]
  Sperrt ein bestimmtes Objekt auf einer Analysis Services-Instanz an.  
  
## <a name="syntax"></a>Syntax  
  
```xml  
  
<Command>  
   <Lock>  
      <ID>...</ID>  
      <Object>...</Object>  
      <Mode>...</Mode>  
   </Lock>  
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
|Übergeordnete Elemente|[Befehl](../../../analysis-services/xmla/xml-elements-properties/command-element-xmla.md)|  
|Untergeordnete Elemente|[ID](../../../analysis-services/xmla/xml-elements-properties/id-element-xmla.md), [Modus](../../../analysis-services/xmla/xml-elements-properties/mode-element-xmla.md), [Objekt](../../../analysis-services/xmla/xml-elements-properties/object-element-xmla.md)|  
  
## <a name="remarks"></a>Hinweise  
 Der **Lock** -Befehl sperrt die gemeinsame oder exklusive Nutzung eines Objekts im Rahmen der derzeit aktiven Transaktion. Nur Datenbankadministratoren oder Serveradministratoren können explizit einen **Lock** -Befehl ausgeben. Eine Sperre in einem Objekt verhindert, dass ein Commit für Transaktionen ausgeführt wird, bevor die Sperre entfernt wurde. [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] unterstützt zwei Arten von Sperren: gemeinsame Sperren und exklusive Sperren. Weitere Informationen zu den von unterstützten Typen von Sperren [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)], finden Sie unter [Mode-Element &#40;XMLA&#41;](../../../analysis-services/xmla/xml-elements-properties/mode-element-xmla.md).  
  
 [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] ermöglicht nur die Sperrung von Datenbanken. Die **Objekt** Element muss einen Objektverweis auf enthalten eine [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] Datenbank. Wenn das **Object** -Element nicht angegeben ist oder wenn das **Object** -Element auf ein Objekt verweist, bei dem es sich nicht um eine Datenbank handelt, tritt ein Fehler auf.  
  
 Andere Befehle geben implizit eine **Sperre** Befehl eine [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] Datenbank. Jeder Vorgang, der Daten oder Metadaten aus einer Datenbank einliest (z. B. jede **Discover** -Methode oder eine **Execute** -Methode, die einen **Statement** -Befehl ausführt), gibt implizit eine gemeinsame Sperre der Datenbank aus. Jede Transaktion, die Änderungen an Daten oder Metadaten zu einem Objekt auf ein Commit ausgeführt wird ein [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] Datenbank, z. B. ein **Execute** externen ausgeführte Methode ein **Alter** Befehl, gibt implizit eine exklusive Sperre für die die Datenbank.  
  
 Alle Sperren werden im Kontext der aktuellen Transaktion abgehalten. Wenn die aktuelle Transaktion ausgeführt oder für diese ein Rollback durchgeführt wird, werden alle Sperren, die innerhalb der Transaktion definiert sind, automatisch aufgehoben.  
  
## <a name="see-also"></a>Siehe auch
 [Unlock-Element &#40;XMLA&#41;](../../../analysis-services/xmla/xml-elements-commands/unlock-element-xmla.md)   
 [Befehle &#40;XMLA&#41;](../../../analysis-services/xmla/xml-elements-commands/xml-elements-commands.md)  
  
  
