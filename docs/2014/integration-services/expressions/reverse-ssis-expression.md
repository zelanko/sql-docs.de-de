---
title: REVERSE (SSIS-Ausdruck) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- REVERSE function
- reverse character expressions
ms.assetid: bcebcc55-7247-4896-8f53-4d582d58cfb4
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: ce882ae32718f634efb6b2f39ed397dfb9cbf785
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "62897336"
---
# <a name="reverse-ssis-expression"></a>REVERSE (SSIS-Ausdruck)
  Gibt einen Zeichenausdruck in umgekehrter Reihenfolge zurück.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
REVERSE(character_expression)  
```  
  
## <a name="arguments"></a>Argumente  
 *character_expression*  
 Der Zeichenausdruck, dessen Reihenfolge umgekehrt werden soll.  
  
## <a name="result-types"></a>Ergebnistypen  
 DT_WSTR  
  
## <a name="remarks"></a>Hinweise  
 Das *character_expression* -Argument muss den Datentyp „DT_WSTR“ aufweisen.  
  
 REVERSE gibt ein NULL-Ergebnis zurück, wenn *character_expression* NULL ist.  
  
## <a name="expression-examples"></a>Beispiele für Ausdrücke  
 In diesem Beispiel wird ein Zeichenfolgenliteral verwendet. Als Ergebnis wird "ekiB niatnuoM" zurückgegeben.  
  
```  
REVERSE("Mountain Bike")  
```  
  
 In diesem Beispiel wird eine Variable verwendet. Falls **Name** Touring Bike enthält, wird als Ergebnis "ekiB gniruoT" zurückgegeben.  
  
```  
REVERSE(@Name)  
```  
  
## <a name="see-also"></a>Siehe auch  
 [Funktionen &#40;SSIS-Ausdruck&#41;](functions-ssis-expression.md)  
  
  
