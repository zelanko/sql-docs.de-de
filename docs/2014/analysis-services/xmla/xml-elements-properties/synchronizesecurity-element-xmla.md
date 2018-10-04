---
title: SynchronizeSecurity-Element (XMLA) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.topic: reference
api_name:
- SynchronizeSecurity Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- microsoft.xml.analysis.synchronizesecurity
- http://schemas.microsoft.com/analysisservices/2003/engine#SynchronizeSecurity
- urn:schemas-microsoft-com:xml-analysis#SynchronizeSecurity
helpviewer_keywords:
- SynchronizeSecurity element
ms.assetid: d37dbb95-f4a4-44ac-8eb9-f661d5bb5018
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 95e43831854720e8a2525edae06165334443dad3
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/02/2018
ms.locfileid: "48224542"
---
# <a name="synchronizesecurity-element-xmla"></a>SynchronizeSecurity-Element (XMLA)
  Gibt an, wie sicherheitsdefinitionen wie Rollen und Berechtigungen während der Synchronisierung ein [synchronisierende](../xml-elements-commands/synchronize-element-xmla.md) Befehl.  
  
## <a name="syntax"></a>Syntax  
  
```xml  
  
<Synchronize>  
   ...  
   <SynchronizeSecurity>...</SynchronizeSecurity>  
   ...  
</Synchronize>  
```  
  
## <a name="element-characteristics"></a>Elementmerkmale  
  
|Merkmal|Description|  
|--------------------|-----------------|  
|Datentyp und -länge|Zeichenfolge (Enumeration)|  
|Standardwert|*skipMembership*|  
|Cardinality|0-1: Optionales Element, das nur einmal auftreten kann.|  
  
## <a name="element-relationships"></a>Elementbeziehungen  
  
|Beziehung|Element|  
|------------------|-------------|  
|Übergeordnete Elemente|[Synchronisieren](../xml-elements-commands/synchronize-element-xmla.md)|  
|Untergeordnete Elemente|None|  
  
## <a name="remarks"></a>Hinweise  
 Die `Security` -Element bestimmt, ob die sicherheitsdefinitionen wie Rollen und Berechtigungen, definiert ein [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] Datenbank synchronisiert werden, während eine `Synchronize` Befehl. Dieses Element bestimmt außerdem, ob Windows-Benutzerkonten und Gruppen, die als Mitglieder der Sicherheitsdefinitionen definiert sind, als Teil des `Synchronize`-Befehls einbezogen werden.  
  
 Der Wert dieses Elements ist auf eine der in der folgenden Tabelle aufgelisteten Zeichenfolgen beschränkt.  
  
|value|Description|  
|-----------|-----------------|  
|*skipMembership*|Einbeziehen von Sicherheitsdefinitionen und Ausschließen von Informationen zur Mitgliedschaft während eines `Synchronize`-Befehls.|  
|*CopyAll*|Einbeziehen von Sicherheitsdefinitionen und Informationen zur Mitgliedschaft während eines `Synchronize`-Befehls.|  
|*IgnoreSecurity*|Ausschließen von sicherheitsdefinitionen während einer `Synchronize` Befehl.|  
  
## <a name="see-also"></a>Siehe auch  
 [Sicherheitselement &#40;XMLA&#41;](security-element-xmla.md)   
 [Eigenschaften &#40;XMLA&#41;](xml-elements-properties.md)  
  
  
