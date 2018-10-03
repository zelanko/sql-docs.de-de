---
title: Capability-Element (XMLA) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.topic: reference
api_name:
- Capability Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- urn:schemas-microsoft-com:xml-analysis#Capability
- http://schemas.microsoft.com/analysisservices/2003/engine#Capability
- microsoft.xml.analysis.capability
helpviewer_keywords:
- Capability element
ms.assetid: 544a733e-77fc-48a0-8f92-9cd1fdbcf824
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 7c6fd189a44ec34283e87cd220f2c582f982ffa9
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/02/2018
ms.locfileid: "48105340"
---
# <a name="capability-element-xmla"></a>Capability-Element (XMLA)
  Gibt die Unterstützung für eine Protokollfunktion im übergeordneten [ProtocolCapabilities](../xml-elements-headers/protocolcapabilities-element-xmla.md) Header-Element.  
  
## <a name="syntax"></a>Syntax  
  
```xml  
  
<ProtocolCapabilities>  
   ...  
   <Capability>...</Capability>  
   ...  
</ProtocolCapabilities>  
```  
  
## <a name="element-characteristics"></a>Elementmerkmale  
  
|Merkmal|Description|  
|--------------------|-----------------|  
|Datentyp und -länge|Zeichenfolge|  
|Standardwert|None|  
|Cardinality|0-n: Optionales Element, das mehr als einmal auftreten kann.|  
  
## <a name="element-relationships"></a>Elementbeziehungen  
  
|Beziehung|Element|  
|------------------|-------------|  
|Übergeordnete Elemente|[ProtocolCapabilities](../xml-elements-headers/protocolcapabilities-element-xmla.md)|  
|Untergeordnete Elemente|None|  
  
## <a name="remarks"></a>Hinweise  
 Die `Capability` Element gibt an, dass eine bestimmte Funktion, wie z. B. Binär- oder Komprimierungsfunktion, entweder von der Anwendung unterstützt wird, die `ProtocolCapabilities` -Headerelement im SOAP-Header der SOAP-Anforderung oder von der Instanz von [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] , enthalten die `ProtocolCapabilities` -Headerelement im SOAP-Header der SOAP-Antwort. Der Wert des `Capability`-Elements ist der Name der Funktion, die unterstützt werden soll.  
  
 [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] unterstützt die in der folgenden Tabelle aufgelisteten Funktionen.  
  
|Name der Funktion|Description|  
|---------------------|-----------------|  
|sx|Binäre XML-Unterstützung|  
|xpress|Komprimierungsunterstützung|  
  
## <a name="see-also"></a>Siehe auch  
 [Verwalten von Verbindungen und Sitzungen &#40;XMLA&#41;](../../multidimensional-models-scripting-language-assl-xmla/managing-connections-and-sessions-xmla.md)   
 [Eigenschaften &#40;XMLA&#41;](xml-elements-properties.md)  
  
  
