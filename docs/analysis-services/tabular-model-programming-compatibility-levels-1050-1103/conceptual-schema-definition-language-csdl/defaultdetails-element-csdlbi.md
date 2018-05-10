---
title: DefaultDetails-Element (CSDLBI) | Microsoft Docs
ms.date: 05/07/2018
ms.prod: sql
ms.technology: analysis-services
ms.component: tabular-models
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 6d64d654ba9bd863c5497bb3c38864c641d7573d
ms.sourcegitcommit: 1aedef909f91dc88dc741748f36eabce3a04b2b1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/08/2018
---
# <a name="defaultdetails-element-csdlbi"></a>DefaultDetails-Element (CSDLBI)
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]
  Das DefaultDetails-Element stellt eine Liste mit Eigenschaftsverweisen dar, die zusammen den "Standardfeldsatz" von Spalten in der Tabelle definieren. Jede Eigenschaft kann nur auf ein Measure oder auf eine Spalte verweisen.  
  
## <a name="elements-and-attributes"></a>Elemente und Attribute  
 In der folgenden Tabelle sind die Elemente und Attribute aufgeführt, die das DefaultDetails-Element definieren.  
  
|Name|Ist erforderlich|Beschreibung|  
|----------|-----------------|-----------------|  
|DefaultDetailsPosition|Nein|Eine positive ganze Zahl, die das Vorhandensein und die Position in der Auflistung angibt.|  
  
## <a name="example"></a>Beispiel  
 **Tabellarische**  
  
 Im folgenden Beispiel wird in CSDLBI, Version 1.1, ein Auszug aus dem AdventureWorks-Beispieldatenmodell dargestellt. Es ist nur eine Standardspalte für die Tabelle Employees festgelegt (Title). Für die Tabelle Produkte wurden jedoch drei Spalten als Standardfeldsatz definiert.  
  
```  
  
<EntityType   
    Name="DimEmployee">  
....  
   <bi:DefaultDetails>  
      <bi:MemberRef Name="Title" />  
   </bi:DefaultDetails>  
.....  
<EntityType   
    Name="Products">  
.....  
   <bi:DefaultDetails>  
      <bi:MemberRef Name="Color" />  
      <bi:MemberRef Name="DealerPrice" />  
      <bi:MemberRef Name="Status" />  
   </bi:DefaultDetails>  
  
```  
  
## <a name="example"></a>Beispiel  
 **Mehrdimensionale**  
  
 Im folgenden Beispiel wird in CSDLBI, Version 1.1, ein Auszug aus der Definition der Tabelle Bike im Contoso-Vorgangscube veranschaulicht. Diese Anmerkung gibt an, dass die Spalte Color standardmäßig angezeigt werden soll, wenn keine andere Anzeigenspalte angegeben wird.  
  
```  
  
<EntityType Name="Bike">  
   <Key>  
   <PropertyRef Name="RowNumber" />  
   </Key>  
....  
<bi:EntityType>  
   <bi:DisplayKey>  
      <bi:MemberRef Name="Color" />  
   </bi:DisplayKey>  
   <bi:DefaultDetails>  
      <bi:MemberRef Name="Color" />  
   </bi:DefaultDetails>  
   <bi:SortMembers>  
      <bi:MemberRef Name="Color" />  
   </bi:SortMembers>  
....  
</bi:EntityType>  
</EntityType>  
```  
  
## <a name="see-also"></a>Siehe auch  
 [Informationen zum tabellarischen Objektmodell auf Kompatibilität Ebenen 1050 bis 1103](../../../analysis-services/tabular-model-programming-compatibility-levels-1050-1103/representation/understanding-tabular-object-model-at-levels-1050-through-1103.md)   
 [CSDLBI-Konzepte](../../../analysis-services/tabular-model-programming-compatibility-levels-1050-1103/csdlbi-concepts.md)  
  
  
