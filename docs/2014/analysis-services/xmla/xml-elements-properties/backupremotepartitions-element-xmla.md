---
title: BackupRemotePartitions-Element (XMLA) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.topic: reference
api_name:
- BackupRemotePartitions Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- microsoft.xml.analysis.backupremotepartitions
- http://schemas.microsoft.com/analysisservices/2003/engine#BackupRemotePartitions
- urn:schemas-microsoft-com:xml-analysis#BackupRemotePartitions
helpviewer_keywords:
- BackupRemotePartitions element
ms.assetid: bd68bcf9-b324-4fa8-b6e5-1f5531f9992c
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 3e18d01ec48264d735a111bc002ca92b08c7b374
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/02/2018
ms.locfileid: "48108183"
---
# <a name="backupremotepartitions-element-xmla"></a>BackupRemotePartitions-Element (XMLA)
  Bestimmt, ob das übergeordnete Element [Sicherung](../xml-elements-commands/backup-element-xmla.md) -Befehl die dem Objekt zugeordneten Remotepartitionen sichert.  
  
## <a name="syntax"></a>Syntax  
  
```xml  
  
<Backup>  
   ...  
   <BackupRemotePartitions>...</BackupRemotePartitions>  
   ...  
</Backup>  
```  
  
## <a name="element-characteristics"></a>Elementmerkmale  
  
|Merkmal|Description|  
|--------------------|-----------------|  
|Datentyp und -länge|Boolean|  
|Standardwert|False|  
|Cardinality|0-1: Optionales Element, das nur einmal auftreten kann.|  
  
## <a name="element-relationships"></a>Elementbeziehungen  
  
|Beziehung|Element|  
|------------------|-------------|  
|Übergeordnete Elemente|[Sicherung](../xml-elements-commands/backup-element-xmla.md)|  
|Untergeordnete Elemente|None|  
  
## <a name="remarks"></a>Hinweise  
 Wenn `BackupRemotePartitions` nastaven NA hodnotu `True`, `Locations` Element, das eine oder mehrere enthält `Location` Elemente enthalten sein müssen, der `Backup` Befehl oder ein Fehler aufgetreten. Weitere Informationen zum Sichern und Wiederherstellen von Remotepartitionen finden Sie unter [sichern, wiederherstellen und Synchronisieren von Datenbanken &#40;XMLA&#41;](../../multidimensional-models-scripting-language-assl-xmla/backing-up-restoring-and-synchronizing-databases-xmla.md).  
  
## <a name="see-also"></a>Siehe auch  
 [Locations-Element &#40;XMLA&#41;](locations-element-xmla.md)   
 [Location-Element &#40;XMLA&#41;](location-element-xmla.md)   
 [Eigenschaften &#40;XMLA&#41;](xml-elements-properties.md)  
  
  
