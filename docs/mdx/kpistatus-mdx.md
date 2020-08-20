---
description: KPIStatus (MDX)
title: Kpistatus (MDX) | Microsoft-Dokumentation
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: 645f7d816d2d51ca5124a8b5300029cd57ae93d9
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/17/2020
ms.locfileid: "88483923"
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
  
## <a name="remarks"></a>Bemerkungen  
 Der Statuswert ist im Allgemeinen ein normalisierter Wert zwischen -1 und 1.  
  
## <a name="example"></a>Beispiel  
 Das folgende Beispiel gibt den KPI-Wert, das KPI-Ziel, den KPI-Status und den KPI-Trend für das channelrevenue-Measure für die nachfolgenden drei Elemente der Fiscal Year-Attribut Hierarchie zurück:  
  
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
  
  
