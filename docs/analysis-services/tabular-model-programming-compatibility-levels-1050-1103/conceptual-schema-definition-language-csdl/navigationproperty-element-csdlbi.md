---
title: NavigationProperty-Element (CSDLBI) | Microsoft Docs
ms.date: 05/07/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: tabular-models
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 9db2facd93380fa3d0e011104bb95950e43340fb
ms.sourcegitcommit: c12a7416d1996a3bcce3ebf4a3c9abe61b02fb9e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/10/2018
---
# <a name="navigationproperty-element-csdlbi"></a>NavigationProperty-Element (CSDLBI)
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]
  Das NavigationProperty-Element ist ein komplexer Typ, der den CSDL-Elementtyp erweitert, um die Navigation in Business Intelligence-Datenmodellen zu unterstützen.  
  
> [!WARNING]  
>  Dieses Element dient der Berichterstellung und kann nicht geändert oder bearbeitet werden.  
  
## <a name="elements-and-attributes"></a>Elemente und Attribute  
 In der folgenden Tabelle sind die Elemente und Attribute aufgeführt, die das NavigationProperty-Element definieren.  
  
|Name|Ist erforderlich|Beschreibung|  
|----------|-----------------|-----------------|  
|CollectionCaption|Nein|Der Pluralname für den Verweis auf einen Satz von Instanzen der Navigationseigenschaft.<br /><br /> Wenn dieses Attribut weggelassen wird, wird das Caption-Attribut des base-Elements verwendet.|  
  
## <a name="example"></a>Beispiel  
 **Tabellarische**  
  
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
 **Mehrdimensionale**  
  
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
 [Informationen zum tabellarischen Objektmodell auf Kompatibilität Ebenen 1050 bis 1103](../../../analysis-services/tabular-model-programming-compatibility-levels-1050-1103/representation/understanding-tabular-object-model-at-levels-1050-through-1103.md)  
  
  
