---
title: SQUARE (SSIS-Ausdruck) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- integration-services
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- SQUARE
- square values
ms.assetid: cecf1bb2-3d55-40a6-9688-ed67bcc150b4
caps.latest.revision: 29
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: db690f1b8ffd3b011ef5a39f442ca44d32b50f33
ms.sourcegitcommit: c8f7e9f05043ac10af8a742153e81ab81aa6a3c3
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/17/2018
ms.locfileid: "39083323"
---
# <a name="square-ssis-expression"></a>SQUARE (SSIS-Ausdruck)
  Gibt das Quadrat eines numerischen Ausdrucks zurück.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
SQUARE(numeric_expression)  
```  
  
## <a name="arguments"></a>Argumente  
 *numeric_expression*  
 Ein numerischer Ausdruck mit einem beliebigen numerischen Datentyp. Weitere Informationen finden Sie unter [Integration Services Datentypen](../data-flow/integration-services-data-types.md).  
  
## <a name="result-types"></a>Ergebnistypen  
 DT_R8  
  
## <a name="remarks"></a>Hinweise  
 SQUARE gibt ein NULL-Ergebnis zurück, wenn das Argument NULL ist.  
  
 Das Argument wird in einen DT_R8-Datentyp umgewandelt, bevor das Quadrat berechnet wird.  
  
## <a name="expression-examples"></a>Beispiele für Ausdrücke  
 In diesem Beispiel wird das Quadrat von 12 zurückgegeben. Als Ergebnis wird 144 zurückgegeben.  
  
```  
SQUARE(12)  
```  
  
 In diesem Beispiel wird das Quadrat des Ergebnisses aus der Subtraktion von Werten in zwei Spalten zurückgegeben. Falls **Value1** 12 und **Value2** 4 enthält, gibt die SQUARE-Funktion 64 zurück.  
  
```  
SQUARE(Value1 - Value2)  
```  
  
 In diesem Beispiel wird die Länge der dritten Seite eines rechtwinkligen Dreiecks zurückgegeben, indem die SQUARE-Funktion auf zwei Variablen angewendet und dann die Quadratwurzel der Summe berechnet wird. Falls **Side1** 3 und **Side2** 4 enthält, gibt die SQRT-Funktion 5 zurück.  
  
```  
SQRT(SQUARE(@Side1) + SQUARE(@Side2))  
```  
  
> [!NOTE]  
>  In Ausdrücken schließen Variablennamen stets das \@ Präfix.  
  
## <a name="see-also"></a>Siehe auch  
 [Funktionen &#40;SSIS-Ausdruck&#41;](functions-ssis-expression.md)  
  
  
