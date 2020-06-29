---
title: () (Klammern) (SSIS-Ausdruck) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- () (parentheses operator)
- evaluation order [Integration Services]
- parentheses operator ()
ms.assetid: 931e10eb-1707-4121-b2f1-43565561119f
author: chugugrace
ms.author: chugu
ms.openlocfilehash: fca370f011d132ccd7aea9a32afbd0f7d062a270
ms.sourcegitcommit: 34278310b3e005d008cd2106a7b86fc6e736f661
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/26/2020
ms.locfileid: "85437157"
---
# <a name="-parentheses-ssis-expression"></a>() (Klammern) (SSIS-Ausdruck)
  Identifiziert die Auswertungsreihenfolge von Ausdrücken. Ausdrücke in Klammern haben die höchste Auswertungsrangfolge. Geschachtelte Ausdrücke, die in Klammern eingeschlossen sind, werden von innen nach außen ausgewertet.  
  
 Durch Klammern werden außerdem komplexe Ausdrücke verständlicher.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
(expression)  
  
```  
  
## <a name="arguments"></a>Argumente  
 *expression*  
 Ist ein beliebiger gültiger Ausdruck.  
  
## <a name="result-types"></a>Ergebnistypen  
 Der Datentyp von *expression*. Weitere Informationen finden Sie unter [Integration Services Datentypen](../data-flow/integration-services-data-types.md).  
  
## <a name="expression-examples"></a>Beispiele für Ausdrücke  
 Dieses Beispiel zeigt, wie die Rangfolge von Operatoren durch die Verwendung von Klammern geändert wird. Der erste Ausdruck wird zu 100 ausgewertet, der zweite zu 31.  
  
```  
(5 + 5) * (4 + 6)  
5 + 5 * 4 + 6  
  
```  
  
## <a name="see-also"></a>Weitere Informationen  
 [Operatorenrangfolge und -assoziativität](operator-precedence-and-associativity.md)   
 [Operatoren &#40;SSIS-Ausdruck&#41;](operators-ssis-expression.md)  
  
  
