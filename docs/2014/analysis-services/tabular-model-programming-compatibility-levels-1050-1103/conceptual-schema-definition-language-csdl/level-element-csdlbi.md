---
title: Level-Element (CSDLBI) | Microsoft-Dokumentation
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
ms.assetid: fdf75c47-77dc-4bdb-9931-8eca198fdb88
caps.latest.revision: 10
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 3fd89aaa69e8dc2b29b80ca82f89d1453dc44017
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/02/2018
ms.locfileid: "37211480"
---
# <a name="level-element-csdlbi"></a>Level-Element (CSDLBI)
  Das Level-Element ist ein komplexer Typ, der eine einzelne Ebene in einer Hierarchie definiert.  
  
## <a name="elements-and-attributes"></a>Elemente und Attribute  
 In der folgenden Tabelle sind die Elemente und Attribute aufgeführt, die das Level-Element definieren.  
  
|Name|Ist erforderlich|Description|  
|----------|-----------------|-----------------|  
|Quelle|ja|Ein Container für den Eigenschaftsverweis.|  
|PropertyRef|ja|Ein Verweis auf eine Instance-Eigenschaft. Andere Attribute der Ebene, wie Beschriftungen, Name oder Verweisname, können von dem Instance-Eigenschaft, auf die verwiesen wird, übernommen werden. In diesem Fall ist es nicht notwendig, diese im Level-Element anzugeben.|  
  
## <a name="remarks"></a>Hinweise  
 Weitere Informationen zu Hierarchien in Tabellenmodellen finden Sie unter [Hierarchy-Element &#40;CSDLBI&#41;](hierarchy-element-csdlbi.md).  
  
## <a name="example"></a>Beispiel  
 **Tabellarisch**  
  
 Das folgende Beispiel zeigt die Definition mehrerer Ebenen in einer Hierarchie des tabellarischen AdventureWorks-Modellbeispiels in CSDLBI, Version 1.1.  
  
```  
  
<bi:Hierarchy Name="Category">  
   <bi:Level Name="CategoryName">  
     <bi:Source>  
       <bi:PropertyRef Name="CategoryName" />  
     </bi:Source>  
   </bi:Level>  
   <bi:Level Name="ProductName">  
     <bi:Source>  
       <bi:PropertyRef Name="ProductName" />  
     </bi:Source>  
   </bi:Level>  
</bi:Hierarchy>  
```  
  
## <a name="example"></a>Beispiel  
 **Multidimensional**  
  
 Im folgenden Beispiel wird eine Hierarchie des Contoso-Vorgangscubes mit mehreren Ebenen in CSDLBI, Version 1.1, veranschaulicht.  
  
```  
<bi:Hierarchy   
   Name="Product_Hierarchy"   
   Caption="Product Hierarchy"   
   ReferenceName="Product Hierarchy">  
     <bi:Documentation>  
        <bi:Summary>DESCRIPTION_ProductModelCateg_Hierarchies</bi:Summary>  
     </bi:Documentation>  
  
     <bi:Level Name="ProductLine">  
        <bi:Source>  
        <bi:PropertyRef Name="ProductLine" />  
        </bi:Source>  
     </bi:Level>  
  
     <bi:Level Name="ModelName">  
        <bi:Source>  
        <bi:PropertyRef Name="ModelName" />  
        </bi:Source>  
     </bi:Level>  
</bi:Hierarchy>  
```  
  
## <a name="see-also"></a>Siehe auch  
 [Grundlegendes zum tabellarischen Objektmodell](../representation/understanding-tabular-object-model-at-levels-1050-through-1103.md)   
 [Grundlegendes zu Funktionen für über-/ Unterordnungshierarchien in DAX](https://msdn.microsoft.com/library/gg492192(v=sql.120).aspx)   
 [Konfigurieren der &#40;alle&#41; Ebene für Attributhierarchien](../../multidimensional-models/database-dimensions-configure-the-all-level-for-attribute-hierarchies.md)  
  
  
