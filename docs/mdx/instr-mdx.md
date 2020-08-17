---
description: Instr (MDX)
title: InStr (MDX) | Microsoft-Dokumentation
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: 877fc4658081108e810e404dfc8d4a368c6964ba
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/17/2020
ms.locfileid: "88387356"
---
# <a name="instr-mdx"></a>Instr (MDX)


  Gibt die Position des ersten Vorkommens einer Zeichenfolge innerhalb einer anderen Zeichenfolge zurück.  
  
## <a name="syntax"></a>Syntax  
  
```  
InStr([start, ]searched_string, search_string[, compare])  
```  
  
## <a name="arguments"></a>Argumente  
 *start*  
 (Optional) Ein numerischer Ausdruck, der die Startposition für jede Suche festlegt. Wenn Sie diesen Wert weglassen, beginnt die Suche an der ersten Zeichenposition. Wenn Start NULL ist, wird von der Funktion ein nicht definierter Wert zurückgegeben.  
  
 *searched_string*  
 Der Zeichenfolgenausdruck, der durchsucht werden soll.  
  
 *search_string*  
 Der Zeichenfolgenausdruck, nach dem gesucht werden soll.  
  
 *Vergleichen*  
 (optional) Ein ganzzahliger Wert. Dieses Argument wird immer ignoriert. Es ist für die Kompatibilität mit anderen **InStr** -Funktionen in anderen Sprachen definiert.  
  
## <a name="return-value"></a>Rückgabewert  
 Ein ganzzahliger Wert mit der Anfangsposition von *Zeichenfolge2* in *Zeichenfolge1*.  
  
 Außerdem gibt die **InStr** -Funktion die Werte zurück, die in der folgenden Tabelle aufgeführt sind, abhängig von der Bedingung:  
  
|Bedingung|Rückgabewert|  
|---------------|------------------|  
|String1 hat die Länge 0 (null)|NULL (0)|  
|String1 ist NULL|nicht definiert|  
|String2 hat die Länge 0 (null)|start|  
|String2 ist NULL|nicht definiert|  
|String2 wurde nicht gefunden|NULL (0)|  
|start ist größer als Len(String2)|NULL (0)|  
  
## <a name="remarks"></a>Bemerkungen  
  
> [!WARNING]  
>  **InStr** führt immer einen Vergleich ohne Beachtung der Groß-und Kleinschreibung durch  
  
## <a name="example"></a>Beispiel  
 Das folgende Beispiel zeigt die Verwendung der **InStr** -Funktion und zeigt verschiedene Ergebnis Szenarios.  
  
```  
with   
    member [Date].[Date].[Results] as "Results"  
    member measures.[lowercase found in lowercase string] as InStr( "abcdefghijklmnñopqrstuvwxyz", "o")  
    member measures.[uppercase found in lowercase string] as InStr( "abcdefghijklmnñopqrstuvwxyz", "O")  
    member measures.[searched string is empty]            as InStr( "", "o")  
    member measures.[searched string is null]             as iif(IsError(InStr( null, "o")), "Is Error", iif(IsNull(InStr( null, "o")), "Is Null","Is undefined"))  
    member measures.[search string is empty]              as InStr( "abcdefghijklmnñopqrstuvwxyz", "")  
    member measures.[search string is empty start 10]     as InStr(10, "abcdefghijklmnñopqrstuvwxyz", "")  
    member measures.[search string is null]               as iif(IsError(InStr( null, "o")), "Is Error", iif(IsNull(InStr( null, "o")), "Is Null","Is undefined"))  
    member measures.[found from start 10]                 as InStr( 10, "abcdefghijklmnñopqrstuvwxyz", "o")  
    member measures.[NOT found from start 17]             as InStr( 17, "abcdefghijklmnñopqrstuvwxyz", "o")  
    member measures.[NULL start]                          as iif(IsError(InStr( null, "abcdefghijklmnñopqrstuvwxyz", "o")), "Is Error", iif(IsNull(InStr( null, "abcdefghijklmnñopqrstuvwxyz", "o")), "Is Null","Is undefined"))  
    member measures.[start greater than searched length]  as InStr( 170, "abcdefghijklmnñopqrstuvwxyz", "o")  
  
select  [Results] on columns,  
       { measures.[lowercase found in lowercase string]  
       , measures.[uppercase found in lowercase string]  
       , measures.[searched string is empty]  
       , measures.[searched string is null]  
       , measures.[search string is empty]  
       , measures.[search string is empty start 10]  
       , measures.[search string is null]  
       , measures.[found from start 10]  
       , measures.[NOT found from start 17]  
       , measures.[NULL start]   
       , measures.[start greater than searched length]  
       } on rows  
  
from [Adventure Works]  
```  
  
 In der folgenden Tabelle werden die erhaltenen Ergebnisse angezeigt:  
  
|Feld in Measures|Ergebnisse|  
|-|-|  
|Kleinbuchstaben in Zeichenfolge mit Kleinbuchstaben gefunden|16|  
|Großbuchstaben in Zeichenfolge mit Kleinbuchstaben gefunden|16|  
|Gesuchte Zeichenfolge ist leer|0|  
|Gesuchte Zeichenfolge ist NULL|Ist nicht definiert|  
|Suchzeichenfolge ist leer|1|  
|Suchzeichenfolge ist leer, Start 10|10|  
|Suchzeichenfolge ist NULL|Ist nicht definiert|  
|Gefunden von Start 10|16|  
|Nicht gefunden von Start 17|0|  
|NULL-Start|Ist nicht definiert|  
|Start ist größer als die gesuchte Länge|0|  
  
  
