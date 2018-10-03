---
title: KPI-Element (CSDLBI) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.topic: reference
ms.assetid: 203ee6e8-eef2-4476-b09f-bd95e492ddaa
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 09f42856788dffa45a03690c87e2383849c5f813
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/02/2018
ms.locfileid: "48189820"
---
# <a name="kpi-element-csdlbi"></a>KPI-Element (CSDLBI)
  Das KPI-Element definiert eine Berechnung, die als Key Performance Indicator (KPI) verwendet werden kann. In einem Business Intelligence-Datenmodell basieren KPIs auf Measures. Somit enthält die KPI-Definition alle Measures zugeordneten Metadaten sowie die für die Darstellung der KPI-Werte benötigten Informationen, einschließlich einer Standardgrafik.  
  
 Das KPI-Element gibt nicht die Formel an, die in der Measuredefinition enthalten ist, sondern die zusätzlichen Metadaten, die Measures zugeordnet sind, die als KPIs verwendet werden. Sobald Sie ein Measure als KPI festgelegt haben, können Sie es in anderen Kontexten nicht als Measure verwenden.  
  
## <a name="elements-and-attributes"></a>Elemente und Attribute  
 In der folgenden Tabelle sind die Elemente und Attribute aufgeführt, die das KPI-Element definieren.  
  
|Name|Ist erforderlich|Description|  
|----------|-----------------|-----------------|  
|Dokumentation|nein|Eine Beschreibung des KPI.|  
|KpiGoal|Benutzerkontensteuerung|Ein Verweis auf eine Spalte, die Werte enthält, die als Ziel verwendet werden können.<br /><br /> Weitere Informationen finden Sie unter [PropertyRef-Element &#40;CSDLBI&#41;](propertyref-element-csdlbi.md).|  
|KpiStatus|Benutzerkontensteuerung|Ein Verweis auf eine Spalte, die Werte enthält, die den aktuellen Status des KPI darstellen.|  
|StatusGraphic|Benutzerkontensteuerung|Ein Verweis auf ein Bild, das den negativen, neutralen oder positiven Fortschritt für im KPI definierte Ziele angibt.|  
  
## <a name="remarks"></a>Hinweise  
 Wenn Sie ein Modell entwerfen, können Sie einen KPI erstellen. Erstellen Sie dazu ein Measure, und weisen Sie dann das Measure zur Verwendung als KPI zu. Fügen Sie dann für KPIs spezifische Informationen hinzu, beispielsweise eine Grafik zum Aufzeigen von Trends.  
  
## <a name="example"></a>Beispiel  
 **Tabellarisch**  
  
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
 **Multidimensional**  
  
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
 [Technische Referenz für BI-Anmerkungen zu CSDL](technical-reference-for-bi-annotations-to-csdl.md)  
  
  
