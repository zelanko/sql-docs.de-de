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
ms.openlocfilehash: eb80a091c9b9585a6efc29088d15139db7033efb
ms.sourcegitcommit: 808d23a654ef03ea16db1aa23edab496b73e5072
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/04/2018
ms.locfileid: "34575192"
---
# <a name="file-element-xmla"></a>File-Element (XMLA)
[!INCLUDE[ssas-appliesto-sqlas-aas](../../../includes/ssas-appliesto-sqlas-aas.md)]
  Identifiziert eine Datei, die vom übergeordneten Element verwendet werden [Sicherung](../../../analysis-services/xmla/xml-elements-commands/backup-element-xmla.md) oder [wiederherstellen](../../../analysis-services/xmla/xml-elements-commands/restore-element-xmla.md) -Befehl oder vom übergeordneten [Speicherort](../../../analysis-services/xmla/xml-elements-properties/location-element-xmla.md) Element.  
  
## <a name="syntax"></a>Syntax  
  
```xml  
  
<Backup> <!-- or one of the elements listed below in the Element relationships table -->  
   ...  
   <File>...</File>  
   ...  
</Backup>  
```  
  
## <a name="element-characteristics"></a>Elementmerkmale  
  
|Merkmal|Description|  
|--------------------|-----------------|  
|Datentyp und -länge|Zeichenfolge|  
|Standardwert|InclusionThresholdSetting|  
|Cardinality|1-1: Erforderliches Element, das nur einmal auftritt.|  
  
## <a name="element-relationships"></a>Elementbeziehungen  
  
|Beziehung|Element|  
|------------------|-------------|  
|Übergeordnete Elemente|[Sicherung](../../../analysis-services/xmla/xml-elements-commands/backup-element-xmla.md), [Speicherort](../../../analysis-services/xmla/xml-elements-properties/location-element-xmla.md), [wiederherstellen](../../../analysis-services/xmla/xml-elements-commands/restore-element-xmla.md)|  
|Untergeordnete Elemente|InclusionThresholdSetting|  
  
## <a name="remarks"></a>Hinweise  
 Das **File** -Element enthält einen UNC-Dateinamen, und das übergeordnete Element bestimmt die Verwendung des **File** -Elements.  
  
 Bei **Backup** -Befehlen bestimmt das **File** -Element den Namen der vom **Backup** -Befehl erstellten Sicherungsdatei. Wenn kein Pfad als Teil des Dateinamens angegeben ist, wird der Pfad angegeben, der **BackupDir** Konfigurationseigenschaft für die Instanz von Analysis Services verwendet wird. Wenn die angegebene Datei bereits vorhanden ist, tritt ein Fehler auf, es sei denn, das **AllowOverwrite** -Element des übergeordneten **Backup** -Befehls ist auf **True**gesetzt.  
  
 Für **Restore** -Befehle bestimmt das **File** -Element den Namen der vom **Restore** -Befehl wiederherzustellenden Sicherungsdatei.  
  
 Für **Speicherort** Elemente, die **Datei** -Element beschreibt eine remotesicherungsdatei für eine [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] -Instanz, die Remotepartitionen enthält. Weitere Informationen zum Sichern und Wiederherstellen von Remotepartitionen finden Sie unter [sichern, wiederherstellen und Synchronisieren von Datenbanken &#40;XMLA&#41;](../../../analysis-services/multidimensional-models-scripting-language-assl-xmla/backing-up-restoring-and-synchronizing-databases-xmla.md).  
  
## <a name="see-also"></a>Siehe auch
 [AllowOverwrite-Element &#40;XMLA&#41;](../../../analysis-services/xmla/xml-elements-properties/allowoverwrite-element-xmla.md)   
 [Eigenschaften &#40;XMLA&#41;](../../../analysis-services/xmla/xml-elements-properties/xml-elements-properties.md)  
  
  
