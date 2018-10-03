---
title: Create-Element (XMLA) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.topic: reference
api_name:
- Create Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- http://schemas.microsoft.com/analysisservices/2003/engine#Create
- urn:schemas-microsoft-com:xml-analysis#Create
- microsoft.xml.analysis.create
helpviewer_keywords:
- Create command (XMLA)
ms.assetid: a623d362-a1ac-40e4-8816-65fac89cb391
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: b64f6b222793fdd7c6b92e7462fc10976c0bc139
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/02/2018
ms.locfileid: "48051290"
---
# <a name="create-element-xmla"></a>Create-Element (XMLA)
  Enthält Analysis Services Scripting Language (ASSL)-Elemente, die verwendet werden, indem die `Execute` Methode zum Erstellen von Objekten in einem [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] Instanz.  
  
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
|Datentyp und -länge|None|  
|Standardwert|None|  
|Cardinality|0-n: Optionales Element, das mehr als einmal auftreten kann.|  
  
## <a name="element-relationships"></a>Elementbeziehungen  
  
|Beziehung|Element|  
|------------------|-------------|  
|Übergeordnete Elemente|[Befehl](../xml-elements-properties/command-element-xmla.md)|  
|Untergeordnete Elemente|[ObjectDefinition](../xml-elements-properties/objectdefinition-element-xmla.md), [ParentObject](../xml-elements-properties/object-element-xmla.md)|  
  
## <a name="attributes"></a>Attribute  
  
|attribute|Description|  
|---------------|-----------------|  
|AllowOverwrite|Optionale `Boolean` Attribut. Bei Festlegung auf "True" können die Objekte, die im `ObjectDefinition`-Element definiert werden, vorhandene Objekte auf der [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]-Instanz überschreiben. Wenn dieses Attribut weggelassen oder auf "False" gesetzt wird, generiert das Vorhandensein eines existierenden Objekts einen Fehler.|  
|Bereich|Optionale `Enum` Attribut. Definiert die Dauer der Objekte, die der `ObjectDefinition` Element. Wenn dieses Attribut weggelassen wird, die Objekte definiert, der `ObjectDefinition` Element werden beibehalten, auf die [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] Instanz. Die folgenden Werte sind verfügbar:<br /><br /> -   *Sitzung*<br />     Die im `ObjectDefinition`-Element definierten Objekte existieren nur während der Dauer der XMLA-Sitzung (XML for Analysis). **Hinweis:** bei Verwendung der *Sitzung* festlegen, die `ObjectDefinition` Element darf nur [Dimension](../../scripting/objects/dimension-element-assl.md), [Cube](../../scripting/objects/cube-element-assl.md), oder [MiningModel ](../../scripting/objects/miningmodel-element-assl.md) ASSL-Elemente.|  
  
## <a name="remarks"></a>Hinweise  
 Jede `Create` Vorgang erstellt ein Hauptobjekt, das unter einem übergeordneten Element angegeben wird, indem die `ParentObject` Element. Wenn das übergeordnete Objekt weggelassen wird, wird davon ausgegangen, dass es die Ziel-[!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]-Instanz ist. Dies generiert einen Fehler, wenn das übergeordnete Element eines Hauptobjekts nicht die Zielinstanz ist.  
  
## <a name="example"></a>Beispiel  
 Im folgenden Beispiel wird eine leere Datenbank mit dem Namen `Test Database` auf einer [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]-Instanz erstellt.  
  
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
 [Befehle &#40;XMLA&#41;](xml-elements-commands.md)  
  
  
