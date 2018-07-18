---
title: NotifyTableChange-Element (XMLA) | Microsoft-Dokumentation
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
- NotifyTableChange Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- urn:schemas-microsoft-com:xml-analysis#NotifyTableChange
- http://schemas.microsoft.com/analysisservices/2003/engine#NotifyTableChange
- microsoft.xml.analysis.notifytablechange
helpviewer_keywords:
- NotifyTableChange command
ms.assetid: b76898eb-20d3-48c8-9eb8-1fd5df638bcc
caps.latest.revision: 13
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 612738591115a2e7af964ba4ee5d9950587e45bc
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/02/2018
ms.locfileid: "37203900"
---
# <a name="notifytablechange-element-xmla"></a>NotifyTableChange-Element (XMLA)
  Benachrichtigt eine Instanz von [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] , die geändert wurden, Tabellen in einer bestimmten Datenquelle.  
  
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
  
|Merkmal|Description|  
|--------------------|-----------------|  
|Datentyp und -länge|InclusionThresholdSetting|  
|Standardwert|InclusionThresholdSetting|  
|Cardinality|0-n: Optionales Element, das mehr als einmal auftreten kann.|  
  
## <a name="element-relationships"></a>Elementbeziehungen  
  
|Beziehung|Element|  
|------------------|-------------|  
|Übergeordnete Elemente|[Befehl](../xml-elements-properties/command-element-xmla.md)|  
|Untergeordnete Elemente|[Objekt](../xml-elements-properties/object-element-xmla.md), [TableNotifications](../xml-elements-properties/tablenotifications-element-xmla.md)|  
  
## <a name="remarks"></a>Hinweise  
 Die `NotifyTableChange` -Befehl ermöglicht es eine Clientanwendung explizit darüber zu benachrichtigen einer [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] Instanz fest, dass eine oder mehrere Tabelle(n) in einer Datenquelle geändert wurden. Beim proaktiven Caching zeigt diese Benachrichtigung an, dass relationale OLAP-Objekte (ROLAP), die auf diesen Tabellen basieren, überprüft und aktualisiert werden sollten.  
  
 Diese Benachrichtigungsmethode wird am besten für ROLAP-Objekte verwendet, die auf Sichten oder benannten Abfragen basieren, die in einer Datenquellensicht definiert sind, deren Änderungen schwer zu erkennen sind.  
  
 Das `Object`-Element muss auf eine Datenquelle in der [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]-Datenbank verweisen. Wenn die `Object` Element bezieht sich auf ein anderes Objekt als eine Datenquelle, ein Fehler auftritt.  
  
 Weitere Informationen zum proaktiven Zwischenspeichern finden Sie unter [Proaktives Zwischenspeichern &#40;Partitionen&#41;](../../multidimensional-models-olap-logical-cube-objects/partitions-proactive-caching.md).  
  
## <a name="see-also"></a>Siehe auch  
 [Befehle &#40;XMLA&#41;](xml-elements-commands.md)  
  
  
