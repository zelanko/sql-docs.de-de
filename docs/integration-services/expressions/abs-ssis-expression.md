---
title: ABS (SSIS-Ausdruck) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- ABS function
- absolute positive value
ms.assetid: 156747f6-e016-44cf-9a9f-ae8e4a1b4f17
author: janinezhang
ms.author: janinez
ms.openlocfilehash: 00f3937c13de5db106732ee919db6671485b691f
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "68057676"
---
# <a name="abs-ssis-expression"></a>ABS (SSIS-Ausdruck)

[!INCLUDE[ssis-appliesto](../../includes/ssis-appliesto-ssvrpluslinux-asdb-asdw-xxx.md)]


  Gibt den absoluten, positiven Wert eines numerischen Ausdrucks zurück.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
ABS(numeric_expression)  
```  
  
## <a name="arguments"></a>Argumente  
 *numeric_expression*  
 Ein numerischer Ausdruck mit oder ohne Vorzeichen.  
  
## <a name="result-types"></a>Ergebnistypen  
 Der Datentyp des numerischen Ausdrucks, der an die Funktion übergeben wird.  
  
## <a name="remarks"></a>Bemerkungen  
 ABS gibt ein NULL-Ergebnis zurück, wenn das Argument NULL ist.  
  
## <a name="expression-examples"></a>Beispiele für Ausdrücke  
 In diesen Beispielen wird die ABS-Funktion auf eine positive und eine negative Zahl angewendet. In beiden Fällen wird 1.23 zurückgegeben.  
  
```  
ABS(-1.23)  
ABS(1.23)  
```  
  
 In diesem Beispiel wird die ABS-Funktion auf einen Ausdruck angewendet, der Werte in den Variablen **HighTemperature** und **LowTempature**subtrahiert.  
  
```  
ABS(@HighTemperature - @LowTemperature)  
```  
  
## <a name="see-also"></a>Weitere Informationen  
 [Funktionen &#40;SSIS-Ausdruck&#41;](../../integration-services/expressions/functions-ssis-expression.md)  
  
  
