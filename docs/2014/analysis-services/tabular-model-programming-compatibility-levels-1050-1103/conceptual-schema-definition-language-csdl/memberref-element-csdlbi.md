---
title: MemberRef-Element (CSDLBI) | Microsoft-Dokumentation
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
ms.assetid: 399aaa34-896c-48e7-aacb-18564f31b568
caps.latest.revision: 4
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 3f308a9c890c36b5948c0f2c8a8468350c2e7cf4
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/02/2018
ms.locfileid: "37265266"
---
# <a name="memberref-element-csdlbi"></a>MemberRef-Element (CSDLBI)
  Das MemberRef-Element identifiziert den Namen einer Eigenschaft, die das Ziel eines Verweises ist.  
  
## <a name="elements-and-attributes"></a>Elemente und Attribute  
 In der folgenden Tabelle sind die Elemente und Attribute aufgeführt, die das MemberRef-Element definieren.  
  
|Name|Ist erforderlich|Description|  
|----------|-----------------|-----------------|  
|Name|ja|De Name der Eigenschaft, die in einem MemberRef-Element enthalten ist.|  
  
## <a name="memberrefs-element"></a>MemberRefs-Element  
 MemberRefs ist ein komplexer Typ, der eine Auflistung von Elementen definiert, die jeweils in einem MemberRef-Element enthalten sind.  
  
 In der folgenden Tabelle sind die Elemente und Attribute des MemberRefs-Typs aufgeführt.  
  
|Name|Ist erforderlich|Description|  
|----------|-----------------|-----------------|  
|MemberRef|ja|Eine Zeichenfolge, die den Parameterverweis enthält.|  
  
## <a name="example"></a>Beispiel  
 **Tabellarisch**  
  
 Im folgenden Beispiel wird in CSDLBI, Version 1.1, ein Teil des AdventureWorks-Beispieldatenmodells dargestellt, das die Products-Tabelle definiert. Hier wird das MemberRef-Element für alle Spalten verwendet, die im Standardfeldsatz für das Modell enthalten sind.  
  
```  
  
<bi:EntityType>  
   <bi:DefaultDetails>  
     <bi:MemberRef Name="Color" />  
     <bi:MemberRef Name="DealerPrice" />  
     <bi:MemberRef Name="Status" />  
   </bi:DefaultDetails>  
  
```  
  
## <a name="example"></a>Beispiel  
 **Multidimensional**  
  
 Im folgenden Beispiel wird in CSDLBI, Version 1.1, ein Teil des Contoso-Vorgangscube dargestellt, der die Bike-Tabelle definiert. In diesem Beispiel wird ein MemberRef-Element verwendet, um den Namen der Spalte angeben, die in Berichten als Standardfeldsatz verwendet wird. Mithilfe eines weiteren MemberRef-Elements wird auf die Spalte verwiesen, die die Sortierreihenfolge bereitstellt.  
  
```  
  
<bi:DefaultDetails>  
   <bi:MemberRef Name="Color" />  
</bi:DefaultDetails>  
  
<bi:SortMembers>  
   <bi:MemberRef Name="Color" />  
</bi:SortMembers>  
  
```  
  
## <a name="see-also"></a>Siehe auch  
 [Technische Referenz für BI-Anmerkungen zu CSDL](technical-reference-for-bi-annotations-to-csdl.md)  
  
  
