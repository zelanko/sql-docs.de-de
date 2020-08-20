---
description: Children (MDX)
title: Children (MDX) | Microsoft-Dokumentation
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: 9a37bc27564baf9d75e10af78fb477ea08be092e
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/17/2020
ms.locfileid: "88466512"
---
# <a name="children-mdx"></a>Children (MDX)


  Gibt die Menge der untergeordneten Elemente eines angegebenen Elements zurück.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
Member_Expression.Children  
```  
  
## <a name="arguments"></a>Argumente  
 *Member_Expression*  
 Ein gültiger MDX-Ausdruck (Multidimensional Expressions), der ein Element zurückgibt.  
  
## <a name="remarks"></a>Bemerkungen  
 Die **Children** -Funktion gibt eine natürlich geordnete Menge zurück, die die untergeordneten Elemente eines angegebenen Elements enthält. Wenn das angegebene Element nicht über untergeordnete Elemente verfügt, gibt die Funktion eine leere Menge zurück.  
  
## <a name="example"></a>Beispiel  
 Im folgenden Beispiel werden die untergeordneten Elemente des United States-Element der Geography-Hierarchie in der Geography-Dimension zurückgegeben.  
  
```  
SELECT [Geography].[Geography].[Country].&[United States].Children ON 0  
FROM [Adventure Works]  
```  
  
 Im folgenden Beispiel werden alle Elemente der **Measures** -Dimension auf der Spalten Achse zurückgegeben, einschließlich aller berechneten Elemente und der Menge aller untergeordneten Elemente der `[Product].[Model Name]` Attribut Hierarchie auf der Zeilen Achse aus dem **Adventure Works** -Cube.  
  
```  
SELECT  
    Measures.AllMembers ON COLUMNS,  
    [Product].[Model Name].Children ON ROWS  
FROM  
    [Adventure Works]  
  
```  
  
|Release|Verlauf|  
|-------------|-------------|  
|[!INCLUDE[ssBOL2005_R03](../includes/ssbol2005-r03-md.md)]|**Geänderter Inhalt:**<br /> -Aktualisierte Syntax und Argumente zur Verbesserung der Übersichtlichkeit.<br /><br /> -Aktualisierte Beispiele wurden hinzugefügt.|  
  
## <a name="see-also"></a>Weitere Informationen  
 [MDX-Funktionsreferenz &#40;MDX&#41;](../mdx/mdx-function-reference-mdx.md)  
  
  
