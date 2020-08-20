---
description: KPIValue (MDX)
title: KPIValue (MDX) | Microsoft-Dokumentation
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: 24189ffb3e9a550fd4819b15cfbd8ae41a48a64f
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/17/2020
ms.locfileid: "88471812"
---
# <a name="kpivalue-mdx"></a>KPIValue (MDX)


  Gibt das Element zurück, das den Wert des angegebenen Key Performance Indicators (KPI) berechnet.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
KPIValue(KPI_Name)  
```  
  
## <a name="arguments"></a>Argumente  
 *KPI_Name*  
 Ein gültiger Zeichenfolgenausdruck, der den Namen des KPIs angibt.  
  
## <a name="remarks"></a>Bemerkungen  
  
## <a name="example"></a>Beispiel  
 Im folgenden Beispiel wird der KPI-Wert, das KPI-Ziel, der KPI-Status und der KPI-Trend für das Channel Revenue-Measure der nachfolgenden Werte dreier Elemente der Fiscal Year-Attributhierarchie zurückgegeben.  
  
```  
SELECT  
   { KPIValue("Channel Revenue"),   
     KPIGoal("Channel Revenue"),  
     KPIStatus("Channel Revenue"),   
     KPITrend("Channel Revenue")  
   } ON Columns,  
Descendants  
   ( { [Date].[Fiscal].[Fiscal Year].&[2002],  
       [Date].[Fiscal].[Fiscal Year].&[2003],  
       [Date].[Fiscal].[Fiscal Year].&[2004]   
     }, [Date].[Fiscal].[Fiscal Quarter]  
   ) ON Rows  
FROM [Adventure Works]  
```  
  
## <a name="see-also"></a>Weitere Informationen  
 [MDX-Funktionsreferenz &#40;MDX&#41;](../mdx/mdx-function-reference-mdx.md)  
  
  
