---
title: DisplayKey-Element (CSDLBI) | Microsoft-Dokumentation
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
ms.assetid: 7d881278-1e77-42e1-8cfc-f1bbd9ec2340
caps.latest.revision: 11
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: adcf9e8b2b87e0302158bbbf5652d8c32277170f
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/02/2018
ms.locfileid: "37297150"
---
# <a name="displaykey-element-csdlbi"></a>DisplayKey-Element (CSDLBI)
  Das DisplayKey-Element enthält eine Liste mit den folgenden Elementen, die einen starken Bezeichner bilden. DisplayKey ist nur als untergeordnetes Element des EntityType-Elements vorhanden. Das Element kann auf Spalten- oder Rollenenden verweisen.  
  
## <a name="elements-and-attributes"></a>Elemente und Attribute  
 In der folgenden Tabelle werden die im DisplayKey-Element enthaltenen Attribute aufgelistet.  
  
|Name|Ist erforderlich|Description|  
|----------|-----------------|-----------------|  
|IsDisplayKey|nein|True oder False|  
  
## <a name="remarks"></a>Hinweise  
 Dieses Element ist für Berichte bestimmt. Das Element, auf das Sie dieses Attribut anwenden, muss nicht der tatsächliche Tabellenschlüssel sein, sondern kann einem Element entsprechen, das Sie als Schlüssel darstellen. Allerdings muss die Spalte, die Sie für DisplayKey verwenden, eindeutige Werte enthalten.  
  
## <a name="example"></a>Beispiel  
 **Tabellarisch**  
  
 Im folgenden Beispiel wird in CSDLBI, Version 1.1, eine Spalte im AdventureWorks-Beispieldatenmodell veranschaulicht, die als DisplayKey für die Tabelle festgelegt wurde.  
  
```  
<sample in progress>  
```  
  
## <a name="example"></a>Beispiel  
 **Multidimensional**  
  
 Im folgenden Beispiel wird in CSDLBI, Version 1.1, ein Auszug aus der Darstellung des Contoso-Vorgangscube veranschaulicht. In diesem Modell ist die Spalte „Color“ als Anzeigeschlüssel für die Tabelle „Bikes“ gekennzeichnet.  
  
```  
  
<EntityType   
    Name="Bike">  
.. .. ..  
<Property   
    Name="Color"   
    Type="String"   
    MaxLength="Max"   
    Unicode="true"   
    FixedLength="false">  
<bi:Property   
    ContextualNameRule="Context"   
    Alignment="Left" Units="counts"   
    SortDirection="Descending"   
    IsRightToLeft="true"   
    DefaultAggregateFunction="Max" />  
</Property>  
.. .. ..  
<bi:EntityType>  
   <bi:DisplayKey>  
      <bi:MemberRef Name="Color" />  
   </bi:DisplayKey>>  
.. .. ..  
</bi:EntityType>  
</EntityType>  
```  
  
## <a name="see-also"></a>Siehe auch  
 [Grundlegendes zum tabellarischen Objektmodell](../representation/understanding-tabular-object-model-at-levels-1050-through-1103.md)   
 [CSDLBI-Konzepte](../csdlbi-concepts.md)  
  
  
