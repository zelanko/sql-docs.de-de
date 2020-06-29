---
title: ISNULL (SSIS-Ausdruck) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- null values [Integration Services]
- ISNULL function
ms.assetid: 88dbf49e-1307-4dda-b9db-ff1632053550
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 51eda21b5c9b85c5f9cfd613d0d92df9729fe620
ms.sourcegitcommit: 34278310b3e005d008cd2106a7b86fc6e736f661
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/26/2020
ms.locfileid: "85428467"
---
# <a name="isnull-ssis-expression"></a>ISNULL (SSIS-Ausdruck)
  Gibt abhängig davon, ob ein Ausdruck NULL ist, ein boolesches Ergebnis zurück.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
ISNULL(expression)  
```  
  
## <a name="arguments"></a>Argumente  
 *expression*  
 Ein gültiger Ausdruck eines beliebigen Datentyps.  
  
## <a name="result-types"></a>Ergebnistypen  
 DT_BOOL  
  
## <a name="expression-examples"></a>Beispiele für Ausdrücke  
 In diesem Beispiel wird TRUE zurückgegeben, falls die **DiscontinuedDate** -Spalte einen NULL-Wert enthält.  
  
```  
ISNULL(DiscontinuedDate)  
```  
  
 In diesem Beispiel wird "Unknown last name" zurückgegeben, falls der Wert in der **LastName** -Spalte NULL ist. Andernfalls wird der Wert in der **LastName**-Spalte zurückgegeben.  
  
```  
ISNULL(LastName)? "Unknown last name":LastName  
```  
  
 In diesem Beispiel wird immer TRUE zurückgegeben, falls die **DaysToManufacture** -Spalte NULL ist, unabhängig vom Wert der **AddDays**-Variablen.  
  
```  
ISNULL(DaysToManufacture + @AddDays)  
```  
  
## <a name="see-also"></a>Weitere Informationen  
 [Funktionen &#40;SSIS-Ausdruck&#41;](functions-ssis-expression.md)   
 [COALESCE &#40;Transact-SQL&#41;](/sql/t-sql/language-elements/coalesce-transact-sql)  
  
  
