---
title: CODEPOINT (SSIS-Ausdruck) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- CODEPOINT function
- leftmost character of expression
ms.assetid: 0783d05e-7f35-42fb-a2c4-9621c46effd6
author: janinezhang
ms.author: janinez
ms.openlocfilehash: c77590de168837b2acd172550fbd4180e6e3b16d
ms.sourcegitcommit: f71e523da72019de81a8bd5a0394a62f7f76ea20
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/17/2020
ms.locfileid: "84967450"
---
# <a name="codepoint-ssis-expression"></a>CODEPOINT (SSIS-Ausdruck)
  Gibt das Unicode-Codeelement des äußeren linken Zeichens eines Zeichenausdrucks zurück.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
CODEPOINT(character_expression)  
```  
  
## <a name="arguments"></a>Argumente  
 *character_expression*  
 Ein Zeichenausdruck, dessen äußeres linkes Zeichen ausgewertet wird.  
  
## <a name="result-types"></a>Ergebnistypen  
 DT_UI2  
  
## <a name="remarks"></a>Bemerkungen  
 *character_expression* muss den Datentyp „DT_WSTR“ aufweisen.  
  
 CODEPOINT gibt ein NULL-Ergebnis zurück, wenn *character_expression* NULL oder eine leere Zeichenfolge ist.  
  
## <a name="expression-examples"></a>Beispiele für Ausdrücke  
 In diesem Beispiel wird ein Zeichenfolgenliteral verwendet. Als Ergebnis wird 77 zurückgegeben, das Unicode-Codeelement für M.  
  
```  
CODEPOINT("Mountain Bike")  
```  
  
 In diesem Beispiel wird eine Variable verwendet. Falls **Name** Touring Front Wheel ist, wird als Ergebnis 84 zurückgegeben, das Unicode-Codeelement für T.  
  
```  
CODEPOINT(@Name)  
```  
  
## <a name="see-also"></a>Weitere Informationen  
 [Funktionen &#40;SSIS-Ausdruck&#41;](functions-ssis-expression.md)  
  
  
