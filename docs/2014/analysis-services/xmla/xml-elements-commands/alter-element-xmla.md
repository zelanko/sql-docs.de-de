---
title: Alter-Element (XMLA) | Microsoft-Dokumentation
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
- Alter Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- http://schemas.microsoft.com/analysisservices/2003/engine#Alter
- microsoft.xml.analysis.alter
- urn:schemas-microsoft-com:xml-analysis#Alter
helpviewer_keywords:
- Alter command
ms.assetid: 84e58385-c9ba-48fa-a867-94d35b777a56
caps.latest.revision: 14
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: e13819d301af842eb2094d7b6ad3367cde424c72
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/02/2018
ms.locfileid: "37192408"
---
# <a name="alter-element-xmla"></a>Alter-Element (XMLA)
  Enthält Analysis Services Scripting Language (ASSL)-Elemente, die verwendet werden, indem die [Execute](../xml-elements-methods-execute.md) Methode zum Ändern von Objekten in einer Instanz von [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)].  
  
## <a name="syntax"></a>Syntax  
  
```xml  
  
<Command>  
   <Alter Scope="enum" AllowCreate="boolean" ObjectExpansion="enum">  
      <Object>...</Object>  
      <ObjectDefinition>...</ObjectDefinition>  
   </Alter>  
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
|Untergeordnete Elemente|[Objekt](../xml-elements-properties/object-element-xmla.md), [ObjectDefinition](../xml-elements-properties/objectdefinition-element-xmla.md)|  
  
## <a name="attributes"></a>Attribute  
  
|attribute|Description|  
|---------------|-----------------|  
|AllowCreate|(Optionales `Boolean`-Attribut) Gibt an, ob Objekte, die im `Alter`-Befehl definiert werden, erstellt werden sollten, wenn sie bisher noch nicht vorhanden sind.<br /><br /> Wenn Set auf "true", die in definierten Objekte die `ObjectDefinition` Element erstellt werden, auf die [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] Instanz, wenn sie nicht bereits vorhanden sind. Mit anderen Worten: Der `Alter`-Befehl wird wie ein `Create`-Befehl behandelt, wenn die Objekte noch nicht auf der Instanz vorhanden sind.<br /><br /> Wenn dieses Objekt ausgelassen oder auf `false` gesetzt wird, tritt ein Fehler auf, wenn die Objekte noch nicht vorhanden sind.|  
|ObjectExpansion|(Optional `Enum` Attribut) definiert den Umfang der Änderung, die durch erfolgen die `Execute` Methode.<br /><br /> Wenn auf festgelegt *ObjectProperties*, `ObjectDefinition` Element sollte nur die vollständige Definition des Hauptobjekts geändert werden, enthalten einschließlich seiner untergeordneten nebenobjekte. Untergeordnete Hauptobjekte des Objekts, die geändert werden sollen, bleiben unverändert. **Hinweis:** bei Verwendung der *ObjectProperties* Einstellung mit der [ClrAssembly](../../scripting/data-type/assembly-data-type-assl.md) -Datentyp, der [Daten](../../scripting/objects/data-element-assl.md) -Element der zugeordneten [ Clrassemblyfile-Objekts](../../scripting/data-type/clrassemblyfile-data-type-assl.md) Datentypen muss nicht angegeben werden. Wenn nicht angegeben, die `ClrAssembly` verwendet vorhandene Dateien. <br /><br /> Wenn auf festgelegt *ExpandFull*, `ObjectDefinition` Element sollten nicht nur die Definition des Objekts, das geändert werden, sondern auch die Definitionen aller Hauptobjekte, die Nachkommen des Objekts geändert werden, sind enthalten. **Hinweis:** der *ExpandFull* Einstellung kann nicht verwendet werden, mit der [Server](../../scripting/objects/server-element-assl.md) Element.|  
|Bereich|(Optional `Enum` Attribut) definiert die Dauer der Objekte, die der `ObjectDefinition` Element.<br /><br /> Wenn auf festgelegt *Sitzung*, definierten Objekte auf der `ObjectDefinition` Element nur für die Dauer der XMLA-Sitzung vorhanden ist. **Hinweis:** bei Verwendung der *Sitzung* festlegen, die `ObjectDefinition` Element darf nur [Dimension](../../scripting/objects/dimension-element-assl.md), [Cube](../../scripting/objects/cube-element-assl.md), oder [MiningModel ](../../scripting/objects/miningmodel-element-assl.md) ASSL-Elemente. <br /><br /> Wenn dieses Attribut weggelassen wird, die Objekte definiert, der `ObjectDefinition` Element werden beibehalten, auf die [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] Instanz.|  
  
## <a name="remarks"></a>Hinweise  
 Jede `Alter` Befehl ändert die Definition eines Hauptobjekts unter dem übergeordneten Objekt durch die [ParentObject](../xml-elements-properties/parentobject-element-xmla.md) Element.  
  
## <a name="see-also"></a>Siehe auch  
 [Befehle &#40;XMLA&#41;](xml-elements-commands.md)  
  
  
