---
title: Statement-Element (XMLA) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.topic: reference
api_name:
- Statement Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- http://schemas.microsoft.com/analysisservices/2003/engine#Statement
- microsoft.xml.analysis.statement
- urn:schemas-microsoft-com:xml-analysis#Statement
helpviewer_keywords:
- Statement command
ms.assetid: bfedc03c-d476-4d55-b5fd-36169f01351a
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 96b37de3307a044b046c67bb4ab6fe341ad5e480
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/02/2018
ms.locfileid: "48056460"
---
# <a name="statement-element-xmla"></a>Statement-Element (XMLA)
  Enthält eine Abfrage oder Anweisung gesendet werden mithilfe der `Execute` Methode mit einer Instanz von [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)].  
  
## <a name="syntax"></a>Syntax  
  
```xml  
  
<Command>  
   <Statement>...</Statement>  
</Command>  
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
|Übergeordnete Elemente|[Befehl](../xml-elements-properties/command-element-xmla.md)|  
|Untergeordnete Elemente|None|  
  
## <a name="remarks"></a>Hinweise  
 Die `Statement` Befehl führt eine Abfrage oder Anweisung auf die [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] Instanz. [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] unterstützt die folgenden Sprachen:  
  
-   Multidimensional Expressions (MDX)  
  
-   Data Mining-Erweiterungen (MDX)  
  
-   Eine Teilmenge von SQL (Structured Query Language)  
  
## <a name="see-also"></a>Siehe auch  
 [Befehle &#40;XMLA&#41;](xml-elements-commands.md)  
  
  
