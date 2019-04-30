---
title: Ordinalzahl (MDX) | Microsoft-Dokumentation
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 83036ec2ee0fa69c9ebb8cc2a905361eeae0aafa
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "63278117"
---
# <a name="ordinal-mdx"></a>Ordinal (MDX)


  Gibt den nullbasierten Ordinalwert, der einer Ebene zugeordnet ist, zurück.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
Level_Expression.Ordinal   
```  
  
## <a name="arguments"></a>Argumente  
 *Level_Expression*  
 Ein gültiger MDX-Ausdruck (Multidimensional Expressions), der eine Ebene zurückgibt.  
  
## <a name="remarks"></a>Hinweise  
 Die **Ordnungszahl** Funktion wird häufig verwendet, in Verbindung mit der **IIF** und **CurrentMember** Funktionen, um unterschiedliche Werte bedingt auf verschiedenen anzeigen Hierarchieebenen, basierend auf der Position der einzelnen speziellen Zellen im Abfrageergebnis. Beispielsweise können Sie die **Ordnungszahl** -Funktion zum Ausführen von Berechnungen auf bestimmten Ebenen und den Standardwert "N/v" auf anderen Ebenen anzeigen.  
  
## <a name="example"></a>Beispiel  
 Im folgenden Beispiel wird die Ordinalzahl für die Calendar Quarter-Ebene in der Calendar-Hierarchie zurückgegeben.  
  
```  
WITH MEMBER Measures.x AS [Date].[Calendar].[Calendar Quarter].Ordinal  
SELECT Measures.x on 0  
FROM [Adventure Works]  
```  
  
## <a name="see-also"></a>Siehe auch  
 [MDX-Funktionsreferenz &#40;MDX&#41;](../mdx/mdx-function-reference-mdx.md)  
  
  
