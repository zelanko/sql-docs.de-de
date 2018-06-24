---
title: Property-Element (CSDLBI) | Microsoft Docs
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
ms.assetid: f0770c5e-6420-4d0c-a5bf-b94eaf6877ca
caps.latest.revision: 7
author: mgblythe
ms.author: mblythe
manager: mblythe
ms.openlocfilehash: a4d1ab0082c4b5475e0fc54127e7b80f63a9b983
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/19/2018
ms.locfileid: "36059242"
---
# <a name="property-element-csdlbi"></a>Property-Element (CSDLBI)
  Das Eigenschaftselement in CSDLBI ist ein komplexer Typ, der Ergänzungen zum CSDL-Eigenschaftselement bereitstellt, um Business Intelligence-Datenmodelle zu unterstützen.  
  
## <a name="elements-and-attributes"></a>Elemente und Attribute  
 In der folgenden Tabelle sind die Elemente und Attribute aufgeführt, die das CSDLBI-Eigenschaftselement definieren.  
  
|Name|Ist erforderlich|Description|  
|----------|-----------------|-----------------|  
|Inhalt|nein|Eine Zeichenfolge, die die LCID der Anforderung enthält.|  
|DefaultAggregationFunction|ja|Eine Zeichenfolge, die die Aggregationsfunktion angibt, die verwendet werden soll, wenn Berechnungen mit dem Attribut ausgeführt werden und keine anderen Funktion angegeben wurde.<br /><br /> Falls nicht angegeben, wird die Standardaggregation für das Modell verwendet; dies ist i. d. R. SUM.|  
|GroupingBehavior|nein|Ein Wert, der angibt, wie Abfrageergebnisse gruppiert werden. Die Inhalte des Attributs werden vom einfachen Typ TGroupingBehavior definiert (siehe Tabelle unten).|  
|OrderBy|nein|Ein Verweis auf eine andere Eigenschaft im Modell, mit der die Sortierreihenfolge für die Werte der Eigenschaft definiert wird.<br /><br /> Die Werte für die beiden Eigenschaften SOLLTEN eine 1:1-Zuordnung haben. Andernfalls ist das Sortierverhalten nicht definiert.<br /><br /> Wenn dieses Element nicht angegeben wird, werden die Eigenschaften nach ihren Werten sortiert.|  
|Stability|nein|Ein Attribut, das die Stabilität der Eigenschaftswerte zwischen Aktualisierungsvorgängen angibt.<br /><br /> Dieses Attribut wird nicht vom Benutzer festgelegt, sondern von der Entwurfszeitumgebung nur für instabile Werte ausgegeben. Es wird immer auf Spalten angewendet, die eine Zeilennummer enthalten, sowie auf Spalten mit Formeln, die unbestimmte Ergebnisse generieren, beispielsweise NOW() oder RAND().<br /><br /> Die Werte für dieses Attribut werden in der Tabelle unten aufgeführt, die den Stabilitysimple-Typ beschreibt.|  
  
## <a name="groupingbehavior"></a>GroupingBehavior  
 In der folgenden Tabelle sind die Werte des einfachen Typs GroupingBehavior aufgeführt.  
  
|value|Description|  
|-----------|-----------------|  
|GroupOnValue|Gruppieren nach dem Wert des xthe-Attributs.|  
|GroupOnEntityKey|Gruppieren nach dem Entitätsschlüssel.|  
  
 Das folgende Beispiel veranschaulicht die Verwendung dieser beiden Werte. Angenommen, die Abfrage wurde entwickelt, um die Gehaltsabzüge für einen bestimmten Benutzer zurückzugeben, der mit Namen angegeben wurde. Wenn die Datenbank zwei Benutzer mit dem gleichen Namen, aber unterschiedlichen Datenbankbezeichnern enthält, würde sich das Abfrageergebniss je nach dem auf die Spalte angewendeten Attributwert unterscheiden:  
  
-   `GroupOnValue`: Die Abfrageergebnisse enthalten die Gehaltsabzüge von beider Benutzer zusammen.  
  
-   `GroupOnEntityKey`: Die Abfrageergebnisse enthalten die Gehaltsabzüge für jeden Benutzer separat.  
  
## <a name="stability"></a>Stability  
 In der folgenden Tabelle sind die Werte des einfachen Typs `Stability` aufgeführt.  
  
|value|Description|  
|-----------|-----------------|  
|Stabil|Die Eigenschaft bleibt zwischen Aktualisierungsvorgängen konstant.|  
|RowNumber|Die Eigenschaft enthält eine Zeilennummer.|  
|Flüchtig|Die Eigenschaft bleibt zwischen Aktualisierungsvorgängen möglicherweise nicht konstant.|  
  
## <a name="example"></a>Beispiel  
 **Tabellarisch**  
  
 Das folgende XML zeigt die Darstellung einiger Eigenschaften in CSDLBI, Version 1.1, im tabellarischen AdventureWorks-Modellbeispiel.  
  
```  
  
<EntityType   
   Name="DimEmployee">  
   <Key>  
      <PropertyRef   
      Name="RowNumber" />  
   </Key>  
  
   <Property   
      Name="RowNumber"   
      Type="Int64"   
      Nullable="false">  
   <bi:Property   
      Hidden="true"   
      Contents="RowNumber"   
      Stability="RowNumber" />  
   </Property>  
  
   <Property   
      Name="EmployeeKey"   
      Type="Int64">  
   <bi:Property />  
   </Property>  
….  
</bi:EntityType>  
</EntityType>  
  
```  
  
## <a name="example"></a>Beispiel  
 **Multidimensional**  
  
 Im folgenden Beispiel werden einige Eigenschaften für Spalten des Datenmodells in CSDLBI, Version 1.1, angezeigt, das den Contoso-Vorgangscube darstellt. Beachten Sie, dass BI-Anmerkungen nicht erforderlich sind bzw. auf die meisten Spalten nicht angewendet werden; die Anmerkungen werden nur für die Spalten verwendet, die eine besondere Behandlung in der Darstellungsschicht erfordern.  
  
```  
  
<EntityType   
   Name="Bike">  
  
   <Key>  
      <PropertyRef Name="RowNumber" />  
   </Key>  
  
   <Property   
      Name="RowNumber"   
      Type="Int64"   
      Nullable="false">  
   <bi:Property   
      Hidden="true"   
      Contents="RowNumber"   
      Stability="RowNumber"   
   />  
   </Property>  
  
   <Property   
      Name="ProductAlternateKey"   
      Type="String"   
      MaxLength="Max"   
      Unicode="true"   
      FixedLength="false">  
   <bi:Property />  
   </Property>  
  
```  
  
## <a name="see-also"></a>Siehe auch  
 [Technische Referenz für BI-Anmerkungen zu CSDL](technical-reference-for-bi-annotations-to-csdl.md)  
  
  