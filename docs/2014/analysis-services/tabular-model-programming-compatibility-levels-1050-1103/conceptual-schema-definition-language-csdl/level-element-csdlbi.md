---
title: Level-Element (CSDLBI) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.topic: reference
ms.assetid: fdf75c47-77dc-4bdb-9931-8eca198fdb88
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 8b932ac5fac719be29bda37f134f9beb06d1483f
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/02/2018
ms.locfileid: "48104780"
---
# <a name="level-element-csdlbi"></a>Level-Element (CSDLBI)
  Das Level-Element ist ein komplexer Typ, der eine einzelne Ebene in einer Hierarchie definiert.  
  
## <a name="elements-and-attributes"></a>Elemente und Attribute  
 In der folgenden Tabelle sind die Elemente und Attribute aufgeführt, die das Level-Element definieren.  
  
|Name|Ist erforderlich|Description|  
|----------|-----------------|-----------------|  
|Source|Benutzerkontensteuerung|Ein Container für den Eigenschaftsverweis.|  
|PropertyRef|Benutzerkontensteuerung|Ein Verweis auf eine Instance-Eigenschaft. Andere Attribute der Ebene, wie Beschriftungen, Name oder Verweisname, können von dem Instance-Eigenschaft, auf die verwiesen wird, übernommen werden. In diesem Fall ist es nicht notwendig, diese im Level-Element anzugeben.|  
  
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
  
  
