---
title: Alter-Element (XMLA) | Microsoft Docs
ms.date: 05/08/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: xmla
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 5ff62bcde0aa40e9bb052691d4d3dee1317c1217
ms.sourcegitcommit: 808d23a654ef03ea16db1aa23edab496b73e5072
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/04/2018
ms.locfileid: "34574602"
---
# <a name="alter-element-xmla"></a>Alter-Element (XMLA)
[!INCLUDE[ssas-appliesto-sqlas-aas](../../../includes/ssas-appliesto-sqlas-aas.md)]
  Enthält Analysis Services Scripting Language (ASSL)-Elementen, die verwendet werden, indem die [Execute](../../../analysis-services/xmla/xml-elements-methods-execute.md) Methode, um Objekte auf einer Instanz von Analysis Services geändert.  
  
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
|Übergeordnete Elemente|[Befehl](../../../analysis-services/xmla/xml-elements-properties/command-element-xmla.md)|  
|Untergeordnete Elemente|[Objekt](../../../analysis-services/xmla/xml-elements-properties/object-element-xmla.md), ["objectdefinition"](../../../analysis-services/xmla/xml-elements-properties/objectdefinition-element-xmla.md)|  
  
## <a name="attributes"></a>Attribute  
  
|attribute|Description|  
|---------------|-----------------|  
|AllowCreate|(Optionales **Boolean** -Attribut) Gibt an, ob Objekte, die im **Alter** -Befehl definiert werden, erstellt werden sollten, wenn sie bisher noch nicht vorhanden sind.<br /><br /> Wenn Set auf "true", die in definierten Objekte die **"objectdefinition"** Element werden erstellt, die [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] Instanz, wenn sie nicht bereits vorhanden sind. Mit anderen Worten: Der **Alter** -Befehl wird wie ein **Create** -Befehl behandelt, wenn die Objekte noch nicht auf der Instanz vorhanden sind.<br /><br /> Wenn dieses Objekt ausgelassen oder auf **false**gesetzt wird, tritt ein Fehler auf, wenn die Objekte noch nicht vorhanden sind.|  
|ObjectExpansion|(Optionales **Enum** -Attribut) Definiert den Umfang der Änderung, die von der **Execute** -Methode ausgeführt werden soll.<br /><br /> Wenn das *ObjectDefinition*-Element auf **ObjectProperties** festgelegt ist, sollte es nur die vollständige Definition des zu ändernden Hauptobjekts, einschließlich seiner untergeordneten Nebenobjekte, enthalten. Untergeordnete Hauptobjekte des Objekts, die geändert werden sollen, bleiben unverändert.<br /><br /> Hinweis: Bei Verwendung der *' ObjectProperties '* festlegen, mit der [ClrAssembly](../../../analysis-services/scripting/data-type/clrassembly-data-type-assl.md) -Datentyp, der [Daten](../../../analysis-services/scripting/objects/data-element-assl.md) Element des verknüpften [ClrAssemblyFile](../../../analysis-services/scripting/data-type/clrassemblyfile-data-type-assl.md) Datentypen muss nicht angegeben werden. Sofern keine Angabe gemacht wird, verwendet **ClrAssembly** vorhandene Dateien.<br /><br /> Wenn das *ObjectDefinition*-Element auf **ExpandFull** festgelegt ist, sollte es nicht nur die Definition des zu ändernden Objekts enthalten, sondern auch die Definitionen aller Hauptobjekte, die Nachkommen des zu ändernden Objekts sind.<br /><br /> Hinweis: Die *ExpandFull* Einstellung kann nicht verwendet werden, mit der [Server](../../../analysis-services/scripting/objects/server-element-assl.md) Element.|  
|Bereich|(Optionales **Enum** -Attribut) Definiert die Lebenszeit der Objekte, die im **ObjectDefinition** -Element definiert sind.<br /><br /> Wenn die im *ObjectDefinition*-Element definierten Objekte auf **Session** festgelegt sind, ist das Element nur für die Dauer der XMLA-Sitzung vorhanden.<br /><br /> Hinweis: Bei Verwendung der *Sitzung* festlegen, die **ObjectDefinition** Element darf nur [Dimension](../../../analysis-services/scripting/objects/dimension-element-assl.md), [Cube](../../../analysis-services/scripting/objects/cube-element-assl.md), oder [MiningModel](../../../analysis-services/scripting/objects/miningmodel-element-assl.md) ASSL-Elemente.<br /><br /> Wenn dieses Attribut weggelassen wird, definiert die Objekte der **ObjectDefinition** Element persistent auf der [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] Instanz.|  
  
## <a name="remarks"></a>Hinweise  
 Jede **Alter** Befehl ändert die Definition eines Hauptobjekts unter dem übergeordneten Objekt von der [ParentObject](../../../analysis-services/xmla/xml-elements-properties/parentobject-element-xmla.md) Element.  
  
## <a name="see-also"></a>Siehe auch
 [Befehle &#40;XMLA&#41;](../../../analysis-services/xmla/xml-elements-commands/xml-elements-commands.md)  
  
  
