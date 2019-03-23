---
title: RTRIM (SSIS-Ausdruck) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- RTRIM function
- trailing blanks
ms.assetid: 529bd43e-3f8a-4682-a33e-569176aa7fc4
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: 53d9bfbb7418a3bc6727ccc7160a5364bac39f58
ms.sourcegitcommit: 5a8678bf85f65be590676745a7fe4fcbcc47e83d
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/22/2019
ms.locfileid: "58374190"
---
# <a name="rtrim-ssis-expression"></a>RSCHNEIDEN (SSIS-Ausdruck)
  Gibt einen Zeichenausdruck zurück, nachdem nachfolgende Leerzeichen entfernt wurden.  
  
> [!NOTE]  
>  Mit RTRIM werden keine Pseudoleerzeichen entfernt, wie z. B. Tabulatoren oder Zeilenvorschubzeichen. Unicode stellt Codeelemente für viele verschiedene Arten von Leerzeichen bereit, diese Funktion erkennt jedoch nur das Unicode-Codeelement 0x0020. DBCS-Zeichenfolgen, die in Unicode konvertiert werden, enthalten u. U. andere Leerzeichen als 0x0020. Diese Leerzeichen können von der Funktion nicht entfernt werden. Zum Entfernen aller Arten von Leerzeichen können Sie die RTrim-Methode von Microsoft Visual Basic .NET in einem Skript verwenden, das aus der Skriptkomponente ausgeführt wird.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
RTRIM(character expression)  
```  
  
## <a name="arguments"></a>Argumente  
 *character_expression*  
 Ein Zeichenausdruck, aus dem Leerzeichen entfernt werden sollen.  
  
## <a name="result-types"></a>Ergebnistypen  
 DT_WSTR  
  
## <a name="remarks"></a>Hinweise  
 RTRIM kann nur mit dem DT_WSTR-Datentyp verwendet werden. Ein *character_expression* -Argument, das ein Zeichenfolgenliteral oder eine Datenspalte mit dem DT_STR-Datentyp ist, wird implizit in den DT_WSTR-Datentyp umgewandelt, bevor RTRIM ausgeführt wird. Andere Datentypen müssen explizit in den DT_WSTR-Datentyp umgewandelt werden. Weitere Informationen finden Sie unter [Integration Services-Datentypen](../data-flow/integration-services-data-types.md) und [CAST &#40;SSIS-Ausdruck&#41;](cast-ssis-expression.md).  
  
 RTRIM gibt ein NULL-Ergebnis zurück, wenn das Argument NULL ist.  
  
## <a name="expression-examples"></a>Beispiele für Ausdrücke  
 In diesem Beispiel werden nachfolgende Leerzeichen aus einem Zeichenfolgenliteral entfernt. Als Ergebnis wird "Hello" zurückgegeben.  
  
```  
RTRIM("Hello   ")  
```  
  
 In diesem Beispiel werden nachfolgende Leerzeichen aus einer Verkettung der Spalten **FirstName** und **LastName** entfernt.  
  
```  
RTRIM(FirstName + " " + LastName)  
```  
  
 In diesem Beispiel werden nachfolgende Leerzeichen aus der **FirstName** -Variablen entfernt.  
  
```  
RTRIM(@FirstName)  
```  
  
## <a name="see-also"></a>Siehe auch  
 [LTRIM &#40;SSIS-Ausdruck&#41;](trim-ssis-expression.md)   
 [TRIM &#40;SSIS-Ausdruck&#41;](trim-ssis-expression.md)   
 [Funktionen &#40;SSIS-Ausdruck&#41;](functions-ssis-expression.md)  
  
  
