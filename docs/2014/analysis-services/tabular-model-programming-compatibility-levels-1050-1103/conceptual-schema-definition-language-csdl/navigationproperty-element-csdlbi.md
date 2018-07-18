---
title: NavigationProperty-Element (CSDLBI) | Microsoft-Dokumentation
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
ms.assetid: a36b4d3b-6a6c-489b-8a46-2e6b925b568f
caps.latest.revision: 9
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 24fe0a9aab029226757cc84ef70e4e8da898e9c5
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/02/2018
ms.locfileid: "37287966"
---
# <a name="navigationproperty-element-csdlbi"></a>NavigationProperty-Element (CSDLBI)
  Das NavigationProperty-Element ist ein komplexer Typ, der den CSDL-Elementtyp erweitert, um die Navigation in Business Intelligence-Datenmodellen zu unterstützen.  
  
> [!WARNING]  
>  Dieses Element dient der Berichterstellung und kann nicht geändert oder bearbeitet werden.  
  
## <a name="elements-and-attributes"></a>Elemente und Attribute  
 In der folgenden Tabelle sind die Elemente und Attribute aufgeführt, die das NavigationProperty-Element definieren.  
  
|Name|Ist erforderlich|Description|  
|----------|-----------------|-----------------|  
|CollectionCaption|nein|Der Pluralname für den Verweis auf einen Satz von Instanzen der Navigationseigenschaft.<br /><br /> Wenn dieses Attribut weggelassen wird, wird das Caption-Attribut des base-Elements verwendet.|  
  
## <a name="example"></a>Beispiel  
 **Tabellarisch**  
  
 Das folgende Beispiel zeigt eine Navigationseigenschaft in CSDLBI, Version 1.1, die die Verknüpfung zwischen der „Product SubCategory“-Tabelle und der „Product“-Tabelle beschreibt.  
  
```  
  
<NavigationProperty   
    Name="Product_Sub_Category_ProductSubcategoryKey"      
    Relationship="Sandbox.Product_Product_Sub_Category_Product_Sub_Category_ProductSubcategoryKey"  
     FromRole="Product_ProductSubcategoryKey"   
    ToRole="Product_Sub_Category_ProductSubcategoryKey">  
<bi:NavigationProperty   
     ReferenceName="Product Sub-Category_ProductSubcategoryKey" />  
</NavigationProperty>  
```  
  
## <a name="example"></a>Beispiel  
 **Multidimensional**  
  
 Das folgende Beispiel zeigt eine Navigationseigenschaft in CSDLBI, Version 1.1, an, die die Beziehung zwischen zwei Tabellen im Contoso-Vorgangscube beschreibt. Die Beziehung verbindet die „Bike Category“-Tabelle und die „Product Subcategory“-Tabelle.  
  
```  
  
<NavigationProperty   
     Name="BikeSubcategory_ProductSubcategoryKey"   
     Relationship="Sandbox.Bike_BikeSubcategory_BikeSubcategory_ProductSubcategoryKey"   
     FromRole="Bike_ProductSubcategoryKey"   
     ToRole="BikeSubcategory_ProductSubcategoryKey">  
   <bi:NavigationProperty />  
</NavigationProperty>  
```  
  
## <a name="see-also"></a>Siehe auch  
 [Grundlegendes zum tabellarischen Objektmodell](../representation/understanding-tabular-object-model-at-levels-1050-through-1103.md)  
  
  
