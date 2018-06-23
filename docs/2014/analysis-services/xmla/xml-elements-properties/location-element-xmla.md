---
title: Location-Element (XMLA) | Microsoft Docs
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
- Location Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- microsoft.xml.analysis.location
- urn:schemas-microsoft-com:xml-analysis#Location
- http://schemas.microsoft.com/analysisservices/2003/engine#Location
helpviewer_keywords:
- Location element
ms.assetid: cea5e776-f435-425a-9bce-812d727a2b71
caps.latest.revision: 12
author: mgblythe
ms.author: mblythe
manager: mblythe
ms.openlocfilehash: 51b0838b9843658b4081f9464c63274631ed74be
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/19/2018
ms.locfileid: "36160511"
---
# <a name="location-element-xmla"></a>Location-Element (XMLA)
  Enthält Informationen über einen Remoteserver für den übergeordneten [Sicherung](../xml-elements-commands/backup-element-xmla.md), [wiederherstellen](../xml-elements-commands/restore-element-xmla.md), oder [Synchronize](../xml-elements-commands/synchronize-element-xmla.md) Befehl.  
  
## <a name="syntax"></a>Syntax  
  
```xml  
  
<Backup> <!-- or one of the elements listed below in the Element Relationships table -->  
   ...  
   <Location>  
```  
  
```  
  
<File>...</File> <!-- for Backup and Restore only -->  
<DataSourceID>...</DataSourceID>  
<DataSourceType>...</DataSourceType> <!-- for Restore and Synchronize only -->  
<ConnectionString>...</ConnectionString> <!-- for Restore and Synchronize only -->  
<Folders>...</Folders> <!-- for Restore and Synchronize only -->  
```  
  
```  
  
   </Location>  
   ...  
</Backup>  
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
|Übergeordnete Elemente|[Sicherung](../xml-elements-commands/backup-element-xmla.md), [wiederherstellen](../xml-elements-commands/restore-element-xmla.md), [synchronisieren](../xml-elements-commands/synchronize-element-xmla.md)|  
  
## <a name="child-elements"></a>Untergeordnete Elemente  
  
|Vorgänger oder übergeordnetes Element|Untergeordnetes Element|  
|------------------------|-------------------|  
|[Sicherung](id-element-xmla.md), [Datei](file-element-xmla.md)|  
|[Wiederherstellen](connectionstring-element-xmla.md), [DataSourceID](datasourceid-element-xmla.md), [DataSourceType](type-element-xmla.md), [Datei](file-element-xmla.md), [Ordner](folders-element-xmla.md)|  
|[Synchronisieren](../xml-elements-commands/synchronize-element-xmla.md)|["ConnectionString"](connectionstring-element-xmla.md), [DataSourceID](datasourceid-element-xmla.md), [DataSourceType](type-element-xmla.md), [Ordner](folders-element-xmla.md)|  
  
## <a name="remarks"></a>Hinweise  
 Für `Backup` Befehle, die `Location` Element enthält Informationen zum Erstellen einer remotesicherungsdatei für eine Remoteinstanz von [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)].  
  
 Bei `Restore`-Befehlen bietet das `Location`-Element Informationen über die Identifizierung und Verbindung mit einer [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]-Remoteinstanz und die Remotesicherungsdatei, die für das Wiederherstellen von Remotepartitionen auf dieser Remoteinstanz verwendet wird.  
  
 Bei `Synchronize`-Befehlen beschreibt das `Location`-Element entweder eine Datenquelle, die von der Zielinstanz verwendet wird, oder eine Remoteinstanz, die auf der Zielinstanz definiert wird und mit der Zielinstanz synchronisiert werden muss. Letzteres ist abhängig vom Wert des `DataSourceType`-Elements des übergeordneten `Synchronize`-Befehls.  
  
 Weitere Informationen zum Sichern und Wiederherstellen von Remoteinstanzen finden Sie unter [Backing Up and Restoring Objects (XMLA)](../../multidimensional-models-scripting-language-assl-xmla/backing-up-restoring-and-synchronizing-databases-xmla.md).  
  
## <a name="see-also"></a>Siehe auch  
 [BackupRemotePartitions-Element &#40;XMLA&#41;](backupremotepartitions-element-xmla.md)   
 [Eigenschaften &#40;XMLA&#41;](xml-elements-properties.md)  
  
  