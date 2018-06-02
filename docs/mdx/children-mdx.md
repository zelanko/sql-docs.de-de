---
title: Untergeordnete Elemente (MDX) | Microsoft Docs
ms.date: 05/30/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 4cf46d1844b8544dbf793ccaf7da98b3ba588fb5
ms.sourcegitcommit: 808d23a654ef03ea16db1aa23edab496b73e5072
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/02/2018
ms.locfileid: "34578502"
---
# <a name="children-mdx"></a>Children (MDX)
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  Gibt die Menge der untergeordneten Elemente eines angegebenen Elements zurück.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
Member_Expression.Children  
```  
  
## <a name="arguments"></a>Argumente  
 *Member_Expression*  
 Ein gültiger MDX-Ausdruck (Multidimensional Expressions), der ein Element zurückgibt.  
  
## <a name="remarks"></a>Hinweise  
 Die **Kinder** Funktion gibt eine natürlich geordnete Menge, die die untergeordneten Elemente eines angegebenen Elements enthält. Wenn das angegebene Element nicht über untergeordnete Elemente verfügt, gibt die Funktion eine leere Menge zurück.  
  
## <a name="example"></a>Beispiel  
 Im folgenden Beispiel werden die untergeordneten Elemente des United States-Element der Geography-Hierarchie in der Geography-Dimension zurückgegeben.  
  
```  
SELECT [Geography].[Geography].[Country].&[United States].Children ON 0  
FROM [Adventure Works]  
```  
  
 Das folgende Beispiel gibt alle Elemente in der **Measures** Dimension auf der Spaltenachse einschließlich aller berechneten Elemente sowie die Menge aller untergeordneten Elemente der der `[Product].[Model Name]` -Attributhierarchie auf der Zeilenachse der **Adventure Works** Cube.  
  
```  
SELECT  
    Measures.AllMembers ON COLUMNS,  
    [Product].[Model Name].Children ON ROWS  
FROM  
    [Adventure Works]  
  
```  
  
|Release|Verlauf|  
|-------------|-------------|  
|[!INCLUDE[ssBOL2005_R03](../includes/ssbol2005-r03-md.md)]|**Geänderter Inhalt:**<br /> – Syntax und Argumente zur Verdeutlichung aktualisiert.<br /><br /> – Aktualisierte Beispiele wurden hinzugefügt.|  
  
## <a name="see-also"></a>Siehe auch  
 [MDX-Funktionsreferenz &#40;MDX&#41;](../mdx/mdx-function-reference-mdx.md)  
  
  
