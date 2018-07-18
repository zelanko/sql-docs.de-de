---
title: Backup-Element (XMLA) | Microsoft-Dokumentation
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
- Backup Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- urn:schemas-microsoft-com:xml-analysis#Backup
- http://schemas.microsoft.com/analysisservices/2003/engine#Backup
- microsoft.xml.analysis.backup
helpviewer_keywords:
- Backup command
ms.assetid: 5bcbc14c-9db9-45b2-99de-f3a265bcb0c4
caps.latest.revision: 19
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: a571681f52fb34e55df238229f659aa883bc84ac
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/02/2018
ms.locfileid: "37215650"
---
# <a name="backup-element-xmla"></a>Backup-Element (XMLA)
  Sichert eine [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] Datenbank in einer Sicherungsdatei.  
  
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
|Übergeordnete Elemente|[Befehl](../xml-elements-properties/command-element-xmla.md)|  
|Untergeordnete Elemente|[AllowOverwrite](../xml-elements-properties/allowoverwrite-element-xmla.md), [ApplyCompression](../xml-elements-properties/applycompression-element-xmla.md), [BackupRemotePartitions](../xml-elements-properties/backupremotepartitions-element-xmla.md), [Datei](../xml-elements-properties/file-element-xmla.md), [Speicherorte](../xml-elements-properties/locations-element-xmla.md), [ Objekt](../xml-elements-properties/object-element-xmla.md), [Kennwort](../xml-elements-properties/password-element-xmla.md), [Sicherheit](../xml-elements-properties/security-element-xmla.md)|  
  
## <a name="remarks"></a>Hinweise  
 Die `Backup` Befehl sichert die [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] Datenbank in der [Objekt](../xml-elements-properties/object-element-xmla.md) Element auf eine Sicherungsdatei und optional Remotepartitionen in remotesicherungsdateien sichert. Wenn das `Object`-Element auf ein Objekt verweist, bei dem es sich nicht um eine [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]-Datenbank handelt, tritt ein Fehler auf.  
  
 Welche Informationen das `Backup` -Befehls gesichert werden, hängt von Objekten in der Datenbank verwendeten Speichermodus. In der folgenden Tabelle werden die Informationen dargestellt, die basierend auf dem verwendeten Speichermodus gesichert werden.  
  
|Speichermodus|Informationen, die gesichert werden|  
|------------------|-----------------------------------|  
|Mehrdimensionale OLAP (MOLAP)|Quelldaten, Aggregationen und Metadaten|  
|Hybride OLAP (HOLAP)|Aggregationen und Metadaten|  
|Relationale OLAP (ROLAP)|Metadaten|  
  
 Während ein `Backup` -Befehls wird eine freigegebene Sperre für die [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] Datenbank in der `Object` Element. Die freigegebene Sperre wird nach der `Backup` -Befehl ausgeführt wurde.  
  
 Mehrere `Backup` -Befehle können gleichzeitig ausgeführt werden, wenn die Befehle, in enthalten sind der [parallele](../xml-elements-properties/parallel-element-xmla.md) Auflistung von einer [Batch](batch-element-xmla.md) Befehl. Mihilfe der `Parallel`-Auflistung kann eine Datenbank in mehreren Sicherungsdateien gleichzeitig gesichert werden.  
  
 Weitere Informationen zum Sichern und Wiederherstellen von Datenbanken finden Sie unter [sichern, wiederherstellen und Synchronisieren von Datenbanken &#40;XMLA&#41;](../../multidimensional-models-scripting-language-assl-xmla/backing-up-restoring-and-synchronizing-databases-xmla.md).  
  
> [!IMPORTANT]  
>  Für jede Sicherungsdatei muss der Benutzer, der den Sicherungsbefehl ausführt, über die Berechtigung zum Schreiben in den für jede Datei angegebenen Sicherungsspeicherort verfügen. Dem Benutzer muss zudem eine der folgenden Rollen zugewiesen worden sein: Mitglied einer Serverrolle für die [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] -Instanz oder Mitglied einer Datenbankrolle mit der Berechtigung „Vollzugriff“ (Administrator) für die wiederherzustellende Datenbank.  
  
## <a name="see-also"></a>Siehe auch  
 [Restore-Element &#40;XMLA&#41;](restore-element-xmla.md)   
 [Synchronize-Element &#40;XMLA&#41;](synchronize-element-xmla.md)   
 [Befehle &#40;XMLA&#41;](xml-elements-commands.md)  
  
  
