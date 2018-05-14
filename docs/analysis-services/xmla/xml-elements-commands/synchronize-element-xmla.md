---
title: Synchronize-Element (XMLA) | Microsoft Docs
ms.date: 05/08/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: xmla
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 5c3a4d20c7799281f40fa6ae13e89010cebe1ec6
ms.sourcegitcommit: c12a7416d1996a3bcce3ebf4a3c9abe61b02fb9e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/10/2018
---
# <a name="synchronize-element-xmla"></a>Synchronize-Element (XMLA)
[!INCLUDE[ssas-appliesto-sqlas-aas](../../../includes/ssas-appliesto-sqlas-aas.md)]
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
  
|Merkmal|Beschreibung|  
|--------------------|-----------------|  
|Datentyp und -länge|Keine|  
|Standardwert|Keine|  
|Kardinalität|0-n: Optionales Element, das mehr als einmal auftreten kann.|  
  
## <a name="element-relationships"></a>Elementbeziehungen  
  
|Beziehung|Element|  
|------------------|-------------|  
|Übergeordnete Elemente|[Befehl](../../../analysis-services/xmla/xml-elements-properties/command-element-xmla.md)|  
|Untergeordnete Elemente|[ApplyCompression](../../../analysis-services/xmla/xml-elements-properties/applycompression-element-xmla.md), [Speicherorte](../../../analysis-services/xmla/xml-elements-properties/locations-element-xmla.md), [Quelle](../../../analysis-services/xmla/xml-elements-properties/source-element-synchronize-xmla.md), [SynchronizeSecurity](../../../analysis-services/xmla/xml-elements-properties/synchronizesecurity-element-xmla.md)|  
  
## <a name="remarks"></a>Hinweise  
 Der **Synchronize** -Befehl synchronisiert die Zieldatenbank mit einer Quellinstanz und -datenbank, die im **Source** -Element festgelegt sind. Optional synchronisiert der Befehl **Synchronize** auf der Quelldatenbank definierte Remote-Partitionen.  
  
 Je nach dem Speichermodus der in der Sicherungsdatei gespeicherten Objekte werden mit dem **Synchronize** -Befehl die in der folgenden Tabelle aufgelisteten Informationen synchronisiert.  
  
|Speichermodus|Informationen|  
|------------------|-----------------|  
|Mehrdimensionale OLAP (MOLAP)|Quelldaten, Aggregationen und Metadaten|  
|Hybride OLAP (HOLAP)|Aggregationen und Metadaten|  
|Relationale OLAP (ROLAP)|Metadaten|  
  
 Bei der Ausführung des **Synchronize** -Befehls wird eine Schreibberechtigungssperre auf die Quelldatenbank und eine Schreibberechtigungssperre auf die Zieldatenbank angewendet. Beide Sperren werden nach Abschluss des **Synchronize** -Befehls wieder aufgehoben.  
  
 Weitere Informationen zum Synchronisieren von Datenbanken finden Sie unter [sichern, wiederherstellen und Synchronisieren von Datenbanken &#40;XMLA&#41;](../../../analysis-services/multidimensional-models-scripting-language-assl-xmla/backing-up-restoring-and-synchronizing-databases-xmla.md).  
  
## <a name="see-also"></a>Siehe auch  
 [Backup-Element & #40; XMLA & #41;](../../../analysis-services/xmla/xml-elements-commands/backup-element-xmla.md)   
 [Batch-Element & #40; XMLA & #41;](../../../analysis-services/xmla/xml-elements-commands/batch-element-xmla.md)   
 [Parallel-Element & #40; XMLA & #41;](../../../analysis-services/xmla/xml-elements-properties/parallel-element-xmla.md)   
 [Restore-Element & #40; XMLA & #41;](../../../analysis-services/xmla/xml-elements-commands/restore-element-xmla.md)   
 [Befehle & #40; XMLA & #41;](../../../analysis-services/xmla/xml-elements-commands/xml-elements-commands.md)  
  
  
