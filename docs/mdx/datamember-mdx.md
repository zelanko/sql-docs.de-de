---
title: DataMember (MDX) | Microsoft Docs
ms.date: 05/30/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 2979799686ad1d97018471111c57670383f7f4f8
ms.sourcegitcommit: 808d23a654ef03ea16db1aa23edab496b73e5072
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/02/2018
ms.locfileid: "34577852"
---
# <a name="datamember-mdx"></a>DataMember (MDX)
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  Gibt das systemgenerierte Datenelement zurück, das einem Nicht-Blattelement einer Dimension zugeordnet ist.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
Member_Expression.DataMember  
```  
  
## <a name="arguments"></a>Argumente  
 *Member_Expression*  
 Ein gültiger MDX-Ausdruck (Multidimensional Expressions), der ein Element zurückgibt.  
  
## <a name="remarks"></a>Hinweise  
 Diese Funktion nimmt Nichtblattelemente in einer beliebigen Hierarchie und kann verwendet werden, indem Sie die [UPDATE CUBE-Anweisung (MDX)](../mdx/mdx-data-manipulation-update-cube.md) um Daten zu direkt einem Nichtblattelement anstatt auf das Blattelement Nachfolger.  
  
> [!NOTE]  
>  Gibt das angegebene Element zurück, wenn es ein Blattelement ist, oder wenn das Nichtblattelement über keine dazugehörigen Datenelemente verfügt.  
  
## <a name="example"></a>Beispiel  
 Im folgenden Beispiel wird die **DataMember** Funktion in einem berechneten Measure, um die Vertriebsvorgaben für jeden einzelnen Mitarbeiter anzuzeigen:  
  
```  
WITH MEMBER measures.InvidualQuota AS   
([Employee].[Employees].currentmember.datamember, [Measures].[Sales Amount Quota])  
,FORMAT_STRING='Currency'  
SELECT {[Measures].[Sales Amount Quota],[Measures].InvidualQuota} ON COLUMNS,  
[Employee].[Employees].MEMBERS ON ROWS  
FROM [Adventure Works]  
```  
  
## <a name="see-also"></a>Siehe auch  
 [MDX-Funktionsreferenz &#40;MDX&#41;](../mdx/mdx-function-reference-mdx.md)   
 [Schlüsselkonzepte in MDX &#40;Analysis Services&#41;](../analysis-services/multidimensional-models/mdx/key-concepts-in-mdx-analysis-services.md)  
  
  
