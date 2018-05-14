---
title: KPI-Element (CSDLBI) | Microsoft Docs
ms.date: 05/07/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: tabular-models
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: bc368aed1186c20e76ce643a33673030713547ba
ms.sourcegitcommit: c12a7416d1996a3bcce3ebf4a3c9abe61b02fb9e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/10/2018
---
# <a name="kpi-element-csdlbi"></a>KPI-Element (CSDLBI)
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]
  Das KPI-Element definiert eine Berechnung, die als Key Performance Indicator (KPI) verwendet werden kann. In einem Business Intelligence-Datenmodell basieren KPIs auf Measures. Somit enthält die KPI-Definition alle Measures zugeordneten Metadaten sowie die für die Darstellung der KPI-Werte benötigten Informationen, einschließlich einer Standardgrafik.  
  
 Das KPI-Element gibt nicht die Formel an, die in der Measuredefinition enthalten ist, sondern die zusätzlichen Metadaten, die Measures zugeordnet sind, die als KPIs verwendet werden. Sobald Sie ein Measure als KPI festgelegt haben, können Sie es in anderen Kontexten nicht als Measure verwenden.  
  
## <a name="elements-and-attributes"></a>Elemente und Attribute  
 In der folgenden Tabelle sind die Elemente und Attribute aufgeführt, die das KPI-Element definieren.  
  
|Name|Ist erforderlich|Beschreibung|  
|----------|-----------------|-----------------|  
|Dokumentation|Nein|Eine Beschreibung des KPI.|  
|KpiGoal|ja|Ein Verweis auf eine Spalte, die Werte enthält, die als Ziel verwendet werden können.<br /><br /> Weitere Informationen finden Sie unter [PropertyRef-Element &#40;CSDLBI&#41;](../../../analysis-services/tabular-model-programming-compatibility-levels-1050-1103/conceptual-schema-definition-language-csdl/propertyref-element-csdlbi.md).|  
|KpiStatus|ja|Ein Verweis auf eine Spalte, die Werte enthält, die den aktuellen Status des KPI darstellen.|  
|StatusGraphic|ja|Ein Verweis auf ein Bild, das den negativen, neutralen oder positiven Fortschritt für im KPI definierte Ziele angibt.|  
  
## <a name="remarks"></a>Hinweise  
 Wenn Sie ein Modell entwerfen, können Sie einen KPI erstellen. Erstellen Sie dazu ein Measure, und weisen Sie dann das Measure zur Verwendung als KPI zu. Fügen Sie dann für KPIs spezifische Informationen hinzu, beispielsweise eine Grafik zum Aufzeigen von Trends.  
  
## <a name="example"></a>Beispiel  
 **Tabellarische**  
  
 Das folgende Beispiel veranschaulicht einen KPI in CSDLBI, Version 1.1, der Verkäufe misst (vom tabellarischen AdventureWorks-Modellbeispiel).  
  
```  
  
<Property Name="InternetCurrSalesPerf" Type="Double">  
  <bi:Measure>  
    <bi:Kpi StatusGraphic="Three Stars Colored">  
      <bi:KpiGoal>  
        <bi:PropertyRef Name="v_InternetCurrSalesPerf_Goal" />  
      </bi:KpiGoal>  
      <bi:KpiStatus>  
        <bi:PropertyRef Name="v_InternetCurrSalesPerf_Status" />  
      </bi:KpiStatus>  
    </bi:Kpi>  
  </bi:Measure>  
</Property>  
  
```  
  
## <a name="example"></a>Beispiel  
 **Mehrdimensionale**  
  
 Im folgenden Beispiel wird in CSDLBI, Version 1.1, ein KPI aus dem Contoso-Vorgangscube veranschaulicht.  
  
```  
<Property Name="Sum_of_SalesAmount" Type="Decimal" Precision="19" Scale="4">  
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
 [Technische Referenz für BI-Anmerkungen zu CSDL](../../../analysis-services/tabular-model-programming-compatibility-levels-1050-1103/conceptual-schema-definition-language-csdl/technical-reference-for-bi-annotations-to-csdl.md)  
  
  
