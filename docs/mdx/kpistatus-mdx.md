---
title: KPIStatus (MDX) | Microsoft-Dokumentation
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: aa07788bc00cc3317024d287f1054a67c6447356
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "67905884"
---
# <a name="kpistatus-mdx"></a>KPIStatus (MDX)


  Gibt einen normalisierten Wert zurück, der den Statusanteil des Key Performance Indicators (KPI) darstellt.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
KPIStatus(KPI_Name)  
```  
  
## <a name="arguments"></a>Argumente  
 *KPI_Name*  
 Ein gültiger Zeichenfolgenausdruck, der den Namen des KPIs angibt.  
  
## <a name="remarks"></a>Hinweise  
 Der Statuswert ist im Allgemeinen ein normalisierter Wert zwischen -1 und 1.  
  
## <a name="example"></a>Beispiel  
 Das folgende Beispiel gibt die KPI-Wert, KPI-Ziel, KPI-Status und KPI-Trend für das Channel Revenue-Measure für die nachfolgenden Werte dreier Elemente der Fiscal Year-Attributhierarchie zurück:  
  
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
  
## <a name="see-also"></a>Siehe auch  
 [MDX-Funktionsreferenz &#40;MDX&#41;](../mdx/mdx-function-reference-mdx.md)  
  
  
