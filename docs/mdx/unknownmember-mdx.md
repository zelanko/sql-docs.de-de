---
title: UnknownMember (MDX) | Microsoft-Dokumentation
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: a0332b200a74044dcd4e7d8d308923cc4b759738
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "68097281"
---
# <a name="unknownmember-mdx"></a>UnknownMember (MDX)


  Gibt das einer Ebene oder einem Element zugeordnete unbekannte Element zurück.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
Member expression syntax  
Member_Expression.UnknownMember  
  
Hierarchy_expression syntax  
Hierarchy_Expression.UnknownMember  
```  
  
## <a name="arguments"></a>Argumente  
 *Member_Expression*  
 Ein gültiger MDX-Ausdruck (Multidimensional Expressions), der ein Element zurückgibt.  
  
 *Hierarchy_Expression*  
 Ein gültiger MDX-Ausdruck (Multidimensional Expressions), der eine Hierarchie zurückgibt.  
  
## <a name="remarks"></a>Bemerkungen  
 Analysis Services erstellt ein unbekanntes Element, um Fakten Tabellendaten einer Hierarchie zuzuordnen, wenn die Hierarchie nicht bekannt ist. Das unbekannte Element kann sich auf einer der folgenden Ebenen befinden:  
  
-   Auf der obersten Ebene für nicht aggregierte Attributhierarchien.  
  
-   Auf der ersten Ebene unterhalb der **all** -Ebene für natürliche Hierarchien.  
  
-   Auf jeder Ebene für unnatürliche Hierarchien.  
  
 Wenn ein Element Ausdruck angegeben ist, gibt die **UnknownMember** -Funktion das unbekannte Member-Element des angegebenen Elements zurück. Wenn das angegebene Element nicht vorhanden ist, gibt die Funktion den Wert NULL zurück.  
  
 Wenn ein Hierarchie Ausdruck angegeben wird, gibt die **UnknownMember** -Funktion das unbekannte Element auf der obersten Ebene zurück, sofern vorhanden.  
  
 Wenn das unbekannte Element auf der Ebene oder dem Element nicht vorhanden ist, erstellt die **UnknownMember** -Funktion einen NULL-Member.  
  
> [!NOTE]  
>  Wenn kein unbekanntes Element in der Hierarchie oder für das Element vorhanden ist, wird ein Fehler generiert.  
  
## <a name="examples"></a>Beispiele  
 Im folgenden Beispiel wird das unbekannte Element für das All Products-Element in der Product-Attributhierarchie für alle Elemente der Measures-Dimension zurückgegeben.  
  
```  
SELECT [Product].[Product].[All Products].UnknownMember  
    ON Columns,  
[Measures].Members  
    ON Rows  
FROM [Adventure Works]  
  
```  
  
 Im folgenden Beispiel wird das unbekannte Element für die Product Categories-Hierarchie für alle Elemente der Measures-Dimension zurückgegeben.  
  
```  
SELECT [Product].[Product Categories].UnknownMember  
    ON Columns,  
[Measures].Members  
    ON Rows  
FROM [Adventure Works]  
  
```  
  
## <a name="see-also"></a>Weitere Informationen  
 [MDX-Funktionsreferenz &#40;MDX-&#41;](../mdx/mdx-function-reference-mdx.md)  
  
  
