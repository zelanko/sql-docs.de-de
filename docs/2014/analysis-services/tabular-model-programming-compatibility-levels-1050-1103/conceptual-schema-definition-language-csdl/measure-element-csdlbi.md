---
title: Measure-Element (CSDLBI) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.topic: reference
ms.assetid: bfbc9274-053a-421a-bb81-2095bba710be
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: de02e5c0233fb5cb1699f038b87871c8757f0256
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/02/2018
ms.locfileid: "48068400"
---
# <a name="measure-element-csdlbi"></a>Measure-Element (CSDLBI)
  Das Measure-Element ist ein komplexer Typ, der auf dem CSDL-Eigenschaftselement basiert. Die CSDLBI-Anmerkungen fügen Attribute hinzu, die die Definition von komplexen Formeln für Business Intelligence-Datenmodelle unterstützen.  
  
## <a name="elements-and-attributes"></a>Elemente und Attribute  
 In der nachfolgenden Tabelle werden die Elemente und Attribute aufgeführt, die das Measure-Element definieren; darüber hinaus werden alle Attribute für das Eigenschaftselement aufgeführt.  
  
|Name|Ist erforderlich|Description|  
|----------|-----------------|-----------------|  
|Kpi|nein|Erforderliches Element nur für Measures, die als KPI verwendet werden. Nicht alle Measures sind KPIs, aber alle KPIs müssen auf der Definition eines Measures basieren.<br /><br /> [KPI-Element &#40;CSDLBI&#41;](kpi-element-csdlbi.md)|  
|IsSimpleMeasure|nein|Ein true/false-Wert, der angibt, ob die Formel, die im Measure verwendet wird, eine einfache Aggregationen ist (SUM, COUNT, MIN, MAX, AVG, DistinctCount).<br /><br /> Der Standardwert ist true.|  
  
## <a name="example"></a>Beispiel  
 **Tabellarisch**  
  
 Das folgende Beispiel veranschaulicht zwei Measures aus dem tabellarischen AdventureWorks-Modellbeispiel in CSDLBI, Version 1.1. Das zweite Measure wurde durch das Hinzufügen von KPI-Elementen in einen KPI konvertiert.  
  
```  
  
<Property   
    Name="Order_Lines_Count"   
    Type="Int64">  
<bi:Measure   
    Caption="Order Lines Count"   
    ReferenceName="Order Lines Count"   
    Width="0"   
    IsSimpleMeasure="false" />  
</Property>  
  
<Property   
    Name="Total_Current_Quarter_Sales_Performance"   
    Type="Double">  
<bi:Measure   
    Caption="Total Current Quarter Sales Performance"   
    ReferenceName="Total Current Quarter Sales Performance"   
    Width="0"   
    IsSimpleMeasure="false">  
    <bi:Kpi   
    StatusGraphic="Three Signs Colored">  
      <bi:KpiGoal>  
        <bi:PropertyRef Name="Measures___Total_Current_Quarter_Sales_Performance_Goal_" />  
      </bi:KpiGoal>  
      <bi:KpiStatus>  
        <bi:PropertyRef Name="Measures___Total_Current_Quarter_Sales_Performance_Status_" />  
      </bi:KpiStatus>  
    </bi:Kpi>  
  </bi:Measure>  
</Property>  
```  
  
## <a name="example"></a>Beispiel  
 **Multidimensiona;**  
  
 Im folgenden Beispiel wird ein Measure aus dem Contoso-Vorgangscube in CSDLBI, Version 1.1, veranschaulicht, das als KPI verwendet wird.  
  
```  
  
<Property   
    Name="Sum_of_SalesAmount"   
    Type="Decimal" Precision="19" Scale="4">  
<Documentation>  
<Summary>KPI Description</Summary>  
</Documentation>  
<bi:Measure   
    Caption="Sum of SalesAmount"   
    ReferenceName="Sum of SalesAmount"   
    FormatString="\$#,0.00;(\$#,0.00);\$#,0.00">  
<bi:Kpi   
    StatusGraphic="Three Circles Colored">  
    <bi:KpiGoal>  
        <bi:PropertyRef Name="v_Sum_of_SalesAmount_Goal" />  
    </bi:KpiGoal>  
    <bi:KpiStatus>  
        <bi:PropertyRef Name="v_Sum_of_SalesAmount_Status" />  
    </bi:KpiStatus>  
</bi:Kpi>  
</bi:Measure>  
</Property>  
```  
  
## <a name="see-also"></a>Siehe auch  
 [Technische Referenz für BI-Anmerkungen zu CSDL](technical-reference-for-bi-annotations-to-csdl.md)  
  
  
