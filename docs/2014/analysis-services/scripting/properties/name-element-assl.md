---
title: Name-Element (ASSL) | Microsoft Docs
ms.custom: ''
ms.date: 03/08/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
api_name:
- Name Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- Name
helpviewer_keywords:
- Name element
ms.assetid: caf2af86-5f9c-4e14-8168-f3a79248b4fe
caps.latest.revision: 39
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: cb2185d9d2a87a2abc3ebb96ad8186fe288e6190
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/19/2018
ms.locfileid: "36061248"
---
# <a name="name-element-assl"></a>Name-Element (ASSL)
  Enthält den Namen des übergeordneten Elements.  
  
## <a name="syntax"></a>Syntax  
  
```xml  
  
<Action> <!-- or one of the elements listed below in the Element Relationships table -->  
   ...  
   <Name>...</Name>  
   ...  
</Action>  
```  
  
## <a name="element-characteristics"></a>Elementmerkmale  
  
|Merkmal|Description|  
|--------------------|-----------------|  
|Datentyp und -länge|Zeichenfolge (bis zu 100 Zeichen)|  
|Standardwert|Unterschiedlich|  
|Cardinality|1-1: Erforderliches Element, das nur einmal auftritt|  
  
## <a name="element-relationships"></a>Elementbeziehungen  
  
|Beziehung|Element|  
|------------------|-------------|  
|Übergeordnete Elemente|[Action](../objects/action-element-assl.md), [Aggregation](../objects/aggregation-element-assl.md), [AggregationDesign](../objects/aggregationdesign-element-assl.md), [AlgorithmParameter](../objects/algorithmparameter-element-assl.md), [Annotation](../objects/annotation-element-assl.md), [Assembly](../objects/assembly-element-assl.md), [ClrAssemblyFile](../data-type/clrassemblyfile-data-type-assl.md), [Cube](../objects/cube-element-assl.md), [CubeDimension](../data-type/dimension-data-type-assl.md), [CubeHierarchy](../data-type/hierarchy-data-type-assl.md), [Database](../objects/database-element-assl.md), [DataSource](../objects/datasource-element-assl.md), [DataSourceView](../objects/datasourceview-element-assl.md), [Dimension](../objects/dimension-element-assl.md), [DimensionAttribute](../data-type/dimensionattribute-data-type-assl.md), [Group](../objects/group-element-assl.md), [Hierarchy](../objects/hierarchy-element-assl.md), [Kpi](../objects/kpi-element-assl.md), [Level](../objects/level-element-assl.md), [MdxScript](../objects/mdxscript-element-assl.md), [Measure](../objects/measure-element-assl.md), [MeasureGroup](../objects/measuregroup-element-assl.md), [MemberProperty](../objects/attributerelationship-element-assl.md), [MiningModel](../objects/miningmodel-element-assl.md), [MiningModelColumn](../data-type/miningmodelcolumn-data-type-assl.md), [MiningStructure](../objects/miningstructure-element-assl.md), [MiningStructureColumn](../data-type/miningstructurecolumn-data-type-assl.md), [Partition](../objects/partition-element-assl.md), [Permission](../data-type/permission-data-type-assl.md), [Perspective](../objects/perspective-element-assl.md), [PerspectiveCalculation](../data-type/perspectivecalculation-data-type-assl.md), [ReportFormatParameter](../objects/reportformatparameter-element-asl.md), [ReportParameter](../objects/reportparameter-element-assl.md), [Role](../objects/role-element-assl.md), [Server](../objects/server-element-assl.md), [ServerProperty](../objects/serverproperty-element-assl.md), [Trace](../objects/trace-element-assl.md)|  
|Untergeordnete Elemente|InclusionThresholdSetting|  
  
## <a name="remarks"></a>Hinweise  
 Jedes Element, das zum Definieren eines Objekts (einer Instanz von [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)], einer Hierarchie, eines Attributs usw.) verwendet wird, verfügt über ein `Name`-Element als Eigenschaft. Der Wert eines `Name`-Elements hat die folgenden Einschränkungen:  
  
-   Der Wert darf keine führenden oder nachgestellten Leerzeichen enthalten. Wenn der Wert eines `Name`-Elements führende oder nachgestellte Leerzeichen enthält, werden diese Leerzeichen implizit von [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] entfernt.  
  
-   Der Wert sollte keine Steuerzeichen enthalten. Es wird dringend von Steuerzeichen in einem Namen abgeraten, da dies in einigen Fällen zu XML-Überprüfungsfehlern führen kann.  
  
     Für Objekte erstellt, mit der `GetNewName` Methode in [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)], AMO sucht und entfernt diese anschließend alle Steuerzeichen sowie führende oder nachfolgende Leerzeichen im Namen. Für diesen Grund mit `GetNewName` ist die empfohlene Vorgehensweise zum Festlegen von Objektnamen.  
  
     Beim direkten Festlegen der `Name`-Eigenschaft werden jedoch nicht die gleichen Überprüfungen ausgeführt, was zu XML-Überprüfungsfehlern führen kann. Ob ein Fehler tatsächlich auftritt, hängt davon ab, welches Steuerzeichen im Namen vorkommt.  
  
     Obwohl in Objektnamen grundsätzlich auf Steuerzeichen verzichtet werden sollte, wird deren Verwendung von Analysis Services nicht ausdrücklich untersagt. Von früheren Analysis Services-Versionen wurden manchmal Steuerzeichen in Objektnamen akzeptiert. Aus diesem Grund [!INCLUDE[ssASCurrent](../../../includes/ssascurrent-md.md)] Steuerzeichen in Objektnamen, um zu vermeiden, dass ältere Lösungen werden ignoriert.  
  
-   Die folgenden reservierten Werte können nicht verwendet werden:  
  
    -   AUX  
  
    -   CLOCK$  
  
    -   COM1 bis COM9 (COM1, COM2, COM3 usw.)  
  
    -   CON  
  
    -   LPT1 bis LPT9 (LPT1, LPT2, LPT3 usw.)  
  
    -   NUL  
  
    -   PRN  
  
 Die folgende Tabelle enthält zusätzliche Zeichen, die im Wert verwendet werden können ein `Name` -Element, abhängig vom übergeordneten Element.  
  
|Übergeordnetes Element|Ungültige Zeichen|  
|--------------------|------------------------|  
|[Server](../objects/server-element-assl.md)|Der Name muss den Regeln für [!INCLUDE[msCoName](../../../includes/msconame-md.md)] Windows-Computernamen. IP-Adressen sind nicht gültig.|  
|[DataSource](../objects/datasource-element-assl.md)|:/\\*&#124;?" () []{}<>|  
|[Ebene](../objects/level-element-assl.md), [-Attribut-Element](../objects/attribute-element-assl.md)|.,;' `:/\\*&#124;?" & % $! += []{}<>|  
|Alle anderen übergeordneten Elemente|.,;' `:/\\*&#124;?" & % $!:: Operator += () []{}<>|  
  
## <a name="see-also"></a>Siehe auch  
 [ID-Element &#40;ASSL&#41;](id-element-assl.md)   
 [Eigenschaften &#40;ASSL&#41;](properties-assl.md)  
  
  