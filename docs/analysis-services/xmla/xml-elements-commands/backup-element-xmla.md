---
title: Backup-Element (XMLA) | Microsoft Docs
ms.date: 05/08/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: xmla
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 4e00a4991226779a91e16806dbe15973d946ec69
ms.sourcegitcommit: 808d23a654ef03ea16db1aa23edab496b73e5072
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/04/2018
ms.locfileid: "34574212"
---
# <a name="backup-element-xmla"></a>Backup-Element (XMLA)
[!INCLUDE[ssas-appliesto-sqlas-aas](../../../includes/ssas-appliesto-sqlas-aas.md)]
  Sichert eine Analysis Services-Datenbank in einer Sicherungsdatei.  
  
## <a name="syntax"></a>Syntax  
  
```xml  
  
<Command>  
   <Backup>  
      <Object>...</Object>  
      <File>...</File>  
      <Security>...</Security>  
      <ApplyCompression>...</ApplyCompression>  
      <AllowOverwrite>...</AllowOverwrite>  
      <Password>...</Password>  
      <BackupRemotePartitions>...</BackupRemotePartitions>  
      <Locations>...</Locations>  
   </Backup>  
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
|Übergeordnete Elemente|[Befehl](../../../analysis-services/xmla/xml-elements-properties/command-element-xmla.md)|  
|Untergeordnete Elemente|[AllowOverwrite](../../../analysis-services/xmla/xml-elements-properties/allowoverwrite-element-xmla.md), [ApplyCompression](../../../analysis-services/xmla/xml-elements-properties/applycompression-element-xmla.md), [BackupRemotePartitions](../../../analysis-services/xmla/xml-elements-properties/backupremotepartitions-element-xmla.md), [Datei](../../../analysis-services/xmla/xml-elements-properties/file-element-xmla.md), [Speicherorte](../../../analysis-services/xmla/xml-elements-properties/locations-element-xmla.md), [ Objekt](../../../analysis-services/xmla/xml-elements-properties/object-element-xmla.md), [Kennwort](../../../analysis-services/xmla/xml-elements-properties/password-element-xmla.md), [Sicherheit](../../../analysis-services/xmla/xml-elements-properties/security-element-xmla.md)|  
  
## <a name="remarks"></a>Hinweise  
 Die **Backup** Befehl sichert die [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] Datenbank in der [Objekt](../../../analysis-services/xmla/xml-elements-properties/object-element-xmla.md) Element, um eine Sicherungsdatei und optional sichert der Remotepartitionen in remotesicherungsdateien. Wenn die **Objekt** Element verweist auf ein Objekt als eine [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] Datenbank, ein Fehler auftritt.  
  
 Welche Informationen mithilfe des **Backup** -Befehls gesichert werden, hängt vom von Objekten in der Datenbank verwendeten Speichermodus ab. In der folgenden Tabelle werden die Informationen dargestellt, die basierend auf dem verwendeten Speichermodus gesichert werden.  
  
|Speichermodus|Informationen, die gesichert werden|  
|------------------|-----------------------------------|  
|Mehrdimensionale OLAP (MOLAP)|Quelldaten, Aggregationen und Metadaten|  
|Hybride OLAP (HOLAP)|Aggregationen und Metadaten|  
|Relationale OLAP (ROLAP)|Metadaten|  
  
 Während einer **Sicherung** Befehl, eine gemeinsame Sperre befindet sich auf die [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] Datenbank in der **Objekt** Element. Die freigegebene Sperre wird nach Abschluss des **Backup** -Befehls wieder aufgehoben.  
  
 Mehrere **Sicherung** -Befehle können gleichzeitig ausgeführt werden, wenn die Befehle, in enthalten sind der [parallele](../../../analysis-services/xmla/xml-elements-properties/parallel-element-xmla.md) Auflistung von einer [Batch](../../../analysis-services/xmla/xml-elements-commands/batch-element-xmla.md) Befehl. Mihilfe der **Parallel** -Auflistung kann eine Datenbank in mehreren Sicherungsdateien gleichzeitig gesichert werden.  
  
 Weitere Informationen zum Sichern und Wiederherstellen von Datenbanken finden Sie unter [sichern, wiederherstellen und Synchronisieren von Datenbanken &#40;XMLA&#41;](../../../analysis-services/multidimensional-models-scripting-language-assl-xmla/backing-up-restoring-and-synchronizing-databases-xmla.md).  
  
> [!IMPORTANT]  
>  Für jede Sicherungsdatei muss der Benutzer, der den Sicherungsbefehl ausführt, über die Berechtigung zum Schreiben in den für jede Datei angegebenen Sicherungsspeicherort verfügen. Dem Benutzer muss zudem eine der folgenden Rollen zugewiesen worden sein: Mitglied einer Serverrolle für die [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] -Instanz oder Mitglied einer Datenbankrolle mit der Berechtigung „Vollzugriff“ (Administrator) für die wiederherzustellende Datenbank.  
  
## <a name="see-also"></a>Siehe auch
 [Restore-Element &#40;XMLA&#41;](../../../analysis-services/xmla/xml-elements-commands/restore-element-xmla.md)   
 [Synchronize-Element &#40;XMLA&#41;](../../../analysis-services/xmla/xml-elements-commands/synchronize-element-xmla.md)   
 [Befehle &#40;XMLA&#41;](../../../analysis-services/xmla/xml-elements-commands/xml-elements-commands.md)  
  
  
