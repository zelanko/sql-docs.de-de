---
title: Datei-Element (XMLA) | Microsoft Docs
ms.date: 05/08/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: xmla
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 1d7422a79112ef09da406eccf6f52f5b71851607
ms.sourcegitcommit: c12a7416d1996a3bcce3ebf4a3c9abe61b02fb9e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/10/2018
---
# <a name="file-element-xmla"></a>File-Element (XMLA)
[!INCLUDE[ssas-appliesto-sqlas-aas](../../../includes/ssas-appliesto-sqlas-aas.md)]
  Identifiziert eine Datei, die vom übergeordneten [Backup](../../../analysis-services/xmla/xml-elements-commands/backup-element-xmla.md) - oder [Restore](../../../analysis-services/xmla/xml-elements-commands/restore-element-xmla.md) -Befehl oder vom übergeordneten [Location](../../../analysis-services/xmla/xml-elements-properties/location-element-xmla.md) -Element verwendet werden soll.  
  
## <a name="syntax"></a>Syntax  
  
```xml  
  
<Backup> <!-- or one of the elements listed below in the Element Relationships table -->  
   ...  
   <File>...</File>  
   ...  
</Backup>  
```  
  
## <a name="element-characteristics"></a>Elementmerkmale  
  
|Merkmal|Beschreibung|  
|--------------------|-----------------|  
|Datentyp und -länge|String|  
|Standardwert|Keine|  
|Kardinalität|1-1: Erforderliches Element, das nur einmal auftritt.|  
  
## <a name="element-relationships"></a>Elementbeziehungen  
  
|Beziehung|Element|  
|------------------|-------------|  
|Übergeordnete Elemente|[Backup](../../../analysis-services/xmla/xml-elements-commands/backup-element-xmla.md), [Location](../../../analysis-services/xmla/xml-elements-properties/location-element-xmla.md), [Restore](../../../analysis-services/xmla/xml-elements-commands/restore-element-xmla.md)|  
|Untergeordnete Elemente|Keine|  
  
## <a name="remarks"></a>Hinweise  
 Das **File** -Element enthält einen UNC-Dateinamen, und das übergeordnete Element bestimmt die Verwendung des **File** -Elements.  
  
 Bei **Backup** -Befehlen bestimmt das **File** -Element den Namen der vom **Backup** -Befehl erstellten Sicherungsdatei. Wenn kein Pfad als Teil des Dateinamens angegeben ist, wird der Pfad angegeben, der **BackupDir** Konfigurationseigenschaft für die Instanz von [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] verwendet wird. Wenn die angegebene Datei bereits vorhanden ist, tritt ein Fehler auf, es sei denn, das **AllowOverwrite** -Element des übergeordneten **Backup** -Befehls ist auf **True**gesetzt.  
  
 Für **Restore** -Befehle bestimmt das **File** -Element den Namen der vom **Restore** -Befehl wiederherzustellenden Sicherungsdatei.  
  
 Für **Speicherort** Elemente, die **Datei** -Element beschreibt eine remotesicherungsdatei für eine [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] -Instanz, die Remotepartitionen enthält. Weitere Informationen zum Sichern und Wiederherstellen von Remotepartitionen finden Sie unter [sichern, wiederherstellen, und Synchronisieren von Datenbanken & #40; XMLA & #41; ](../../../analysis-services/multidimensional-models-scripting-language-assl-xmla/backing-up-restoring-and-synchronizing-databases-xmla.md).  
  
## <a name="see-also"></a>Siehe auch  
 [AllowOverwrite-Element & #40; XMLA & #41;](../../../analysis-services/xmla/xml-elements-properties/allowoverwrite-element-xmla.md)   
 [Datenbankeigenschaften & #40; XMLA & #41;](../../../analysis-services/xmla/xml-elements-properties/xml-elements-properties.md)  
  
  
