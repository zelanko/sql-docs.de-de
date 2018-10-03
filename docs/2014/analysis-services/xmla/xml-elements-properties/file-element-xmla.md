---
title: File-Element (XMLA) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.topic: reference
api_name:
- File Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- microsoft.xml.analysis.file
- http://schemas.microsoft.com/analysisservices/2003/engine#File
- urn:schemas-microsoft-com:xml-analysis#File
helpviewer_keywords:
- File element
ms.assetid: 3dfd0e9b-746b-4ce5-8a95-610d2e573739
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: a5ae3390405bc7a722934f3b3fb3652825b2ea03
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/02/2018
ms.locfileid: "48125450"
---
# <a name="file-element-xmla"></a>File-Element (XMLA)
  Identifiziert eine Datei, die vom übergeordneten Element verwendet werden [Sicherung](../xml-elements-commands/backup-element-xmla.md) oder [wiederherstellen](../xml-elements-commands/restore-element-xmla.md) -Befehl oder vom übergeordneten Element [Speicherort](location-element-xmla.md) Element.  
  
## <a name="syntax"></a>Syntax  
  
```xml  
  
<Backup> <!-- or one of the elements listed below in the Element Relationships table -->  
   ...  
   <File>...</File>  
   ...  
</Backup>  
```  
  
## <a name="element-characteristics"></a>Elementmerkmale  
  
|Merkmal|Description|  
|--------------------|-----------------|  
|Datentyp und -länge|Zeichenfolge|  
|Standardwert|None|  
|Cardinality|1-1: Erforderliches Element, das nur einmal auftritt.|  
  
## <a name="element-relationships"></a>Elementbeziehungen  
  
|Beziehung|Element|  
|------------------|-------------|  
|Übergeordnete Elemente|[Sicherung](../xml-elements-commands/backup-element-xmla.md), [Speicherort](location-element-xmla.md), [wiederherstellen](../xml-elements-commands/restore-element-xmla.md)|  
|Untergeordnete Elemente|None|  
  
## <a name="remarks"></a>Hinweise  
 Das `File`-Element enthält einen UNC-Dateinamen, und das übergeordnete Element bestimmt die Verwendung des `File`-Elements.  
  
 Bei `Backup`-Befehlen bestimmt das `File`-Element den Namen der vom `Backup`-Befehl erstellten Sicherungsdatei. Wenn kein Pfad als Teil des Dateinamens angegeben ist, wird der Pfad angegeben, der `BackupDir` Konfigurationseigenschaft für die Instanz von [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] verwendet wird. Wenn die angegebene Datei bereits vorhanden ist, tritt ein Fehler auf, es sei denn, das `AllowOverwrite`-Element des übergeordneten `Backup`-Befehls ist auf `True` gesetzt.  
  
 Für `Restore` Befehle, die `File` Element bestimmt den Namen der Sicherungsdatei aus, die wiederhergestellt werden die `Restore` Befehl.  
  
 Für `Location`-Elemente beschreibt das `File`-Element eine Remotesicherungsdatei für eine [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]-Instanz, die Remotepartitionen enthält. Weitere Informationen zum Sichern und Wiederherstellen von Remotepartitionen finden Sie unter [sichern, wiederherstellen und Synchronisieren von Datenbanken &#40;XMLA&#41;](../../multidimensional-models-scripting-language-assl-xmla/backing-up-restoring-and-synchronizing-databases-xmla.md).  
  
## <a name="see-also"></a>Siehe auch  
 [AllowOverwrite-Element &#40;XMLA&#41;](allowoverwrite-element-xmla.md)   
 [Eigenschaften &#40;XMLA&#41;](xml-elements-properties.md)  
  
  
