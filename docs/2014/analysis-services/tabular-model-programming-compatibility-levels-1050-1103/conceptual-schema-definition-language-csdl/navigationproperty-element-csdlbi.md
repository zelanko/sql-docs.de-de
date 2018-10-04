---
title: NavigationProperty-Element (CSDLBI) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.topic: reference
ms.assetid: a36b4d3b-6a6c-489b-8a46-2e6b925b568f
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: fbb0d38a4bcab7592893aaa63acb1bbb96dac5c3
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/02/2018
ms.locfileid: "48157580"
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
  
  
