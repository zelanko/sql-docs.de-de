---
title: Synchronize-Element (XMLA) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.topic: reference
api_name:
- Synchronize Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- microsoft.xml.analysis.synchronize
- urn:schemas-microsoft-com:xml-analysis#Synchronize
- http://schemas.microsoft.com/analysisservices/2003/engine#Synchronize
helpviewer_keywords:
- Synchronize command
ms.assetid: 9401323c-feff-409a-a9da-94aee47e0563
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 13bdb64dbc3ba0b034af3a54ae10a50c403555a7
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/02/2018
ms.locfileid: "48225820"
---
# <a name="synchronize-element-xmla"></a>Synchronize-Element (XMLA)
  Synchronisiert eine [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] -Datenbank mit einer anderen vorhandenen Datenbank.  
  
## <a name="syntax"></a>Syntax  
  
```xml  
  
<Command>  
   <Synchronize>  
      <Source>...</Source>  
      <SynchronizeSecurity>...</SynchronizeSecurity>  
      <ApplyCompression>...</ApplyCompression>  
      <Locations>...</Locations>  
   </Synchronize>  
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
|Untergeordnete Elemente|[ApplyCompression](../xml-elements-properties/applycompression-element-xmla.md), [Speicherorte](../xml-elements-properties/locations-element-xmla.md), [Quelle](../xml-elements-properties/source-element-synchronize-xmla.md), [SynchronizeSecurity](../xml-elements-properties/security-element-xmla.md)|  
  
## <a name="remarks"></a>Hinweise  
 Die `Synchronize` -Befehl synchronisiert die Zieldatenbank mit einer Quellinstanz und die Datenbank angegeben wird, der `Source` Element. Optional synchronisiert der Befehl `Synchronize` auf der Quelldatenbank definierte Remote-Partitionen.  
  
 Je nach dem Speichermodus der in der Sicherungsdatei gespeicherten Objekte werden mit dem `Synchronize`-Befehl die in der folgenden Tabelle aufgelisteten Informationen synchronisiert.  
  
|Speichermodus|Information|  
|------------------|-----------------|  
|Mehrdimensionale OLAP (MOLAP)|Quelldaten, Aggregationen und Metadaten|  
|Hybride OLAP (HOLAP)|Aggregationen und Metadaten|  
|Relationale OLAP (ROLAP)|Metadaten|  
  
 Bei der Ausführung des `Synchronize`-Befehls wird eine Schreibberechtigungssperre auf die Quelldatenbank und eine Schreibberechtigungssperre auf die Zieldatenbank angewendet. Beide Sperren werden aufgehoben, nachdem die `Synchronize` -Befehl ausgeführt wurde.  
  
 Weitere Informationen zur Synchronisierung von Datenbanken finden Sie unter [sichern, wiederherstellen und Synchronisieren von Datenbanken &#40;XMLA&#41;](../../multidimensional-models-scripting-language-assl-xmla/backing-up-restoring-and-synchronizing-databases-xmla.md).  
  
## <a name="see-also"></a>Siehe auch  
 [Sichern des Elements &#40;XMLA&#41;](backup-element-xmla.md)   
 [Batch-Element &#40;XMLA&#41;](batch-element-xmla.md)   
 [Parallele Element &#40;XMLA&#41;](../xml-elements-properties/parallel-element-xmla.md)   
 [Restore-Element &#40;XMLA&#41;](restore-element-xmla.md)   
 [Befehle &#40;XMLA&#41;](xml-elements-commands.md)  
  
  
