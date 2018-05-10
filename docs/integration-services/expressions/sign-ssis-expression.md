---
title: SIGN (SSIS-Ausdruck) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: integration-services
ms.component: expressions
ms.reviewer: ''
ms.suite: sql
ms.technology:
- integration-services
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- positive values [Integration Services]
- SIGN function
- negative values
ms.assetid: 1547db08-4329-4781-91c2-36898ed71b15
caps.latest.revision: 32
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 8ab30748b50df8cbb176c5fa1bdb6c11f0b2b132
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/03/2018
---
# <a name="sign-ssis-expression"></a>SIGN (SSIS-Ausdruck)
  Gibt das positive (+1) oder negative (-1) Vorzeichen oder Null (0) für einen numerischen Ausdruck zurück.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
SIGN(numeric_expression)  
```  
  
## <a name="arguments"></a>Argumente  
 *numeric_expression*  
 Ein gültiger numerischer Ausdruck mit Vorzeichen. Weitere Informationen finden Sie unter [Integration Services Datentypen](../../integration-services/data-flow/integration-services-data-types.md).  
  
## <a name="result-types"></a>Ergebnistypen  
 DT_I4  
  
## <a name="remarks"></a>Remarks  
 SIGN gibt ein NULL-Ergebnis zurück, wenn das Argument NULL ist.  
  
## <a name="expression-examples"></a>Beispiele für Ausdrücke  
 In diesem Beispiel wird das Vorzeichen eines numerischen Literals zurückgegeben. Als Ergebnis wird -1 zurückgegeben.  
  
```  
SIGN(-123.45)  
```  
  
 In diesem Beispiel wird das Vorzeichen aus der Subtraktion der **StandardCost** -Spalte von der **DealerPrice** -Spalte zurückgegeben.  
  
```  
SIGN(DealerPrice - StandardCost)  
```  
  
## <a name="see-also"></a>Weitere Informationen finden Sie unter  
 [Funktionen &#40;SSIS-Ausdruck&#41;](../../integration-services/expressions/functions-ssis-expression.md)  
  
  
