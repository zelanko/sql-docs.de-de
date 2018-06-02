---
title: Ordinalzahl (MDX) | Microsoft Docs
ms.date: 05/30/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 61c5c3c4bbb2f04f1ebb9743e18eb8088632eab0
ms.sourcegitcommit: 808d23a654ef03ea16db1aa23edab496b73e5072
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/02/2018
ms.locfileid: "34581262"
---
# <a name="ordinal-mdx"></a>Ordinal (MDX)
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  Gibt den nullbasierten Ordinalwert, der einer Ebene zugeordnet ist, zurück.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
Level_Expression.Ordinal   
```  
  
## <a name="arguments"></a>Argumente  
 *Level_Expression*  
 Ein gültiger MDX-Ausdruck (Multidimensional Expressions), der eine Ebene zurückgibt.  
  
## <a name="remarks"></a>Hinweise  
 Die **Ordinal** -Funktion wird häufig in Verbindung mit der **IIF** und **CurrentMember** Funktionen, um unterschiedliche Werte bedingt auf verschiedenen Hierarchieebenen anzuzeigen auf Grundlage der Position der einzelnen speziellen Zellen im Abfrageergebnis vorhergesagt. Beispielsweise können Sie die **Ordnungszahl** -Funktion Berechnungen auf bestimmten Ebenen ausführen und den Standardwert "N/v" auf anderen Ebenen angezeigt.  
  
## <a name="example"></a>Beispiel  
 Im folgenden Beispiel wird die Ordinalzahl für die Calendar Quarter-Ebene in der Calendar-Hierarchie zurückgegeben.  
  
```  
WITH MEMBER Measures.x AS [Date].[Calendar].[Calendar Quarter].Ordinal  
SELECT Measures.x on 0  
FROM [Adventure Works]  
```  
  
## <a name="see-also"></a>Siehe auch  
 [MDX-Funktionsreferenz &#40;MDX&#41;](../mdx/mdx-function-reference-mdx.md)  
  
  
