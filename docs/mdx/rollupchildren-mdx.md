---
title: RollupChildren (MDX) | Microsoft Docs
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 5df035ab7ae2949164869536c498c341327916c3
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "63149321"
---
# <a name="rollupchildren-mdx"></a>RollupChildren (MDX)


  Gibt einen Wert zurück, der durch einen Rollup der Werte der untergeordneten Elemente eines angegebenen Elements mithilfe des angegebenen unären Operators generiert wird.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
RollupChildren(Member_Expression, Unary_Operator)   
```  
  
## <a name="arguments"></a>Argumente  
 *Member_Expression*  
 Ein gültiger MDX-Ausdruck (Multidimensional Expressions), der ein Element zurückgibt.  
  
 *Unary_Operator*  
 Ein gültiger Zeichenfolgenausdruck, der einen unären Operator angibt.  
  
## <a name="remarks"></a>Hinweise  
 Die **RollupChildren** -Funktion führt einen Rollup der untergeordneten Elemente des angegebenen Elements mithilfe des angegebenen unären Operators.  
  
 Die folgende Tabelle beschreibt die gültigen unären Operatoren für diese Funktion.  
  
|Operator|Ergebnis|  
|--------------|------------|  
|**+**|Gesamt = Gesamt + aktuelles untergeordnetes Element|  
|**-**|Gesamt = Gesamt - aktuelles untergeordnetes Element|  
|**\***|Gesamt = Gesamt * aktuelles untergeordnetes Element|  
|**/**|Gesamt = Gesamt / aktuelles untergeordnetes Element|  
|**%**|Gesamt = (Gesamt / aktuelles untergeordnetes Element) * 100|  
|**~**|Das untergeordnete Element wird im Rollup nicht verwendet. Sein Wert wird ignoriert.|  
  
 Falls der Operator in der Elementeigenschaft nicht in der Liste aufgeführt ist, tritt ein Fehler auf. Die Reihenfolge der Auswertung wird durch die Reihenfolge der gleichgeordneten Elemente bestimmt, nicht durch die Rangfolge der Operatoren.  
  
## <a name="example"></a>Beispiel  
 Im folgenden Beispiel wird eine Elementeigenschaft mit dem Namen "Alternate Rollup Operator" verwendet, die alternative Werte für den unären Operator zum Ausführen eines alternativen Rollups der untergeordneten Elemente der Net Profit-Hierarchie in der Account-Dimension enthält. Diese Elementeigenschaft ist im Adventure Works-Cube nicht vorhanden, kann aber erstellt werden. Diese Verwendung von der **RollupChildren** Funktion in einer budgetierungsanwendung zur was-wenn-Analyse verwendet werden kann.  
  
```  
RollupChildren  
   ( [Account].[Net Profit]  
   , [Account].CurrentMember.Properties ('Alternate Rollup Operator') )  
```  
  
## <a name="see-also"></a>Siehe auch  
 [MDX-Funktionsreferenz &#40;MDX&#41;](../mdx/mdx-function-reference-mdx.md)  
  
  
