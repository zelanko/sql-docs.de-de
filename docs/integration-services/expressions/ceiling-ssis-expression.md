---
title: CEILING (SSIS-Ausdruck) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- smallest integer great than or equal to expression
- CEILING function [SSIS]
ms.assetid: c35bd4ee-1ab6-46ab-89a7-cf771527faa2
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: b0b9c9c7ab5ed0067d86b3beaa69461ab6e90672
ms.sourcegitcommit: fd71d04a9d30a9927cbfff645750ac9d5d5e5ee7
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/16/2019
ms.locfileid: "65725567"
---
# <a name="ceiling-ssis-expression"></a>CEILING (SSIS-Ausdruck)

[!INCLUDE[ssis-appliesto](../../includes/ssis-appliesto-ssvrpluslinux-asdb-asdw-xxx.md)]


  Gibt die kleinste ganze Zahl zurück, die größer oder gleich einem numerischen Ausdruck ist.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
CEILING(numeric_expression)  
```  
  
## <a name="arguments"></a>Argumente  
 *numeric_expression*  
 Ein gültiger numerischer Ausdruck.  
  
## <a name="result-types"></a>Ergebnistypen  
 Der Datentyp des numerischen Ausdrucks, der an die Funktion übergeben wird.  
  
## <a name="remarks"></a>Remarks  
 CEILING gibt ein NULL-Ergebnis zurück, wenn das Argument NULL ist.  
  
## <a name="expression-examples"></a>Beispiele für Ausdrücke  
 In diesen Beispielen wird die CEILING-Funktion auf positive und negative Werte und auf Null angewendet.  
  
```  
CEILING(123.74)  
```  
  
 Gibt 124,00 zurück.  
  
```  
CEILING(-124.27)  
```  
  
 Gibt -124.00 zurück.  
  
```  
CEILING(0.00)  
```  
  
 Gibt 0.00 zurück.  
  
## <a name="see-also"></a>Weitere Informationen  
 [FLOOR &#40;SSIS-Ausdruck&#41;](../../integration-services/expressions/floor-ssis-expression.md)   
 [Funktionen &#40;SSIS-Ausdruck&#41;](../../integration-services/expressions/functions-ssis-expression.md)  
  
  
