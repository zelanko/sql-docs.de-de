---
title: Hierarchy-Element (CSDLBI) | Microsoft-Dokumentation
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
ms.assetid: 9debb638-1b28-401b-9499-8f63943863e9
caps.latest.revision: 12
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: be67c3059f09beefae68d0264fd0316579344d64
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/02/2018
ms.locfileid: "37250790"
---
# <a name="hierarchy-element-csdlbi"></a>Hierarchy-Element (CSDLBI)
  Das Hierarchy-Element ist ein logischer Container für Felder in einer Tabelle, die miteinander verknüpft werden können, um eine Hierarchie zu bilden. Das Hierarchy-Element wird vom CSDL-Member-Element abgeleitet und wurde zur Unterstützung der in Business Intelligence-Datenmodellen erstellten Hierarchien erweitert.  
  
## <a name="elements-and-attributes"></a>Elemente und Attribute  
 In der folgenden Tabelle sind die Elemente und Attribute aufgeführt, die das Hierarchy-Element definieren.  
  
|Name|Ist erforderlich|Description|  
|----------|-----------------|-----------------|  
|Dokumentation|nein|Eine Beschreibung der Hierarchie.|  
|Ebene|ja|Eines oder mehrere Level-Elemente, mit denen die Spalten in der Hierarchie definiert werden.<br /><br /> Weitere Informationen finden Sie unter [Level-Element &#40;CSDLBI&#41;](level-element-csdlbi.md).|  
  
## <a name="remarks"></a>Hinweise  
 In Tabellenmodellen werden Hierarchien erstellt, indem Beziehungen zwischen über- und untergeordneten Elementen in Spalten derselben Tabelle angegeben werden. Weitere Informationen finden Sie unter [Hierarchien &#40;SSAS – tabellarisch&#41;](../../tabular-models/hierarchies-ssas-tabular.md).  
  
## <a name="example"></a>Beispiel  
 **Tabellarisch**  
  
 Im folgenden Beispiel wird in CSDLBI, Version 1.0, eine Hierarchie im AdventureWorks-Beispielmodell veranschaulicht, die der Tabelle Products hinzugefügt wurde.  
  
```  
  
<bi:Hierarchy Name="Categoryy">  
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
  
 Im folgenden Beispiel wird in CSDLBI, Version 1.1, eine Hierarchie aus dem RetailOperations-Cube von Contoso veranschaulicht.  
  
```  
  
<bi:Hierarchy Name="Product_Hierarchy" Caption="Product Hierarchy" ReferenceName="Product Hierarchy">  
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
  
  
