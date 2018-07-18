---
title: DefaultDetails-Element (CSDLBI) | Microsoft-Dokumentation
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
ms.assetid: 05a08baa-23cc-4011-9c2e-f60a20bb87da
caps.latest.revision: 12
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 708e829f1af3ebc9d727e3abfd6643913cd460f2
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/02/2018
ms.locfileid: "37330230"
---
# <a name="defaultdetails-element-csdlbi"></a>DefaultDetails-Element (CSDLBI)
  Das DefaultDetails-Element stellt eine Liste mit Eigenschaftsverweisen dar, die zusammen den "Standardfeldsatz" von Spalten in der Tabelle definieren. Jede Eigenschaft kann nur auf ein Measure oder auf eine Spalte verweisen.  
  
## <a name="elements-and-attributes"></a>Elemente und Attribute  
 In der folgenden Tabelle sind die Elemente und Attribute aufgeführt, die das DefaultDetails-Element definieren.  
  
|Name|Ist erforderlich|Description|  
|----------|-----------------|-----------------|  
|DefaultDetailsPosition|nein|Eine positive ganze Zahl, die das Vorhandensein und die Position in der Auflistung angibt.|  
  
## <a name="example"></a>Beispiel  
 **Tabellarisch**  
  
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
 **Multidimensional**  
  
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
 [Grundlegendes zum tabellarischen Objektmodell](../representation/understanding-tabular-object-model-at-levels-1050-through-1103.md)   
 [CSDLBI-Konzepte](../csdlbi-concepts.md)  
  
  
