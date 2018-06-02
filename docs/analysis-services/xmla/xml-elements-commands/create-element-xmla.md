---
title: Create-Element (XMLA) | Microsoft Docs
ms.date: 05/08/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: xmla
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 78cdf8b38828e8b9f96a89ffc026ec39ae40366b
ms.sourcegitcommit: 808d23a654ef03ea16db1aa23edab496b73e5072
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/02/2018
ms.locfileid: "34574572"
---
# <a name="create-element-xmla"></a>Create-Element (XMLA)
[!INCLUDE[ssas-appliesto-sqlas-aas](../../../includes/ssas-appliesto-sqlas-aas.md)]
  Enthält Analysis Services Scripting Language (ASSL)-Elementen, die verwendet werden, indem die **Execute** Methode zum Erstellen von Objekten auf einer Analysis Services-Instanz.  
  
## <a name="syntax"></a>Syntax  
  
```xml  
  
<Command>  
   <Create Scope="enum" AllowOverwrite="boolean">  
      <ParentObject>...</ParentObject>  
      <ObjectDefinition>...</ObjectDefinition>  
   </Create>  
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
|Untergeordnete Elemente|[ObjectDefinition](../../../analysis-services/xmla/xml-elements-properties/objectdefinition-element-xmla.md), [ParentObject](../../../analysis-services/xmla/xml-elements-properties/parentobject-element-xmla.md)|  
  
## <a name="attributes"></a>Attribute  
  
|attribute|Description|  
|---------------|-----------------|  
|AllowOverwrite|Optionales **Boolean** -Attribut. Wenn die Objekte auf "true" festgelegt, in definiert werden. die **ObjectDefinition** Element werden, vorhandene Objekte auf die [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] Instanz. Wenn dieses Attribut weggelassen oder auf "False" gesetzt wird, generiert das Vorhandensein eines existierenden Objekts einen Fehler.|  
|Bereich|Optionales **Enum** -Attribut. Definiert die Dauer der Objekte, die im **ObjectDefinition** -Element definiert sind. Wenn dieses Attribut weggelassen wird, definiert die Objekte der **ObjectDefinition** Element persistent auf der [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] Instanz. Der folgende Wert ist verfügbar:<br /><br /> *Sitzung*: die in definierten Objekte die **"objectdefinition"** Element nur für die Dauer des XML für Analysis (XMLA) Sitzung vorhanden sein.<br />                  Beachten Sie, dass bei Verwendung der *Sitzung* festlegen, die **ObjectDefinition** Element darf nur [Dimension](../../../analysis-services/scripting/objects/dimension-element-assl.md), [Cube](../../../analysis-services/scripting/objects/cube-element-assl.md), oder [MiningModel](../../../analysis-services/scripting/objects/miningmodel-element-assl.md) ASSL-Elemente.|  
  
## <a name="remarks"></a>Hinweise  
 Jeder **Create** -Vorgang erstellt unter einem vom **ParentObject** -Element gegebenen übergeordneten Element ein Hauptobjekt. Wenn das übergeordnete Objekt weggelassen wird, wird davon ausgegangen, dass es die Ziel-[!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]-Instanz ist. Dies generiert einen Fehler, wenn das übergeordnete Element eines Hauptobjekts nicht die Zielinstanz ist.  
  
## <a name="example"></a>Beispiel  
 Das folgende Beispiel erstellt eine leere Datenbank mit dem Namen **Testdatenbank** auf eine [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] Instanz.  
  
```  
  
      <Create xmlns="http://schemas.microsoft.com/analysisservices/2003/engine">  
   <ObjectDefinition>  
      <Database xmlns:xsd="http://www.w3.org/2001/XMLSchema" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance">  
         <Name>Test Database</Name>  
         <Description>A test database.</Description>  
      </Database>  
   </ObjectDefinition>  
</Create>  
```  
  
## <a name="see-also"></a>Siehe auch
 [Befehle &#40;XMLA&#41;](../../../analysis-services/xmla/xml-elements-commands/xml-elements-commands.md)  
  
  
