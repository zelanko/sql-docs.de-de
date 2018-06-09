---
title: Location-Element (XMLA) | Microsoft Docs
ms.date: 05/08/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: xmla
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 4953981e7657706a986e9a2407f6786ff676a854
ms.sourcegitcommit: 808d23a654ef03ea16db1aa23edab496b73e5072
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/04/2018
ms.locfileid: "34575602"
---
# <a name="location-element-xmla"></a>Location-Element (XMLA)
[!INCLUDE[ssas-appliesto-sqlas-aas](../../../includes/ssas-appliesto-sqlas-aas.md)]
  Enthält Informationen über einen Remoteserver für den übergeordneten [Sicherung](../../../analysis-services/xmla/xml-elements-commands/backup-element-xmla.md), [wiederherstellen](../../../analysis-services/xmla/xml-elements-commands/restore-element-xmla.md), oder [Synchronize](../../../analysis-services/xmla/xml-elements-commands/synchronize-element-xmla.md) Befehl.  
  
## <a name="syntax"></a>Syntax  
  
```xml  
  
<Backup> <!-- or one of the elements listed below in the Element relationships table -->  
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
|Übergeordnete Elemente|[Sicherung](../../../analysis-services/xmla/xml-elements-commands/backup-element-xmla.md), [wiederherstellen](../../../analysis-services/xmla/xml-elements-commands/restore-element-xmla.md), [synchronisieren](../../../analysis-services/xmla/xml-elements-commands/synchronize-element-xmla.md)|  
|Untergeordnete Elemente|Siehe Tabelle unten.|  
  
|Vorgänger oder übergeordnetes Element|Untergeordnetes Element|  
|------------------------|-------------------|  
|[Sicherung](../../../analysis-services/xmla/xml-elements-commands/backup-element-xmla.md)|[DataSourceID](../../../analysis-services/xmla/xml-elements-properties/datasourceid-element-xmla.md), [Datei](../../../analysis-services/xmla/xml-elements-properties/file-element-xmla.md)|  
|[Wiederherstellen](../../../analysis-services/xmla/xml-elements-commands/restore-element-xmla.md)|["ConnectionString"](../../../analysis-services/xmla/xml-elements-properties/connectionstring-element-xmla.md), [DataSourceID](../../../analysis-services/xmla/xml-elements-properties/datasourceid-element-xmla.md), [DataSourceType](../../../analysis-services/xmla/xml-elements-properties/datasourcetype-element-xmla.md), [Datei](../../../analysis-services/xmla/xml-elements-properties/file-element-xmla.md), [Ordner](../../../analysis-services/xmla/xml-elements-properties/folders-element-xmla.md)|  
|[Synchronisieren](../../../analysis-services/xmla/xml-elements-commands/synchronize-element-xmla.md)|["ConnectionString"](../../../analysis-services/xmla/xml-elements-properties/connectionstring-element-xmla.md), [DataSourceID](../../../analysis-services/xmla/xml-elements-properties/datasourceid-element-xmla.md), [DataSourceType](../../../analysis-services/xmla/xml-elements-properties/datasourcetype-element-xmla.md), [Ordner](../../../analysis-services/xmla/xml-elements-properties/folders-element-xmla.md)|  
  
## <a name="remarks"></a>Hinweise  
 Für **Backup** Befehle, die **Speicherort** -Element stellt Informationen zum Erstellen einer remotesicherungsdatei für eine Remoteinstanz von Analysis Services bereit.  
  
 Für **wiederherstellen** Befehle, die **Speicherort** Element enthält Informationen über die Identifizierung und Verbindung mit einer [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] Instanz sowie die remotesicherungsdatei, remote wiederherstellen Partitionen, die auf dieser Remoteinstanz.  
  
 Bei **Synchronize** -Befehlen beschreibt das **Location** -Element entweder eine Datenquelle, die von der Zielinstanz verwendet wird, oder eine Remoteinstanz, die auf der Zielinstanz definiert wird und mit der Zielinstanz synchronisiert werden muss. Letzteres ist abhängig vom Wert des **DataSourceType** -Elements des übergeordneten **Synchronize** -Befehls.  
  
 Weitere Informationen zum Sichern und Wiederherstellen von Remoteinstanzen finden Sie unter [Backing Up and Restoring Objects (XMLA)](../../../analysis-services/multidimensional-models-scripting-language-assl-xmla/backing-up-restoring-and-synchronizing-databases-xmla.md).  
  
## <a name="see-also"></a>Siehe auch
 [BackupRemotePartitions-Element &#40;XMLA&#41;](../../../analysis-services/xmla/xml-elements-properties/backupremotepartitions-element-xmla.md)   
 [Eigenschaften &#40;XMLA&#41;](../../../analysis-services/xmla/xml-elements-properties/xml-elements-properties.md)  
  
  
