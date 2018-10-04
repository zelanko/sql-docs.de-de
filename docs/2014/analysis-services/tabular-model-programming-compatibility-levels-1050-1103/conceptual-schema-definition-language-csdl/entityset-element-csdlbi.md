---
title: EntitySet-Element (CSDLBI) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.topic: reference
ms.assetid: d4703c9e-5594-472e-a85b-0f5bd0d73d6f
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: dabe6cf0748f220fcef7bfb9b2577426c7ff65a2
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/02/2018
ms.locfileid: "48091630"
---
# <a name="entityset-element-csdlbi"></a>EntitySet-Element (CSDLBI)
  Das EntitySet-Element definiert eine Auflistung von Entitäten eines bestimmten Typs in einem CSDLBI-Datenmodell.  
  
 Das EntitySet muss jeden der Entitätstypen angeben, die im Datenmodell enthalten sind. Informationen zu diesen Modellentitäten werden anhand der Auflistung von untergeordneten Entitäten des Typs (Entitätselement) angegeben. Weitere Informationen finden Sie unter [EntityType-Element &#40;CSDLBI&#41;](entitytype-element-csdlbi.md).  
  
 Eigenschaften wie Sortierung und Sprache werden auf der EntityContainer-Ebene und nicht auf Ebene einzelner Objekte definiert. Spalten und Textattribute innerhalb des Modells können jedoch über Beschriftungen oder Übersetzungen in anderen Sprachen verfügen.  
  
## <a name="elements-and-attributes"></a>Elemente und Attribute  
 In der folgenden Tabelle sind die Elemente und Attribute aufgelistet, die ein EntitySet definieren.  
  
|Attributname|Ist erforderlich|Description|  
|--------------------|-----------------|-----------------|  
|Beschriftung|nein|Eine benutzerfreundliche Beschreibung der Entitätenmenge.|  
|CollectionCaption|nein|Eine Zeichenfolge, die den Namen der Entität im Plural enthält.|  
|ReferenceName|nein|Enthält den nicht zusammengeführten und vollqualifizierten Namen der Entität. In einem mehrdimensionalen Modell entspricht dies dem CubeDimensions-Namen.|  
|Ausgeblendet|nein|Gibt an, ob das die Entität ausgeblendet ist. Standardmäßig werden Entitäten nicht ausgeblendet.|  
  
## <a name="example"></a>Beispiel  
 **Tabellarisch**  
  
 Im folgenden Beispiel werden die Definitionen der Date- und der Geography-Tabelle aus dem tabellarischen AdventureWorks-Modell in CSDLBI, Version 1.1, veranschaulicht.  
  
```  
  
<EntitySet   
   Name="Date"   
   EntityType="Sandbox. Date">  
<bi:EntitySet />  
</EntitySet>  
  
<EntitySet   
   Name="Geography"   
   EntityType="Sandbox.Geography">  
<bi:EntitySet />  
</EntitySet>  
```  
  
## <a name="example"></a>Beispiel  
 **Multidimensional**  
  
 Im folgenden Beispiel werden einige EntitySet-Elemente aus dem Contoso Retail Operations-Cube in CSDLBI, Version 1.1, veranschaulicht.  
  
```  
  
<EntitySet Name="Outage" EntityType="Sandbox.Outage">  
       <bi:EntitySet />  
</EntitySet>  
  
<EntitySet Name="Store" EntityType="Sandbox.Store">  
     <bi:EntitySet />  
</EntitySet>  
```  
  
## <a name="see-also"></a>Siehe auch  
 [Technische Referenz für BI-Anmerkungen zu CSDL](technical-reference-for-bi-annotations-to-csdl.md)  
  
  
