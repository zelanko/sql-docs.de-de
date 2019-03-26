---
title: ISNULL (SSIS-Ausdruck) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/04/2017
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- null values [Integration Services]
- ISNULL function
ms.assetid: 88dbf49e-1307-4dda-b9db-ff1632053550
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: f7cdee630de0a3827dd2a9b2ad4a1353efb2ff2d
ms.sourcegitcommit: 7ccb8f28eafd79a1bddd523f71fe8b61c7634349
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/20/2019
ms.locfileid: "58279704"
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
 [Funktionen &#40;SSIS-Ausdruck&#41;](../../integration-services/expressions/functions-ssis-expression.md)   
 [COALESCE &#40;Transact-SQL&#41;](../../t-sql/language-elements/coalesce-transact-sql.md)  
  
  
