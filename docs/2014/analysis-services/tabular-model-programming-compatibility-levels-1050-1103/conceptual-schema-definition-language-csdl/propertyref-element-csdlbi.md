---
title: PropertyRef-Element (CSDLBI) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.topic: reference
ms.assetid: 8299efb9-e224-4a82-bdfc-a74ec92f8711
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 2c9a60f61a846ddbef3dcdcdcc484f415643e306
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/02/2018
ms.locfileid: "48067780"
---
# <a name="propertyref-element-csdlbi"></a>PropertyRef-Element (CSDLBI)
  Das PropertyRef-Element ist ein einfacher Typ, der einen Verweis auf eine Spalte enthält, die einen Wert angibt, der von einer anderen Eigenschaft benötigt wird.  
  
## <a name="elements-and-attributes"></a>Elemente und Attribute  
 In der folgenden Tabelle sind die Elemente und Attribute aufgeführt, die das PropertyRef-Element definieren.  
  
|Name|Ist erforderlich|Description|  
|----------|-----------------|-----------------|  
|Name|Benutzerkontensteuerung|Eine Zeichenfolge, die den Namen der Eigenschaft enthält, die Ziel des Verweises ist.|  
  
## <a name="propertyrefs-element"></a>PropertyRefs-Element  
 PropertyRefs ist ein komplexer Typ, der eine Auflistung von Eigenschaften definiert, wobei jede Eigenschaft in einem PropertyRef-Element enthalten ist.  
  
 In der folgenden Tabelle sind die Elemente und Attribute des PropertyRefs-Typs aufgeführt.  
  
|Name|Ist erforderlich|Description|  
|----------|-----------------|-----------------|  
|PropertyRef|Benutzerkontensteuerung|Eine Zeichenfolge, die den Eigenschaftsverweis enthält.|  
  
## <a name="example"></a>Beispiel  
 **Tabellarisch**  
  
 Im folgenden Beispiel wird für das tabellarische AdventureWorks-Modellbeispiel in CSDLBI, Version 1.1, ein PropertyRef-Element veranschaulicht, das den Ursprung einer Formel angibt, die in einem Measure verwendet wird.  
  
```  
<bi:Measure Caption="Total Current Quarter Margin Performance" ReferenceName="Total Current Quarter Margin Performance" Width="0" IsSimpleMeasure="false">  
  <bi:Kpi StatusGraphic="Three Symbols UnCircled Colored">  
    <bi:KpiGoal>  
      <bi:PropertyRef Name="Measures___Total_Current_Quarter_Margin_Performance_Goal_" />  
    </bi:KpiGoal>  
    <bi:KpiStatus>  
      <bi:PropertyRef Name="Measures___Total_Current_Quarter_Margin_Performance_Status_" />  
    </bi:KpiStatus>  
  </bi:Kpi>  
</bi:Measure>  
```  
  
## <a name="example"></a>Beispiel  
 **Multidimensional**  
  
 Im folgenden Beispiel wird in CSDLBI, Version 1.1, ein KPI aus dem Contoso-Vorgangscube veranschaulicht. Die PropertyRef-Elemente zeigen auf den Spalten, die die Formel oder die Werte enthalten, die verwendet werden, um das Ziel und den Status des KPI in Bezug auf das Ziel zu definieren.  
  
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
  
  
