---
title: NotifyTableChange-Element (XMLA) | Microsoft Docs
ms.date: 05/08/2018
ms.prod: sql
ms.technology: analysis-services
ms.component: xmla
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 125cea75f5c892cd30e3f346c0b755ab8de55ae5
ms.sourcegitcommit: 38f8824abb6760a9dc6953f10a6c91f97fa48432
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/10/2018
---
# <a name="notifytablechange-element-xmla"></a>NotifyTableChange-Element (XMLA)
[!INCLUDE[ssas-appliesto-sqlas-aas](../../../includes/ssas-appliesto-sqlas-aas.md)]
  Benachrichtigt eine Instanz von [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] , dass Tabellen in einer bestimmten Datenquelle geändert wurden.  
  
## <a name="syntax"></a>Syntax  
  
```xml  
  
<Command>  
   <NotifyTableChange>  
      <Object>...</Object>  
      <TableNotifications>...</TableNotifications>  
   </NotifyTableChange>  
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
|Untergeordnete Elemente|[Object](../../../analysis-services/xmla/xml-elements-properties/object-element-xmla.md), [TableNotifications](../../../analysis-services/xmla/xml-elements-properties/tablenotifications-element-xmla.md)|  
  
## <a name="remarks"></a>Hinweise  
 Die **NotifyTableChange** Befehl ermöglicht einer Clientanwendung explizit benachrichtigen ein [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] Instanz fest, dass eine oder mehrere Tabelle(n) in einer Datenquelle geändert wurden. Beim proaktiven Caching zeigt diese Benachrichtigung an, dass relationale OLAP-Objekte (ROLAP), die auf diesen Tabellen basieren, überprüft und aktualisiert werden sollten.  
  
 Diese Benachrichtigungsmethode wird am besten für ROLAP-Objekte verwendet, die auf Sichten oder benannten Abfragen basieren, die in einer Datenquellensicht definiert sind, deren Änderungen schwer zu erkennen sind.  
  
 Die **Objekt** -Element muss auf eine Datenquelle in verweisen die [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] Datenbank. Wenn das **Object** -Element auf ein Objekt verweist, bei dem es sich nicht um eine Datenquelle handelt, tritt ein Fehler auf.  
  
 Weitere Informationen zum proaktiven Zwischenspeichern finden Sie unter [Proaktives Zwischenspeichern &#40;Partitionen&#41;](../../../analysis-services/multidimensional-models-olap-logical-cube-objects/partitions-proactive-caching.md).  
  
## <a name="see-also"></a>Siehe auch  
 [Befehle & #40; XMLA & #41;](../../../analysis-services/xmla/xml-elements-commands/xml-elements-commands.md)  
  
  
