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
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 15392de2f7a77edd0a4f43f2edc1346a52cd1a5e
ms.sourcegitcommit: c8e1553ff3fdf295e8dc6ce30d1c454d6fde8088
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/22/2020
ms.locfileid: "86914546"
---
# <a name="isnull-ssis-expression"></a>ISNULL (SSIS-Ausdruck)

[!INCLUDE[sqlserver-ssis](../../includes/applies-to-version/sqlserver-ssis.md)]


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
  
  
