---
title: Property-Element (CSDLBI) | Microsoft Docs
ms.date: 05/07/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: tabular-models
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 48262a12e13f548e96e765b785b85f556419ff24
ms.sourcegitcommit: c12a7416d1996a3bcce3ebf4a3c9abe61b02fb9e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/10/2018
ms.locfileid: "34041134"
---
# <a name="property-element-csdlbi"></a>Property-Element (CSDLBI)
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]
  Das Eigenschaftselement in CSDLBI ist ein komplexer Typ, der Ergänzungen zum CSDL-Eigenschaftselement bereitstellt, um Business Intelligence-Datenmodelle zu unterstützen.  
  
## <a name="elements-and-attributes"></a>Elemente und Attribute  
 In der folgenden Tabelle sind die Elemente und Attribute aufgeführt, die das CSDLBI-Eigenschaftselement definieren.  
  
|Name|Ist erforderlich|Beschreibung|  
|----------|-----------------|-----------------|  
|Inhalt|Nein|Eine Zeichenfolge, die die LCID der Anforderung enthält.|  
|DefaultAggregationFunction|ja|Eine Zeichenfolge, die die Aggregationsfunktion angibt, die verwendet werden soll, wenn Berechnungen mit dem Attribut ausgeführt werden und keine anderen Funktion angegeben wurde.<br /><br /> Falls nicht angegeben, wird die Standardaggregation für das Modell verwendet; dies ist i. d. R. SUM.|  
|GroupingBehavior|Nein|Ein Wert, der angibt, wie Abfrageergebnisse gruppiert werden. Die Inhalte des Attributs werden vom einfachen Typ TGroupingBehavior definiert (siehe Tabelle unten).|  
|OrderBy|Nein|Ein Verweis auf eine andere Eigenschaft im Modell, mit der die Sortierreihenfolge für die Werte der Eigenschaft definiert wird.<br /><br /> Die Werte für die beiden Eigenschaften SOLLTEN eine 1:1-Zuordnung haben. Andernfalls ist das Sortierverhalten nicht definiert.<br /><br /> Wenn dieses Element nicht angegeben wird, werden die Eigenschaften nach ihren Werten sortiert.|  
|Stability|Nein|Ein Attribut, das die Stabilität der Eigenschaftswerte zwischen Aktualisierungsvorgängen angibt.<br /><br /> Dieses Attribut wird nicht vom Benutzer festgelegt, sondern von der Entwurfszeitumgebung nur für instabile Werte ausgegeben. Es wird immer auf Spalten angewendet, die eine Zeilennummer enthalten, sowie auf Spalten mit Formeln, die unbestimmte Ergebnisse generieren, beispielsweise NOW() oder RAND().<br /><br /> Die Werte für dieses Attribut werden in der Tabelle unten aufgeführt, die den Stabilitysimple-Typ beschreibt.|  
  
## <a name="groupingbehavior"></a>GroupingBehavior  
 In der folgenden Tabelle sind die Werte des einfachen Typs GroupingBehavior aufgeführt.  
  
|Wert|Beschreibung|  
|-----------|-----------------|  
|GroupOnValue|Gruppieren nach dem Wert des xthe-Attributs.|  
|GroupOnEntityKey|Gruppieren nach dem Entitätsschlüssel.|  
  
 Das folgende Beispiel veranschaulicht die Verwendung dieser beiden Werte. Angenommen, die Abfrage wurde entwickelt, um die Gehaltsabzüge für einen bestimmten Benutzer zurückzugeben, der mit Namen angegeben wurde. Wenn die Datenbank zwei Benutzer mit dem gleichen Namen, aber unterschiedlichen Datenbankbezeichnern enthält, würde sich das Abfrageergebniss je nach dem auf die Spalte angewendeten Attributwert unterscheiden:  
  
-   **GroupOnValue**: Die Abfrageergebnisse enthalten die Summe der Gehaltsabzüge beider Benutzer.  
  
-   **GroupOnEntityKey**: Die Abfrageergebnisse enthalten die Gehaltsabzüge für jeden Benutzer separat.  
  
## <a name="stability"></a>Stability  
 In der folgenden Tabelle sind die Werte des einfachen Typs **Stability** aufgeführt.  
  
|Wert|Beschreibung|  
|-----------|-----------------|  
|Stabil|Die Eigenschaft bleibt zwischen Aktualisierungsvorgängen konstant.|  
|RowNumber|Die Eigenschaft enthält eine Zeilennummer.|  
|Flüchtig|Die Eigenschaft bleibt zwischen Aktualisierungsvorgängen möglicherweise nicht konstant.|  
  
## <a name="example"></a>Beispiel  
 **Tabellarische**  
  
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
 **Mehrdimensionale**  
  
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
 [Technische Referenz für BI-Anmerkungen zu CSDL](../../../analysis-services/tabular-model-programming-compatibility-levels-1050-1103/conceptual-schema-definition-language-csdl/technical-reference-for-bi-annotations-to-csdl.md)  
  
  
