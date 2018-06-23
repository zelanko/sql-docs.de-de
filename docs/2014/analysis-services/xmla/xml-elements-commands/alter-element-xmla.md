---
title: Alter-Element (XMLA) | Microsoft Docs
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
author: mgblythe
ms.author: mblythe
manager: mblythe
ms.openlocfilehash: 5ea2c3ed3105c66b0c0848138acb5941978dd9bf
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/19/2018
ms.locfileid: "36058995"
---
# <a name="alter-element-xmla"></a>Alter-Element (XMLA)
  Enthält Analysis Services Scripting Language (ASSL)-Elementen, die verwendet werden, indem die [Execute](../xml-elements-methods-execute.md) Methode, um Objekte auf einer Instanz von alter [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)].  
  
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
|Untergeordnete Elemente|[Objekt](../xml-elements-properties/object-element-xmla.md), ["objectdefinition"](../xml-elements-properties/objectdefinition-element-xmla.md)|  
  
## <a name="attributes"></a>Attribute  
  
|attribute|Description|  
|---------------|-----------------|  
|AllowCreate|(Optionales `Boolean`-Attribut) Gibt an, ob Objekte, die im `Alter`-Befehl definiert werden, erstellt werden sollten, wenn sie bisher noch nicht vorhanden sind.<br /><br /> Wenn Set auf "true", die in definierten Objekte die `ObjectDefinition` Element werden erstellt, die [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] Instanz, wenn sie nicht bereits vorhanden sind. Mit anderen Worten: Der `Alter`-Befehl wird wie ein `Create`-Befehl behandelt, wenn die Objekte noch nicht auf der Instanz vorhanden sind.<br /><br /> Wenn dieses Objekt ausgelassen oder auf `false` gesetzt wird, tritt ein Fehler auf, wenn die Objekte noch nicht vorhanden sind.|  
|ObjectExpansion|(Optional `Enum` Attribut) definiert den Umfang der Änderung auf die `Execute` Methode.<br /><br /> Wenn auf festgelegt *' ObjectProperties '* die `ObjectDefinition` Element dürfen nur die vollständige Definition des Hauptobjekts geändert werden soll, einschließlich seiner untergeordneten nebenobjekte. Untergeordnete Hauptobjekte des Objekts, die geändert werden sollen, bleiben unverändert. **Hinweis:** bei Verwendung der *' ObjectProperties '* festlegen, mit der [ClrAssembly](../../scripting/data-type/assembly-data-type-assl.md) -Datentyp, der [Daten](../../scripting/objects/data-element-assl.md) -Element der zugeordneten [ ClrAssemblyFile](../../scripting/data-type/clrassemblyfile-data-type-assl.md) Datentypen muss nicht angegeben werden. Wenn nicht angegeben, die `ClrAssembly` verwendet vorhandene Dateien. <br /><br /> Wenn auf festgelegt *ExpandFull*, `ObjectDefinition` -Element sollten nicht nur die Definition des Objekts, die geändert werden, sondern auch die Definitionen aller Hauptobjekte, die Nachkommen des Objekts geändert werden, sind enthalten. **Hinweis:** der *ExpandFull* Einstellung kann nicht verwendet werden, mit der [Server](../../scripting/objects/server-element-assl.md) Element.|  
|Bereich|(Optional `Enum` Attribut) definiert die Dauer der Objekte, die der `ObjectDefinition` Element.<br /><br /> Wenn auf festgelegt *Sitzung*, die in definierten Objekte die `ObjectDefinition` Element nur für die Dauer der XMLA-Sitzung vorhanden sein. **Hinweis:** bei Verwendung der *Sitzung* festlegen, die `ObjectDefinition` Element darf nur [Dimension](../../scripting/objects/dimension-element-assl.md), [Cube](../../scripting/objects/cube-element-assl.md), oder [MiningModel ](../../scripting/objects/miningmodel-element-assl.md) ASSL-Elemente. <br /><br /> Wenn dieses Attribut weggelassen wird, definiert die Objekte der `ObjectDefinition` Element persistent auf der [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] Instanz.|  
  
## <a name="remarks"></a>Hinweise  
 Jede `Alter` Befehl ändert die Definition eines Hauptobjekts unter dem übergeordneten Objekt von der [ParentObject](../xml-elements-properties/parentobject-element-xmla.md) Element.  
  
## <a name="see-also"></a>Siehe auch  
 [Befehle &#40;XMLA&#41;](xml-elements-commands.md)  
  
  