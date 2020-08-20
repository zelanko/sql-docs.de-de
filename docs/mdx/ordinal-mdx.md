---
description: Ordinal (MDX)
title: Ordinal (MDX) | Microsoft-Dokumentation
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: 74811da22f8c73536749acad41dfbe859b00eeea
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/17/2020
ms.locfileid: "88471732"
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
  
## <a name="remarks"></a>Bemerkungen  
 Die **ordinalfunktion** wird häufig in Verbindung mit den **IIf** -und **CurrentMember** -Funktionen verwendet, um unterschiedliche Werte auf verschiedenen Hierarchieebenen bedingt auf der Grundlage der Ordnungsposition der einzelnen einzelnen Zellen im Abfrageergebnis anzuzeigen. Beispielsweise können Sie die **ordinalfunktion** verwenden, um Berechnungen auf bestimmten Ebenen auszuführen und den Standardwert "N/v" auf anderen Ebenen anzuzeigen.  
  
## <a name="example"></a>Beispiel  
 Im folgenden Beispiel wird die Ordinalzahl für die Calendar Quarter-Ebene in der Calendar-Hierarchie zurückgegeben.  
  
```  
WITH MEMBER Measures.x AS [Date].[Calendar].[Calendar Quarter].Ordinal  
SELECT Measures.x on 0  
FROM [Adventure Works]  
```  
  
## <a name="see-also"></a>Weitere Informationen  
 [MDX-Funktionsreferenz &#40;MDX&#41;](../mdx/mdx-function-reference-mdx.md)  
  
  
