---
title: Synchronize-Element (XMLA) | Microsoft Docs
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
caps.latest.revision: 15
author: mgblythe
ms.author: mblythe
manager: mblythe
ms.openlocfilehash: 367d237cab7ea63b85e000433742d866466b3f62
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/19/2018
ms.locfileid: "36159040"
---
# <a name="synchronize-element-xmla"></a>Synchronize-Element (XMLA)
  Synchronisiert eine [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] Datenbank mit einer anderen vorhandenen Datenbank.  
  
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
|Datentyp und -länge|InclusionThresholdSetting|  
|Standardwert|InclusionThresholdSetting|  
|Cardinality|0-n: Optionales Element, das mehr als einmal auftreten kann.|  
  
## <a name="element-relationships"></a>Elementbeziehungen  
  
|Beziehung|Element|  
|------------------|-------------|  
|Übergeordnete Elemente|[Befehl](../xml-elements-properties/command-element-xmla.md)|  
|Untergeordnete Elemente|[ApplyCompression](../xml-elements-properties/applycompression-element-xmla.md), [Speicherorte](../xml-elements-properties/locations-element-xmla.md), [Quelle](../xml-elements-properties/source-element-synchronize-xmla.md), [SynchronizeSecurity](../xml-elements-properties/security-element-xmla.md)|  
  
## <a name="remarks"></a>Hinweise  
 Die `Synchronize` -Befehl synchronisiert die Zieldatenbank mit einer Quellinstanz und Datenbank angegeben wird, dem `Source` Element. Optional synchronisiert der Befehl `Synchronize` auf der Quelldatenbank definierte Remote-Partitionen.  
  
 Je nach dem Speichermodus der in der Sicherungsdatei gespeicherten Objekte werden mit dem `Synchronize`-Befehl die in der folgenden Tabelle aufgelisteten Informationen synchronisiert.  
  
|Speichermodus|Information|  
|------------------|-----------------|  
|Mehrdimensionale OLAP (MOLAP)|Quelldaten, Aggregationen und Metadaten|  
|Hybride OLAP (HOLAP)|Aggregationen und Metadaten|  
|Relationale OLAP (ROLAP)|Metadaten|  
  
 Bei der Ausführung des `Synchronize`-Befehls wird eine Schreibberechtigungssperre auf die Quelldatenbank und eine Schreibberechtigungssperre auf die Zieldatenbank angewendet. Beide Sperren werden aufgehoben, nachdem die `Synchronize` -Befehls wieder aufgehoben.  
  
 Weitere Informationen zum Synchronisieren von Datenbanken finden Sie unter [sichern, wiederherstellen und Synchronisieren von Datenbanken &#40;XMLA&#41;](../../multidimensional-models-scripting-language-assl-xmla/backing-up-restoring-and-synchronizing-databases-xmla.md).  
  
## <a name="see-also"></a>Siehe auch  
 [Sichern des Elements &#40;XMLA&#41;](backup-element-xmla.md)   
 [Batch-Element &#40;XMLA&#41;](batch-element-xmla.md)   
 [Parallele Element &#40;XMLA&#41;](../xml-elements-properties/parallel-element-xmla.md)   
 [Restore-Element &#40;XMLA&#41;](restore-element-xmla.md)   
 [Befehle &#40;XMLA&#41;](xml-elements-commands.md)  
  
  